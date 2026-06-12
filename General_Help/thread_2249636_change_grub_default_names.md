---
title: "change grub default names"
date: 2014-10-23
forum: General Help
---

### Post by Louis_Levene on 2014-10-23
hello everyone! i just recently created a custom version of ubuntu with some of my favorite apps installed using remastersys, however when it installs in a dual-boot grub calls it "ubuntu" is there anyway i could change what grub calls it by default?
thanks!

---

### Post by deadflowr on 2014-10-23
Make a custom grub
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Then name each system whatever you want.

---

### Post by ajgreeny on 2014-10-23
It is much easier, I think, to edit the part of the line shown in red between the quotes or backticks, or whatever they are, in /etc/default/grub that says
```
GRUB_DISTRIBUTOR=[COLOR=#ff0000]`lsb_release -i -s 2> /dev/null || echo Debian`[/COLOR]
```
 to read with whatever you want in the grub menu, but change the backticks to normal double quotation marks.

As an example I have edited the file in my OS to read```
GRUB_DISTRIBUTOR="Xubuntu-12.04-amd64 Precise"
```so **Xubuntu-12.04-amd64 Precise** is exactly what shows in my grub menu.

It was very handy in the past when I had 5 different versions of the *ubuntu family on my machine, and without these changes they all showed as Ubuntu; most unhelpful!

---

### Post by Louis_Levene on 2014-10-23
alright ill give both these a try and see what i get thanks a bunch! :D

---

### Post by Louis_Levene on 2014-10-25
i tried both of these and changing /etc/default/grub and then remastering and installing caused a fatel error and the other one looks like it is for people with the operating system already installed. What i meant was how do get grub to call the new operating system something other than "ubuntu".... for example if i were to install Lubuntu grub calls it lubuntu by default instead of ubuntu

---

### Post by ajgreeny on 2014-10-25
I do not understand why the edit of /etc/default/grub that I suggested should cause any problems; it is what I have been doing for a long time on just about every machine that I have and it has never, ever presented any problem to my system.  What do you mean by "remastering and installing"?

Can you show me exactly what you edited the file to; it may give some clues.

Just a thought; did you run ```
sudo update grub
``` after the file edit?

Just as an experiment, edit the file again, run sudo update-grub, then use the command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-85
```to show us what your grub.cfg file and therefore the grub menu will show.

I do not know of any way you can make the changes prior to installing an OS; I believe it is only possible once you've installed an OS, and incidentally if you have many OSs on one machine you need to edit the /etc/default/grub files and run sudo update-grub on all of them including your main OS that manages grub, even if you have not edited the file in that OS.

---

### Post by Louis_Levene on 2014-10-26
ok ill give this a try.. also what i mean by "remastering" is that i edit the file and then i use remastersys to create the iso file and then when i boot into the iso using a live usb and install a get a fatal error about grub

---

### Post by yancek on 2014-10-26
Post the fatal error you get when you try to boot the remastered iso, might help.

---

### Post by ajgreeny on 2014-10-26
I know little to.nothing about remastersys so can not help with that. However I still think.it is easiest to just edit the /etc/default/grub files of the OSs after installing.

---

### Post by Louis_Levene on 2014-10-26
i know it would be easier for me to just do it after installing, but i want grub to say the correct operating system when it installs so that it would be more convinient for the actual user...

---

### Post by Dennis N on 2014-10-26
This may be what you are looking for - How to change the "distribution name" provided on the iso. See this:

[http://askubuntu.com/questions/83521/where-do-i-need-to-change-ubuntu-when-naming-my-own-custom-distribution](http://askubuntu.com/questions/83521/where-do-i-need-to-change-ubuntu-when-naming-my-own-custom-distribution)

The solution given uses isomaster (in the Ubuntu repos).

---

### Post by Louis_Levene on 2014-10-31
sorry fore l8 reply ive been busy but ill give this a try it looks like its gonna work so ill tell you what happens! :D

---

### Post by Louis_Levene on 2014-11-02
ok so i tried this and it worked and now grub calls it what i want however now when i open the software and updates app  it says it has experienced an internal error and the software center app just dosent open, i know it has something to do with the lsb-release file becuase when i change that back to defaults the apps work, any ideas? thanks

---

### Post by Louis_Levene on 2014-11-04
everything is working fine now except for the software center still because it is refereing to the lsb-release file to open and dosent recognize the os name so wont open... any help PLEASE

---

### Post by Louis_Levene on 2014-11-11
ok ive got everything working now thanks for all the help

---

