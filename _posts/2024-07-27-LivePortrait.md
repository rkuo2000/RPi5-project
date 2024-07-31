---
layout: post
title:  LivePortrait
author: rkuo
categories: [ Jekyll, tutorial ]
image: assets/images/liveportrait_showcase.gif?raw=true
featured: true
hidden: false
---
LivePortrait 讓靜態人物照片具有生動表情 

---
### [論文首頁](https://liveportrait.github.io)
**Paper:** [LivePortrait: Efficient Portrait Animation with Stitching and Retargeting Control](https://arxiv.org/pdf/2407.03168)<br>

Pipeline of the first stage: base model training.<br>
![](https://liveportrait.github.io/src/img/pipeline_first_stage.jpg)
Pipeline of the second stage: stitching and retargeting modules training.<br>
![](https://liveportrait.github.io/src/img/pipeline_second_stage.jpg)

---
### [Github](https://github.com/KwaiVGI/LivePortrait)
1) 安裝與複製程式碼<br>
`sudo apt install ffmpeg`<br>

```
git clone https://github.com/KwaiVGI/LivePortrait
cd LivePortrait

# create env using conda
conda create -n LivePortrait 
conda activate LivePortrait

# install dependencies
pip install -r requirements.txt
```

2) 下載預訓練模型<br>
```
# first, ensure git-lfs is installed, see: https://docs.github.com/en/repositories/working-with-files/managing-large-files/installing-git-large-file-storage
git lfs install
# clone and move the weights
git clone https://huggingface.co/KwaiVGI/LivePortrait temp_pretrained_weights
mv temp_pretrained_weights/* pretrained_weights/
rm -rf temp_pretrained_weights
```

3) 執行<br>
* 輸入來源是照片（512x512 大頭照）, 驅動短片是d0.mp4 (頭像與語音）
```
python inference.py -s assets/examples/source/s9.jpg -d assets/examples/driving/d0.mp4
```

* 輸入來源是影片, 驅動短片是d0.mp4 (頭像與語音）
```
python inference.py -s assets/examples/source/s13.mp4 -d assets/examples/driving/d0.mp4
```

---
### 應用平台
`python app.py`<br>
![](https://github.com/rkuo2000/GenAI-projects/blob/master/assets/images/liveportrait_app.png?raw=true)

`http://127.0.0.1:8890`<br>
![](https://github.com/rkuo2000/GenAI-projects/blob/master/assets/images/liveportrait_app_webui.png?raw=true)

---
### 展示影片
<iframe width="315" height="560" src="https://www.youtube.com/embed/HYllSDxbKkI" title="LivePortrait s7--d20" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<iframe width="315" height="560" src="https://www.youtube.com/embed/sVAxE-0tIpI" title="Hedra 深夜情歌" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

<iframe width="698" height="393" src="https://www.youtube.com/embed/wBO0VsiWC2s" title="LivePortrait ~ Kai Trump" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

