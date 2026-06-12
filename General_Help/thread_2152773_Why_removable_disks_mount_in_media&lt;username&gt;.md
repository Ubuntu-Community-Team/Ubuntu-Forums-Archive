---
title: "Why removable disks mount in /media/&lt;username&gt;, not /media?"
date: 2013-06-09
forum: General Help
---

### Post by epikvision on 2013-06-09
After encountering this [bug report]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/1068277"), I learned that since 12.10, Ubuntu changed the behavior of removable media devices.  Instead of mounting in the /media directory, they actually mount in the /media/<username> directory (e.g. home/john/JOHN).  Why did Ubuntu opt for this change?

---

### Post by HiImTye on 2013-06-09
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
[http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location](http://askubuntu.com/questions/214646/how-to-configure-the-default-automount-location)

---

### Post by epikvision on 2013-06-09
Awesome, but are there any specific reasons for and benefits from it?

---

### Post by 3rdalbum on 2013-06-09
A quick search didn't yield an answer of the rationale, but it might be something to do with multiple users. For instance, it's possible to set up a network that has one server that runs all programs for all users. The thin clients are virtually just displays, keyboards and mice. You can even have it set up so that the users can plug in a USB flash drive on their thin client, and the programs running on the server can access the flash drives.

In order to make this easier or more practical, mounting these into /media/<username>/ would make more sense than just dumping the USB drives for 30 users into /media. Most people leave the default disk label for their flash drive, and I can see problems if two or more users plug in USB drives with the label "Kingston" or "Datatraveller" or something like that.

---

### Post by Morbius1 on 2013-06-09
> Why did Ubuntu opt for this change?                 
Can't blame Ubuntu on this one. This comes from RedHat.

It certainly makes things a whole lot better for the home user. Consider the following scenario: You have an external ext4 formatted usb "drive". You want to share that with everyone on your Windows/Linux/OSX home network. You've done this before without issues.

***Old Way:*** You create a Samba share allowing guest access and to accommodate that you change permissions of /media/LABEL to 777. Everything works.

***New Way:*** You create a Samba share allowing guest access and to accommodate that you change permissions of /media/$USER/LABEL to 777. It doesn't work.

Why? Take a look at the permissions of /media/$USER:
```
ls -dl /media/$USER
```
What you will get is something like this:
> drwxr-x---+ 2 root root 4096 Jun  8 08:39 /media/morbius
Looks like only root's going to access anything mounted under /media/$USER until you see that little "+" at the end - that's an Access Control List designation. So let's look at the ACL's for this directory:
```
getfacl -t /media/$USER
```
Only root and morbius are going to be able to get access to anything beyond that folder.

There are ways to work around this "design decision" of course but if you're new to this you will probably post a question on a forum somewhere. That will force them to understand or at least be introduced to the concepts of Linux permissions, ACL's, and Samba. The developers have taken something simple and made it more complex. It's a win-win for everyone.

---

### Post by epikvision on 2013-06-09
Alright.  Thanks for the helpful replies!

---

### Post by ardian923 on 2014-05-02
I have many symbolic link created with previous /media/<external hardisk label> :(
Those links doesnt work anymore. Is there a way to return the way ubuntu 14.04 automounted like 12.04?



<Edit>
Found this :
[http://askubuntu.com/questions/451503/14-04-not-auto-mounting-external-drives-since-upgrading-from-12-04](http://askubuntu.com/questions/451503/14-04-not-auto-mounting-external-drives-since-upgrading-from-12-04)

---

