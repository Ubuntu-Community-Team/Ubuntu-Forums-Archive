---
title: "how to build my own linux from ubuntu"
date: 2006-09-26
forum: General Help
---

### Post by vilto on 2006-09-26
i was wonderring how do i make my own linux distro using any existing linux distro.....i mean like nubuntu.....which is based on ubuntu but have different wallpaper,different boot screen saying nubuntu instead of ubuntu, have reduced packages,some other aditional packages like security tools,and things like that.....;)

i mean how to change all these things.....add aditional packages,remove some unwanted packages.....change wallpaper....change boot image...etc..............
 
plz help me:cool:

---

### Post by kidders on 2006-09-26
Hi there,

All you seem to want to do is play around cosmetically with your Linux ... Ubuntu is happy to let you remove packages, or change any of the graphics. Actually making your own distro involves making far more fundamental alterations, the first of which is typically patching/rebuilding your kernel to your own specifications.

How to make the kinds of superficial changes you mention depends on things like what graphical environment you're using, and what bootloader you have. Have a play around with the features of each :-)

---

### Post by vilto on 2006-09-27
thanx...... but how do i modify the packages inside the iso files........i want to do it before installation......:(

---

### Post by kidders on 2006-09-27
It is my sincere hope that doing that would break the installer! I'd hate to think someone could alter a file in a Ubuntu installation without being detected!!

Are you trying to create a "branded" Ubuntu install for use on your network, perhaps?

---

### Post by slimdog360 on 2006-09-27
[http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1]("http://reconstructor.aperantis.com/index.php?option=com_frontpage&Itemid=1")
reconstructor

there is also something called ubuntu customisation kit, here is the link but it wasnt working when I tried it just now. Maybe its down for a short period of time?
[http://uck.sourceforge.net/]("http://uck.sourceforge.net/")

---

### Post by vilto on 2006-09-28
i will try them......
ihave a doubt.....

like if i want to install xgl using reconstructor....i have to make some changes in some files ......can i do it by using this????

how do i change the ubuntu logo?

---

### Post by kidders on 2006-09-29
Removing all the Ubuntu branding may not be completely legal. You should review Ubuntu's documentation before proceeding.

---

### Post by vilto on 2006-09-30
ye i understood thanx kidders...

but i have a problem after customizing using reconstructor......

1)some of the icons are not visible like homefolder,terminal caluculator,etc.....
2)when i tried to login as root it says somthing like
   unable to lookup live cd via gethostbyname()
3)login error saying 
   Could not load icon

   Details: Failed to open file         '/usr/share/icons/OSX/scalable/apps/evolution.png': Permission denied

other than this everything looks fine

to note i have changed the live cd user name and password .....did this created the problem??

here is the screenshot
[[IMG]http://img89.imageshack.us/img89/6889/vijpf6.th.jpg[/IMG]](http://img89.imageshack.us/my.php?image=vijpf6.jpg)

---

