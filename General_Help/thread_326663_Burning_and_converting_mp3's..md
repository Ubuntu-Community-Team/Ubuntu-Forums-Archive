---
title: "Burning and converting mp3's."
date: 2006-12-28
forum: General Help
---

### Post by Inevitable on 2006-12-28
Im new to linux and i need a program to burn audio to cds to play on my cd player. they download as mp3 and mp3 doesnt play on my cd player. so i need a program that converts them from mp3 to other file types.  i have k3b and serpentine and gnomebaker and they dont work for me so i need another suggestion.. any help is good thanks :)

---

### Post by iamhugeinjapan on 2006-12-28
You can use k3b to do it if you install libk3b2-mp3

```
sudo aptitude install libk3b2-mp3
```

This will let you select mp3s to burn as CD audio tracks.

---

### Post by Inevitable on 2006-12-28
Hello it burnt but it did not work on my cd player becasue  i need to to burn .mp3 and .ogg into .wav

---

### Post by iamhugeinjapan on 2006-12-28
If you choose to make an Audio CD and import mp3s they will be burnt as WAV files. Did you choose to do a Data disc instead?

---

### Post by Inevitable on 2006-12-28
well how do i check if i burnt to mp3:( :confused:

---

### Post by iamhugeinjapan on 2006-12-28
Open the CD with a computer and see if there are mp3 files on it. If you can see mp3 files, you burnt it as a data disc. Try again as an audio disc.

---

### Post by mcduck on 2006-12-28
gnomebaker can burn mp3-files into audio CD's, you just need to have Gstreamer0.8-plugins installed.

---

### Post by Inevitable on 2006-12-28
iamhugeinjapan i tryed your sulution :)  but when i put the cd in the drive it comes up with sound juices but if i click on the audio disk in nautilus it says  ```
cdda://dev/hdb is  not a valid location
``` so im trying the gnome baker option now

---

