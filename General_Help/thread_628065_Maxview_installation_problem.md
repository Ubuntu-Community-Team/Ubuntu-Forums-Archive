---
title: "Maxview installation problem"
date: 2007-11-30
forum: General Help
---

### Post by malibusurfer2 on 2007-11-30
I am trying to install Maxview as an alternative to Paperport for document scanning and viewing.
I downloaded the file maxview0.5-bin.tar.gz into folder /home/corer/Temp.
I then opened a Terminal window and ran
sudo aptitude install build-essential
tar xvzf maxview0.5-bin.tar.gz
cd maxview
All of the above commands seemed to work fine.

ls shows only 1 file: maxview.

./configure gives "No such file or directory"

What am I missing?

The instructions say after ./configure, make, and then sudo make install.


corer@corer:~/Temp$ tar xvzf maxview0.5-bin.tar.gz
maxview0.5-bin/
maxview0.5-bin/maxview
corer@corer:~/Temp$ cd maxview
corer@corer:~/Temp/maxview$ ./configure
bash: ./configure: No such file or directory
corer@corer:~/Temp/maxview$ ls
maxview

---

### Post by perspectoff on 2008-04-11
Make sure you have libqt3-mt package installed (e.g. through Synaptic Package Manager) first.

---

