---
title: "Setting up Samba in 14.04"
date: 2015-01-31
forum: General Help
---

### Post by christian53 on 2015-01-31
Hello! I have been using Xubuntu 14.04 for about 6 months now and everything worked just fine. A few days ago i had a system-update done and since then my Samba does not work the same way as before. Explain: have one ofe these little android TV-sticks attached to our TV  and video streaming worked perfectly. I looked for the file I wanted to watch with my browser, clicked on it and voilá - there it opened and my wife and I could see the video. Since the last xubuntu update I can "see" the files, but every attempt to watch a video is commented with something like "Can't open this file". I tried to copy the file to my TV-stick, but it starts and after about a half second it stops without comment. So searching on internet I came to this thread and read it more than once, since I am not so familiar with "programming",  BUT I could find out reading the smb.conf and comparing it with what I read after doing testparm, that in samba.conf there are missing a couple of lines:

[series]
    path = /home/c/Downloads/series  
    read only = No
    guest ok = Yes

while in testparm [global] i cannot find the following line which is in samba.conf 

passdb backend = tdbsam


I have configured Samba with it&#347; graphical tool. Now, I really wonder where testparm gets these lines from, since they are not in samba.conf. 

I would really appreciate anybodys help

Thank you so much in advance :-)

---

