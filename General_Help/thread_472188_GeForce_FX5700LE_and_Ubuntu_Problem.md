---
title: "GeForce FX5700LE and Ubuntu Problem"
date: 2007-06-12
forum: General Help
---

### Post by Citizin on 2007-06-12
I used ubuntu back when it was in the 5.xx stages. It never worked with my nvidia card at all, only my onboard intel. I just installed 7.04 Yesterday, 2 versions later shows a lot of hard work was put off, everything is so much easier to use, and it just WORKS, but I still have the same problem with my video card.

Well, I was going to enable desktop effects, if that worked I planned on installing Beryl. I enabled desktop effects (while on my Intel Integrated Card) and it told me it needed to enable NVIDIA-GLX Graphics accelerated drivers, ok so I let it do so.

I restart my computer, go to my BIOS, enable my PCI card, then plug the monitor into my PCI video card and restart. The progress bar for ubuntu booting stops about 10% in, probably when its detecting hardware.

So Im on another fresh install of Ubuntu because enabled those nvidia drivers rendered my OS useless until I reinstalled it.

I REALLY want to use my nvidia card, can anyone help me out?

---

### Post by Shazaam on 2007-06-12
PCI or PCI-E? Or AGP?

---

### Post by Citizin on 2007-06-12
Just PCI, my computer has no AGP/PCI-E

---

### Post by Citizin on 2007-06-12
I really hate double posting but I need to bump this, it's already on the second page.

Isn't there any easy way to do this?

Also, I reconfigured the xserver-xorg when I rebooted on my intel card after the nvidia drivers were installed, sense xserver wouldn't start I got a console and there was 2 drivers I could of used, "NV" or "NVIDIA", hope that makes a diffrence, and it also gave me a message saying no screen/monitor could be found, or something to that matter, like the card wasn't in the PCI slot.

---

### Post by andymushu on 2007-06-12
you might try these commands. they worked for me for a similar problem.

sudo /etc/init.d/gdm stop
sudo dpkg -i envy*.deb
sudo apt-get install -f
sudo envy -t
sudo /etc/init.d/gdm start

---

### Post by Citizin on 2007-06-12
could you explain to me what each of those commands is going to do, not only would I like to fix this problem but I'd like to learn how to fix it as well.

---

### Post by andymushu on 2007-06-12
i am not too clear about them, but i will try to explain them. someone correct me about any errors. the first one stops the gnome interface (the gui). the second downloads envy, which is a program for video drivers. the third installs envy. the fourth runs envy, and the last one restarts the gnome interface. good luck

---

### Post by Citizin on 2007-06-12
It all sounds good to me.

Now, should I have my Integrated enabled and in use when I do this, or should I have my nvidia card enabled when i do this?

---

### Post by andymushu on 2007-06-12
envy automatically detects what you are using and gets the drivers for it, so in theory it shouldn't matter. if you are going to be using your card, which i assume you are, i would recommend disabling the onboard then trying this.

---

### Post by Citizin on 2007-06-12
Thanks for the help, im going to backup this time, and then try this. If for some reason I can't get X to start, Ill be back here on my laptop begging for help :)

---

### Post by andymushu on 2007-06-12
good luck, feel free to ask some more questions. i spent 3 days trying to get x to work on my install. i feel your pain.

---

### Post by Citizin on 2007-06-12
Well, I ran the system off the PCI card and booting normally in ubuntu just froze the startup like usual when the card is connected, and doing recovery mode brought up some interesting text that just stayed on the screen.

[http://img156.imageshack.us/img156/6069/1009068ku6.jpg](http://img156.imageshack.us/img156/6069/1009068ku6.jpg)

[http://img404.imageshack.us/img404/681/1009069jw4.jpg](http://img404.imageshack.us/img404/681/1009069jw4.jpg)

Those 2 pics are what I see when I try to go into recovery mode, so I can't get to any kind of terminal with the card plugged in unless I install the restricted drivers.

---

### Post by andymushu on 2007-06-12
do you have any important files or anything on this ubuntu installation? if not, i recommend reinstalling with the feisty alternate cd. you can install in text mode (which i had to do to fix my problem). it should install fine and take you to a terminal, where you can input those commands.

---

### Post by Citizin on 2007-06-12
There not anything I need to keep on this install, I just dont want to go through installing again.

Right now im running ENVY and manually installing the 100. Nvidia drivers, hopefully this will work.

So you installed with the alternate cd and it fixed your problem?

---

### Post by andymushu on 2007-06-12
ya i couldn't even do a regular install. the x server would shut down and give me a bunch of errors. someone recommended me the alternate cd. i installed in text mode so i didn't have to use x and i used those commands i gave you to get the right drivers. it worked very well for my problem.

---

### Post by Citizin on 2007-06-12
Well, I rendered my OS unusable again lol, anyway its doing the same thing I got the alternate disc downloading on the laptop im on now, and hopefully it will work. Thanks for the help you givin me so far, and to answer the question you had your thread about WINE, Crossover is a commercial version of WINE only I think it is muich better, it works so much faster and smoother, its not free, but I can send you the .deb package of the professional version if you want it after I get ubuntu up and running.

---

### Post by andymushu on 2007-06-12
good luck with that alternate disc, i know how much of a pain it is for these things not to work. i would love to try out that crossover deb file once you get all this up and running. good luck and feel free to pm me if you run into any more problems.

---

### Post by Citizin on 2007-06-13
Well, I got bad news, and more bad news, at least for me.

I ran the alternate disc, it does nothing but install Ubuntu like the Live CD does, I went throught the install, no where could I find a spot to type in the lines to install envy and get some drivers up, so I let it go through and when it booted ubuntu it did the same thing, while it was loading it froze, so I took the nvidia card out and then I booted off my Intel integrated, so I get this screen now that says there is no PCI card in the slot and that no screens are found.



Im really having a hard time trying to figure out how to fix this problem.

I cant use envy without using my integrated card and booting in ubuntu, even then I can install nvidia drivers, and it still dosn't want to work.

Is my video card just a card that WONT work with linux regardless of what I do?

---

### Post by Citizin on 2007-06-13
*BUMP*

Ok, im throwing my computer out the window, this is useless, how is it THIS hard to get a damn video card to work. I want to get this setup so I can go to sleep so I have a working computer to get on tomarrow.

---

### Post by rvdavid on 2007-06-13
Hi Citizin...

Can you post what it says in your /var/log/Xorg.0.log (if you have access to it)?
Also post the contents of /etc/X11/xorg.conf

I don't know what could be causing the problem, but this could give us some idea as to what is going wrong. 

Also... what did you mean when you said that Envy has rendered your OS unusable? did it hang? 

If it does hang next time, try pressing CTRL + ALT + F5  key and see if you get a tty screen.

If it does, try logging in and typing in the command

```

$ startx

```

If you can't get to this stage when using your Geforce card, then I'm afraid I've expended what little experience I have. Someone else may be able to help you out.

regards,

---

### Post by andymushu on 2007-06-13
if you installed in text mode, after it installed and everything there should have been a command line.

---

### Post by Citizin on 2007-06-13
After I install in text mode, it just seems like a regular install without the live cd. After its done it ejects the disc and reboots into ubuntu, no command line anywhere, I can run the installer with my GeForce card but it still isn't picked up.

Now, Im on ANOTHER fresh install I completed just 5 minutes ago, as far as my log files, there gone but I did look at them myself.

What seemed what the problem was, is that I cant use my Nvidia card in Ubuntu at all, I never get past the loading bar, and in recovery mode I get a bunch of gibberish that dosn't mean anything at all, so I HAVE To use my integrated to get any kind of command line to get into ubuntu, if I do that and then run envy, it installed Nvidia drivers, but it dosn't set my xorg.conf file to my nvidia card, in the xorg.conf file it had my intel card, cause I ran envy with it, I even try "nvidia-settings" and that didn't help much at all.

Heres a screenshot of what I get with my nvidia card plugged in and nvidia drivers installed.

[IMG]http://img486.imageshack.us/img486/6634/1009070vu7.jpg[/IMG]


Im just going to get used to the fact that this can't be fixed, but Im starting to like linux to much, so I guess im just never going to be able to run anything 3d -_-

---

### Post by Citizin on 2007-06-13
*BUMP*

Second page again...

---

### Post by Citizin on 2007-06-13
*BUMP BUMP*

Ok, this is the last time im going to bump, cause im assuming theres no solution to this.

- Jay

---

### Post by scott_g on 2007-06-13
Have you ever tried installing Ubuntu with your computer hooked up to/using the video card?  Or will it not boot the liveCD?

Just a thought;
Scott

---

### Post by Citizin on 2007-06-13
It dont work with the LIVECD, but it does with the alternate cd.

---

### Post by Citizin on 2007-06-14
Cant ANYONE help me.....

*BUMPBUMPBUMP*

---

### Post by reset3x on 2007-06-15
Citizin... See if you can login in recovery mode with the pci card installed.... You may have to hit esc when grub starts to able to get to that option... When you get to the command line type "lspci" (without the quotes)... Then look to see if both your nVidia card and you onboard are showing up.... Let us know what you come up with.... Do you know what chipset your PC has? It would be helpful if you let us know more about your PC...  ie: Make and model etc.....


EDIT:

I just noticed in your screenshot above that your card isn't where you xorg config thinks it is... You'll have to do this:

1. Login like I mentioned above.

2. At the command line type  lspci 

3. Look for your video card and write down the bus identifer in front of it... You'll need it when you get further down this list....

4. type sudo dpkg-reconfigure xserver-xorg

4. When asked to autodetect choose yes. You'll probably end up with a list...

5. Highlight nv by using the arrow keys and press enter to get to OK....

6. You be presented with a screen to enter the identifier for you card... If it says NVIDIA Corporation NVIDIA Default Card hit enter... If not poke that in.... and hit enter..

7: Now your're at a screen that says something out you bus identifier... blah... blah... hit enter....

8. Now you're at screen to enter your bus identifier.... This is where your problem is... This can be tricky because its not exactly what gets listed by lspci so follow carefully... take the numbers you got from lspci and remove the first zero.. Then poke that in... In other words if you got 01:00:00 what you need to have on the line is PCI:1:0:0.. now hit enter....

9. The nest screen wants your video cards memory in kilobytes... so you need to multiply you video cards memory by 1024... So if your vid mem is 128 it will be 131072.... if your card has 256 it will be 262144 and so on... poke in your video memory and hit enter....

10. know you're at the frame buffer device screen... Choose no and hit enter....

11. Now you should be at autodetect keyboard.... Hit enter...

12 Hit enter....

13 Hit enter...  Carefully keep hitting  enter until you get to keyboard model...

14. When you get to keyboard model you'll probably get pc104 or something... if you know what you have you can poke it in... if not hit enter... you'll be ok with a 104.... Hit enter....

15. Carefully keep hitting enter until you get to Mouse Protocol....

16. If you're using a two or three button mouse just hit enter... if not find what you have... Then hit enter....

17. This screen should say emulate 3 button mouse? Hit enter...

18. Hit enter....

19. This screen is where you pick the xorg server modules... you navigate them with the arrow keys and highlight them with the space bar...   Choose bitmap, dbe, dri, extmod, freetype, glx, int13, record and vbe... Then hit enter....

20. Choose yes and hit enter... 

21.  Now you're at a screen to auto detect your monitor... Choose yes and hit enter....

22. Now you're at the video modes screen... choose and highlight the the resolutions your monitor will handle... by navigating thw the up and down arrow keys and highlighting them with the spacebar.... Then hit enter..... 

23. Now you're at a screen that gives you choices about enter your monitors refresh rates... This is for both vertical and horizontal... Hit enter...

24. If your positive you know your vertical and horizontal refresh rates  (You should be able to find them at the manufacturer's website) choose advanced and poke in your refresh rates...  if you're not sure you'll be ok with choosing medium.... If you choose medium pick the best resolution and vertical refresh rates your monitor will handle.... then hit enter....

25. Now youre at a screen that says write to configuration file... choose yes and hit enter...

26. Now you're at screen for color depth... Unless your monitor is pretty old you should be safe with 24 bits...  Choose what you think is best and hit enter....

27. Reboot you computer.....

28. When you get back to your desktop go here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and download envy... it's a deb package.. it's easy to install.. just double click on it after you download it.... This will install the best driver for your cand and configure xorg for you... just let it do it's thing and follow the prompts....


29. I hope this helps!!!! Good luck!!!!

---

### Post by Incarnadine on 2007-06-15
Wow I can't believe the problems you are having right now with that video card. I'm starting to thank god I have a Radeon. I had a lot of problems with my card too. For example I couldn't play any games or even look at a decent screen until I enabled my video card under the "Restricted Drivers Manager".

You say that Ubuntu doesn't boot for you and that it gets stuck on %10 or so? I would try to hit Esc to enter the gnome menu and try loading the previous kernal and see if that gets stuck on %10 too. Chances are it won't. I have to load my previous kernal all the time for now until the bug gets fixed in the newest one. I guess this new kernal isn't video card friendly or something, but anyways I hope this saves you the pain of having to install Ubuntu all over again just because it won't load. I find the previous kernal a lot more compatible with my computer and games. Maybe it might be the same for you.

---

### Post by Citizin on 2007-06-15
Well I already tried using the older kernel and it does the same thing. hopefully the instructions above from reset3x will help me.

Wish me luck! As Always, if I fail Ill be back with my laptop complaining about how I have to reinstall ubuntu again -_-

---

### Post by reset3x on 2007-06-16
Citizin!!! I forgot to add that you have to UNINSTALL your nVidia drivers with envy before you re-install them!!! My bad!!! Sorry!!!

---

### Post by Citizin on 2007-06-16
It dosn't matter, I already reinstalled XP, thanks for trying to help though. It only took my 5 Minutes to set up my video prefrences, its to bad Ubuntu fails to work with my card. Ill download it in its next big release :) hopefully it will work then.

---

### Post by reset3x on 2007-06-17
Hope to see you back!!! Good Luck!!

---

### Post by DARKGuy on 2007-06-18
Hey Citzin ;)

Well, people on the IRC say to not to make users use envy, but then in the forum some encourage it... so it's up to you anyways. I like envy because it has an awesome way to remove EVERYTHING nvidia-related and make a "clean" install if you somehow broke anything up.

I'd suggest using a fresh Ubuntu install ... that's cool because you say you're on a fresh one now.

If you used envy and it didn't work, run the script and tell it to uninstall the nvidia driver then to remove ANYTHING nvidia-related. That way you can start off again with a "clean" install.

Now, you need the build-essential packages, and maybe the X development packages. Open a terminal and get 'em (someone correct me if xserver-xorg-dev has a different name... I'm doing all this by memory):
> sudo apt-get install build-essential xserver-xorg-dev

Now, for nVIDIA, the best thing is to download the latest driver from the official site. If you have some bandwidth to waste, download the latest one (100.something) and try to run it... for doing that, open a terminal (assuming you downloaded the nVIDIA driver to your home folder):
> chmod +x NVIDIA-installer-blahblahblah.run
sudo ./NVIDIA-installer-blahblahblah.run
That will install the nVIDIA driver. If it complains about your card not being supported by the driver, it usually tells you which driver series support it, so download the latest one from that serie... say, if the driver says your card is supported by the 96XX series, then download the latest 9639 driver (I think that's the latest one according to the nVIDIA site), then repeat the process.

Also, let the installer modify your X.org file... if you can't get back to X then you can run:
> sudo dpkg-reconfigure xserver-xorgAnd run the nVIDIA installer again. When it finishes, edit the xorg.conf file and change the line "driver      "nv" " by "driver     "nvidia" ". You can edit it with this command:> gksudo gedit /etc/X11/xorg.conf

Good luck! :D

---

