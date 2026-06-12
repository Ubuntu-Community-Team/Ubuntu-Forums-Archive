---
title: "Dual use 'home' with Ubuntu and Suse"
date: 2006-07-13
forum: General Help
---

### Post by xenomorph99 on 2006-07-13
Hi,

I have my Ubuntu root and home 'dirs' on seperate partitions currently. Let's say, for example, that I wanted to install Suse 10.1 in addition to Ubuntu (root on another partition) but wanted Suse and Ubuntu to 'share' the same home dir after multibooting. 

Is this going to work? Will installing Suse trash the home dir already there and/or will switching between the two on a regular basis cause any problems?

Ta,
Xeno

---

### Post by grte on 2006-07-13
It will work in that your files will be easily read from both.  However, you may run into some issues with configuration files for different programs which are stored in your home directory.  Even that shouldn't be too much of an issue.

---

### Post by Ramses de Norre on 2006-07-13
I think it could cause major problems when application versions differ between the two distros. Many apps have config files in your home directory (in hidden folders) and sometimes a newer version has changes in the way config files are interpreted. So when for example ubuntu uses a more recent version of a certain program with an updated config file structure this app will give many errors and will probably crash in suse (which uses the older config interpretation). I don't know whether there are much version differences between ubuntu and suse packages but it wouldn't surprise me..
The best way to access files from both distros would be symlinking I think.. symlink the suse home dir to some folder in the ubuntu one and vice versa.

---

### Post by schilcha on 2006-07-13
Also, take care of user- and group-ids, so you don't run into permission-related problems. e.g. if your SuSE account has an UID=501, make sure that your ubuntu-account has UID=501 as well. This must be checked for all UIDs and GIDs that occur in your home.

---

### Post by xenomorph99 on 2006-07-13
Crikey...sounds like it may be more trouble than it is worth especially as I am quite inexperienced in Linux.

I just wanted to try Suse out to see how it compared performance-wise with Ubuntu. Maybe I'll gain more time by simply leaving Ubuntu alone? ;)

Ta,
Xeno

---

### Post by Jasper Houtman on 2006-07-13
How about a swap partition? can you share that with 2 distro's?

---

### Post by Ramses de Norre on 2006-07-13
Yes, no problem with that (it is erased completely every reboot).

---

### Post by Jasper Houtman on 2006-07-13
Thanks! I'm planning to try edgy on a seperate partition as soon as it becomes more stable, this will save me some hard drive space :)

---

### Post by panurge77 on 2006-07-13
> **xenomorph99 said:**
> 
I just wanted to try Suse out to see how it compared performance-wise with Ubuntu. Maybe I'll gain more time by simply leaving Ubuntu alone? ;)
I used Suse until I tried Ubuntu some months ago and wow, Ubuntu is a performance champ. Suse install tons of things you'll probably never ever know what they are. And it uses older versions of xorg and gnome etc., so if it'sd performance you want and if you're new to linux, I think you could happily stay with Ubuntu, because it's fast and apt-get makes your life easy. I was always annoyed by suses package management.

---

### Post by xenomorph99 on 2006-07-14
That's weird because I did install Suse 10.0 on an old (700MHz) machine I had and it seemed to work a little better than Ubuntu did, hence my wanting to try it on my AMD2400 machine.

I know Suse comes with a lot of cobblers that I'd never use which I agree is a bad point. On the plus side, I think the desktop looks a little more professional in Suse.

---

### Post by Lord Illidan on 2006-07-14
If you were mentioning Ubuntu and Debian, or Ubuntu and Mepis, I don't think there would have been any probs with the home partition. But SUSE and Ubuntu are very different animals, particularly with config files and stuff.. Blame novell or Canonical for that.

In terms of polish, I prefer Dapper. Suse got on my nerves after 1 day or two.

---

