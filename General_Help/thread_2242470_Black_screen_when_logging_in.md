---
title: "Black screen when logging in"
date: 2014-09-02
forum: General Help
---

### Post by 1ktmeadows on 2014-09-02
I have been using Ubuntu 14.04 for a little bit but I'm still new to  Ubuntu. My computer runs Window 8 and Ubuntu 14.04. Recently I have not  been able to do anything on my laptop because when I login with my  password all I get is a black screen; and that's it. I have tried:

```

$ sudo apt-get install gnome
$ sudo reboot

```

That did not work, and I tried:

```

sudo apt-get install ubuntu-session

sudo apt-get install --reinstall ubuntu-session
```

That also did not work. So I'm not sure what to do now. Can someone please help me.
Thank You

---

### Post by claracc on 2014-09-02
Could you please give as your hardware specifications?, also it is important to know the graphics card.

In the past could you access your ubuntu 14.04 system or you never could?, what way did you install 14.04, fresh or upgrading?, have you run any update?.

Perhaps you have to add the nomodeset option to your grub file. Please see: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) for specificic how to instructions.

---

### Post by 1ktmeadows on 2014-09-02
The laptop that I have is a Samsung np470rse-k01ub with 6GB of RAM and 750 of hard drive space. The video card is Intel® HD Graphics 4000. I installed Ubuntu 12.10 with dual boot right when I got the computer. I have partitioned the hard drive with 25 GB for the Ubuntu side of the operating system and the rest is on windows 8. About a few month's ago a few months ago, I upgraded the computer to 14.10 and everything went well. Recently for some reason after I did a little update my computer has not been the same on the Ubuntu side. 
Thank you for responding back and helping me I really appreciate it alot.

---

### Post by claracc on 2014-09-02
> **1ktmeadows said:**
> The laptop that I have is a Samsung np470rse-k01ub with 6GB of RAM and 750 of hard drive space. The video card is Intel® HD Graphics 4000. I installed Ubuntu 12.10 with dual boot right when I got the computer. I have partitioned the hard drive with 25 GB for the Ubuntu side of the operating system and the rest is on windows 8. About a few month's ago a few months ago, I upgraded the computer to 14.10 and everything went well. Recently for some reason after I did a little update my computer has not been the same on the Ubuntu side. 
Thank you for responding back and helping me I really appreciate it alot.

I supose you mean 14.04, isn't it?. Have you update or install othe graphics driver?

In principle, it seems there is not any problem between your graphics card and ubuntu 14.04.

I would try two things, first to use the default recommended driver for your graphics card, please see [http://askubuntu.com/questions/465402/how-to-install-intel-hd-4000-ubuntu-14-04](http://askubuntu.com/questions/465402/how-to-install-intel-hd-4000-ubuntu-14-04) to see how. 

Second, try to use the nomodeset option as it is recommended in the previously given link

---

### Post by 1ktmeadows on 2014-09-02
Yes I meant 14.04 and I have not update my graphics drivers. I was just doing a little Ubuntu update for the computer and then my computer has not been the same. At first when I tried to login all I would get is background screen of Ubuntu 14.04 and nothing else would load. So then I decide to do these steps:
$ sudo apt-get install gnome
$ sudo reboot That did not work, and I tried:

 	Code:

 	sudo apt-get install ubuntu-session

sudo apt-get install --reinstall ubuntu-session After trying these steps I just get a black screen when I login. I will try what you said above and see what that does. 
Thank You again.

---

### Post by 1ktmeadows on 2014-09-04
Thank you again for the help. I'm not able to use this link see: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)  because I can not get anywhere after I login. I just get a black screen and nothing else. I tried: [SIZE=4]How to temporarily set kernel boot options on an installed OS (not wubi)[/SIZE].  I was not able to get anywhere because the first skip did not work. I might be doing it wrong but I held down the shift key after the bios logo and then I did it before the bios logo; nothing happened. Was there something that I did wrong or I'm I not understanding the first step? 
Then I tried:[SIZE=4] How to permanently set kernel boot options on an installed OS (not wubi)
[/SIZE]Alt + F2 did not open up the terminal for so I did Ctrl + Alt +F2 and then I was able to get to the terminal. I logged in with username and password and then I typed: 
gksudo gedit /etc/default/grub

but I got something saying "Gtk-WARNING **: cannot open display ". I'm not sure what that means but it does not go with the skips 
to continue on. I'm not sure what I'm doing wrong, any advice PLEASE. Lastly would it be easier to reinstall Ubuntu 12.10 and 
then upgrade to 14.04? 

Thank You

---

### Post by 1ktmeadows on 2014-09-04
I have been trying to fix my computer and I have a lot of different strategies from: 
 	Code:
 	$ sudo apt-get install gnome
$ sudo reboot 
That did not work, and I tried:

 	Code:
 	sudo apt-get install ubuntu-session

sudo apt-get install --reinstall ubuntu-session

[FONT=arial][/FONT]

Then I tried: [SIZE=4]
How to temporarily set kernel boot options on an installed OS (not wubi)[/SIZE].  I was not able to get anywhere with doing nomodeset. I just got a black screen again after login.

Then I tried:[SIZE=4] How to permanently set kernel boot options on an installed OS (not wubi)
[/SIZE]Alt + F2 did not open up the terminal for so I did Ctrl + Alt +F2  and then I was able to get to the terminal. I logged in with my username  and password and then I typed: 
gksudo gedit /etc/default/grub

but I got something saying "Gtk-WARNING **: cannot open display ". I'm  not sure what that means but it does not go with the skips 
to continue on. I'm not sure what I'm doing wrong, any advice PLEASE. Lastly would it be easier to reinstall Ubuntu 12.10 and 
then upgrade to 14.04?

Thank You

---

### Post by grahammechanical on 2014-09-04
> [COLOR=#000000]Lastly would it be easier to reinstall Ubuntu 12.10 and [/COLOR][COLOR=#000000]then upgrade to 14.04?[/COLOR]

That would not be easy at all. 

1) We cannot upgrade from 12.10 to 14.04 unless we first upgrade to 13.04 and then 13.10 and then 14.04. 

2) Ubuntu 12.10 and 13.04 and 13.10 have all reached end of life and are no longer supported. The software repositories are now closed and have been moved to a new location. This wiki page will describe the principles of upgrading from and through versions of Ubuntu that are no longer supported.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

> [COLOR=#000000]"Gtk-WARNING **: cannot open display "[/COLOR]

That kind of error message is normal when we run an application that uses a GUI (Graphical User Interface) from the terminal.

You tell us what you did that does not work but you do not tell us what was wrong in the first place.

Nor do you tell us the hardware specifications of your machine and whether it has another operating system on it.

Sometimes, re-installing is a good and easy, in fact, simple way of fixing problems. I have done it myself.

What you have done does not make sense. This command

[COLOR=#000000]```
gksudo gedit /etc/default/grub
```

[/COLOR]would open Gedit with administrator privileges and allow you to edit one of the Grub configuration files. Why would you want to do that? Why are you trying to edit the grub configuration files? If you can get to a login screen, then Grub has already done its job and shut down. 

The same thing applies to the use of nomodeset as a boot parameter. If you are getting to a login screen then Ubuntu is well past the need for the use of nomodeset as a boot parameter.

If after login in you get a blank screen it could be a problem with the proprietary video driver. At the Grub menu try loading Recovery Mode. You may find it in the Advanced Option sub-menu. Then at the Recovery menu select Resume. That will try to load Ubuntu using an open source video driver. If that works go to Additional Drivers and try another video driver. Try the open source video driver.

Regards.

---

### Post by sandyd on 2014-09-05
threads merged

---

### Post by 1ktmeadows on 2014-09-05
Thank you for responding back this is my computer specs:I have is a Samsung np470rse-k01ub with 6GB of RAM and 750 of hard  drive space. The video card is Intel® HD Graphics 4000. I installed  Ubuntu 12.10 with dual boot right when I got the computer. I have  partitioned the hard drive with 25 GB for the Ubuntu side of the  operating system and the rest is on windows 8. About a few month's ago a  few months ago, I upgraded the computer to 14.04 and everything went  well. 

I used those codes above because that was some of the solutions that I found online that might help fix my computer. Sorry if I have been causing a problem but I'm just trying to fix my computer. I tried what you said to do and nothing happened; still a black screen. I have been looking online for different ways that might help fix my computer and the ones that I found has not worked. Lastly, I tried open up Ubuntu from my usb drive and nothing happen.
Thank You

---

### Post by 1ktmeadows on 2014-09-10
A few days ago I have been having issues with my computer and I came to this forum for help and advice. Some has helped me out; which I appreciate. I still  have not been able to get my computer to work and no one has posted any  idea's on how to fix my computer in the last 5 day. I have been  researching and I have not been able to get anywhere. I'm not sure what  to do, so can anybody please give me some advice on what I should do. 
Thank You

---

### Post by kansasnoob on 2014-09-11
It sounds like you can run your old 12.10 live USB, is that right?

If so please post a screenshot of Gparted so I can rule out a disc space problem.

Also post the output of this command using the live USB:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

That will provide some specific graphics chip details that may help me rule out a recent update that broke Optimus graphics drivers.

One thing I haven't seen suggested that you might try while booting your installed Ubuntu is to select advanced options and then try booting an older kernel.

Haven't noticed you say yet, but can you still boot Windows?

BTW if you should choose to reinstall beware of this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by 1ktmeadows on 2014-09-11
Thank you for helping. I can not run my 12.10 live USB, for some reason when I try to go into it just to see if I'm able to reinstall. All I get is a black screen and then it will reboot. I'm able to run windows 8.

---

### Post by kansasnoob on 2014-09-11
OK, you're going to need a working live USB or DVD. Probably just reuse the 13.10 USB since you already have it, and it would be best to have a 14.04.1 live image to work with anyway because 13.10 is EOL.

So in Win 8 first download the image:

[http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/)

Then create the live USB:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Note: I usually use UNetbootin but it doesn't work with Win 8.

---

### Post by kansasnoob on 2014-09-11
BTW I'm subscribed to this thread now, and I'll receive notifications in my mailbox, so one way or another we'll figure something out ;)

---

### Post by 1ktmeadows on 2014-09-11
Thank You, Thank You so much I appreciate it a lot.

---

### Post by 1ktmeadows on 2014-09-20
Sorry for responding back so late, I have been really busy but I'm about to install Ubuntu 14.10 on a Live USB but before I try to do a reinstall. I read that if I reinstall Ubuntu on a Windows 8 computer, that the reinstall will wipe my computer completely. Is that true? If it is true what can I do so that it will not wipe my computer ?

---

### Post by kansasnoob on 2014-09-20
> **1ktmeadows said:**
> Sorry for responding back so late, I have been really busy but I'm about to install Ubuntu 14.10 on a Live USB but before I try to do a reinstall. I read that if I reinstall Ubuntu on a Windows 8 computer, that the reinstall will wipe my computer completely. Is that true? If it is true what can I do so that it will not wipe my computer ?

I hope you mean 14.04.1 and not 14.10. 14.10 is still in development and won't be released until October + the fact that it's only supported for 9 months.

It is true that reinstalling Ubuntu can wipe the whole drive! To provide guidance so you'll be able to avoid that we'll need you to provide some info using the live USB, but give me a little while to review this all.

I still think it may be possible to save the existing Ubuntu installation, although reinstalling may be almost faster. Regardless you'll need that new live USB so once it's created boot it to the [advanced boot menu]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options") and select Check disc for defects. That takes a few minutes to complete but it will verify that the live USB was created properly and has no errors. Then reboot, and this time select Try Ubuntu without installing. 

Then from the live desktop open the terminal and post the full output of the following commands [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") (just copy-n-paste):

```
lsb_release -a
```

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

```
sudo parted -l
```

```
sudo fdisk -lu
```

I'd give you bonus points if you'd include a screenshot of Gparted :D

BTW, I was recently hospitalized when my A-fib turned into V-tach and while I'm now doing just fine my new meds have produced a tremor which has slowed me down greatly. So expect slow replies. Occasionally it's bad enough that I just can't type at all.

---

### Post by kansasnoob on 2014-09-20
In case someone else wants to jump in here keep in mind:

This install began as 12.10 at only 25 GB, it's since been upgraded to 14.04. We need to see the output of the commands above to see if this in fact a simple Intel graphics chip, if so I doubt it's just a graphics issue, but I want to rule out the Optimus scenario since a recent update broke Optimus in 14.04.

The reason I requested a screenshot of Gparted is to rule out a disc/partition space issue. 25 GB is not a huge amount of room for an install that's existed for nearly two years and the meta-package 'gnome' is huge (625 MB). If it's a partition free space issue remember that Windows partitions should be resized using only Windows own partitioning tools.

Quite honestly I'd never install the meta-paclage 'gnome' because it provides a bunch of junk that conflicts with Unity. I can provide a detailed list of just what gets installed if someone wants to play at purging it all if (or) when we get this install to boot.

---

### Post by 1ktmeadows on 2014-09-28
Sorry for getting back so late, just been busy from morning to night this week. Kansasnoob I hope you get better and I just want to say thank you for all of your help; I really appreciate it alot. I made a live usb of Ubuntu 14.04.1 and I was able to get to where I can try Ubuntu without installing and I have screenshots of the commands that you wanted me to type. Also a screenshot of Gparted:
[IMG]Screenshot from 2014-09-28 05_19_39.png[/IMG]

Screenshot of lsb_release -a and lspci -v -s `lspci | awk '/VGA/{print $1}'`:
[IMG]Screenshot from 2014-09-28 05_17_18.png[/IMG]

Screenshot of sudo parted -l:
[IMG]Screenshot from 2014-09-28 05_18_22.png[/IMG]

Screenshot of sudo fdisk -lu:
[IMG]Screenshot from 2014-09-28 05_19_04.png[/IMG]

Lastly did you find any information on how I can reinstall Ubuntu without wiping my hardware completely?
Thank You

---

### Post by kansasnoob on 2014-09-28
> **1ktmeadows said:**
> Sorry for getting back so late, just been busy from morning to night this week. Kansasnoob I hope you get better and I just want to say thank you for all of your help; I really appreciate it alot. I made a live usb of Ubuntu 14.04.1 and I was able to get to where I can try Ubuntu without installing and I have screenshots of the commands that you wanted me to type. Also a screenshot of Gparted:
[IMG]Screenshot from 2014-09-28 05_19_39.png[/IMG]

Screenshot of lsb_release -a and lspci -v -s `lspci | awk '/VGA/{print $1}'`:
[IMG]Screenshot from 2014-09-28 05_17_18.png[/IMG]

Screenshot of sudo parted -l:
[IMG]Screenshot from 2014-09-28 05_18_22.png[/IMG]

Screenshot of sudo fdisk -lu:
[IMG]Screenshot from 2014-09-28 05_19_04.png[/IMG]

Lastly did you find any information on how I can reinstall Ubuntu without wiping my hardware completely?
Thank You

Hi, nothing attached there, but the output of those four commands is easiest for us to read if the full terminal output is just copy-n-pasted using code tags as described here:

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

A screenshot of Gparted would help me rule out a free space issue with the old install and just make it all-around easier to see what exactly we're working with. To attach a screenshot just click on the paperclip at the top of this reply box:

[ATTACH=CONFIG]256772[/ATTACH]

Then a new window will open where you'll want to click on "browse":

[ATTACH=CONFIG]256773[/ATTACH]

After clicking on "browse" yet another window opens where you can navigate to the desired screenshot or picture:

[ATTACH=CONFIG]256774[/ATTACH]

Then just double-click on the proper pic and it'll appear in the previous window (example: car_seat.JPG):

[ATTACH=CONFIG]256775[/ATTACH]

After adding all desired images click on Upload and watch the progress bar at the bottom of that window (waiting for ubuntuforums.org) in this screenshot:

[ATTACH=CONFIG]256776[/ATTACH]

It can sometimes take a little while for the pics to completely upload depending on how busy the server is. Then if you click on the paperclip again you can attach each image individually or attach them all in a string. The only screenshot we really need to see in your case is that of Gparted.

Regarding this:

> did you find any information on how I can reinstall Ubuntu without wiping my hardware completely?

We first need to know if you have anything at all in the old install that you wish to backup and save - documents, pictures, browser profiles, etc. Then the general process will be to select the "Something else" partitioning option and select exactly which partition(s) to reuse something like this:

[http://ubuntuforums.org/showthread.php?t=2242245&page=6&p=13116544#post13116544](http://ubuntuforums.org/showthread.php?t=2242245&page=6&p=13116544#post13116544)

But your device designations will almost certainly be different than those displayed in that post so we'll need to see the output of those commands to know what partitioning scheme we're dealing with.

One thing I'm unsure of is what you'll encounter regarding UEFI mode while installing/reinstalling Ubuntu because I haven't yet installed Ubuntu on that new of hardware. So we may have to ask an additional question regarding that before reinstalling.

---

### Post by 1ktmeadows on 2014-09-28
Thank you, here are the screenshots: 

Screenshot of Gparted:
[ATTACH=CONFIG]256785[/ATTACH]

Screenshot of lsb_release -a and lspci -v -s `lspci | awk '/VGA/{print $1}'`:
[ATTACH=CONFIG]256787[/ATTACH]

Screenshot of sudo parted -l:
[ATTACH=CONFIG]256788[/ATTACH]

Screenshot of sudo fdisk -lu:
[ATTACH=CONFIG]256789[/ATTACH]

---

### Post by kansasnoob on 2014-09-28
I asked ***oldfred*** to help out. I can see that you have a GPT disc which I'm clueless about, and I suspect that it's also UEFI boot instead of BIOS.

The only thing I can see for sure is that Ubuntu's / partition is on /dev/sda8 so that's the partition you want to be sure and reinstall on.

I didn't see anything obvious about why you're getting a black screen at boot.

---

### Post by oldfred on 2014-09-28
It is a UEFI install with gpt partitioning.

See the caution in the link in my signature. Only use something else if you elect to reinstall. And make sure you back up efi partition and all of Windows.

With Intel sometimes other boot parameters than nomodeset are required. And some Intel systems need other parameters also.

The link below by ubfan1 has the parameters you can use if you can get to a grub menu. If you can choose in UEFI menu the ubuntu entry and then use escape to bring up grub if it does not come up.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

If that does not work, use Boot-Repair from live installer and post a link to the report it creates. It will not fix video type issues as those are after grub had loaded. It may add a boot parameter?
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by 1ktmeadows on 2014-09-28
Okay so should I go ahead and reinstall on the /dev/sda8 partition or should we wait to hear from oldfred? Lastly this might sound like a dumb question but just to make sure. If I do the reinstall on the /dev/sda8 partition, that should only wipe the information on just that partition and not the complete hard drive? If it wipes all of the information on the /dev/sda8 partition only then that's fine with me because there was not any important information on it.

---

### Post by kansasnoob on 2014-09-29
> **1ktmeadows said:**
> Okay so should I go ahead and reinstall on the /dev/sda8 partition or should we wait to hear from oldfred? Lastly this might sound like a dumb question but just to make sure. If I do the reinstall on the /dev/sda8 partition, that should only wipe the information on just that partition and not the complete hard drive? If it wipes all of the information on the /dev/sda8 partition only then that's fine with me because there was not any important information on it.

Good morning, it looks like you and ***oldfred*** posted at exactly the same time. Did you see his post just above yours?

At first glance it looks like he suggested a few things that may help you get past the black screen issue, but let me wake up a little better and I'll look through everything more closely.

---

### Post by kansasnoob on 2014-09-29
> **oldfred said:**
> It is a UEFI install with gpt partitioning.

See the caution in the link in my signature. Only use something else if you elect to reinstall. And make sure you back up efi partition and all of Windows.

With Intel sometimes other boot parameters than nomodeset are required. And some Intel systems need other parameters also.

The link below by ubfan1 has the parameters you can use if you can get to a grub menu. If you can choose in UEFI menu the ubuntu entry and then use escape to bring up grub if it does not come up.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

If that does not work, use Boot-Repair from live installer and post a link to the report it creates. It will not fix video type issues as those are after grub had loaded. It may add a boot parameter?
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Many, many thanks. You're the best.

---

### Post by kansasnoob on 2014-09-29
Regarding re-installation (if that's what you decide to do) I asked a question of my own for clarification:

[http://ubuntuforums.org/showthread.php?t=2246226&p=13131679#post13131679](http://ubuntuforums.org/showthread.php?t=2246226&p=13131679#post13131679)

If in doubt always ask another question :biggrin:

---

