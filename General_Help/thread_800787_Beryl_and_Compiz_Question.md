---
title: "Beryl and Compiz Question"
date: 2008-05-20
forum: General Help
---

### Post by ttmw on 2008-05-20
Firstly i appologize if this is posted in the wrong place but wasnt sure where else to put it.

I have a new pc on the way and will be setting up the newest version of ubuntu on it. I've only used it once before on a poor spec laptop and it wasnt for long when i did.

I will now be putting it on my pc with linux and windows for now and was wondering if i will be able to support beryl/compiz effects with my spec and graphics card.

heres the spec of my new computer...

[http://www.novatech.co.uk/novatech/specpage.html?PC-1146](http://www.novatech.co.uk/novatech/specpage.html?PC-1146)

Also, where do i get all the different effects for beryl and compiz?

---

### Post by chewearn on 2008-05-20
Yes, you should be able to run compiz.  Don't use beryl; it's obsolete.

After installing ubuntu 8.04, first enable nvidia restricted driver.  Look for the checkbox under:
Menu > System > Administration > Hardware Driver.

You would be asked to reboot.  After reboot, if you are lucky, the GUI desktop will come back with correct screen resolution.  Compiz will now be enabled by default (you don't have to do anything).

However, the default compiz is limited; many effects are not enabled.  To go further, install compizconfig-settings-manager:
```
sudo apt-get install compizconfig-settings-manager
```

After you install, you will now get a new item under:
Menu > System > Preferences > Advanced Desktop Effects Settings

Don't go too crazy on the settings.  If you break it, you get the keep the pieces. :mrgreen:

.

---

### Post by benjes on 2008-05-20
Hello, i was reading this post and have tried all of the above. but when i enter the code it comes up with this: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

I have an ATI radeon graphics card with 256 VRAM, but my PC is about 6 years old, do you think that could be the reason for it not working?

---

### Post by bobjenkins on 2008-05-20
Hmm I dont think it wouldn't be able to find the package because of an old PC, try using the synaptic packet manager to install, just search for it.

[B]EDIT, did you try   sudo apt-cache search compizconfig-settings-manager
If so did anything come up with that name?
Otherwise this might update repositories   sudo apt-get update
goodluck:)[/B]


I am a noob, I thought compiz-fusion was beryl and compiz combined?
If thats correct is compizconfig-settings-manager package just compiz? or both?

---

### Post by Exsecrabilus on 2008-05-20
> **benjes said:**
> Hello, i was reading this post and have tried all of the above. but when i enter the code it comes up with this: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-settings-manager

I have an ATI radeon graphics card with 256 VRAM, but my PC is about 6 years old, do you think that could be the reason for it not working?
It seems you have not enabled the extra repositories. To do so, go **System** >> **Administration** >> **Software Sources**.

Under **Ubuntu Software** tab, check the boxes that have text next to them reading *main*, *universe*, *restricted* and *multiverse*.

Now click **Close**. A new window should pop up. Click **Reload** and wait for it to finish with the updates.

Now run:

```
sudo apt-get install compizconfig-settings-manager simple-ccsm
```

To access them, press Alt+F2 and type in *compizconfig-settings manager* or *simple-ccsm*.

> **bobjenkins said:**
> I am a noob, I thought compiz-fusion was beryl and compiz combined?
If thats correct is compizconfig-settings-manager package just compiz? or both?
Yes, Compiz and Beryl did merge. Now they are one project called Compiz Fusion.
CompizConfig Settings Manager covers the new merged project effects.

---

### Post by ttmw on 2008-05-22
I have the same problem but i do not have a working internet connection on that cputer yet, is there another way i can install them, or something else i can do to get compiz running?

---

### Post by Forlong on 2008-05-22
What problems do you have exactly with Compiz?

As for installing ccsm without an internet connection: try downloading **compizconfig-settings-manager** and **python-compizconfig** from here: [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by ttmw on 2008-05-22
ok thanks, after downloading how do i get it to run, and where should i put the files ?

---

### Post by Forlong on 2008-05-22
First of all: do you have Compiz running or not?
Is something other than *None* enabled in *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects*?

---

### Post by ttmw on 2008-05-22
no i dont think so.None is enabled at the moment in the visual effects tab, if i try to enable extra effects it gives me a notice about enabling the graphics card, then says...


'the software source for the package:

nvidia-glx-new

is not enabled'

---

### Post by jacob123 on 2008-05-22
Hello Friends,

            I am using a messenger called &#8220;barablu&#8221;, it can be installed in PC and mobile as well, It has many free features like Call, video, file transfer, voicemail, conference call, Group chat. 

Also you can make call to any mobiles/ landline from Barablu @ cheap rates [http://www.barablu.com/pages/products/rates.aspx]("http://www.barablu.com/pages/products/rates.aspx")

You can also try this software and enjoy using Barablu [http://www.barablu.com/pages/download.aspx]("http://www.barablu.com/pages/download.aspx")

Have a Good day !

---

### Post by Forlong on 2008-05-22
OK, you need the proprietary Nvidia driver but Ubuntu can't download it, because you don't have an internet connection.

May I ask why that is? Because you should try to fix this first.

---

### Post by ttmw on 2008-05-22
yes im in the preocess of trying to sort that aswell, but ive never  had the internet connected on linux before so i havent a clue what im doing, heres the thread if you can/have the time to help?


[http://ubuntuforums.org/showthread.php?p=5017578#post5017578](http://ubuntuforums.org/showthread.php?p=5017578#post5017578)

---

### Post by Exsecrabilus on 2008-05-22
> **ttmw said:**
> no i dont think so.None is enabled at the moment in the visual effects tab, if i try to enable extra effects it gives me a notice about enabling the graphics card, then says...


'the software source for the package:

nvidia-glx-new

is not enabled'
[http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb](http://mirrors.kernel.org/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb)

It will download the package. Transport it using a USB or something to your Ubuntu computer, and double-click on it.
GDebi Package Install will open up and install it for you. Type in your password, etc.

P.S. If it says "Dependancies could not be matched" or something, post here and we'll help.

---

### Post by ttmw on 2008-05-23
I've clicked on the link you gave and it just gives me a screen full of text/code, how do i download it from there?

---

### Post by ttmw on 2008-05-23
ok, worked it out. I downloaded the driver and ran it and all seemed well, it asked me to reboot the computer which i then did and got the message...

ubuntu is running in low-graphics mode

your screen and graphics cared could not be detected correctly. to use higher hesolutions,visual effects or multiple screens, you have to configure the display yourself.

it then carrys on to the desktop and when i try to turn extra visual effects on it says...

desktop effects could not be enabled.

---

### Post by ttmw on 2008-05-23
plus the resolution is wrong also so everything is way bigger than it should be. any ideas?

---

