---
title: "I need make bigger my disk space in ubuntu (installed with wubi). Can i do it?"
date: 2008-04-29
forum: General Help
---

### Post by shotokan on 2008-04-29
I was install ubuntu with wubi, but, i have a little disk (80 Gb.) and i need space for my games in windows, so, i did it giving just 10 Gb. to Ubuntu, but, Hardy Heron need 5 Gb. and now, with all my linux programs i have just 3 Gb. free, I NEED MORE SPACE, I WON'T DELETE AND REINSTALL MY UBUNTU BECAUSE MY UBUNTU IS FULLY CUSTOMIZED, IS HARD CUSTOMIZE AGAIN, AND, I HAVE NO IDEA ABOUT HOW CAN I MAKE BIGGER MY SPACE IN UBUNTU. PLEASE HELP. bye.

---

### Post by ago on 2008-04-29
[https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c)

You may want to increase the /usr disk, since it looks like you installed lots of apps. In which case replace "home" with "usr" in the above recipe.

---

### Post by owoito on 2008-04-29
I have the same question and will really appreciate any explanation from someone. My Wubi has 8GB of disk space in the window compartment, and i would like to expand it to 14GB without having to reinstall Wubi all over again. Does anyone know how to go about doing this?
Thanks.

---

### Post by ohCanada on 2008-04-30
I have the same question...installed via Wubi to 4GB inside vista home basic. Is it really enough to raise the volume for one file set or is it possible to raise the total available size of the virtual partition that wubi creates at install?? Im just unwilling to follow those command since I dont really understand what they are changing...
Any advice would be much appreciated. 
Pax

---

### Post by owoito on 2008-04-30
Please can someone help us out on how to expand the disk space in Wubi without having to go through so much complex command?
Any help regarding this issue will be highly appreciated.
Thanks.

---

### Post by ago on 2008-04-30
Don't the instructions in the link above work?

---

### Post by owoito on 2008-04-30
Thanks Ago for your help.I think that the command lines are complex and my fear is that i might end up messing up the entire OS. If you know of something less intimidating, kindly post it here.
Thanks

---

### Post by ago on 2008-04-30
Not at this stage, the above commands can basically be packed into a script but I haven't much time at the moment for that (I first need to make sure that any remaining issue is dealt with by point release). Once LVPM will support 8.04 that can be used too.

---

### Post by ohCanada on 2008-05-01
@Ago: Thanks a lot for your quick responses and help. I am happy with the coding, My only concern is how Vista is going to respond to the change in the apparent Ubuntu virtual partition if I use this method. I know vista has problems if you use non-vista software to re-size partitions and am worried it will have the same problem with accepting resized virtual partitions. 

Has anyone done this successfully on a Vista machine without running into problems.

Thanks in advance

---

### Post by ago on 2008-05-01
The procedure in [https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c](https://wiki.ubuntu.com/WubiGuide#head-c1b3095de0e43733f9336427bb90d7ef322de99c) does not change any partition, it creates an EXTRA virtual disk and moves part of the filesystem there. Hence should be fairly roubust. If things go wrong you can always revert the changes (do not delete the backup folder until you know its working)

---

### Post by vuvanquang on 2008-09-16
Hi guru,
Are there any way to increase the space of Ubuntu more than 10Gb since the installation? I don't mind if I reinstall my new Ubuntu but It seems that Wubi does not allow Ubuntu 8.04 to have a choice of more than 10Gb (am I wrong?). Any idea will help, thanks a lot.
vuvanquang

---

### Post by Orlsend on 2008-09-16
Actually you can do up to 30 gigs I think.

---

### Post by ago on 2008-09-16
Yes it is 30GB on ntfs (on fat file sizes cannot be larger than 4G) provided of course you have enough free disk space. 30GB is ok for most installations. Particularly since you can save data also to the ntfs partition (/host). If you need more than that, you should seriously consider a full installation to a dedicated partition (and hence I am not going to increase the 30GB limit).

---

