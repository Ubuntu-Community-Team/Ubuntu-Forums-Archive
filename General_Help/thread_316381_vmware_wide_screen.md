---
title: "vmware wide screen?"
date: 2006-12-10
forum: General Help
---

### Post by tocleora on 2006-12-10
Alright, *now* I have Windows XP installed in vmware on Ubuntu, even BETTER than my previous thread regarding Windows 2000!  It works great, but my laptop is a wide screen.  I can do 1024 x 768 fine but it stretches the screen.  Any way to get it to to set to 1280 x 800 like Ubuntu?  The additional setting it provides seem to stay in perspective to 1024 x 768 and even trying those gives me some sort of error.  Thanks in advance!

---

### Post by useResa on 2006-12-10
Have you got VMWare Tools installed?
Because dt the end of the tools installation process you are given a list of screen sizes that you can choose from.

---

### Post by francisco.colaco on 2006-12-10
I have the same kind of laptop.  Once you have vmware tools installed, you will be able to do 1280x800 easily.

To install, boot your virtual machine.  Once booted, pick "Install VMWARE Tools" from one of the menus of VMWARE (the application at the host).  A virtual CD is mounted and detected at the guest (in this case Windows XP).  Just follow the installation wizard through.  After that, you may change the resolution.  One other thing is that if you have DRI on your host (like I do not on my laptop), you will have also a partally accelerated guest, good enough to play Caesar IV or other strategy games at the least.

I hope that was of help.

---

### Post by tocleora on 2006-12-10
Yeah I installed the tools but it didn't give me an option of what screen resolutions at the end.  Should I have done "custom" or something?  I don't remember if I was given an option to do custom or not, I usually do custom when it's offered... Any other way?

---

### Post by useResa on 2006-12-10
Sorry, forgot it's Windows. :-D
If you have VMWare Tools installed you should be able to alter your display settings as you would normally do in Windows.

---

### Post by tocleora on 2006-12-10
Sorry, I should have been more specific.  That's the way I'm trying to change the resolution settings, right-mouse click properties on the desktop.  But it doesn't give me any 1:1.6 ratio options similar to the 1280x800 resolution I'm running in Ubuntu.  It only gives me the typical 1:1.3 ratio, like 1024x768, 800x600, etc.  Am I SOL? :(

---

### Post by tocleora on 2006-12-10
I'm attaching a screen shot, hope that helps explain my dilemma.

---

### Post by tocleora on 2006-12-10
Oh, and vmware tools *is* installed, I have the icon in the system tray and if I try to install it again it asks me if I want to modify, reinstall or remove.

---

### Post by useResa on 2006-12-11
I have checked the VMWare Forums for this and the only thing to get the resolution you wish by modifying the Windows registry.  More information on how to do this can be found [here](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1003&sliceId=SAL_Public). Hope this will help you further.

---

### Post by VividHazE on 2006-12-13
thanks useResa, I have this problem also and that link you gave me looks promising, I'll let you know if it works for me when I try it laters :D

---

### Post by tocleora on 2006-12-15
Ok finally got a chance to try this and the link did help resolve the problem (Thanks useResa!), but wasn't completely accurate (for VividHazE and future readers).  Once I got down to Device0 I did not have any Resolution.x (x being numbers starting with 0) in there.  I went ahead and followed the instructions just in case, but rebooting gave me no results.  So I went back into RegEdit and did a search for "Resolution.0".  I found three instances, one of them was down the branches in CurrentControlSet.  I had 11 Resolutions in there so I created a Binary (not a string like the instructions, because the others are Binary I wanted to match) and named it Resolution.11 (because the 1st started with 0 keep up! hah!)  And you have to type it in hex which the instructions useResa gave include the hex values, so in my instance I'm creating 1280 x 800, I entered "31 32 38 30 78 38 30 30 00", 78 being the "x" and 00 being  a period at the end. The rest had that so I wanted to match what was on the other resolutions.  It will show you what you've entered as you are entering it so you should know if you are right.  Once you are finished entering that in  save/close RegEdit and reboot.  Once you are back, right click on your desktop and you should be able to set your resolution to the new value.

---

### Post by useResa on 2006-12-15
Well done! Glad to read that you have your wide screen working now.

Furthermore, thank you for posting your findings here so others can benefit from your experience.

---

### Post by tocleora on 2006-12-16
Yes, I was using it earlier today full screen and other than a few hiccups every once in a while I don't think anyone watching me would even be able to tell that I'm running XP through Ubuntu!  I recommend this to EVERYONE, EVERYONE GO OUT THERE AND INSTALL THIS RIGHT NOW SO YOU CAN HAVE YOUR CAKE *AND* EAT IT TOO!  Ok, maybe I'm a little too excited about it. ;)  But yes I'm very greatful! :)

---

### Post by cephlon on 2007-01-10
WOw, that totally worked on my Acer Aspire widescreen. Thanks for posting your findings, you sure helped me!

---

### Post by PartisanEntity on 2007-03-04
Just wanted to say thank you to **tocleora** for posting your findings here. Your instructions worked like a charm :)

---

### Post by andy_cowman on 2007-04-11
> **useResa said:**
> I have checked the VMWare Forums for this and the only thing to get the resolution you wish by modifying the Windows registry.  More information on how to do this can be found [here](http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=1003&sliceId=SAL_Public). Hope this will help you further.

Just like to say thanks for that link, it solved my problems a treat!

Andy

---

### Post by useResa on 2007-04-11
> **andy_cowman said:**
> Just like to say thanks for that link, it solved my problems a treat!

AndyYou're welcome and glad that it helped solve your problems.
Resa

---

### Post by andy_cowman on 2007-04-19
LOL my harddrive died and when I came to rebuild I had the same problem and no memory of how I did it.... Just found this post again :D so thanks again!!

Andy

---

### Post by funnyguyfunnyguy on 2007-05-14
I tried tocleora's instructions to resolve the issues with widescreen. However, I was neither able to find any Resolutio.x entries in my registry when I searched, nor was I able to add the widescreen resolution when I tried. (I tried both Resolution.0 and Resolution.11. I have 11 resolution entries in the Display Properties window.) Ideas?

---

### Post by SilverWave on 2007-11-26
> **tocleora said:**
> Ok finally got a chance to try this and the link did help resolve the problem (Thanks useResa!), but wasn't completely accurate (for VividHazE and future readers).  ...  Once you are back, right click on your desktop and you should be able to set your resolution to the new value.

Worked for me as well, much appreciated :)

VMware Wide Screen Issue: missing resolution 1680x1050 (for a new SAMSUNG SyncMaster 226BW).

Using regedt32 I searched for "Resolution.0" and found two of them in CurrentControlSet.
e.g. HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Video\{C90973F8-2114-4C78-BB94-FD8721591CCF}\0000
In each location I created a Binary Key "Resolution.11" .
Added this data to key: 31 36 38 30 78 31 30 35
Rebooted the VM of XP and new resolution showed up, worked like a charm
Added it to my HOWTO here: [http://ubuntuforums.org/showthread.php?t=591732](http://ubuntuforums.org/showthread.php?t=591732)

---

### Post by fjgaude on 2007-11-26
Funny, I wonder if at the VMware Edit/Preferences/Display you would check both boxes for auto adjusting the display to fit if that would have fixed the widescreen issue?

---

### Post by useResa on 2007-11-27
> **fjgaude said:**
> Funny, I wonder if at the VMware Edit/Preferences/Display you would check both boxes for auto adjusting the display to fit if that would have fixed the widescreen issue?
AFAIK it will just stretch the screen to fit in your window, thus this could easily change Paris Hilton into Roseanne Barr ;-)

IIRC to get proper wide screen display in VMware the indicated solution is the way to go.

---

### Post by OliverN on 2008-01-17
I solved the exact same problem by

```
sudo gedit ~/.vmware/preferences
```,

changing 
```
pref.autoFitFullScreen = "fitHostToGuest"
``` 
to
```
pref.autoFitFullScreen = "fitGuestToHost"
```

and

```
pref.autoFit = "FALSE"
```

to

```
pref.autoFit = "TRUE"
```

Should be easier if it works for everybody.

---

### Post by Mongo5000 on 2008-02-22
> **OliverN said:**
> I solved the exact same problem by

```
sudo gedit ~/.vmware/preferences
```,

changing 
```
pref.autoFitFullScreen = "fitHostToGuest"
``` 
to
```
pref.autoFitFullScreen = "fitGuestToHost"
```

and

```
pref.autoFit = "FALSE"
```

to

```
pref.autoFit = "TRUE"
```

Should be easier if it works for everybody.

Anybody try this?  Other way works great but would be cool if this did as well

---

