---
title: "[Urgent] How do I completely remove Xubuntu 12.04 and keep windows"
date: 2012-11-06
forum: General Help
---

### Post by JoshuaMiller0 on 2012-11-06
Hi. I love Ubuntu and I love xubuntu more, I dislike a lot of things about windows and I am not leaving Ubuntu.


[COLOR=Red][U][B][SIZE=4]This paragraph has a lot of random ramblings of not a lot but my personal issues with the computer.[/SIZE]
[/B][SIZE=3][COLOR=DarkRed]*Conclusion of paragraph: I have a dual boot **Xubuntu 12.04/Windows 7 Enterprise (or something)** and I need to remove Xubuntu and hopefully leave the partitions the same as they originally were with one main partition for windows*.[/COLOR][/SIZE][/U][/COLOR]
Instead my problem is that I love xubuntu too much and I decided to install it on my school computer. This was actually very easy with no BIOS security and I successfully have a dual-boot Xubuntu 12.04/Windows 7 Enterprise (or something). I was never caught and a got a lot more done on xubuntu (plus no internet blocking when at home >:D) My problem now is removing it as the laptop took damage and I need to take it in for repairs. When taken in for repairs the school will "re-image" the hard drive to the school's default computer settings and everything on Windows 7. Last time this happened I had Ubuntu 11.10 installed and I handed it anyway, nothing was mentioned and my computer was reset. This time however I do not want to risk it. I may get in trouble for having it installed and worse still it could interfere with the "re-imaging". So all I need is xubuntu uninstalled, simple, right? I have spent ages googling and searching on here to no conclusion and I have no idea on what to do. So I decided to ask the experts myself, here I am.

So all I need is the simplist way to completely remove xubuntu, or at least to the point it is not noticeable that is it on there when you boot up the computer and use "My Computer" to check the size of the hard drive. So basically removing the grub screen and shrinking the partition to not much would do the trick, as "re-imaging" seems to remake all partitions. Oh and I have no administrative powers on my windows part, so not much can be done there, I think. I also have plenty of 4gb+ USBs hanging around if I need to install GParted or something.

I have backed all my data up and I care nothing for my settings etc. Please only reply if you are asking for essential information or if you have the answer very clear and step, by step. Last time I tried this (when I tried to remove Ubuntu last time and failed) some people posted some useless things and I got no answer and no-one further replied and the post has been endlessly lost.

Bad replies include:
[LIST]
[*]"Use GParted", How do I install it? Where do I download it? etc.
[*]Advice like "leave it on there"
[*]"Just remove the grub screen" I am an ubuntu noob, please don't tell me to do things, because I won't know how.
[*]"Use wubi" I have no administrative access, it won't work.
[*]"put the windows 7 install dvd", Who the hell has these? And I need windows to stay unchanged such as still not being admin and having all the server settings and all that stuff.
[*]"In which case I doubt if you were authorised to install Ubuntu.  Looking  at this another way... would you be happy for someone else to install a  new OS on *your* PC without your permission?

I suggest you confess all to your IT department and ask them to repair Windows as discussed." I am not always a good person, I will lie and hide such things and I won't go confessing to those evil IT guys any time soon... Also, I want no advice for my real life things, I just want to fix the problem myself (with your help of course)
[/LIST]
Well... if you read all of that, congratulations, you now know me and my lack of staying to the point (like now).


Please, please, please help this problem is is very urgent and I just need to get it done ASAP. I will keep bumping this post as necessary, although I'm not convinced it will do any good.

---

### Post by Elfy on 2012-11-06
Assuming you can still boot windows as far as I know there is an option to create system repair disc which you can use to repair the boot - then grub is removed, you can then resize the disk in windows to get back the space you used for Xubuntu.

But frankly if you installed on a machine you shouldn't have then ... 

> I will keep bumping this post as necessaryNot more than once in 24 hours please.

---

### Post by vandorjw on 2012-11-06
gparted is found here:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Download the ISO, much like you did Ubuntu, and run the live CD.

However, when you installed Xununtu, it installed boot-loaded called grub as well, where you can choose to boot between windows and Xuntuntu. Removing the Xununtu will remove the boot loader, and you will no longer be able to boot into windows as well.

If you are too stubborn to learn how grub works, then no one here will help you. **You cannot remove Xununtu AFAIK, and still boot windows, without a windows recovery CD.**
EDIT:[COLOR="Red"]I was wrong. All that needs to be done is follow BCBC's instructions latter in this thread.[/COLOR]


Also, re-imaging doesn't care what was on the computer previously.
**"Hidding Xununtu is easy"**

open a terminal and type

```

sudo gedit /etc/default/grub

```

OR, if gedit is not installed
```

sudo leafpad /etc/default/grub

```
Set grub_default to 1, and grub_timeout to 0. This will imediately launch the 2nd entry in grub without waiting.
What I suggest, first change the default, then update grub, and once you are sure the default boot entry is windows, then change the timeout to 0.

GRUB_DEFAULT=1
GRUB_TIMEOUT=0

Once you have changed the config setting, save it,

then run

```

sudo update-grub

```

restart the computer.
After "hidding" xubuntu, a smart IT guy will still notice a lack of HHD space. Not much YOU can do about that.

As well, for windows admin power, there is a LOT that can be done.
Trinity Rescue Kit. I am not going to teach you how to use it, because you were never meant to have Admin priviledges on your computer. Read the documentation yourself if you care enough.

---

### Post by bcbc on 2012-11-07
Boot an Ubuntu CD/USB, select "Try Ubuntu"...

Install a windows style bootloader:
1. connect to the internet
2. go to a terminal (Ctrl+Alt+T):
```
sudo apt-get update 
sudo apt-get install lilo
```You'll get some big warning screen which you can ignore. Tab to OK and hit enter. 
Now install the windows style bootloader:
```
sudo lilo -M /dev/sda mbr
```Reboot, make sure it boots straight into Windows.
Then boot back from the live CD/USB. Run GParted (it's on the live CD). Delete the Ubuntu partition(s). Expand the Windows partition to take up the free space.

You're done.

---

### Post by stinkeye on 2012-11-07
This application run from a live CD/usb should do it for you.
[**_[COLOR="DarkRed"]OS-Uninstaller[/COLOR]_**]("https://help.ubuntu.com/community/OS-Uninstaller")

---

### Post by JoshuaMiller0 on 2012-11-08
> **Elfy said:**
> Assuming you can still boot windows as far as I know there is an option to create system repair disc which you can use to repair the boot - then grub is removed, you can then resize the disk in windows to get back the space you used for Xubuntu.

 
I believe you need [COLOR=black][FONT=Tahoma]a[/FONT][/COLOR][COLOR=black][FONT=Tahoma]dministrative permissions to do this[/FONT][/COLOR]
[COLOR=black][FONT=Tahoma][/FONT][/COLOR] 
> **vandorjw said:**
> 
If you are too stubborn to learn how grub works...**"Hidding Xununtu is easy"**

 
I am happy to learn how grub works, I am happy with hiding xubuntu only.
 
> **vandorjw said:**
>  
open a terminal and type
 
```

sudo gedit /etc/default/grub

```
 
Set grub_default to 1, and grub_timeout to 0. This will imediately launch the 2nd entry in grub without waiting.
What I suggest, first change the default, then update grub, and once you are sure the default boot entry is windows, then change the timeout to 0.
 
GRUB_DEFAULT=1
GRUB_TIMEOUT=0
 
Once you have changed the config setting, save it,
 
then run
 
```

sudo update-grub

```
 
restart the computer.

 
Thank you so much for answering with something that actually helps. I tried this but ran into a few problems.
 
First of all in "GRUB_DEFAULT" is number '0' the first option, '1' the second etc.?
 
I set "GRUB_TIMEOUT" to 0 and that worked fine, but I set "GRUB_DEFAULT" to 6 (because with other things that came with the xubuntu installation like memory test, other ubuntu versions and recovery modes come before windows, sitting at the bottom in 6th place) and when I restarted the computer it immediatlely booted up xubuntu and I tried again setting the timeout to 3 and it still had the first option selected as xubuntu.
 
Also, not that it matter much, but as a note to other xubuntu users using this, instead of the code he said, use this one as xubuntu by default has leafpad and not gedit:
 
```

sudo leafpad /etc/default/grub

```
 
So basically just replace gedit with leafpad.
 
[SIZE=1]*Sorry for some lack of spelling in this, but I have posted this using windows and it only had the dreaded _internet explorer_ on it. I really like spell checkers on firefox and crome.*[/SIZE]

---

### Post by pqwoerituytrueiwoq on 2012-11-08
> **bcbc said:**
> Boot an Ubuntu CD/USB, select "Try Ubuntu"...

Install a windows style bootloader:
1. connect to the internet
2. go to a terminal (Ctrl+Alt+T):
```
sudo apt-get update 
sudo apt-get install lilo
```You'll get some big warning screen which you can ignore. Tab to OK and hit enter. 
Now install the windows style bootloader:
```
sudo lilo -M /dev/sda mbr
```Reboot, make sure it boots straight into Windows.
Then boot back from the live CD/USB. Run GParted (it's on the live CD). Delete the Ubuntu partition(s). Expand the Windows partition to take up the free space.

You're done.
That is all i had to do O.O the once or twice i had to do that i used a windows install disk and went into its recovery mode and ran fixboot/fixmbr then deleted the partition and resized windows to fill

---

### Post by richtathamjr on 2012-11-08
Easiest way to do this is to make a garted boot CD.  Just download the gparted Live CD ISO and burn it to disc.


[LIST=1]
[*]boot off gparted live CD and start gparted (the gnome partition editor).
[*]delete the partition containing the Xubuntu you want to get rid of.
[*]reboot and your Xubuntu is gone.
[/LIST]
you may want to resize the windows partition to use the space previously taken up by xubuntu.  To do this (after doing 1,2,3 above):

[LIST=1]
[*]boot off gparted live CD and start gparted.
[*]select the windows partition
[*]resize the partition to take up remaining space on the drive.
[/LIST]
You'll need to fix grub.  Do this by following other peoples answers to your question here in the forum, OR (my preference):

[LIST=1]
[*]download and burn a Boot Repair disc from [http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[*]boot off this CD and it will doo alol the work automagically for you.
[/LIST]

---

### Post by vandorjw on 2012-11-09
BCBC has the best answer. I never used lilo before and therefore didn't even consider it.

@JoshuaMiller0:

yes, in grub, grub_default 0 means the first option.
grub_default 1 is the second option
grub_default 2 is the third and so forth.

my suggestion was to keep changing the default until you have the right number and it boots straight into windows.

(remeber that after you change the number to run)

sudo update-grub

for changes to take effect.

But, what BCBC wrote is even better, as my method just hides xubuntu, while his completely erases it.

---

### Post by JoshuaMiller0 on 2012-11-11
> **vandorjw said:**
> BCBC has the best answer. I never used lilo before and therefore didn't even consider it.
 
@JoshuaMiller0:
 
yes, in grub, grub_default 0 means the first option.
grub_default 1 is the second option
grub_default 2 is the third and so forth.
 
my suggestion was to keep changing the default until you have the right number and it boots straight into windows.
 
(remeber that after you change the number to run)
 
sudo update-grub
 
for changes to take effect.
 
But, what BCBC wrote is even better, as my method just hides xubuntu, while his completely erases it.
 
Hiding it is fine, your way is easier, I will however save bcbc's answer elsewhere as this may come in handy, but I will use yours

---

