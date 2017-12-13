# Objectdetectionapi --> pigface  train and detection
此练习项目是为了猪脸识别，进行的构建数据集，以及模型训练。
因文件数量很多，故按目录压缩了下。使用方法如下。

本项目是在tf的ObjectDetectionAPI基础上进行了修改。能独立运行，不依赖tf的models。

1、把所有压缩包解压后拷贝到统一的object_detection目录。
   注意,Annotations.zip,ImageSets,JPEGImages.7z.001-JPEGImages.7z.001
        需要放到object_detection目录的子目录pigfaces\VOC2007下。

2、需要从tf官网下载faster_rcnn_resnet101_voc07的预训练模型文件。
   解压后放到model目录下。

3、为生成tfrecord文件，再运行如下命令：
cd 到xxx\object_detection目录下。
python create_pascal_tf_record.py --data_dir=xxxx\object_detection\pigfaces --year=VOC2007 --set=train --output_path=data\pig_train.record

	注意：--data_dir的是绝对路径名
	      --output_path是相对目录，且要带有文件名 XXXX.record

4、之后为开始训练，运行如下命令：
cd 到xxx\objectdetection\object_detection目录下。
python train.py --train_dir=data --pipeline_config_path=models\faster_rcnn_resnet101_voc07.config
