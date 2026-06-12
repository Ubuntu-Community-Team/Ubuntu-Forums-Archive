---
title: "lubuntu screen problem - live CD - OS not installed!"
date: 2015-03-07
forum: General Help
---

### Post by ubunt72 on 2015-03-07
I'm just wondering if someone can identify or recognize what is wrong (When I try to boot up).

I googled and there's various hits that come up - but nothing really exactly resembles my issue.   Now, I must note that I was mostly just testing it on my computer.   In actuality, I was going to set up a friend's computer (which is older) and that's why I downloaded and copied (burned?) the image (.iso) to usb stick (flash drive).   However, it might not even work with his computer.    I might need to burn a CD/DVD.   Still, I am wondering why it won't boot on my system properly.   I am thinking it might be because of the nvidia card I have - gtx 750.   

Anyway, the screen looks stretched and the only icons I can see (which are incredibly distorted and barely recognizable) are the trash icon and 'install' one.   I can't get to the menu.   I assume it's off screen.

Any ideas of what to do?

I looked at the options (function keys) and lga=771 looked like it had potential but I don't know how to get to the point in which I can input that option.   I know 'nomodeset' is often suggested as something to try but again, not sure how to get to that option.  

I wanted to boot up so I can take a look at the newest edition of Lubuntu 14.10 (which I have not seen nor tried yet) so I would know what to explain and mention when my friend tries it.   They have an older Pentium III computer and I might not be able to use the flash (usb) drive to boot but I usually use 'dd' and install a Linux OS that way on my computer.   It's how I test the OS out before install (evaluate it etc.).

I have Ubuntu (w/Gnome) and Debian on my computer, currently.   But, I haven't had boot problems w/ live media in a while.   I don't think it's a problem with the burn/copy image - I believe I'll have the situation no matter how many times I burn/copy the image.  

'Hope someone offers some suggestions.   Not sure what's wrong.   I suppose the problem won't show up on the older computer - if it's video driver related, they have different (older) graphics hardware, obviously.

---

### Post by Portaro on 2015-03-07
Try to see here - [http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers](http://askubuntu.com/questions/425140/unable-toboot-with-nvidia-gtx-750-ti-even-with-latest-beta-drivers),

The pc is on use - work before you try to install lubuntu?
If yes is a problem with the card and new kernel.

If not try to unplug the card and plug and then connect the pc to electric circuit and then try to see if the image works.
(first you disconnect the pc of electric circuit, give 10 minutes without use and without electric circuit and then unplug the graphic card, then plug the graphic and connect the pc, and run the lubuntu) = In some cases I have this problem on past - if the pc is stoped without any work after much time the graphics have distortion output. So this is for see if the card have distortion output because she is stoped on last months or years.

If the problem subsist - take a look on the link.

---

### Post by ubunt72 on 2015-03-07
Yes, the PC is in use.   I don't really get what you're saying - as the computer is running.... The usb stick is in one of the usb ports... I reboot my machine - there is an OS already installed so I am just re-starting - re-booting and then I hit F8 so that I have a choice of the usb stick in the boot options.   

The link seems to describe problems when someone buys or upgrades to a new Nvidia card.   In their case, they have a change in hardware.    I am talking about a problem of using the live edition of Lubuntu and all the defaults - straight booting (no changes).   I remember, that 'live' distros often offered a choice of minimum or safe graphics options - it didn't always work but at least, the devs were indicating they knew graphics drivers were a potential issue.  I'm not even 100% certain it's the video drivers but I don't have any other theories at the moment.

---

### Post by Portaro on 2015-03-07
I understand , and the problem is graphic , can be caused by the graphic card.

Do you try enter on the openbox session of Lubuntu? to see if the image is more acceptable? (Is an idea)

---

