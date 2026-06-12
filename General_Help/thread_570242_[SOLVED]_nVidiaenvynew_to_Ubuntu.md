---
title: "[SOLVED] nVidia/envy/new to Ubuntu"
date: 2007-10-08
forum: General Help
---

### Post by xOriginalNinjax on 2007-10-08
Ok, I've read every thread I can find, done everything they've said, and nothing works.
I just installed Ubuntu this morning (runs like a dream from teh Live CD...but that's not what I want).  I tried to boot from HD several times, and always get teh xserver error.  I tried the reconfig on that, that didn't help.  I came back, searched again, found the whole "Envy" thing, tried to install it, but it won't install...something to do with missing something somewhere...dependencies for something...and so every time I load, I keep getting that, and it won't go away...help!

EDITED past here.

I could NOT get Envy to work, so these are the steps I took to get my drivers working.  I'd also like to give credit to Ek0nomik and Roachk71 for the help.  This guide is NOT an end-all to nVidia driver issues, but is a guideline for those experiencing similar/identical issues.

If you're experiencing an xserver boot error that sends you to command prompt only, start here.  If not, continue on to step 3.

1.  In the command prompt, type&#8220;```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and set that up as best as you can (it's fairly simple, resolution settings only iirc, and set it up as &#8220;nv&#8221; as that stands for nVidia.

2.  Then, after that completes, type ```
sudo reboot
``` to reboot your system to your hard drive installation of Ubuntu.

3.  Once in your hard drive installation, either 
A.  Go to the terminal and type ```
lspci
```
B.  Open your case and read your card, or
C.  Skip this if you know what your exact model graphics card is.

4.  Now that  you know the model of your graphics card, you can proceed to [www.nvidia.com](www.nvidia.com) and go to the download drivers section, where you can locate the linux drivers for your card (make sure you get the 64 bit drivers if you're running 64 bit...if they're supported)

5.  After those have downloaded, figure out the directory they're in (example: mine dled to home/matt/Desktop)  which you can figure out by right clicking on the file, and then write that directory down (or print it out).

6.  Then, if you had the xserver issue, continue on from here, if not skip to step 7. (If skipping doesn't work, come back to this step and repeat from here on.)
For safety's sake, and installation time's sake as well, go ahead and run the following in the terminal(unless you've run some of these previously.) ```
sudo apt-get install build-essential linux-headers-2.6.20-16-lowlatency pkg-config xserver-xorg-dev libc6-dev
``` that way when you go to run the installation for the drivers, it has everything it needs.

7.  When that finishes, either type in the terminal ```
sudo init 1
``` or press ctrl+alt+F1 to go to command prompt.  If you use the ctrl+alt+F1, when the command prompt comes up, type in ```
sudo init 1
``` to get to the init 1 setup.

8.  After getting into init 1, change your directory (cd) so you're in the directory with your nVidia driver (example: my driver was in home/matt/Desktop, so I typed &#8220;cd /home/matt/Desktop&#8221;)

9.  Once you're in that directory, you just type &#8220;sh <insert file name here>&#8221; (For example, my filename for the drivers was NVIDIA-Linux-x86-100.14.19-pkg1.run, so I used ```
sh NVIDIA-Linux-x86-100.14.19-pkg1.run
``` and press enter.  Your nVidia installer should come up at this point.
(Also note, the <> are NOT required, I have them there to show where to input the name)

10.  As the installer starts up, it recognizes that you're not in init 3 (the standard setup for your graphic interface) and that you're in init 1.  Tell it that you don't want to exit because you know what you're doing.  It'll also bring up things about kernels (at least it did for me) and tell it not to dl them, and just let it build it's own.  It should ask if you want the xserver configured for you, if you don't know how to do so, I suggest letting it, if you have stuff you want to tweak (you l33t h4xor you) tell it no.

11.  After the installer finishes (if it doesn't, post what it says) use ```
sudo nano /etc/default/linux-restricted-modules-common
``` Find the line DISABLED_MODULES="" and place nv nvidia_new between the quotes. Use Ctrl-X to save and exit Nano.  Then run```
sudo nano /etc/modules
``` and place nvidia at the bottom of the file, then again use Ctrl-X to save and exit.

12.  After saving and exiting that file, use ```
sudo reboot
``` and boot Ubuntu up, where it should at least flash an nVidia logo...at least that's all mine did, and very briefly at that...but if so, congrats!

---

### Post by Ek0nomik on 2007-10-08
> **xOriginalNinjax said:**
> Ok, I've read every thread I can find, done everything they've said, and nothing works.
I just installed Ubuntu this morning (runs like a dream from teh Live CD...but that's not what I want).  I tried to boot from HD several times, and always get teh xserver error.  I tried the reconfig on that, that didn't help.  I came back, searched again, found the whole "Envy" thing, tried to install it, but it won't install...something to do with missing something somewhere...dependencies for something...and so every time I load, I keep getting that, and it won't go away...help!

It will be much easier to diagnose your problem if you can post exact error messages.

What is the exact xserver error you're getting?  What dependencies are you missing?  How did you try to install Envy?  What kind of video card do you have?

If you can be a bit more specific, you'll be able to get a lot of help from this community.

Cheers!

---

### Post by xOriginalNinjax on 2007-10-08
> **Ek0nomik said:**
> It will be much easier to diagnose your problem if you can post exact error messages.

What is the exact xserver error you're getting?  What dependencies are you missing?  How did you try to install Envy?  What kind of video card do you have?

If you can be a bit more specific, you'll be able to get a lot of help from this community.

Cheers!

The xserver error...I'll have to reboot when a few things finish up..and get frustrated again...

The "module-assistant" dependency is "not satisfiable" when installing envy from package installer, and I can't access getautomatix.com to get that...page isn't loading.

All I know about my card is that it was the cheapest knockoff card I could get at Fry's, and that it's nVidia chipset.  Other than that, i don't even remember.

---

### Post by Ek0nomik on 2007-10-08
> **xOriginalNinjax said:**
> The xserver error...I'll have to reboot when a few things finish up..and get frustrated again...

The "module-assistant" dependency is "not satisfiable" when installing envy from package installer, and I can't access getautomatix.com to get that...page isn't loading.

All I know about my card is that it was the cheapest knockoff card I could get at Fry's, and that it's nVidia chipset.  Other than that, i don't even remember.

You can just download the .deb file (similar to Windows .exe file) and install Envy.  It should take care of the dependencies for you.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb)

This is only for Ubuntu 6.06, 6.10, and 7.04.

---

### Post by xOriginalNinjax on 2007-10-08
> **Ek0nomik said:**
> You can just download the .deb file (similar to Windows .exe file) and install Envy.  It should take care of the dependencies for you.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu12_all.deb)

This is only for Ubuntu 6.06, 6.10, and 7.04.

Ok, I'm trying that now.  (Sorry, I was working on the computer and fell asleep waiting on it to load after checking the xserver error, which I have a log of now if you want to read the huge frickin thing).  And I'm running 7.04.  At least...attempting to anyway...haha

---

### Post by xOriginalNinjax on 2007-10-08
Ok, I tried that, but it didn't work.  It may be because I'm running the live disc.  I'm gonna reboot to safe mode and see if that works....

---

### Post by Ek0nomik on 2007-10-08
If you can get to a command prompt and type

```
lspci
```

it may display your video card model.

---

### Post by xOriginalNinjax on 2007-10-08
ok, I'm at work for another 6 or so hours, when I get home I'll give that a try, see if I can't figure out what model I'm running.  I appreciate all the help thus far.  I'm really liking what I can get to in ubuntu though...haha...which is why i want this solved and not just revert back to XP...

---

### Post by xOriginalNinjax on 2007-10-09
00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:07.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
01:08.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0222 (rev a1)

That's what I get.  AKA, I don't know that it knows, does it?  I found my driver CD, but I'm running the live CD...so I can't stick it in and see if I can pull anything up (one CD drive ftl).  All I know about it now (well, I've known already) that it's an nVidia nForce2, AGP, 256 mb card.  I'm gonna go to nVidia's site and see if I can't find anything based on that...hahahahha....

---

### Post by xOriginalNinjax on 2007-10-09
ok, opened up the case (derrrrrr, shoulda done this first...RETARDED I AM)...it's a GeForce 6200LE.  I'm dling the 6-series Linux drivers now...seeing if that fixes it...

---

### Post by xOriginalNinjax on 2007-10-09
no go on that, I'm gonna reboot not in live, and try the xserver reconfig again, I found out a few settings I had wrong due to my card not supporting it...let's hope this works...

---

### Post by xOriginalNinjax on 2007-10-09
Ok...nothing.  I'm at your guys' full mercy.  What are your suggestions at this point?

---

### Post by roachk71 on 2007-10-09
Hmm...

Sounds to me like you're not receiving the correct instructions. At this point, envy can't help ya.

First, boot into your hard disk installation.

The proprietary Linux drivers from the nVidia site need to be compiled from source, but don't let this fact hold you back. First of all, is your version of Ubuntu 32- or 64-bit? If you're running 32-bit Ubuntu on a 64-bit system the graphics display will be kinda sluggish compared with 64-bit (at least that's been my experience.)

Next, it is best if you follow the instructions at this nV News Forums thread:

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

Those are the instructions I followed, and the graphics driver works like a charm. Be sure you've downloaded the driver installer script from the nVidia site first.

By the way, my graphics chipset is an nVidia GeForce 6150 LE.

---

### Post by xOriginalNinjax on 2007-10-09
> **roachk71 said:**
> *snip*

Ok, I have NO clue how to do ANYTHING you just said :(  My ubuntu is 32 bit.  I'm only running an AMD XP 3000+, though plan on upgrading to a dual-core X64 motherboard and processor eventually.  I'm gonna see if I can't decipher all this...I'm just so...lost...now.  I never thought drivers for a video card would be so complicated.../sigh.


And the biggest issue is I can't get more than a command prompt off my hard drive install due to an xserver error that won't go away.  At all.  No matter what I do to it.

---

### Post by xOriginalNinjax on 2007-10-09
here's my most recent xserver log...with errors...do I need to disable or reinstall the framebuffer?  That seems to be all I could find wrong...

---

### Post by xOriginalNinjax on 2007-10-09
Oi....anyone? :(  I need this solved...and need your help...really badly.  Like badly badly.

---

### Post by roachk71 on 2007-10-09
If you really need your X server (without acceleration), you could login and type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```and reboot with:
```
sudo reboot
```

I'll have a look at the xserver log you've attached, and try to help from there...

---

### Post by roachk71 on 2007-10-09
Additionally, something that would be an even better help would be your /etc/X11/xorg.conf file as an attachment; Please post that, and we'll see where the problem lies. The X server log isn't much help at this point. :neutral:

---

### Post by xOriginalNinjax on 2007-10-09
SWEETTTTTT.  I'm actually in my HD install now.  Here's the file you asked for btw.  Would it be safe to run the Restricted Drivers to see if it will get my video card working properly?  Or should I be fine now?

---

### Post by roachk71 on 2007-10-09
At this point you're using the unaccelerated nVidia open source driver, which is fine for most applications (except 3D games and screensavers, etc.) The restricted drivers manager may or may not be of help; in fact it didn't help me get full acceleration from the card. Desktop effects certainly didn't work.

Your best bet is to visit the link I mentioned earlier, after downloading the installation file from the nVidia web site, and printing and following those instructions (look in the Debian/Ubuntu section). NOTE: In order to make the installer work, you need to log in from a text console using Ctrl-Alt-F1 (_NOT a terminal window_) and type:

```
sudo init 1
```This will put your computer into single-user text mode for the installation. The installer might complain, but ignore that. Next, go to the directory you downloaded the installer to:

```
cd path to the directory {ex: /home/user/packages/}
```and set the file as executable:
```
chmod u+x filename.sh
```Then, execute it:
```
./filename.sh
```You can, of course use your tab key to complete the filename.

Be sure to select both the replacement OpenGL extensions and the automatic configuration from the installer. Once the installation is complete, restart your machine with a reboot command, and when the X server starts you should be greeted by an nVidia logo and acceleration, to let you know it's working.

And remember, if something goes wrong, you can revert using
```
sudo dpkg-reconfigure -phigh xserver-xorg
```from your user account at any time.

Oh! And where you're told to install a package, simply use, from a terminal window:
```
sudo apt-get install build-essential linux-headers pkg-config xserver-xorg-dev
```
This only needs to be done once.

---

### Post by xOriginalNinjax on 2007-10-09
Well, I'm starting to get there...it's going forward little by little at least...I can actually get INTO the installer for the drivers...but it claims it's missing the "libc header files" and when I run the sudo apt-get, it tells me there's no file specefied and quits the operation.  Where do I go from here?  I feel soooo close...but yet so far away...

---

### Post by doron387 on 2007-10-09
it seems exactly like what is happening to me right now,
i am trying to figure how to copy the xork.conf (the graphics settings) from the live cd,
because they work (!!!) _on_ the xorg.conf that is in the installation.
i think it should work.
if you know how to do this action then go on and tell us, if you don't read my threads right now, it seems that we are getting to the end of this 3 hours long discussion.
doron387

---

### Post by roachk71 on 2007-10-09
Oops... In the case of missing libc6 headers, you also need to use apt-get to install libc6-dev. I should have included that in the reply!

Sorry I'm late replying, but it was about 11:00 pm here, and bedtime for me, since I have work at noon, and like waking up with plenty of time to spare. :KS

---

### Post by xOriginalNinjax on 2007-10-09
You aren't too far from me.  I'm only up in IN.  I was up till 4:30 trying to get this to work.  Luckily, I have an hour till I have to be there.  What is the command line to get the libc6-dev?  is it just **sudo apt-get install build-essential linux-headers pkg-config libc6-dev**?  Am I close?  I hope I'm catching on quick..heh...

---

### Post by roachk71 on 2007-10-09
First, use **sudo apt-get install libc6-dev**, since that'll be required first. If those other packages have already been successfully installed, their installation doesn't need to be repeated.

Was it the installer that gave you the error message, or apt-get? If it's the latter you have a real problem (the developers are probably updating the header package, and you might have to wait until the libc6 headers become available again.)

---

### Post by xOriginalNinjax on 2007-10-09
> **roachk71 said:**
> First, use **sudo apt-get install libc6-dev**, since that'll be required first. If those other packages have already been successfully installed, their installation doesn't need to be repeated.

Was it the installer that gave you the error message, or apt-get? If it's the latter you have a real problem.

libc6 installed.  10 minutes till I leave for work...brb, time to try nVidia installer again...

---

### Post by xOriginalNinjax on 2007-10-09
I have to leave for work...but after the installer finished and I rebooted, I had an xserver kernel error, almost identical to the previous one...what do I need to do now that I have the drivers and kernel correct?  Run the package install I tried that failed?


quick edit:  found out why that previous attempt failed.  I didn't have a specefic header location chosen.  There were a few mirrors I had to pick from or something...not totally sure.  I picked the low-latancy one...but that package install is going now.

---

### Post by roachk71 on 2007-10-09
Okay, now you need to use **sudo nano /etc/default/linux-restricted-modules-common. **Find [FONT=Courier New]DISABLED_MODULES="" and place [/FONT][FONT=Courier New]**nv nvidia_new** between the quotes. Use Ctrl-X to save the file and leave the editor. You're getting that kernel module error message due to a default driver module conflicting with the nVidia kernel module, so it has to be disabled.

Then, use **sudo nano /etc/modules** and add this line to the file:

```
nvidia
```Save and exit again, then reboot. It should work fine after this. Don't forget to re-run the installer to uninstall first, then reinstall and configure! I'd almost forgotten that part again. Phew!

**:eek: A Word of Warning: **It is best to run GNOME instead of KDE, since KDE will always use a default resolution, and using its resolution control will overwrite your xorg.conf file, using the default nv driver. GNOME will allow you to safely change resolutions. :eek:
[/FONT]

---

### Post by xOriginalNinjax on 2007-10-09
> **roachk71 said:**
> Don't forget to re-run the installer to uninstall first, then reinstall and configure! I'd almost forgotten that part again. Phew!


Just to clarify this part; you mean to run the nvidia driver installer to uninstall those drivers, that way I can then run that installer again, to reinstall and configure those drivers, correct?  After this is solved, I'm going to do a step-by-step of how I got this done for other new users btw...

---

### Post by roachk71 on 2007-10-09
That is correct...

Once all this is done, your new nVidia driver should present you with an nVidia logo at X server start-up, to let you know it's working, along with full 2D and 3D acceleration.

I would advise against using desktop effects too much though: they appear to still be a bit unstable (no show-stopping glitches, but some very noticeable bugs.) But you'll love what it does for your screensavers and overall display responsiveness.

---

### Post by xOriginalNinjax on 2007-10-09
> **roachk71 said:**
> That is correct...

Once all this is done, your new nVidia driver should present you with an nVidia logo at X server start-up, to let you know it's working, along with full 2D and 3D acceleration.

I would advise against using desktop effects too much though: they appear to still be a bit unstable (no show-stopping glitches, but some very noticeable bugs.) But you'll love what it does for your screensavers and overall display responsiveness.

Ok, when I get home in about an hour and a half or so, I'll give it a go and see if I can't get it all up and running properly.  The only desktop effect I saw I liked was the "cube" funtion.  Should I avoid using it, or would using just it be fine?  And is there anyway to disable the "flip" effect when using it, so it switches like a normal workspace?

---

### Post by Cariboo1938 on 2007-10-09
> **xOriginalNinjax said:**
>  After this is solved, I'm going to do a _**step-by-step**_ of how I got this done for other new users btw...Hello,
I tried to follow this thread and I was not successful yet to install the new nVidia driver with "envy".  
Problem is that after the installation of new nvidia driver "Xserver failed to start".
I'm looking forward for your step-by-step Howto. 
See my signature for details about my hardware.

---

### Post by roachk71 on 2007-10-09
On my machine, the cube function is iffy at best, so I leave it disabled. You might have better results. Of course, from your machine's description its architecture is 32-bit (Athlon XP). Mine's a 64-bit dual-core system, and the 64-bit Ubuntu version I'm using isn't entirely stable, either.

Improvements continue to be made, though...

There's one final caveat: when your kernel is updated you'll have to repeat this procedure (except maybe editing those two files.) And usually, the core libraries and development headers are updated with it, so you shouldn't have to reinstall those.

---

### Post by xOriginalNinjax on 2007-10-09
SOLVED!!!!!!!!!!!!!!!!!!!!!!! FRICKIN SCORE!!!! You guys ROCK.  Thank you SOOOOO much for the help!  Write up is in progress now.

---

### Post by xOriginalNinjax on 2007-10-10
If you're experiencing an xserver boot error that sends you to command prompt only, start here.  If not, continue on to step 3.
1.In the command prompt, type“```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and set that up as best as you can (it's fairly simple, resolution settings only iirc, and set it up as “nv” as that stands for nVidia.
2.Then, after that completes, type ```
sudo reboot[/CODE” to reboot your system to your hard drive installation of Ubuntu.
3.Once in your hard drive installation, either go to the terminal and type [CODE]lspci
```, open your case and read your card, or skip this if you know what your exact model graphics card is.
4.Now that  you know the model of your graphics card, you can proceed to [www.nvidia.com](www.nvidia.com) and go to the download drivers section, where you can locate the linux drivers for your card (make sure you get the 64 bit drivers if you're running 64 bit...if they're supported)
5.After those have downloaded, figure out the directory they're in (example: mine dled to home/matt/Desktop)  which you can figure out by right clicking on the file, and then write that directory down (or print it out).
6.Then, if you had the xserver issue, continue on from here, if not skip to step 7. (If skipping doesn't work, come back to this step and repeat from here on.)
For safety's sake, and installation time's sake as well, go ahead and run the following in the terminal(unless you've run some of these previously.) ```
sudo apt-get install build-essential linux-headers-2.6.20-16-lowlatency pkg-config xserver-xorg-dev libc6-dev
``` that way when you go to run the installation for the drivers, it has everything it needs.
7.When that finishes, either type in the terminal ```
sudo init 1
``` or press ctrl+alt+F1 to go to command prompt.  If you use the ctrl+alt+F1, when the command prompt comes up, type in ```
sudo init 1
``` to get to the init 1 setup.
8.After getting into init 1, change your directory (cd) so you're in the directory with your nVidia driver (example: my driver was in home/matt/Desktop, so I typed “cd /home/matt/Desktop”)
9.Once you're in that directory, you just type “sh <insert file name here>” (For example, my filename for the drivers was NVIDIA-Linux-x86-100.14.19-pkg1.run, so I used ```
sh NVIDIA-Linux-x86-100.14.19-pkg1.run
```.  Also note, the <> are NOT required, I have them there to show where to input the name)  and press enter.  Your nVidia installer should come up at this point.
10.  As the installer starts up, it recognizes that you're not in init 3 (the standard setup for your graphic interface) and that you're in init 1.  Tell it that you don't want to exit because you know what you're doing.  It'll also bring up things about kernels (at least it did for me) and tell it not to dl them, and just let it build it's own.  It should ask if you want the xserver configured for you, if you don't know how to do so, I suggest letting it, if you have stuff you want to tweak (you l33t h4xor you) tell it no.
11 .After the installer finishes (if it doesn't, post what it says) use ```
sudo nano /etc/default/linux-restricted-modules-common
```. Find the line DISABLED_MODULES="" and place nv nvidia_new between the quotes. Use Ctrl-X to save and exit Nano.  Then ```
run sudo nano /etc/modules
``` and place nvidia at the bottom of the file, then again use Ctrl-X to save and exit.
12.  After saving and exiting that file, use ```
sudo reboot
``` and boot Ubuntu up, where it should at least flash an nVidia logo...at least that's all mine did, and very briefly at that...but if so, congrats!




Kind of a little rough around the edges, but it should get you there fairly simply.

---

### Post by Cariboo1938 on 2007-10-10
> **xOriginalNinjax said:**
> If you're experiencing an xserver boot error that sends you to command prompt only, start here. ......
...............................................................................................
11.After the installer finishes (if it doesn't, post what it says) use “sudo reboot” to restart your computer.   When it boots Ubuntu up, it should at least flash an nVidia logo...at least that's all mine did, and very briefly at that...but if so, congrats!
Kind of a little rough around the edges, but it should get you there fairly simply.So you didn't use "envy" as the installer at all???

---

### Post by roachk71 on 2007-10-10
Nope, Envy didn't work for either of our configurations, so we had to use this (somewhat convoluted) workaround. Neither did the restricted drivers manager.

Oh, and *lib6-dev* should read *libc6-dev*, in case you get a dpkg or apt-get error message.

:)

---

### Post by xOriginalNinjax on 2007-10-10
> **Cariboo1938 said:**
> So you didn't use "envy" as the installer at all???

No, it wouldn't work for my computer (had a missing dependency no matter what I did) so I ran this weird, strange concoction of coding.

> **roachk71 said:**
> Nope, Envy didn't work for either of our configurations, so we had to use this (somewhat convoluted) workaround. Neither did the restricted drivers manager.

Oh, and *lib6-dev* should read *libc6-dev*, in case you get a dpkg or apt-get error message.

:)

Fixed that, thanks.  I said it was rough! hahaha.  This definitely should get you running though.

---

### Post by Cariboo1938 on 2007-10-10
Thank you,  roachk71 and xOriginalNinjax,
for the response...
tonight I take the time to go through this procedure:confused:...
I'll keep you posted...

---

### Post by xOriginalNinjax on 2007-10-10
> **Cariboo1938 said:**
> Thank you,  roachk71 and xOriginalNinjax,
for the response...
tonight I take the time to go through this procedure:confused:...
I'll keep you posted...

Honestly, it shouldn't take you more than an hour or two tops, depending on your internet connection.  Mine took so long because we were all compiling the data...hahah.  It's been compiled now, so it's just a matter of (hopefully) type and go. Good luck and let us know how it goes.

---

### Post by quagmire4278 on 2007-10-10
So I've followed all of these instructions because I've been having the same problems but I still get the same x server error.  I will post the appropriate posts below.

---

### Post by quagmire4278 on 2007-10-10
My x server log says: 

(WW) NVIDIA: No matching Device section for instance (Bus ID PCI:1:7:0) found
(EE) No devices detected
Fatal server error:
no screens found

---

### Post by Cariboo1938 on 2007-10-10
> **xOriginalNinjax said:**
> Honestly, it shouldn't take you more than an hour or two tops,......... Good luck and let us know how it goes. Yes, I certainly will!!!
Before I start do go this, for me, uncomfortable route, I have one more question:
Synaptic Package Manager shows me under "not installed" the packages;
- nvidia-glx
- nvidia-glx-new
- nvidia-new-kernel-source
- and others

What are these for? Aren't these the one I wanted to install with envy?
Sorry, I'm a bit slow......:confused:

---

### Post by roachk71 on 2007-10-10
I doubt it. These are installed by the Restricted Drivers Manager, and they didn't work in this case. You're much better off using the instructions posted in this thread.
Good Luck! Two of us already have fully accelerated video... :KS

---

### Post by roachk71 on 2007-10-10
> **quagmire4278 said:**
> My x server log says: 

(WW) NVIDIA: No matching Device section for instance (Bus ID PCI:1:7:0) found
(EE) No devices detected
Fatal server error:
no screens found

Do you have an older nVidia card, or a newer model? The older cards may require the legacy drivers installed through the Restricted Drivers Manager, Synaptic or Apt-get.

Or, have you told the installer you want it to modify your xorg.conf file?

Note: Discrepancy found; Please see the next post.

---

### Post by roachk71 on 2007-10-11
Uh Oh, the howto is missing two important steps:

After the installer finishes, open **sudo nano /etc/default/linux-restricted-modules-common. **Find the line **DISABLED_MODULES=""** and place **nv nvidia_new** between the quotes. Use Ctrl-X to save and exit Nano.

Next, you need to add the nVidia kernel module to your boot routine for the acceleration to work fully. Use:

```
sudo nano /etc/modules
```and place **nvidia** at the bottom of the file. Reboot, and all should be well.

It appears that you might be experiencing a driver conflict with the built-in modules. [-X

---

### Post by xOriginalNinjax on 2007-10-11
> **roachk71 said:**
> Uh Oh, the howto is missing two important steps:

After the installer finishes, open **sudo nano /etc/default/linux-restricted-modules-common. **Find the line **DISABLED_MODULES=""** and place **nv nvidia_new** between the quotes. Use Ctrl-X to save and exit Nano.

Next, you need to add the nVidia kernel module to your boot routine for the acceleration to work fully. Use:

```
sudo nano /etc/modules
```and place **nvidia** at the bottom of the file. Reboot, and all should be well.

It appears that you might be experiencing a driver conflict with the built-in modules. [-X

This is why you're here, I forget things.  Fixing again.


Edit:
Fixed for the addition, as well as adding "code" lines in, for simpler reading.

---

### Post by Cariboo1938 on 2007-10-11
> **xOriginalNinjax said:**
>  .......................
6.Then, if you had the xserver issue, continue on from here, if not skip to step 7. (If skipping doesn't work, come back to this step and repeat from here on.)
For safety's sake, and installation time's sake as well, go ahead and run the following in the terminal(unless you've run some of these previously.) “[COLOR="Magenta"]sudo apt-get install build-essential linux-headers-2.6.20-16-lowlatency pkg-config xserver-xorg-dev libc6-dev[/COLOR]” that way when you go to run the installation for the drivers, it has everything it needs.......................

Can I run [COLOR="Magenta"]this command[/COLOR] at any time. 
I' m just about checking if the conditions listed [HERE]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") are full filled.
:confused:

---

### Post by Cariboo1938 on 2007-10-11
> **roachk71 said:**
> I doubt it. These are installed by the Restricted Drivers Manager, and they didn't work in this case. You're much better off using the instructions posted in this thread.
Good Luck! Two of us already have fully accelerated video... :KS
OK, I got the picture...;)

---

### Post by xOriginalNinjax on 2007-10-11
> **Cariboo1938 said:**
> Can I run [COLOR="Magenta"]this command[/COLOR] at any time. 
I' m just about checking if the conditions listed [HERE]("http://www.nvnews.net/vbulletin/showthread.php?t=72490") are full filled.
:confused:

They should be fulfilled.  I based some of the guide off of that one, as I was reading up EVERYTHING I could get, along with roachk's assistance.  And yes, you can run it whenever pre-installer...I just put it in the most logical order for what is going on.

Also, I put the guide (in a cleaner looking format) on the first page that way it's easier to find. [first page, first post])

---

### Post by Cariboo1938 on 2007-10-11
> **xOriginalNinjax said:**
> ....................
Also, I put the guide (in a cleaner looking format) on the first page that way it's easier to find. [first page, first post])Thanks for the 'cleaner format' of your guide!
I'm ready to go for it now.....talk to you later....
Thanks again:roll:

---

### Post by xOriginalNinjax on 2007-10-11
> **Cariboo1938 said:**
> Thanks for the 'cleaner format' of your guide!
I'm ready to go for it now.....talk to you later....
Thanks again:roll:

Don't thank me till it's done...hahaha

---

### Post by Cariboo1938 on 2007-10-11
> **xOriginalNinjax said:**
> Don't thank me till it's done...hahaha
It's not quite done yet....
Going through the installation procedure as you describe it was a 'piece of cake'...everything went smooth...No error messages at all...
Coming to the finish of the NVIDIA installer there was one question asked which you didn't mention: "Install NVIDIA's32-bit compatibility Open GL libraries?"
I didn't exactly know what I did when I answered "Yes", I just thought it wouldn't hurt. 
So anyway, after "reboot" I got this dark screen with this bothering message: "Failed to start Xserver bla, bla, bla..." and I had to change my file  /etc/X11/xorg.conf  exchanging 'nvidia' for 'nv' in the device section to get the GUI running again. I can not imagine what went wrong! Would it help if I post  'log-files'? If yes, which ones?

BTW:
My Synaptic Package Manager shows only two 'nvidia-related' packages installed:
--- NVIDIA binary kernel module for Linux 2.6.20-15-generic 100.14.19-0ubuntu3+2.6.20-15.27  and
--- NVIDIA binary kernel module common files 20051028+1ubuntu7
whereas it seems that all linux headers are there.
I have no idea where I would find the new nVidia driver which was installed flawless.

PS.: 
With the 'find' command I checked my computer for all nvidia related files and their locations. I attached this result of the 'find' command. 
Isn't it quit a mess?

---

### Post by roachk71 on 2007-10-11
The two packages you just mentioned are conflicting modules, and should be removed (these are provided through the Ubuntu repos, and are less than reliable on the latest cards and chipsets.)

After those are removed, retry the installer twice, once to remove the existing drivers, and again to reinstall.

Let me know how this goes.

OOPS--
I'd nearly forgotten (since I just got home from work and am tired): the website you need to download the latest driver from is at this [link.]("http://www.nvidia.com/")
Avoid the prerelease drivers, since they may not be too stable.

---

### Post by Cariboo1938 on 2007-10-11
> **roachk71 said:**
> The two packages you just mentioned are conflicting modules, and should be removed (these are provided through the Ubuntu repos, and are less than reliable on the latest cards and chipsets.) After those are removed, retry the installer twice, once to remove the existing drivers, and again to reinstall.Let me know how this goes. My graphic card is not really the latest though it's a GeForce FX5200.
To remove the packages, can I use Synaptic PM?

> **roachk71 said:**
> 
OOPS--
I'd nearly forgotten (since I just got home from work and am tired): the website you need to download the latest driver from is at this [link.]("http://www.nvidia.com/")
Avoid the prerelease drivers, since they may not be too stable.

The driver I downloaded from [THERE]("http://www.nvidia.com/object/linux_display_amd64_100.14.19.html") is: NVIDIA-Linux-x86_64-100.14.19-pkg2.run. Is this correct?

BTW:
I attached a text file with locations of nvidia related files on my computer. I think it's quite a mess, isn't it?
I also attached a Screenshot of Synaptic Package Manager where I marked the two packages in question for 'complete removal'. I'm not sure if there will be deleted to much?

---

### Post by roachk71 on 2007-10-11
It is correct, if your CPU is an Athlon 64 or 64 X2, or 64-bit Intel chip. To check what kind of CPU is in your machine, open a terminal window, and type:
```
uname -a
```If it's listed on the right-hand side as x86_64, you should be fine. Next, you have to restart into runlevel 1 (using sudo init 1), change into the directory containing the installer, and chmod +x {insert the filename of the installer here}. Then, execute the installer with sh {installer filename again}. The braces aren't required. Make sure it installs both the driver and OpenGL acceleration!

Also, make certain you allow the installer to modify your xorg.conf file. It will automatically create a backup.

The final steps are the most important. If these aren't performed the built-in driver modules will be loaded at boot time, conflicting with the nVidia accelerated drivers. On the command line, use:

```
nano /etc/default/linux-restricted-modules-common
```Find the line containing **DISABLED_modules=""**, and place **nv nvidia_new** inside the quotes. Now save the file and close the editor with Ctrl-X.

And finally:

```
nano /etc/modules
```and place **nvidia** at the end of the file. Save and exit with Ctrl-X. Perform these steps only if you haven't already.

Now, simply issue a **reboot** command. Everything should work as described at this point. A special note: Some monitors are a bit slow in mode and resolution switching, so you may or may not see the logo. Not to worry; if your X server starts without a hitch, everything worked.

**Advisory:** Some 3D games rely on the open source GLX libraries. Until the game devs work everything out with nVidia regarding development with their driver source, no luck there. Besides, if you have a modern nVidia card you probably couldn't play these games with the default configuration anyway...

---

### Post by Cariboo1938 on 2007-10-11
> **roachk71 said:**
> The two packages you just mentioned are conflicting modules, and should be removed .....Can I use Synaptic PM for that? It seems it will remove more (see attachment).
What do you think about the nVidiaFiles?(see also attachment)

---

### Post by roachk71 on 2007-10-11
Make sure you're running from the generic kernel before making these changes, since removing a running kernel could have unpredictable results!

[B]If you've removed that, you should reinstall it right away.
[/B]
Press [Esc] at the GRUB prompt before the timer expires to get the boot menu.

By the way, could you post a screenshot of the properties?

Edit: Never mind that, it is safe to remove those...I didn't read that well enough the first time. :mrgreen:

---

### Post by Cariboo1938 on 2007-10-12
> **roachk71 said:**
> 
By the way, could you post a screenshot of the properties?
 Which properties do you mean?
I attached the /boot/grub/menu.lst
> **roachk71 said:**
> 
Edit: Never mind that, it is safe to remove those...I didn't read that well enough the first time.:mrgreen: So you say I can remove the packages which the Synaptic PM listed?(see screenshot)

---

### Post by xOriginalNinjax on 2007-10-12
Yeah, you should be able to.  Sounds to me like when it asked that, you reverted it to 32 bit...and you're running 64...so it had conflicts there as well maybe.  :shrug:

---

### Post by Cariboo1938 on 2007-10-12
> **roachk71 said:**
> ......  To check what kind of CPU is in your machine, open a terminal window, and type:
```
uname -a
```
Uname -a gives me the kernel version installed:
> root@karibu-desktop:/# uname -a
Linux karibu-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
root@karibu-desktop:/# 
 While -->System -->Preferences -->Hardware Information shows the CPU and other hardware components.

---

### Post by Cariboo1938 on 2007-10-12
> **roachk71 said:**
> 
By the way, could you post a screenshot of the properties?
Edit: Never mind that, it is safe to remove those...I didn't read that well enough the first time. :mrgreen:
Here are the properties of the two packages I'm supposed to remove:

---

### Post by Cariboo1938 on 2007-10-12
> **xOriginalNinjax said:**
> Yeah, you should be able to.  Sounds to me like when it asked that, you reverted it to 32 bit...and you're running 64...so it had conflicts there as well maybe.  :shrug:having  Feisty-64bit installed, are you saying I'm running into conflicts when I answer 'Yes' to the installer question "Install NVIDIA's32-bit compatibility Open GL libraries?"
Or shall I, with my next try, rather answer 'No' at this point?:confused:

---

### Post by xOriginalNinjax on 2007-10-12
> **Cariboo1938 said:**
> having  Feisty-64bit installed, are you saying I'm running into conflicts when I answer 'Yes' to the installer question "Install NVIDIA's32-bit compatibility Open GL libraries?"
Or shall I, with my next try, rather answer 'No' at this point?:confused:

I would answer no, because it's possible with it being a "compatibility option" that it may be over-riding the 64 bit...and hence a problem.

---

### Post by Cariboo1938 on 2007-10-13
> **roachk71 said:**
> 
After those are removed, retry the installer twice, once to remove the existing drivers, and again to reinstall.

Let me know how this goes.

I started a second installation after removing the package "nvidia-kernel 2.6.20-15-generic". I did not remove the package "nvidia-kernel-common" yet, because it would also had removed the packages "linux-generic, linux-restricted-modules-generic, linux-restricted-modules-2.6.20-15-generic and linux-restricted-modules-2.6.20-16-generic".
I was not sure if this would be OK.
In contrary to the first try, I got now an Error: 
"Unable to create 'lib/modules/2.6.20-15-generic/nvidia/nvidia.ko' for copying(No such file or directory)". The dialog offered only an 'OK' to enter. After that I got the Warning:
"Unable to restore file 'lib/modules/2.6.20-15-generic/nvidia/nvidia.ko'. also here, the dialog offered only an 'OK' to enter. The installation finished and after reboot, again Xserver did not start! I seldom give up, but here I just don't know what to do anymore to get it to work.:frown:

BTW. The Installer didn't offer an option to 'remove existing drivers' in my understanding of the dialog.

---

### Post by roachk71 on 2007-10-13
In this case, you may need more than just the Linux headers, you might also need to install and unpack **linux-source**. Here's how:[LIST=1]
[*]After installing **linux-source** via Synaptic or apt-get, open a terminal window and use **sudo -s** to enter superuser mode.
[*]Use **cd /usr/src/** to enter your source directory,
[*]Now, type **tar --bzip2 -xvf linux-source-***whichever version is installed***.tar.bz2. **Unpacking will take a few minutes.
[*]Next, type in **ln -s /usr/src/linux-source-***version* **/usr/src/linux.** This will create a necessary symlink for the build procedure.
[*]**Important: **You'll probably need to copy the current kernel configuration. issue **cp /boot/config-***version* **/usr/src/linux/.config**
[*]Now retry the driver build.[/LIST]It would appear that the Linux kernel headers alone aren't enough for the build. And running the installer with the *--uninstall* option should uninstall the drivers.
I usually make a point of installing both the kernel headers *and *the kernel source tree, just in case. :!:[B]HOWTO ALERT:!:

[/B]If all of this doesn't work still, you're probably running a 32-bit kernel on 64-bit hardware, (which, in itself isn't a bad thing,) and simply downloaded the wrong installer. Try downloading the 32-bit installer instead.

---

### Post by roachk71 on 2007-10-13
Something else I just thought of:

It looks like you have an old kernel (pre-update) still on your hard drive. You may want to keep it handy, but to avoid confusion you should remove old kernels. This also frees hard disk space, if you're running low.

Again, this can be done via Synaptic. Just make sure you're running the latest kernel before proceeding, and select the kernel image itself for removal.

---

### Post by Cariboo1938 on 2007-10-13
> **roachk71 said:**
> In this case, you may need more than just the Linux headers, you might also need to install and unpack **linux-source**. Here's how:[LIST=1]
[*]After installing **linux-source** via Synaptic or apt-get, open a terminal window and use **sudo -s** to enter superuser mode.
[*]Use **cd /usr/src/** to enter your source directory,
[*]Now, type **tar --bzip2 -xvf linux-source-***whichever version is installed***.tar.bz2. **Unpacking will take a few minutes.
[*]Next, type in **ln -s /usr/src/linux-source-***version* **/usr/src/linux.** This will create a necessary symlink for the build procedure.
[*]**Important: **You'll probably need to copy the current kernel configuration. issue **cp /boot/config-***version* **/usr/src/linux/.config**
[*]Now retry the driver build.[/LIST]It would appear that the Linux kernel headers alone aren't enough for the build. And running the installer with the *--uninstall* option should uninstall the drivers.
I usually make a point of installing both the kernel headers *and *the kernel source tree, just in case. :!:[B]HOWTO ALERT:!:

[/B]If all of this doesn't work still, you're probably running a 32-bit kernel on 64-bit hardware, (which, in itself isn't a bad thing,) and simply downloaded the wrong installer. Try downloading the 32-bit installer instead.

Hi, first of all I want to say thank you for the detailed response!
Because I'm not really familiar whit these kind of actions I'm very hesitant to begin before I'm not knowing , at least roughly, what I'm doing. So, here some questions:
Synaptic tells me that there are two linux-source packages not installed-
a) linux-source Version 2.6.20.16.28.1
b) linux-source-2.6.20 Version 2.6.20.16.32
Which is the correct one?
The file browser tells me that there are currently two /boot/config<version>files:
a) config-2.6.20-15-generic
b) config-2.6.20-16-generic
Because the system boots into 2.6.20-16, I believe you mean b) to be copied to **/usr/src/linux/.config**

BTW: When I opened /usr/src/linux/.config with gedit I noticed that it is referring to kernel 2.6.20-15 while the system boot with versin 2.6.20-16

I'll attach the config files (they are text-files, the extension zip is fake)and maybe you find time to check them. Maybe this /usr/src/linux/.config is the reason for the dilemma.

---

### Post by Cariboo1938 on 2007-10-13
> **roachk71 said:**
> Something else I just thought of:

It looks like you have an old kernel (pre-update) still on your hard drive. You may want to keep it handy, but to avoid confusion you should remove old kernels. This also frees hard disk space, if you're running low.

Again, this can be done via Synaptic. Just make sure you're running the latest kernel before proceeding, and select the kernel image itself for removal.
I don't know if this is the actual kernel but this is installed:
> karibu@karibu-desktop:~$ uname -a
Linux karibu-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linux
karibu@karibu-desktop:~$ 

---

### Post by roachk71 on 2007-10-13
The 2.6.20-15 kernel ought to be removed in this case. Like I said, this'll help avoid confusion during the installation (in other words, you won't end up installing into the wrong kernel's directories, or booting the wrong kernel only to have your X session crash.)

The one you're running now is the updated kernel. And be sure to delete the .config file and replace it with the 2.6.20-16 configuration file.

---

### Post by Cariboo1938 on 2007-10-14
> **roachk71 said:**
> The 2.6.20-15 kernel ought to be removed in this case. Like I said, this'll help avoid confusion during the installation (in other words, you won't end up installing into the wrong kernel's directories, or booting the wrong kernel only to have your X session crash.)The one you're running now is the updated kernel. And be sure to delete the .config file and replace it with the 2.6.20-16 configuration file.So, this means I do **not** have to go through the procedure you described earlier (installing linux-source), am I right?

---

### Post by roachk71 on 2007-10-14
Actually, I'm not quite too sure about that. Like I said, I've made a habit of installing the kernel source and unpacking then setting it up, just in case it's required (and it *is *for some configurations.) Besides, you'll probably end up compiling other modules, and some of those will need the kernel source.

Generally, you're better off with the source tree, so keep that. The kernel source is usually updated with the kernel packages in the first place, so you won't have to worry about updating it yourself manually.

---

### Post by Cariboo1938 on 2007-10-14
After changing  the "usr/src/linux/.config" to the 2.6.20-16 version, I tried the installation again---no success! Still Xserver does not start, although I don't get any error message during the installation procedure.  I attached the 'nvidia-installer.log' (the extension 'zip' is fake). Do I really need to install the linux-source? if yes, which one?
Maybe an expert can figure out what's wrong with me, I mean with my installation?

---

### Post by roachk71 on 2007-10-14
Have you tried downloading the 32-bit installer and running that after uninstalling the installed drivers?

It sounds to me like you're using a 32-bit OS on your machine. The 64-bit drivers won't even initialize with a 32-bit kernel.

---

### Post by Cariboo1938 on 2007-10-14
> **roachk71 said:**
> 
It sounds to me like you're using a 32-bit OS on your machine. The 64-bit drivers won't even initialize with a 32-bit kernel.
Isn't "uname -a" what tells me which OS is installed?
> root@karibu-desktop:~# uname -a
Linux karibu-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC [COLOR="Magenta"]2007 x86_64 GNU/Linux[/COLOR]
root@karibu-desktop:~#

---

### Post by roachk71 on 2007-10-14
It doesn't tell you whether 32- or 64-bit Ubuntu is installed, only that you're running the Generic kernel (which supports 64-bit architectures). It does tell you what CPU type is installed in your machine, though.

The kernel may support both architectures, but the 32-bit system and X libraries don't. This difference could explain why the 64-bit installer won't work for ya. Try downloading and installing the 32-bit driver version, and we'll see if the problem persists. Another option would be allowing the script to install the 32-bit compatibility libraries, but this would probably have little effect.

This is also the condition the installation log file suggests...

Note: According to the nVidia driver download site, your card is supported by the accelerated drivers.

---

### Post by Cariboo1938 on 2007-10-15
> **roachk71 said:**
>  It does tell you what CPU type is installed in your machine, though.Sorry, but I don't understand where > Linux karibu-desktop 2.6.20-16-generic #2 SMP Sun Sep 23 18:31:23 UTC 2007 x86_64 GNU/Linuxtells me what CPU Type I have installed in my computer?

I got a live CD shipped from Canonical Ltd. and the label says:**Ubuntu 7.04 for your 64-bit PC** 
'More Info':
I Installed the OS from there and I assume that 64-bit system is installed.
The file README.diskdefines on the CD says:> #define DISKNAME  Ubuntu 7.04 "Feisty Fawn" - Release amd64
#define TYPE  binary
#define TYPEbinary  1
#define **ARCH  amd64**
#define **ARCHamd64  1**
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1
The first lines of the file md5sum.text show only entries about amd64 packages: > cb6f52393adee4793dcdf7010a80f3e9  ./dists/feisty/main/**binary-amd64**/Release
2dc09c91fd2257004dc345da9229d315  ./dists/feisty/main/**binary-amd64**/Packages
338467c42464734ada995155cc157278  ./dists/feisty/main/**binary-amd64**/Packages.gz
b086bd57e3a16dcc1bcc27cf677a2c18  ./dists/feisty/restricted/**binary-amd64**/Release
5da46419b8418cb4b84952f86afc54f1  ./dists/feisty/restricted/**binary-amd64**/Packages
89fdde0da0d90580329ee70a5f68c45a  ./dists/feisty/restricted/**binary-amd64**/Packages.gz
627e219901cb6fb5d700bb23ca4503ea  ./dists/feisty/Release
bfe5ed525bb8e11434f3c8f7cd1f6284  ./dists/feisty/Release.gpg
2e0205dadb5a1f48d1a6b46bfac0b1f4  ./.disk/info
d6229877f2068de9b852cf1a0ae5aa10  ./.disk/release_notes_url
7f0456c23a95237a4a4762ee9636a70c  ./README.diskdefines
I can't understand why there could be any doubt about having a 64-bit installation?

---

### Post by roachk71 on 2007-10-15
Not the specific CPU, just which type (x86_64).

Whoa, all these steps, and we still can't get that card recognized by the driver. I'll have to research the subject in more detail...

---

### Post by Cariboo1938 on 2007-10-15
> **roachk71 said:**
> Not the specific CPU, just which type (x86_64).
OK, I got it....and thanks for offering more research...
If you would like to check, I put 'More Info'  about my installation to my previous reply....

---

### Post by roachk71 on 2007-10-15
I've been looking through other threads and websites, and found that the nvidia-kernel startup option may have to be disabled, since it's useless when using the accelerated driver.

By the way, you did have the correct version of the installer the first time, since you're running the 64-bit Ubuntu.

Not certain if this'll work for you, but it did for me, so I'll include some instructions:[LIST=1]
[*]Use Synaptic to install **sysv-rc-conf.**
[*]Open a terminal window, and type the command as shown above, preceded with **sudo**.
[*]Use Ctrl-N to scroll to the next page, Ctrl-P for previous, until you encounter nvidia-kernel- something. It may be abbreviated with a dollar sign at the end.
[*]You might want to note which runlevels have it enabled, so you can re-enable it later if it doesn't work.
[*]Disable this service by clearing the X's with the space bar.
[*]use Q to quit. Any changes are automatically saved.
[*]Reboot your computer.[/LIST]There are additional services you could disable, but disabling the wrong services could make your computer unusable until they're re-enabled, so let's leave those for now...

---

### Post by Cariboo1938 on 2007-10-16
For roachk71;
Thank you very much for your patience and for your help...
I'm kind of a 'chicken' and I don't have enough experience to dare this kind of operations you mentioned in your previous post. I wait until Envy works. I reported my difficulties and they sent me a bug confirmation#, so some how they know about the problem.

---

### Post by roachk71 on 2007-10-16
I wish you the best of luck...At least you still have use of the open source nVidia driver (without acceleration) and, if necessary, you could use "vesa" in a pinch. Frankly, I'm kinda stumped.

These solutions work for some and not for others, and it seems we couldn't help much in this case.

Of course, I Googled around regarding MSI and their motherboards. It seems these boards have a few compatibility issues.

---

### Post by Cariboo1938 on 2007-10-22
I'm back here at the "[SOLVED]nVidia.." thread because the Envy team couldn't help me and I hope the issue can be 'SOLVED' for me too. 
They recommended to contact [THAT FORUM]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14") to get help. Now, there I got the information that I have to upgrade my BIOS, specially to enable the IOMMU option, and now I'm totally lost...what on earth is that and what is the problem with these drivers. Since I joint the Ubuntu Community in 2006 I had trouble with each release (Dapper, Edgy, Feisty) to get updated nvidia drivers running and it always takes days, even weeks to settle the issue. 
In Feisty there is the "Restricted Drivers Manager" and  it doesn't work for my installation, and even worse, nobody is out there to help...
What the heck ...........????

Edit:
I had to edit /boot/grub/menu.lst:

1) Find this section and add "iommu=noaperture":
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e4af70f0-d555-49ab-8dd0-687cc3e7f81c ro [COLOR="Magenta"]iommu=noaperture
[/COLOR]
2) Save the file and type:
Code: "sudo update-grub"

and then 
3) Restart my computer!

BTW:
There must be a conflict between my BIOS (Phoenix Award Ga -K8NS Ultra-939 F5) and the kernel so that AGP aperture is not reported correctly. It works right now with the nvidia-glx-new driver but sooner or later I have to get a BIOS upgrade.

---

