---
title: "Thumb drive permission changes and moving files"
date: 2023-10-06
forum: General Help
---

### Post by sofasurfer on 2023-10-06
I have used this command for a couple of years. ```
  cd Downloads; for f in *.mp3 ;do mv "$f" /media/daryl/"Clip Sport"/Podcasts 
 
```
Suddenly now my permissions have changed, probably because I never bother to "eject" before removing drive from USB port. ```
 mv: failed to access '/media/daryl/Clip Sport/Podcasts': Permission denied
[1]+  Exit 1                  rm "$f"
mv: failed to access '/media/daryl/Clip Sport/Podcasts': Permission denied
  
```
I am aware that I can fix this problem by reformatting the drive. My question is...I can not move the files by using the above command, but, I CAN move the files be using drag n drop. Why is this?
Also, I changed my permissions using "$ sudo nautilus" but I still have the problem. Why?

---

### Post by sofasurfer on 2023-10-06
I went ahead and reformatted the mp3 player and the problem is still there...but I found the solution...just not the cause of the problem.
I noticed that although the left panel of my file browser shows "clip sport" and "16 gb volume" ( the memory card which I am not using), when I hover the mouse over the "clip sport" it shows as  . So I changed my command to read "clip sport1" instead of "clip sport". 
Why is it saying "clip sport1"?

---

### Post by yancek on 2023-10-07
>  Why is it saying "clip sport1"? 				

That often happens when > because I never bother to "eject" before removing drive from USB port

The first instance was mounted when you inserted again and it added the 1.  This is one likely possibility.

---

