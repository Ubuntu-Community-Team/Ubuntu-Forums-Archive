---
title: "Error -1 mounting bluray .iso in Linux?"
date: 2019-06-17
forum: General Help
---

### Post by kdantas on 2019-06-17
[COLOR=#1A1A1B][FONT=&quot]What´s wrong with my command line? I created the "iso" folder in /media.. I always got this error --> mount: /media/iso: mount failed: Unknown error -1[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]root@mx7367723:/home/kdantas/rtorrent/download/[A.Long.And.Lasting.Love]("https://www.youtube.com/redirect?redir_token=DZMnk-clSiM3TV3PHRlWS_4Ei5N8MTU2MDkwNzM5N0AxNTYwODIwOTk3&q=http%3A%2F%2Fa.long.and.lasting.love%2F&stzid=Ugwar3fBEVy-MYFya2x4AaABAg&event=comments").Vivian.Chow.Live.2018.Blu-ray.1080p.AVC.DTS-HD.MA.5.1# ls[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]A LONG AND LASTING LOVE D1.iso[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]A LONG AND LASTING LOVE D2.iso[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]root@mx7367723:/home/kdantas/rtorrent/download/[A.Long.And.Lasting.Love]("https://www.youtube.com/redirect?redir_token=DZMnk-clSiM3TV3PHRlWS_4Ei5N8MTU2MDkwNzM5N0AxNTYwODIwOTk3&q=http%3A%2F%2Fa.long.and.lasting.love%2F&stzid=Ugwar3fBEVy-MYFya2x4AaABAg&event=comments").Vivian.Chow.Live.2018.Blu-ray.1080p.AVC.DTS-HD.MA.5.1# sudo mount -o loop -t udf A\ LONG\ AND\ LASTING\ LOVE\ D1.iso /media/iso[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&quot]mount: /media/iso: mount failed: Unknown error -1

OBS: My OS is the Ubuntu 16.04 LTS (GNU/Linux 4.5.2-armada375 armv7l)[/FONT][/COLOR]

---

### Post by dino99 on 2019-06-18
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by yancek on 2019-06-18
You haven't posted the command you used to create the iso so how would anyone answer?  Have you tried without specifying the fs type?  Unusual to have a file with so many spaces in the name.  Have you tried mounting it with quotes around the name?  Is this a music CD/DVD?

---

### Post by kdantas on 2019-06-18
> **yancek said:**
> You haven't posted the command you used to create the iso so how would anyone answer?  Have you tried without specifying the fs type?  Unusual to have a file with so many spaces in the name.  Have you tried mounting it with quotes around the name?  Is this a music CD/DVD?

Hi @yancek, the ISO file of a VIDEO MUSIC BLURAY was downloaded from a private tracker. I didn´t created it, but I want to mount it for get the .M2TS files. And yes, I tried mounting it with quotes and without specifyng the fs type, as you can see below, but I got the same error.

[EMAIL="kdantas@mx7367723:~/rtorrent/download/A.Long.And.Lasting.Love.Vivian.Chow.Live.2018.Blu-ray.1080p.AVC.DTS-HD.MA"]kdantas@mx7367723:~/rtorrent/download/A.Long.And.Lasting.Love.Vivian.Chow.Live.2018.Blu-ray.1080p.AVC.DTS-HD.MA[/EMAIL].5.1$ sudo mount -o loop "A LONG AND LASTING LOVE D1.iso" /media/iso
mount: /media/iso: mount failed: Unknown error -1

I watched this tutorial: [https://www.youtube.com/watch?v=vh6OJesThjc](https://www.youtube.com/watch?v=vh6OJesThjc)

---

