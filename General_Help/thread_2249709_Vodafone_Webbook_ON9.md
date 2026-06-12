---
title: "Vodafone Webbook ON9"
date: 2014-10-24
forum: General Help
---

### Post by Andr_Gabriel_Coe on 2014-10-24
Hi there,

I am an IT Technician, I am based in South Africa so I mostly work with Windows. Anything from 98 up to 8.1. Anyway, I got a netbook yesterday that I have to fix with Ubuntu on it. After a day and a half of doing research etc, trying numerous amounts of things, I am completely at a loss. I have no idea how to fix it. 

It is a Vodafone Webbook ON9, absolutely terrible. ARM Processor, 512mb RAM, 4GB flash. Not very useful, to me anyway. As far as my research goes, it has Ubuntu 10.04 on it, but I do not know how to confirm this on the webbook itself. Also, there is no DVD-ROM.

 The problem is, when it boots, it gets to the login screen, when the user is selected and correct password is typed in, the mouse is shown for a few seconds, and a black screen, and then it shows the login screen again. One simply cannot log in. I think the OS is corrupt. I figured out how to use the terminal, if I press ctrl+alt+F1 at the login screen, I can get to a terminal. 

I tried to connect to the internet wirelessly via the terminal, but it just won`t work. There is some kind of driver association failure with the "Wext" driver. Anyway, I tried a lot of things, I can`t get it to connect to the internet, and there isn`t even an ethernet port, so I have no idea what to do. Oh, and to make it even worse, this thing is like a cellphone or a tablet, it doesn`t have a conventional BIOS, I don`t even know how to let it boot from a usb device OR an external DVD-Drive. So I can`t use a LIVE CD. To make it even more worse, I do not even know what Ubuntu version to download, since this thing has an ARM Processor. Even if I did know exactly what Ubuntu to download, I`ve no idea how to reinstall it on this thing.

As you can see, this is my first real experience with Ubuntu, I have no idea what to do. Can someone please help me? As normal every-day Ubuntu users, what would you do? I`d be happy to provide logs and even videos of exactly the state this webbook is in, so you can see for yourself what happens when it boots. If this wwas your webbook, what would you do to fix it? The idea that I had, was to try and connect it to the internet, then find some kind of command that can check the OS, then download and repair everything within the OS that is broken, so it can boot normally again. Any help whatsoever would be sincerely appreciated. I don`t believe in giving up, and I don`t want to tell a customer to go to someone else better suited to fix a Linux OS, I`d rather push through, gain some experience, learn how Ubuntu works and fix this thing. But right now, I don`t know how to do that.

Thank you for taking the time to read my dilemma. Any help would be sincerely appreciated.

---

### Post by debiant on 2014-10-24
Hi There,
Not really sure what you're trying to do and more importantly, why?  
Is 10:04 something your friend was using and felt passionate about? Surely you can just re-install Ubuntu?
Does it have a USB port or something to attach a DVD?  If not, then it has to work over the net.

If it does have a USB port or some way of attaching a DVD, here are some options...
1. Download the latest version of Ubuntu, burn it to a DVD (will that thing boot from a USB stick?) and then run a live session.  Recover any files to USB sticks or upload to the cloud, install the new Ubuntu OS.  It will guide you through most of it or tell you where documentation and resources are.
2. Install on part of the disk, it will guide you through this too-the other partition gets shrunk-all the documents or other files are still there, recover them to the new partition and then use gparted or another disk utility to delete the old partition.
3.  I think the set-up now actually lets you migrate settings, and data from an old installation to a new one anyway!

You won't lose any data, its the same OS, just updated.  It will look quite different, 10 was a few years ago and the Linux desktop has evolved considerably,  but all of that is configurable.  If your friend hates "Unity" (I do!) they can go back to Gnome 2 or whatever it was back then, or use "Mate" which a lot of Gnome fans seem to like. You get lots of choice with Ubuntu, or any Linux OS, that can be a little bewildering at first but there's a lot of help available.
Best wishes,
D

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Well, I`m an IT Technician, I mostly work with Windows. But a customer brought me this webbook yesterday with Ubuntu on it that I have to fix. Not "friend", "Customer" hahaha. The Vodafone Webbook comes with Ubuntu 10.04 preinstalled. As I said, I`m not sure what Ubuntu to download to attempt a reinstall, as this webbook uses an ARM Processor, it`s not Intel nor AMD. 

To be honest, I don`t think it even will boot from a USB Device. I have no idea how to let it, considering it`s more like a tablet and doesn`t have a conventional BIOS. I`m not sure what to do, how to go about repairing or reinstalling the OS. Is there some kind of repair command? Where the OS will check itself and the download and install all missing or broken OS files?

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Thanks for the reply Debiant. I`ll see what I can figure out with this webbook. But it`s pretty useless, Reinstalling is the best option, I agree with you, now I just have to figure out how to go about doing that, without being able to set some kind of boot order. Also, do you have any idea what Ubuntu version will work for a system running an ARM Processor? If so, can you please provide me with a link? Or will it automatically configure itself correctly during installation, sort of like Windows?

---

### Post by /ADM on 2014-10-24
There is an ARM Ubuntu Desktop?  As far as I know ARM is only for Ubuntu Server.  Check the release page for Lucid (10.04.4) [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Only x64 and x86 are there, unless they are hidden somewhere?

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Well to be honest I`m not sure. I`ve never really worked with Linux before, nor this webbook. If I access the terminal at the login screen via ctrl+alt+F1, log in, it shows Ubuntu 10.04.4 LTS is installed. I don`t know if it`s Ubuntu Server. This webbook was given to me, the guy showed me he can`t log in, and I was told to fix it. If only there were an easy way to fix this login fail. Because if one logs in, it only displays the mouse for a few seconds and a black screen, only to return you to the login page again.

---

### Post by debiant on 2014-10-24
Hi there,
I looked it up-oh wow there's only 512 Mb of RAM?
I love what its about-The origins of Ubuntu are people from your country and this web book is supposed to be a cheap little computer, especially for children in Africa, to get them something to learn on and get connected to the world.  That's really cool, but the latest Ubuntu needs more RAM than that!!!  You could re-install an old version-10:04 again?  There is a page for legacy versions, they're still safe online.
/ADM put a link for 10:04.
14:04 is the long term stable-therefore lots of support (and you won't have to do all this again for a long time)it does support ARM chips.  Might have to play with the desktop environment to get a "same day service" on this little machine!
;)

---

### Post by /ADM on 2014-10-24
Via terminal, what does the below command say (it should give the version and in brackets the specific branch i.e Desktop, Dev, Server etc).

lsb_release -a

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Debiant, I was just as surprised when I saw the specs. Well that all seems good in theory and like a nice gesture, but trust me, money is always number one. This webbook comes mostly as part of a cellphone deal / contract, and is a bit too expensive if bought directly if I may add. Most people who get this webbook here sell it within the first week. It`s really quite terrible hahaha. Thanks Debiant, I`d love too but I`m still not sure how to achieve that on this webbook. No boot order options, no conventional BIOS. I`m starting to feel like it should just be taken to a Vodafone shop so it can be fixed there. I`ve no idea how to reinstall Ubuntu on this thing.

ADM, it says the following : 

No LSB Modules are available.
Distributor ID : Ubuntu
Description: Ubuntu  10.04.4 LTS
Release 10.04
Codename : lucid

---

### Post by kc1di on 2014-10-24
Let's see if we can figure out what happening.

Go to the terminal and type the following commands and list the outputs here.```
lspci
```
```
lsmod
```
```
lshw
```
```
lsusb
```
We will start with that. 
These things only came with 4GB H.D. and depended upon online storage contracts for more storage 4GB is not much and it may be full already.
So I suspect that the clients contract for on line storage may have lapsed.  You'll have to get more info from the customer.
Also believe that it depends on an cellphone modem to connect to the net.

---

### Post by matt_symes on 2014-10-24
Hi

> One simply cannot log in. I think the OS is corrupt.

> Even if I did know exactly what Ubuntu to download, I`ve no idea how to reinstall it on this thing.

You're too much into the windows mindset here.

I just sounds like X is crashing and dumping you back to the login prompt which will be GDM under 10.04 (assuming that is what you have).

I would be very surprised if this is not fixable. You should not need to reinstall at all. 

There are a many posters already, on this thread already so i'll just subscribe to it for the moment.

Kind regards

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Thank you kc1di. I`m sorry I can`t copy and paste the logs directly, the webbook can`t log in and the only way for me to even access a terminal is by using ctrl+alt+F1 at the login screen. I typed those commands and this was the output for each of them. 

**lspci :**
pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.

[B]lsmod:
Module                                 Size                   Used by
[/B]uvcvideo                         58057             0
rtl8712s                          320981           0 
gpu                                104773           2
uio_pdrv_genirq                  2716           0
usbhid                             29349           0

[B]lshw:
[/B]-bash: lshw: command not found

[B]lsusb:
[/B]Bus 001 Device 004: ID 064e:e215 Suyin Corp.
Bus 001 Device 003: ID 177a:ff00
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Hi Matt,

I think you`re right. Normally with windows this would be such an easy fix. I could system restore, boot the windows disc and repair, or even just boot Hiren`s and use one of several programs to fix the issue, but with Ubuntu I am clueless hahaha. Do you have any ideas for me? Initially I tried to connect to the internet via the terminal, but I couldn`t get it to work. There is a problem with the "Wext" driver. I wanted to connect it to the internet and then use "sudo aptitude" to see if updating all those components might fix the issue. However, after coming to terms with the fact that I have absolutely no idea what I`m doing on Ubuntu, I thought it`d be wiser to open a thread first hahaha.

What would you do in this situation? Any help would be greatly and sincerely appreciated. 

Kind Regards,
André

---

### Post by matt_symes on 2014-10-24
Hi

> What would you do in this situation? Any help would be greatly and sincerely appreciated.

I'm Just about to go offline as i have some guests coming this evening, however if you can wait till tomorrow and there has been no progress then we can look to see what you have installed, what exactly has broken and then attempt to fix it.

I have some questions to start with though to get some background. Please be as thorough as possible when answering them. 

1. I take it Ubuntu was working on the netbook but has recently stopped working ?
2. If the above is the case, did it stop working after an update, a system crash, a hard power off or something else ?
3. If not, is this a new installation ?
4. Can you boot into the recovery mode from the Grub menu screen ?
5. Can you boot into failsafe graphics mode ?

Can you supply the basic system specs please.

Kind regards

---

### Post by /ADM on 2014-10-24
@Matt

The netbook runs Ubuntu 10.04 pre-installed from what I could gather it is a South African computer only.  

800MHz Freescale iMX515 based on ARM Cortex-A8
512MB RAM, and 4GB of flash storage

Just to help the OP out.  I got the info from here: [http://www.techcentral.co.za/vodafone-webbook-review-cheap-and-cheerful-ubuntu-netbook/27074/](http://www.techcentral.co.za/vodafone-webbook-review-cheap-and-cheerful-ubuntu-netbook/27074/)

I presume this is 'the one' :)

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Hi Matt,

Thank you so much, I sincerely appreciate you being willing to help. Not a lot of people would do that today. I can definitely wait 'till tomorrow, it`s almost the end of my work day anyway, and I haven`t really made any progress with the webbook. 

I shall try to be as thorough as possible but you should also know I really don`t have a lot of information about this webbook.

1. Yes, the webbook recently stopped working.
2. I have no idea, the customer was extremely vague and didn`t offer a lot of information as to what happened. In fact, he thought he had forgotten his password, he thought it was a password issue. I eliminated this though, by removing the battery and setting the switch to "Setup" or something of the sort and changing the password of his account by choosing the option "execute a shell". If I remember correctly, it was called "Ash". After the password change, the netbook still just shows a black screen for a few seconds after login then returns to the login screen again.
3. After trying to fix the issue after countless hours spent in the terminal, I can safely say it is definitely not a new installation. I used the "dir" command to see what`s on the HDD and found some videos, pictures etc. Though the HDD is only 4GB. 
4. No, I cannot. It is one of the first things I tried with the netbook after doing my research, I tried holding and pressing the ESC and Left + Right Shift keys (Not at the same time, first ESC, then Left Shift, then Right shift), it does not boot into another GRUB menu screen nor do I see any recovery modes or options. I found one other thread where someone with the same netbook also stated that he had also tried booting into a recovery menu by holding down the SHIFT key, but it did not work. I think that function was purposefully removed with this Vodafone Webbook.
5. Also a no. At the login screen after selecting an account. At the bottom I can choose one of four options before login. Failsafe GNOME, GNOME, Unity 2D or xterm. None of them work, it does exactly the same thing as mentioned above no matter what option is chosen at the bottom before login. 

Kind regards,
André

---

### Post by Andr_Gabriel_Coe on 2014-10-24
Hi /ADM,

That is the exact one. Thank you for your help and for providing the specifications hahaha. I really appreciate the help. You guys have been very kind so far and I sincerely appreciate it.

Kind Regards,
André

---

### Post by Andr_Gabriel_Coe on 2014-10-27
Hi everyone,

Just wanted to say I solved the issue. I did a lot of research again, and I learned that in Ubuntu, for a User to be able to log in correctly, an Xauthority file has to be created and the permissions have to be set for that file. After screwing around in the terminal, I noticed that there was absolutely no free space on the enormous 4GB HDD (What a shocker), so I deleted a large video file in the home folder while I was in the terminal. Restarted with "sudo reboot" and viola! No more login screen loop. Everything is fixed, no re-install is necessary. I`m just glad I don`t have to tell this guy he has to go to a vodafone shop to get it fixed. Thanks for everyone`s help, I sincerely appreciate you guys taking the time to help out a Windows user hahaha. Everyone is very kind.

Kind Regards,
André

---

