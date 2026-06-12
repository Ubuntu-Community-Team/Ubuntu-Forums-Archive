---
title: "Do not have permission to acces /dev/video0 16.04 cli"
date: 2019-07-20
forum: General Help
---

### Post by adrian-h on 2019-07-20
I am using an old 32 bit box with ubuntu 16.04 server installed to basically play and try to understand linux better and to lean to use a few aplications when I can.

I was trying to use ffmpeg as in:

```
ffmpeg -f v4l2 -s 544x288 -i /dev/video0 -framerate 30 -vcodec libx264 -f mpegts ~/video2.ts
``` but when I try to run this I get an error of 
Cannot open video device /dev/video0: Permission denied

running as sudo works OK.

I installed several packages such as ffmpeg and others manually, but always with sudo apt install, in case that makes any difference?

The user is localuser how do I resolve this, I am assuming it is a groups problem,  On another PC with Opensuse I can go in to a gui screen to add groups to a user but in Linux command line I am a bit lost.

Just had a thought and did a ls -al /dev/video0 and the result was:
localuser@ubuntu:~$ ls -al /dev/video0
crw-rw---- 1 root video 81, 0 Jul 20 22:15 /dev/video0

I guess I could change the permissions but as soon as the camera is unplugged it will disapear and probably come back with the same issue as before when plugged back in.
So anyone have a clue to the correct fix?

Adrian

---

### Post by sisco311 on 2019-07-20
Just add your user to the video group. There are many ways to do this. I prefer the gpasswd command:
```
sudo gpasswd -a $USER video
```

The $USER variable should expand to the currently logged in user, but you can replace it with the actual username you want to add to the group.

You will have to log out and log back in in order the changes to take effect.

---

### Post by adrian-h on 2019-07-20
Well thank you for your quick response, that has solved the issue for me.
Another quick question how do I list what groups the user has and what would you normally expect to be in the list?

Many thanks again for the fix.

Adrian

---

### Post by adrian-h on 2019-07-20
Duh, just typed in groups and I got the following

localuser adm cdrom sudo dip video plugdev lxd lpadmin sambashare

Is there anything else one thinks I should normally be in?

Adrian

---

