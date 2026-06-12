---
title: "Help with ffmpeg"
date: 2006-11-24
forum: General Help
---

### Post by DAaaMan64 on 2006-11-24
Alright I want to run this command:

ffmpeg -i *.flv -y *.avi


Which works fine, however I am looking to loop through all the flvs in a folder so I try this:

for i in `ls *flv`;do ffmpeg -y `echo $i | sed s/.flv/.avi/` $i; done;

But I am getting 'incorrect parameters'.  What I am doing wrong?  I am very new to bash scripting.  Thank you :)

---

