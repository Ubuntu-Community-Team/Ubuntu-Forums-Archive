---
title: "Got a question about a strange file name on my desktop"
date: 2006-11-19
forum: General Help
---

### Post by cjax1 on 2006-11-19
Hi everyone.

Before I ask my question I just want to say I realy love Ubuntu even though I got realy realy ticked about something after installing 6.06 and said I would never come back. The main thing was my wireless didn't work in 6.06 because they decided to install some bcm43xx driver. I may have been able to make it work but I got stuck on one thing right at the begining. I came accross a  this comand, ```
echo 'blacklist bcm43xx' | sudo tee -a
```

See that vertical slash, how the h*** do you type that in the comand line? I've tried but never figured it out. Nothing I could see in the terminal menus. I thought maybe it was just a seperator. Didn't know at the time I could just copy and paste it. People on the forums need to realize that we are not all comand line gurus out here. (In my case just assume I'm stupid) And why would I want to use bcm43xx if it only supports up to 11Mbs? Since that time I have tried a few other distros, one was Mepis. Come to find out it's based on Ubuntu. But they got something right unlike Ubuntu. It came preinstalled with ndiswrapper and the driver for my broadcom card (bcmwl5). Right after installing Mepis I did ndiswrapper -l in terminal and it said hardware present, driver present. They also had drivers installed for several other cards. I still had to blacklist bcm43xx if I remember right. Figured out how to do that by opening the file in terminal and entering it manually. So maybe they got it right in the newest Ubuntu release but I don't know yet, I'm still using 6.06. I'm half afraid to change things again. The last experience left a bad taste in my mouth.

So after getting that off my chest for the last time (sorry for the ranting) I humbly come here to ask a new question. Something happened to one of my icons file name on the desktop. The one that used to say sda2 (my fat32 backup partition) now has a bunch of weird square symbols. (screenshot below) I think this happened after the latest update I got yesterday but not sure. I haven't changed or installed anything new. And naturally for some stupid reason it will not allow me to rename it. I still can open it though.

Anyone know what's up with this. It hasn't broken anything so I don't feel this is realy important but if this can happen what's next? My home folder will be called %*#@!$%& tomorrow? I can't find anything in anyone's posts.

Thanks for putting up with me. I plan to stick with Ubuntu (and screw MS if you know what I mean).

Screenshot,

[http://i65.photobucket.com/albums/h222/puddlejumper-photos/Screenshot.png](http://i65.photobucket.com/albums/h222/puddlejumper-photos/Screenshot.png)

Edit, I tried using html tags for the image, I tried using using bb code. No luck when I hit Preview post so I just copied and pasted the link.

Sorry about the large picture size to download. Next time I'll make it smaller.

Thanks anyone.
Have a great day.

---

### Post by seanUSXIII on 2006-11-19
The | character is on the same key as the \ character under the backspace key. Press Shift+\ to get it

---

### Post by doobit on 2006-11-19
> **cjax1 said:**
> Hi everyone.

ranting) I humbly come here to ask a new question. Something happened to one of my icons file name on the desktop. The one that used to say sda2 (my fat32 backup partition) now has a bunch of weird square symbols. (screenshot below) I think this happened after the latest update I got yesterday but not sure. I haven't changed or installed anything new. And naturally for some stupid reason it will not allow me to rename it. I still can open it though.

Anyone know what's up with this. It hasn't broken anything so I don't feel this is realy important but if this can happen what's next? My home folder will be called %*#@!$%& tomorrow? I can't find anything in anyone's posts.

Thanks for putting up with me. 

FYI the | symbol is a pipe and it just sends the first command output to the next one. For example, the command ls lists all of the visible files in a directory. the command ls | list.txt will send the list of files to a text file called list.txt so you can open it with a text editor or word processor.  You don't need to be a command line guru, but there are a few simple things that you should learn that can really help you find your way around, and feel more comfortable. You can get a good idea of some of them from sites like [www.linuxcommand.org](www.linuxcommand.org) and others. Google is a linux based search engine, and they love linux, so they have a whole search engine section dedicated to linux. [http://www.google.com/linux](http://www.google.com/linux)

I think the problem with your desktop link is that you no longer have the font installed that the link used to use. You should be able to just rename the link. That may have happened because you downloaded a desktop or Xorg change, and a font's name was changed, for example.

---

### Post by cjax1 on 2006-11-19
OK thank you both. Now I understand what "|" means. Another question. Why is just the one link changed and not sda1 and sda6 icons if a font got uninstalled? Shouldn't that have changed all of them?

Another screenshot with file browser open.

[http://i65.photobucket.com/albums/h222/puddlejumper-photos/Ubuntu/Screenshot-1.jpg](http://i65.photobucket.com/albums/h222/puddlejumper-photos/Ubuntu/Screenshot-1.jpg)

Also I try to rename it and a window pops up saying The item could not be renamed. It has to be a command right? I tried Googleing it. By the way I've used Google/linux before. That other link looks really usefull. Thanks. I'm going to read it all. But right now I cannot find out how to rename the link to the volume. That's one thing I don't see right now. I just would like to rename it back to sda2 or even whatever I may want to. I never downloaded a desktop or made an Xorg change. Unless that last update did but I cannot remember what it was now. Is there a way to view the update history or even roll back my system to before the update was downloaded and installed just to see if that's what caused this? I mean I do not want things to be renamed on my system without my knowledge. I want to know who or what is doing this. Maybe it's just a bug. :-k Maybe I should get some bug spray. 

Many thanks for your help.

---

### Post by taurus on 2006-11-19
Maybe it's time to have a look at your /etc/fstab!

```
cat /etc/fstab
```

---

### Post by cjax1 on 2006-11-19
OK taurus here it is. I don't know what it's telling me.

Oh yeah, I thought the icon was formerly called sda2 but it was sda4, my fat32 partition or my E drive partition in Windows. OK I can't remember everything.

```
chris@ubuntu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
/dev/sda4       /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1/dev/sda6       /media/sda6     ext3    defaults        0       2
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
chris@ubuntu-desktop:~$
```

What does this tell you? Is there anything wrong here?

---

### Post by cjax1 on 2006-11-20
Hi again,

I just noticed something else strange. I went to Places - Computer - Filesystem - media and checked the properties on the sda4 folder. The date says it was modified in 1969. I looked at the other screenshots and noticed the same thing. I checked the properties on the sda1 and sda6 folders and they have the proper dates in 2006. When I open the sda4 folder and look at the Location bar it is named those weird symbols, not sda4 like it should be.

Screenshot:
[http://i65.photobucket.com/albums/h222/puddlejumper-photos/Screenshot-1.png](http://i65.photobucket.com/albums/h222/puddlejumper-photos/Screenshot-1.png)

Is this a serious bug or something else? Should I even worry about it? After all I can still access the partition and do things like normal. I googled some stuff about renaming a volume and found one site but I was totaly lost. I'm thinking all I need to do is rename the volume. But now I'm not sure if that is the problem.

:-?

---

### Post by cjax1 on 2006-11-22
Ok never mind. I'm happy to report that the name has changed back to the original name on its own, sda4. It may have had something to do with the last set of updates yesterday. But who knows. I do not think so. The name didn't change right away. I was just going to say that my wireless card no longer activates at boot time. I thought it may be another clue. Well whatever. The file name is back to the original but I have to modprobe ndiswrapper each time I boot. I searched for the file that is supposed to contain the modprobe ndiswrapper command but can't find it. Isn't it supposed to be in the etc directory? Maybe it's just gone. I did a file search and nothing. Nothing surprises me. I have to modprobe ndiswrapper each time I friggin boot.

Gotta love Ubuntu. :)

---

