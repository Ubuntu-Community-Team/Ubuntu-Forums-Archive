---
title: "Newest updates screwed up my rig."
date: 2007-02-10
forum: General Help
---

### Post by Roasted on 2007-02-10
I got the latest updates and it said system restart required. So I reboot and I get all of these nvidia errors. I can't boot into a gui now. I forget what the errors were, but there were a few, all having to do with nvidia failing to run properly or something.

This is great. You get an update and this happens? Even Microsoft was better than this!! :(

---

### Post by PriceChild on 2007-02-10
Hi.

Could you tell me what method you used to install the nvidia drivers please?

---

### Post by Roasted on 2007-02-10
Uhh, what method? Uh. I don't even know how to answer that. Everything just seemed to work when I booted Edgy up. *shrug*

---

### Post by CodyEbberson on 2007-02-10
My machine is also screwed up after the latest updates.

I installed nvidia drivers as described here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

At startup, I get the error message  "Screens not found"

I reverted my xorg.conf to the original with the "nv" drivers.  Now Ubuntu seems to startup because I get the drum sounds that you normally get at the login screen, however nothing is sent to the screen, at all.  (my monitors show the little animation as if the computer was powered off)

I have an nvidia geforce 6800 with dual mon.

---

### Post by Roasted on 2007-02-10
Cody, so even though you put the nvidia drivers in, you're still having issues? :(

---

### Post by CodyEbberson on 2007-02-10
Correct, neither "nvidia" nor "nv" are functional for me right now.

"nvidia" crashes and burns at startup with "Screens not found"
"nv" does not crash, but does not output anything to the monitors

---

### Post by mrbungle on 2007-02-10
i am also having the same problem:confused: 


this seems to happen every couple updates i do.

---

### Post by Roasted on 2007-02-10
Can we revert back to the system was prior to the updates?

---

### Post by Maestro23 on 2007-02-10
> **CodyEbberson said:**
> Correct, neither "nvidia" nor "nv" are functional for me right now.

"nvidia" crashes and burns at startup with "Screens not found"
"nv" does not crash, but does not output anything to the monitors

Don't know if you Nvidia guys have seen this thread.  It discusses the latest updates and Nvidia problems. 36-page thread, but I remember seeing a ton of Nvidia post in there.

[http://ubuntuforums.org/showthread.php?t=356408&page=36](http://ubuntuforums.org/showthread.php?t=356408&page=36)

---

### Post by kvonb on 2007-02-10
You lot MUST have the Nvidia binary drivers installed (from the Nvidia website).

When you installed it, it had to build a kernel module, the module is built to run on the kernel version at the time of install.

Now if the kernel changes, the module becomes outdated, and needs to be re-compiled in order to work with the new kernel.

So what you need to do is re-run the Nvidia driver/install package.

If you don't know how to do it, see Pricehild's excellent howto on this page:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Go straight to STEP2, Option2, and follow the instructions exactly!

You DO NOT need to go to STEP3, stop there and reboot.

Everytime there is a kernel update YOU WILL HAVE TO DO THIS AGAIN, so keep the instructions and driver handy.

If this is too much of a hassle for you, then you could always turn off updates and just keep the system as it is (once it's working again that is!), or switch to another O/S :).

Regards, Kev :)

---

### Post by Roasted on 2007-02-10
So since I can only get into the command line, I just log in, and type all of those commands in at the command line? Am I still going to be able to edit my sources list if I'm stuck in command line?

---

### Post by CodyEbberson on 2007-02-10
Excellent, that worked for me.  I'm up and running again.

Roasted--  Yes, you'll need to run those commands.  If you don't still have the latest nvidia install script (the "NVIDIA-Linux-x86-1.0-9629-pkg1.run"), you'll have to download it again.  You can download files using the wget command.

---

### Post by freddybob on 2007-02-10
Here is how I solved the same problem...

1. after the "Failed to start X server" message I got to the command prompt and entered "**sudo dpkg-reconfigure xserver-xorg**"

2. I accepted all the default values in the reconfigure wizard except that I chose **VESA** as the video driver

3. when that was completed I rebooted the machine and was able to get back into Ubuntu - but without 3D acceleration

4. I then downloaded and ran **Envy** following the simple instructions on this page: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Full thread: [http://ubuntuforums.org/showthread.php?t=357868](http://ubuntuforums.org/showthread.php?t=357868)

---

### Post by Roasted on 2007-02-10
Okay. Confused. You guys just told me I could edit my sources.list file in order to add the repo, but with me it said I cannot open display. Sooooo how can I add the repo to fix this issue? I'm speaking about the repository, the first one listed in the very first step at step 2. It just says, add this repo: *repolistedhere*. Sooooooooo now what?

---

### Post by Roasted on 2007-02-10
Hi. Me again. I hate Windows. How do I edit the repos from the command prompt? THX!

---

### Post by dabl on 2007-02-10
Here's a tip, from a semi-noob that was recently a total noob.  Get the "Envy" installed from Alberto Milone's site here:

[http://albertomilone.com/projects.html](http://albertomilone.com/projects.html)

Follow the instructions to install Envy.  Then, in your console window, enter "envy" and it will bring up the driver installation routine.  On my system, there's a little trick.  Here's how it goes. When I run Envy, it starts by telling me that it never heard of my Nvidia card, do I want to continue?  I give it a "yes".  Then it tells me the same thing again, and asks if I know what the heck I'm doing.  Disregarding the truth, I give it another "yes".  Then it plays its trick -- it disappears and leaves me looking at a blinking cursor.  But, knowing nothing about unix, I didn't know any better than to do a Ctrl-Alt F1, and lo and behold there it is on the first console screen, asking if I want to start the X server?  I give it a "y", and it runs the X server, starting with the big Nvidia splash screen.  Afterwards, it always boots to the X window system automatically, after showing the Nvidia splash screen.

Now, this morning when I rebooted (and after the kernel update), I had exactly the same situation as the first guy on this thread reported, and found myself looking at the damned text login prompt.  All I did was type "envy", and VOILA! it re-installed my Nvidia driver, started the xserver, and all is OK-fine on my system.

Today's two cents' worth.  :guitar:

---

### Post by Roasted on 2007-02-10
Wait, so I'm supposed to download something and install it? How do you reckon I do that from the command prompt?

---

### Post by dabl on 2007-02-10
You need to shutdown and reboot, and choose the previous kernel version.  From the command prompt, give it "sudo shutdown -r now", followed by the administrator password.

Upon reboot, when you get the grub menu list, cursor down two rows to the 2.6.17-10-generic, and touch "Enter".  If it worked yesterday, it should still work today.  Then you can download Envy and proceed.

---

### Post by RRS on 2007-02-10
> **Roasted said:**
> Wait, so I'm supposed to download something and install it? How do you reckon I do that from the command prompt?

```
sudo nano /etc/apt/sources.list
```
This will allow you to make any needed changes to your sources list.
```
sudo apt-get update
```
```
sudo apt-get install "whatever you need"
```

---

### Post by Roasted on 2007-02-10
Aight, got it workin with using sudo nano to edit the sources.list.

Little confused though. The stable edgy repo was already in there. I didn't realize it, and added a 2nd one and got an error. I searched through and saw the same repo twice, so I took one out, and changed the other to the unstable version, then updated. Okay fine, no errors. So I figured I'd take the unstable one out, and put the stable one in. Updated. Okay fine. No errors. But I wonder why? Why did I get no errors the 2nd time but originally I got errors? Blah, but besides that, it took a solid 15 minutes to update everything and finally I saw the gorgeous Ubuntu screen and logged in. Here I am. <3

fyi - I used the guide that I believe was posted on the first page. I only used "step 2" of the setup, because I believe the entire setup was how to get beryl running, but step 2 of the guide was STRICTLY to get nvidia working again, which worked for me.

---

### Post by kvonb on 2007-02-10
> Roasted: fyi - I used the guide that I believe was posted on the first page. I only used "step 2" of the setup, because I believe the entire setup was how to get beryl running, but step 2 of the guide was STRICTLY to get nvidia working again, which worked for me.
> kvonb: Go straight to STEP2, Option2, and follow the instructions exactly!

You DO NOT need to go to STEP3, stop there and reboot.That is exactly what I said to do in my post :).

Glad to hear you got it working :).

We had a test at school one day, (back in the good old days, when they actually taught stuff in schools!), in English class I think it was.  The test was a single sheet of paper, with an introduction at the top, a list of about 10 questions, and a closing paragraph.

The introduction said this: "Put your name on the paper then read through this entire page before answering any questions on this sheet.  Give the best answer using clear and concise language."

Next some rather hard questions.

The interesting bit was the last paragraph on the page, it said: "Do not answer any of the questions on this paper, if you do you will fail the test!"

And guess how many people failed, me included? :rolleyes:

---

### Post by thx_1138 on 2007-02-11
I solved the problem on my rig without having to use an outside script

I first rebooted into the previous stable kernel by selecting it from the list in grub (2.6.17.10) and boot up fully. once you are done, bring up a terminal and type

sudo apt-get update
sudo apt-get -f install linux-generic
sudo apt-get -f install linux-headers-generic
sudo apt-get -f install linux-image-generic
sudo apt-get -f install linux-restricted-modules-generic
sudo apt-get -f install nvidia-glx

I would only say to try this if you are running an nvida card, I had to rebuild the module for my ati card on my laptop. I hope this helps anyone whom had issues after the kernel update if there are still some of those whom are stuck on getting it fixed

---

### Post by racmar on 2007-02-11
Yup, all I had to do was:
```
sudo apt-get install linux-restricted-modules-generic
```

Also, I found this out by re-running automatix2 using a no-machine's nxserver / nxclient from my laptop.

---

### Post by Spr0k3t on 2007-02-11
I don't mean to thread jack but my issue is related.  Let me give you details here.

My computer system is over 200' from the closest router in my house (as the cord runs), so I have to use wireless.  When I try to use the updated kernel (2.6.17-11) with "nvidia", X refuses to start.  If I use "nv" my second monitor does not function and my wireless is bunk.  In 2.6.17-10, the wireless card works out of the box.

**Wireless LSPCI Line** 
02:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

**VGA LSPCI Line**
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)

I read through PriceChild's absolutely wonderful guide (which is the same one I used to set up my Edgy install), but without being able to connect to a network, what are my options?

Almost forgot, if I use Envy I get the message "Your graphic card does not seem to be supported by the driver." and then quits regardless of what option I type.

---

### Post by Spr0k3t on 2007-02-11
ACK!  Okay, I packed up my system and moved it to the part of the house where I could get wired internet access.  I was able to upgrade my kernel and install the nVidia drivers according to PriceChild's Step2Option2, but now I have no wireless connectivity.  The Netgear card (AR5212 chipset) isn't recognized.  Any suggestions?

---

### Post by rag on 2007-02-11
I manually updated 'linux-restricted-modules-2.6.17-10-386' to 'linux-restricted-modules-2.6.17-11-386' and everything worked again.

---

### Post by Spr0k3t on 2007-02-11
I'll give that a shot and post my findings.

---

### Post by gommle on 2007-02-11
I found a nice solution with almost no command line stuff, if you have Automatix2 installed.

When in command line, type:
```
sudo nano /etc/X11/xorg.conf
```

edit the Device section and change
```
Driver "nvidia"
```
to
```
Driver "vesa"
```.

Now type
```
sudo killall gdm
sudo gdm
```

Now just start up Automatix2, uninstall the Nvidia drivers, and install them again, without restarting. Restart after you have installed them. Now it should work fine :D

---

### Post by Spr0k3t on 2007-02-11
I left Automatix2 out of my system when I did my main computer (lappy has since been redone as well without Automatix2).  Personally I would rather learn what needs to be done in the background rather than allowing a script to do the majority of the work for me.  It doesn't make me a better user or you any less of one for using it, it just helps me learn what I need to know about the operating system.  When I've figured out what I want to know about the OS, then I'll look into things like Automatix2 and other scriptable paths.  With that said, I'm not that fond of Synaptic Package Manager either.  I'm all about the command line.

---

### Post by Roasted on 2007-02-11
Why is it that I have some extra options at the boot screen now? I forget what I had before, but I didn't have as many as I do now.

Right now I have:

Ubuntu Kernel 2.6.17-11 Generic
Ubuntu Kernel 2.6.17-11 Generic Recovery Mode
Ubuntu Kernel 2.6.17-10-386
Ubuntu Kernel 2.6.17-10-386 Recovery Mode
Ubuntu Kernel 2.6.17-10 Generic
Ubuntu Kernel 2.6.17-10 Generic Recovery Mode
Ubuntu Memtest86+
Windows 2000 Professional

---

### Post by Spr0k3t on 2007-02-11
It has to do with the kernel update.  You can remove the extra options from the list by doing the following from the terminal

```
sudo nano /boot/grub/menu.lst
```

My recomendation on this, don't remove the extra lines of code, just comment them out with a "header comment" regarding why they've been commented out.  This way if you need to enable the kernel for some reason, you can go back to it without any problems.

---

### Post by warri0r on 2007-02-11
same problem here. when i allow to update tats it. ubuntu wont boot again when i make a restart. it ll display some errors.

one error tat i remember: [some code] Bug: soft , cpu , lock          (sorry i remember the keywords only]

this is my 13th install which i made it today. i simply turned off the update manager from poping up.

what is the solution for this problem or i dont need updates anymore?. :(

my computer configurations:

AMD athlon XP @ 2000 MHZ
 
Nvidia geforce FX 5200 (256 MB)

Linksys WMP54G wireless card (ralink)

1.25 GB DDR RAM

2 X 80 GB HDD

someone help plz.

---

### Post by PriceChild on 2007-02-11
> **Spr0k3t said:**
> It has to do with the kernel update.  You can remove the extra options from the list by doing the following from the terminal

```
sudo nano /boot/grub/menu.lst
```My recomendation on this, don't remove the extra lines of code, just comment them out with a "header comment" regarding why they've been commented out.  This way if you need to enable the kernel for some reason, you can go back to it without any problems.Please don't edit the file yourself for this.... instead remove the installed kernels from synaptic.

---

### Post by Roasted on 2007-02-11
Which should I remove? Everything but the top 2 lines and the memtest86?

---

### Post by Spr0k3t on 2007-02-11
That was it!  Thanks.  I just had to redo my video drivers on the kernel after that though.

---

### Post by Spr0k3t on 2007-02-12
> **PriceChild said:**
> Please don't edit the file yourself for this.... instead remove the installed kernels from synaptic.

AH!  Cool... I didn't know about this.  Question though, how would one go about doing this in the terminal with aptitude or apt-get?

/me jots more information down into my Linux Install Journal.

---

### Post by PriceChild on 2007-02-12
```
sudo apt-get remove linux-image-<<whatever version here>>
```

---

### Post by Roasted on 2007-02-12
Just out of curiosity, what are the point of those anyway? What's the point of generic mode and memtest and all that?

---

