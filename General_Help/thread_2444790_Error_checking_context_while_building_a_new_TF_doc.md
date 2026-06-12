---
title: "Error checking context while building a new TF docker image"
date: 2020-06-04
forum: General Help
---

### Post by py-ohayo on 2020-06-04
Hello,


 Here is what happens when I try to build new TF image:
 pavel@ALABAMA:~$ docker image build -t tensorflow_as:latest .
error checking context: 'can't stat '/home/pavel/.cache/dconf''.

Here is my **Dockerfile**
pavel@ALABAMA:~$ more Dockerfile
FROM tensorflow/tensorflow:latest-gpu
RUN apt-get install -y libsm6 libxext6 libxrender-dev && pip install scikit-learn opencv-python imutils
 Any suggestions/comments ?


 Thanks.

---

