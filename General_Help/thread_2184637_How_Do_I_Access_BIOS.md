---
title: "How Do I Access BIOS?"
date: 2013-10-30
forum: General Help
---

### Post by dave90210la on 2013-10-30
I'm only running Ubuntu 13.04 on my Leovo G500. I tried the novo key which is recommended by my manufaturer but does not load the BIOS settings! Is there anyway within Ubuntu I can easily adjust the boot order? I no longer can access Windows just Ubuntu

---

### Post by dave90210la on 2013-10-30
Ubuntu is the only operating system on my Lenovo G500 and I want to  completly uninstall it! Ubuntu corrupted my BIOS  and replaced it with  Grub, so I want to uninstall Ubuntu so I can change the boot order and  install Windows. I'm not interested in trying to change the boot order in Ubuntu it's way to time consuming! FYI my laptop wont boot from CD so I can't put the Windows CD in and boot from that unfortunatly. Grub changed my whole boot order and messed everything up!!!

---

### Post by Bucky Ball on 2013-10-30
***Threads Merged.***

Switch the computer off. When you boot, immediately start mashing the 'novo' key (whatever that is). You need to do this at boot. It won't work at any other time (you can not get to the BIOS any time other than at boot).

If that doesn't work you might want to try some others. F2, F10, Delete are common. Not sure this has anything to do with it in any case.

Try this. When in Ubuntu, open a terminal and run this command:

```
sudo update-grub
```

That should pick up Windows. Reboot. It may be that the grub list is just not set to show. In that case, when you boot the machine hit 'shift' (you might also try esc). That should bring up the list. Is Windows on it?

---

### Post by Bucky Ball on 2013-10-30
I've just replied to your other thread. Try that. You are making no sense whatsoever in this one. Grub does not replace the BIOS. Nothing does. Not sure how you can say that anyhow as you can't even get grub up according to your other post. Slow down and have another look at the other thread.

In any case, Windows is probably best for you but you have a problem. You need to boot from the install CD (which you would need to access grub to do), open Gparted when you are at a desktop and delete all partitions. Reboot from a Windows CD and install Windows.

I suggest you have a little more patience, but perhaps you should never have installed Ubuntu in the first place if you were not ready to learn about a new operating system. 

Try the suggestions in the other post before you do anything else.

What I can't work out is that, to install Ubuntu in the first place, you would need to access the BIOS to boot from the install media. How did you do that??? Or is this a Wubi install, Ubuntu INSIDE Windows, not next to it? I've never used it so wouldn't know how to identify.

---

### Post by dave90210la on 2013-10-30
Windows is not on my machine at all. I tried every single F key and the Novo key a million times over the course of 24 hours. I will try the command line entry and shift key but I'm not optimistic! 

> **Bucky Ball said:**
> Switch the computer off. When you boot, immediately start mashing the 'novo' key (whatever that is). You need to do this at boot. It won't work at any other time (you can not get to the BIOS any time other than at boot).

If that doesn't work you might want to try some others. F2, F10, Delete are common. Not sure this has anything to do with it in any case.

Try this. When in Ubuntu, open a terminal and run this command:

```
sudo update-grub
```

That should pick up Windows. Reboot. It may be that the grub list is just not set to show. In that case, when you boot the machine hit 'shift' (you might also try esc). That should bring up the list. Is Windows on it?

---

### Post by Bucky Ball on 2013-10-30
Just wondering what the problem is if you don't have Windows on the machine. You installed Ubuntu and it works fine. So ... 

In the other thread, you complain that grub has deleted your BIOS!@! This is nonsensical I'm sorry. So, in other words, what you're really saying is, 'I don't like Ubuntu and want to install Windows.'? If that is the case, you DO come back to this problem: how do I get to BIOS. Well, how did you do that when you booted from the Ubuntu install media? Is that method just not working anymore?

Set me straight before I waste time explaining anything else that is redundant: You do NOT want to actually get to the grub menu, you just want to uninstall Ubuntu. Correct?

PS: May be a silly question, but you are trying the keys at boot, no other time, to get into the BIOS? Like I say, they make no difference on a running system. You need to get the right key IMMEDIATELY at boot, at just the right time.

---

### Post by Bucky Ball on 2013-10-30
I have merged your two threads because they are basically talking to the same end: You want to get to the BIOS to boot from a CD and uninstall Ubuntu ... I presume. 

Please do not create another (duplicate) thread regarding this. Thanks. ;)

---

### Post by dave90210la on 2013-10-30
Ubuntu doesn't work well with me and is not compatible with any of my PC programs and Wine is garbage and doesn't work at all. I had Windows and the BIOS functioned and was accessable when I had Windows installed, after I deleted Windows and installed Ubuntu it's now inpossible with the tradional method to access my BIOS, none of the keys work when I boot. I went to the Grub menu on boot and it doesn't give me any boot order at all. It has 3 options 1. Ubuntu, and the other two are unrelated to boot order. 

> **Bucky Ball said:**
> Just wondering what the problem is if you don't have Windows on the machine. You installed Ubuntu and it works fine. So ... 

In the other thread, you complain that grub has deleted your BIOS!@! This is nonsensical I'm sorry. So, in other words, what you're really saying is, 'I don't like Ubuntu and want to install Windows.'? If that is the case, you DO come back to this problem: how do I get to BIOS. Well, how did you do that when you booted from the Ubuntu install media? Is that method just not working anymore?

Set me straight before I waste time explaining anything else that is redundant: You do NOT want to actually get to the grub menu, you just want to uninstall Ubuntu. Correct?

PS: May be a silly question, but you are trying the keys at boot, no other time, to get into the BIOS? Like I say, they make no difference on a running system. You need to get the right key IMMEDIATELY at boot, at just the right time.

---

### Post by Bucky Ball on 2013-10-30
I'll start by saying Linux is not Windows (not much research would have been required to find this out), PC programs won't work with it, and not sure why you went down the path you did. Bit like buying an orange and getting upset it doesn't taste like a peach. If you wanted to use Windows programs why didn't you stick with Windows? Or do a dual-boot? I can't actually see any reason whatsoever that you would have wanted to replace Windows with Ubuntu ...

Anyway, that is neither here nor there. This may sound silly, but do the keys work when you do a restart rather than a complete shutdown? My machine is the same. If I switch it totally off, the keyboard doesn't work when I switch it on. If I let it get to the login screen then hit the 'restart' button (on the screen, top right for me), the keys work fine on restart, at which time you should be able to get into BIOS. Or not. 

Give it a try if you haven't, but this is rather odd in any case. 

So, for clarity once more, your actual problem is that 'none of the keys work when I boot,' NOT the fact that Ubuntu has somehow eaten your BIOS or you are hitting the wrong key or the right key is not responding. The keyboard is just not working when you switch your computer on???

---

### Post by dave90210la on 2013-10-30
I'm not stupid I installed Ubuntu becuase my Windows was corrupted and I used Ubuntu to have a temporary operating system until I got a copy of Windows to reinstall. I didn't switch to Ubuntu to run Windows programs I was anticipating on possibly using some Windows programs using Wine. I'm not a avid Linux user and had no idea Wine was unuseable with most programs. This Ubuntu install was supposed to be temporary so I can use my computer until I got the Windows cd.

When I boot the only 1 key that works is the Shift key and it takes me to Grub menu. The laptop is brand new btw so nothing is broken with the hardware  > **Bucky Ball said:**
> I'll start by saying Linux is not Windows (not much research would have been required to find this out), PC programs won't work with it, and not sure why you went down the path you did. Bit like buying an orange and getting upset it doesn't taste like a peach. If you wanted to use Windows programs why didn't you stick with Windows? Or do a dual-boot? I can't actually see any reason whatsoever that you would have wanted to replace Windows with Ubuntu ...

Anyway, that is neither here nor there. This may sound silly, but do the keys work when you do a restart rather than a complete shutdown? My machine is the same. If I switch it totally off, the keyboard doesn't work when I switch it on. If I let it get to the login screen then hit the 'restart' button (on the screen, top right for me), the keys work fine on restart, at which time you should be able to get into BIOS. Or not. 

Give it a try if you haven't, but this is rather odd in any case.

---

### Post by Bucky Ball on 2013-10-30
Please read ideas in last post I just edited. Have you restarted (warm boot) rather than shutdown and switched on? Please confirm it is the keyboard not working at boot and nothing else, as you will find at end of previous post, for clarity.

(PS: You don't need to quote my posts in yours each time. Thanks. ;))

---

### Post by dave90210la on 2013-10-30
I've tried all boot options and nothing works. The keys function properly once Ubuntu is loaded. I used to be able to press the Novo key to access BIOS on boot but since I installed Ubuntu that key no longer functions on boot. My Delete key, F2 key and Shift key all go to Grub menu when I press then when booting. I'm assuming they would go to BIOS if Ubuntu wasn't installed. All other keys do nothing when I press them on boot   

> **Bucky Ball said:**
> Please read ideas in last post I just edited. Have you restarted (warm boot) rather than shutdown and switched on? Please confirm it is the keyboard not working at boot and nothing else, as you will find at end of previous post, for clarity.

(PS: You don't need to quote my posts in yours each time. Thanks. ;))

---

### Post by Bucky Ball on 2013-10-30
So, for clarity, and for other helpers because I have nothing, please confirm:

When you either reboot your computer (warm boot) or switch you computer on from an off state (cold boot) the keyboard does not work and therefore you cannot access BIOS by hitting the correct key (the 'novo' key, according to the manufacturer's manual)?

The odd thing about this is that Ubuntu has nothing to do with anything before the grub kicks in, so shouldn't be interfering with you getting into the BIOS at boot in anyway. You could try plugging in a USB keyboard, but doubt that will make any difference. 

The manual actually says hit the 'novo' key to enter BIOS??? Is this what you did to install Ubuntu???

---

### Post by dave90210la on 2013-10-30
To clarify the manual says use the Novo button or key it's the only key assigned to get into BIOS. The keyboard functions just fine, all I'm saying all the F keys and Shift keys go to the Grub menu when pressed on startup. Once Ubuntu loads all keys work perfectly. I have a Lenovo G500 if that helps you find out how to get to the BIOS. 

All I need and want to do right now is boot from the CD so I can delete this Ubuntu 

> **Bucky Ball said:**
> So, for clarity, and for other helpers because I have nothing, please confirm:

When you either reboot your computer (warm boot) or switch you computer on from an off state (cold boot) the keyboard does not work and therefore you cannot access BIOS by hitting the correct key (the 'novo' key, according to the manufacturer's manual)?

The odd thing about this is that Ubuntu has nothing to do with anything before the grub kicks in, so shouldn't be interfering with you getting into the BIOS at boot in anyway. You could try plugging in a USB keyboard, but doubt that will make any difference. 

The manual actually says hit the 'novo' key to enter BIOS??? Is this what you did to install Ubuntu???

---

### Post by Bucky Ball on 2013-10-30
I find nothing whatsoever about hitting the 'novo' key. You could try the ones I've underlined below:

 >    Press F1 or F2 after powering on the computer.
    Older Lenovo products allow access to BIOS using [B][U]Ctrl+Alt+F3, Ctrl+Alt+Ins, or Fn+F1.
[/U][/B]

This needs to happen when you see the 'Lenovo' screen at boot. My guess is this:

CTRL+Alt+F3 at the boot screen. Put your fingers over those keys and get them ready when you boot the machine.

---

### Post by varunendra on 2013-10-30
> **dave90210la said:**
> I'm not stupid
I can see that clear as daylight.

> **dave90210la said:**
> I'm assuming they would go to BIOS if Ubuntu wasn't installed.
Easy one. Turn your laptop upside down, open the lid that lets you access the hard disk drive, unscrew it > pull it out > boot and voila ! You are suddenly in the BIOS again !! Change the settings as you like > save > power off. Re-plug the hdd and boot with your windows installation medium.

Anymore help needed > contact the vendor who provided that 'User Friendly' BIOS or the (le?)novo key. Or maybe a Windows forum can help better, since it was the one responsible for 'forcing' you to use Ubuntu 'temporarily'.

---

### Post by nativehound on 2013-10-30
I think it's a Windows 8 Hybrid shutdown issuse. [http://support.lenovo.com/en_US/detail.page?LegacyDocID=SF13-T0025]("http://support.lenovo.com/en_US/detail.page?LegacyDocID=SF13-T0025")
Sounds like pulling the hardrive it the best way.

---

### Post by dave90210la on 2013-10-30
I will be trying that since none of the above options have worked. 

> **nativehound said:**
> I think it's a Windows 8 Hybrid shutdown issuse. [http://support.lenovo.com/en_US/detail.page?LegacyDocID=SF13-T0025](http://support.lenovo.com/en_US/detail.page?LegacyDocID=SF13-T0025)
Sounds like pulling the hardrive it the best way.

---

### Post by dave90210 on 2013-10-30
Im Dave90210la my computer stopped functioning so now I have to login using my other account on my phone! Heres an update


I got this new error message when trying to re install wimdows after I deleted the partitions [http://tinypic.com/r/157bsrs/5](http://tinypic.com/r/157bsrs/5) now I get this error message when I reboot  [http://s22.postimg.org/mrd4c6yvl/20131030_020447.jpg](http://s22.postimg.org/mrd4c6yvl/20131030_020447.jpg)

---

### Post by PeterRJG on 2013-10-30
Try what Microsoft suggest here: [http://technet.microsoft.com/en-us/library/dn336946.aspx](http://technet.microsoft.com/en-us/library/dn336946.aspx)

---

### Post by mastablasta on 2013-10-30
wow! microsoft really messed up these boots.
it should be BIOS/UEFI-->loads GRUB or windows boot loader ---> loads the OS

---

### Post by buzzingrobot on 2013-10-30
The BIOS must be accessed before the operating system is booted.  On *any* OS.

The BIOS is firmware, i.e., it's code burned into a chip in your machine. The odds that Ubuntu, or Windows, or any OS, "corrupted" the BIOS are infinitessmal.

The way to access a BIOS is by pressing BIOS-specific key combinations as the machine boots. (Different BIOS vendors use different key triggers.) If the G500 is not responding to the key(s) you are pressing, perhaps that is the incorrect key combination.  On my Lenovo, it's the F1 key.

More likely, then:

1. Wrong key(s).

2. The machine is not fully rebooting but simply restarting the Linux boot process.  Power down the machine completely.

3. Tap but do not hold the key that triggers BIOS access.  I've seen some machines that will display the BIOS and then instantly continue the boot if the trigger key is held down.

4.  Often, the trick is to press the trigger at the exact right moment because the BIOS may be listening for it for a very short time, perhaps one second or less.

---

### Post by The Spectre on 2013-10-30
I just downloaded the User Guide for the  Leovo G500 and according to it do the folowing to access the BIOS...

To start the BIOS setup utility:
1 Shut down the computer.
2 Press the Novo button and then select BIOS Setup.


Or this should also work...

Hold Fn + F2 during startup.

---

### Post by Bucky Ball on 2013-10-30
Posted in error.

---

### Post by buzzingrobot on 2013-10-30
[Deleted.  Wrong thread.]

---

### Post by Bucky Ball on 2013-10-30
You need to deal with this error:

[http://tinypic.com/r/157bsrs/5](http://tinypic.com/r/157bsrs/5)

Forget about the other. That is just booting to grub and there's nothing for grub to boot now (if you've wiped Ubuntu).

You will need to boot to the Windows Recovery Console, as far as I know. Can't be specific as don't know much about Windows nowadays and this is not the best place to ask about it. You would have the best luck posting a new thread on an MS forum or ***Other OS*** here to find out how to re-write MBR. 

Your original problem is solved (you can get into BIOS) so the title doesn't describe this new one anyway and the new, consequently, is off-topic. You should mark this thread as solved and post elsewhere ... 

Good luck with it.

---

