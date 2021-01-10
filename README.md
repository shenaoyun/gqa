# gqa
## 环境配置
### 1.安装Python 3（建议使用Anaconda：https : //www.continuum.io/downloads）
### 2.安装PyTorch：pip install torch torchvision
### 3.安装一些其他的依赖包（NumPy，HDF5，YAM）：pip install numpy h5py pyyaml
### 4.下载此存储库或使用Git进行克隆，然后输入存储库的根目录：git clone https://github.com/shenaoyun/gqa.git && cd lcgn
## 下载GQA数据集
### 从https://cs.stanford.edu/people/dorarad/gqa/下载GQA数据集，并将其符号链接到exp_gqa/gqa_dataset。
## GQA数据集训练步骤（注意切换到文件目录下）
### 1.将此存储库的根目录添加到PYTHONPATH中： export PYTHONPATH=.:$PYTHONPATH
### 2.训练空间特征：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_spatial.yaml train True
### 3.训练物体特征：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_objects.yaml train True
### 4.训练具有“完美视野”的对象名称和属性：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_scene_graph.yaml train True
## 在GQA上测试
### 1.将此存储库的根目录添加到PYTHONPATH中： export PYTHONPATH=.:$PYTHONPATH
### 2.使用空间特征进行测试:
#### 2.1在val_balanced拆分上进行本地测试：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_spatial.yaml TEST.SPLIT_VQA val_balanced
#### 2.2在testdev_balanced拆分上进行本地测试：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_spatial.yaml TEST.SPLIT_VQA testdev_balanced
#### 2.3在submission_allEvalAI上生成提交文件：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_spatial.yaml TEST.SPLIT_VQA submission_all TEST.DUMP_PRED True
### 3.测试对象功能
#### 3.1在val_balanced拆分上进行本地测试：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_objects.yaml TEST.SPLIT_VQA val_balanced
#### 3.2在testdev_balanced拆分上进行本地测试：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_objects.yaml TEST.SPLIT_VQA testdev_balanced
#### 3.3在submission_allEvalAI上生成提交文件（显示的精度将为零；这需要很长时间）：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_objects.yaml TEST.SPLIT_VQA submission_all TEST.DUMP_PRED True
### 4.使用“完美视野”对象名称和属性进行测试：
#### 4.1在val_balanced拆分上进行本地测试：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_scene_graph.yaml TEST.SPLIT_VQA val_balanced
#### 4.2在本地测试testdev_balanced：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_scene_graph.yaml TEST.SPLIT_VQA testdev_balanced
#### 4.3产生对提交文件submission_all进行EvalAI：python exp_gqa/main.py --cfg exp_gqa/cfgs/lcgn_scene_graph.yaml TEST.SPLIT_VQA submission_all TEST.DUMP_PRED True
