---
title: "mv problems"
date: 2006-10-09
forum: General Help
---

### Post by starwarsfan982 on 2006-10-09
Hi, I was looking for a gui solution for encoding video, and this one seems really nice. Only one problem, it doesn't work. When i run this from the terminal, it pops up. I select to encode in AVI from a vob file i got using vobcopy. I output to a directory naming it whatever.avi When I click encode, a terminal pops up and then closes. When i check the Terminal I ran it from, i get the this error:

mv: invalid option -- r
Try `mv --help' for more information.

Anyone know how to fix this? Thankyou

---

### Post by Jussi Kukkonen on 2006-10-09
Did you forget a link to the script you are using or something? There's not enough info to help you...

---

### Post by starwarsfan982 on 2006-10-09
Well vive is a frontend for ffmpeg, vobcopy and cpdvd. I hope this helps

---

### Post by Jussi Kukkonen on 2006-10-10
Well, without seeing the script the only thing I can say is that somewhere there the script calls *mv* with wrong options... One would fix this by looking at that part of the script and fixing the options.

---

### Post by Bigbluecat on 2006-10-10
I have used VLC to transcode video files before (admittedly in windows) and it works very well.

---

### Post by mssever on 2006-10-10
It seems that the majority of video editing software for Linux is buggy, but I've been using avidemux without problems.

---

### Post by starwarsfan982 on 2006-10-10
Okay I got the script. Help me linux experts! I uploaded the file at [http://www.vx7000world.com/vive.txt](http://www.vx7000world.com/vive.txt) If it's not too much trouble then could some one patch the file and reupload it here? Thankyou!

---

### Post by mssever on 2006-10-10
Your error message complained about an invalid option for the mv (move/rename) command. Open up your file and do a search for mv. correct the command. You can find a list of valid options for mv by typing "man mv".

Hint: as the error message said, -r isn't a valid option, so it needs to be deleted. You may or may not want to add in other options.

I'm not simply fixing this because fixing it yourself will help you in the future.

---

