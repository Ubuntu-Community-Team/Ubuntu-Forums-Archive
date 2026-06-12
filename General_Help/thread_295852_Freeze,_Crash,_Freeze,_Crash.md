---
title: "Freeze, Crash, Freeze, Crash"
date: 2006-11-08
forum: General Help
---

### Post by ububaba on 2006-11-08
I have done a clean install but the computer keeps on freezing, sometimes
even just after the start. My double-boot is not working either. XP's start
is not visible in Grub. Even if I remove other HDs with XP, the situation does
not improve at all. It can be just one program:Evolution, FireFox, Nautilus,
VLC or whatever, it simply freezes the computer. :confused:

---

### Post by ReaderRat on 2006-11-08
For folks to help, please give more info....RAM, HDDs (internel/USB), Order you installed your OSs in...

---

### Post by ububaba on 2006-11-09
> **ReaderRat said:**
> For folks to help, please give more info....RAM, HDDs (internel/USB), Order you installed your OSs in...

Here it is: GeForce FX5200| Asus P4P800S |Asus V9520/TD| 2 x 512mb RAM PC 3200 | 200gb Seagate HDD |
MSI DVD/Rom+-RW | SyncMaster 940B TFT | Dual boot Ubuntu 6.10 32 bit & Windows XP Sp2 |


I had removed the other HDs with XP while updating to Edgy. With Dapper, all worked fine, 
well almost.

---

### Post by ububaba on 2006-12-19
](*,) Freeze problem does not seem to go over. ](*,) It freezes just after I start the first utility.
Whatever it may be.](*,) It feezes right in the middle of using Evolution.](*,) It freezes while surfing.
](*,) I can see hundreds of mails about freezing.](*,) The questions don't get answered](*,) 
Is there a way to get out of this quagmire:confused:

---

### Post by Sef on 2006-12-19
Sounds like a bad install, so I have some questions:

1) Did you md5sum the disk?

2) Did you burn it at 4x or less?

3) If you installed the Live CD, were there any problems using it?

4) check the cd to make sure it is good and not bad.

---

### Post by jbus on 2006-12-19
Did you install the latest drivers for your graphics card?

---

### Post by ububaba on 2006-12-19
> **Sef said:**
> Sounds like a bad install, so I have some questions:

1) Did you md5sum the disk?

2) Did you burn it at 4x or less?

3) If you installed the Live CD, were there any problems using it?

4) check the cd to make sure it is good and not bad.


1) Sorry this one is not known to me.

2) Was such a long ago that I can't recall.

3) Some problems. Had to make several attempts to get the task done.

4) How does one go about ascertaining the good/bad aspect of a CD?

If it does not sound silly, I keep updating whatever drops down through Automatix2. I can 
very well download and burn a new copy of Dapper. How can I in a definite way save my old
mail and other files if I have to re-install? Please be kind to me. I know I am sinner.:-D

---

### Post by ububaba on 2006-12-19
In /etc/X11/xorg.conf file changed **"nvidia**" to **"nv"**, all troubles seem to have 
disappeared.\\:D/

---

### Post by pdiddy on 2006-12-26
> **ububaba said:**
> In /etc/X11/xorg.conf file changed **"nvidia**" to **"nv"**, all troubles seem to have 
disappeared.\\:D/

Please help! 

Where can I change the value from "nvidia" to "nv" in the xorg.conf file mentioned above? I am having a similar ](*,) problem to what is described in this post,  and I really need to see if this fix works for me.

My error details are posted at: 

[http://www.ubuntuforums.org/showthread.php?t=315974&page=2](http://www.ubuntuforums.org/showthread.php?t=315974&page=2)

Thanks

---

### Post by ububaba on 2006-12-26
> **pdiddy said:**
> Please help! 

Where can I change the value from "nvidia" to "nv" in the xorg.conf file mentioned above? I am having a similar ](*,) problem to what is described in this post,  and I really need to see if this fix works for me.

My error details are posted at: 

[http://www.ubuntuforums.org/showthread.php?t=315974&page=2](http://www.ubuntuforums.org/showthread.php?t=315974&page=2)

Thanks

In your Terminal write
[COLOR="Red"]
sudo gedit /etc/X11/xorg.conf[/COLOR] 

this will open** xorg.conf** file which can be then edited. Find 
[COLOR="Red"]Section "Device"[/COLOR] as illustrated below and do the necessary changes

[HTML]

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "[COLOR="Red"]nv[/COLOR]"
EndSection

[/HTML]

---

### Post by pdiddy on 2006-12-26
This is a disaster. I have done something seriously wrong - the GUI of my system is completely gone. 

I followed the instructions in the last post and changed the Identifier "Generic Monitor" to "SyncMaster". Then my system frooze so I had to restart it. 

Now on startup my screen says:

"Failed to start X Server (your GUI). It is likely that it is not set up correctly. Would you like to view the x server output to diagnose the problem?"

I Click OK:

"Data incomplete in file /etc/x11/xorg.conf
Undefined Monitor "Generic Monitor" referenced by Screen "Default Screen""

"Fatal Server Error: No Screens found"

Click OK again:

"The X Server is now disabled. Restart GDM when it is configured correctly"

First time I clicked ok, it said:

"Out of Memory: Kill process 5971 (beagled-helper) score 484458 and children"
"Out of Memory: Killed process 5971 (beagled-helper)"

"Out of Memory: Kill process 5996 (beagled-helper) score 484458 and children"
"Out of Memory: Killed process 5996 (beagled-helper)"

"Out of Memory: Kill process 6001 (beagled-helper) score 484458 and children"
"Out of Memory: Killed process 6001 (beagled-helper)"

But now after I click the final OK, the screen just goes pitch black....

I seriously don't know what to do....it looks like my laptop is screwed. This is not good. Can you please give me some advice how to fix it?

---

### Post by ububaba on 2006-12-26
Please visit this link where Tseliott/Alberto Milone has a very thorough description of 
intallation process of Nvidia graphic cards. Do follow the instructions carefully. 
Good luck

**[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)**

---

### Post by pdiddy on 2006-12-26
Sorry, I'm a bit confused here...

In the link for intallation process of Nvidia graphic cards, Step 1 of "How to Install the package" says: 

1) Download and install the deb package.

But if my GUI is gone, how can I access the internet from my laptop to download the deb package?

Thanks - Peter

---

### Post by ububaba on 2006-12-26
Peter, when you start your computer do you see a black screen with a menu on it. Part of it
should look something like this:

[HTML]title		Ubuntu, kernel 2.6.15-27-386 **(recovery mode)**
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot[/HTML]

Please access (recovery mode), There you will be required to login and provide your password.

1) Write sudo nano /etc/X11/xorg.conf   ...(remember it is caps X and then one one not ii)
2) With the down arrow again locate [HTML]Section "Device"
    Identifier     "NVIDIA Corporation NV34 [your own card's name/number]"
    Driver         "nv"
EndSection[/HTML]

there change "nv" to "nvidia"

3) Then hold down Ctrl and press "o" (not zero)

4) Then accept the change by "Enter", You have edited "xorg.conf"

5) Now hold down Ctrl and press "x", This means you now get out of editing mode.

6) Now write "sudo reboot" anter password if asked

If all went ok then this will take you back to the normal looking Ubuntu. In case of failure
do write back. There are many here who have a greater knack and will surely help, if I can't.

---

### Post by pdiddy on 2006-12-27
Ububaba, thank you so much. 

In Section "Monitor", I changed the value of "SyncMaster" back to "Generic Monitor" and my GUI came back.

Then I ran "sudo get-apt dist-upgrade" instead of just "sudo get-apt upgrade", and my laptop stayed on for about 20 mins. I thought that had fixed the problem but it started to freeze again then.

Now I want to try the following fix from your last post: 

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [your own card's name/number]"
    Driver         "nv"
EndSection
 
But since my graphics card is Intel, not Nvidia, what should I type?  

Thanks, Peter

---

### Post by ububaba on 2006-12-27
> **pdiddy said:**
> Ububaba, thank you so much. 

In Section "Monitor", I changed the value of "SyncMaster" back to "Generic Monitor" and my GUI came back.

Then I ran "sudo get-apt dist-upgrade" instead of just "sudo get-apt upgrade", and my laptop stayed on for about 20 mins. I thought that had fixed the problem but it started to freeze again then.

Now I want to try the following fix from your last post: 

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [your own card's name/number]"
    Driver         "nv"
EndSection
 
But since my graphics card is Intel, not Nvidia, what should I type?  

Thanks, Peter

The computer froze again, as the graphic card has not been configured as yet. 
Don't you have some manual that accompanied your LapTop? The graphic card 
would have been described there. You have nothing to do with Nvidia at all. 
The **Identifier** would thus be "Intel whatever..." then try to have "Vesa" as a **Driver.**

Please go through this mail, it might be of some help to you.
[http://ubuntuforums.org/showthread.php?t=179426&highlight=intel+card](http://ubuntuforums.org/showthread.php?t=179426&highlight=intel+card)

---

