---
title: "ATi Radeon X800 XL help (Funky Dual Screens and Drivers)"
date: 2013-08-30
forum: General Help
---

### Post by chrisbarnes1992 on 2013-08-30
Hi all,

I have decided to try running Linux on a Desktop of mine  and i would like to keep the Dual Screens (Got bored of Xp :-) ). The install went well until it booted into the KDE desktop first time. The left displays had many scary lines and wiggly blocks on the left hand side. The Right monitor is about 20% - 30% out of view. And looking at the desktop wallpapers it is only a clone view.

So i have decided to unplug the right monitor and the left screen went to useable state. I then tried to run Additionial Drivers and it found nothing. Which did annoy me a little. 

Next step was for me to go to ATi/AMD site and grab the drivers. Which was a great sucess, Found the correct driver, made sure it was excutable and ran it in the terminal. It started ok then it said :

>  ==================================================

  ATI Technologies Linux Driver Installer/Packager  
 ==================================================
 

 Error: ./default_policy.sh does not support version
 default:v2:x86_64:lib::none:3.8.0-19-generic; make sure that the version is being
 correctly set by --iscurrentdistro
 

 Removing temporary directory: fglrx-install.qKCpFg
  

I cant see any reason why it wont install. And it is a fresh install of kubuntu. My main aim is to get both screen working together again. I am only posting for help now is that after 4 - 6 hours of searching and testing is going no where. 

Thanks in advance,

---

### Post by QIII on 2013-08-30
Hello!

What version of Kubuntu are you using and what model is the GPU?

---

### Post by chrisbarnes1992 on 2013-08-30
Its kubuntu 13.04

And the GPU is ASUS ATi R430 (Radeon X800 XL)

---

### Post by QIII on 2013-08-30
Unfortunately, ATi dropped Linux driver support for that card about 4 years ago and the driver that would otherwise work with it will not work with recent versions of X Server.

That's why you can't find anything in Additional Drivers.

The only driver that will work with that card is the default open source Radeon driver (installed with Kubuntu). 

Could you post a screen shot of the odd behavior (please use the "paperclip" above the input box to attach the image) so we can see exactly what you are talking about?

---

### Post by chrisbarnes1992 on 2013-08-30
I tried to get a screen shot but no matter what i did i could not get the mouse to respond to anything while the montiors went into funky mode. The little screenshot window opened but no responce from the mouse / mice (Marbel, Normal Mouse & Trackpad) . 

So i had to take a picture with my phone instead. I have swapped the DVI cables around as another test so the wacky blocks are now on the right hand screen.

---

### Post by chrisbarnes1992 on 2013-08-30
Is there any other Drivers that i can use on my system to get the screens to Display and work correctly etc?

---

### Post by chrisbarnes1992 on 2013-09-02
Can anyone help me. I would really like to keep Kubuntu / Ubuntu on this pc and it seems a shame to go back to windows to get the Dual screen working again.

---

### Post by chrisbarnes1992 on 2013-09-09
Is there anything i can do to make the dual screen to work at all? Single screen seems a shame as the card can do dual screens but the software wont let me use it.

---

### Post by Mark Phelps on 2013-09-10
As QIII already told you, AMD dropped restricted Linux driver support for that video chipset years ago -- so no, there are no drivers you can download that will work with anything newer than Ubuntu 9.x.

When you click on the Display settings, you should see a checkbox in the panel indicating the screen is mirrored. You should see if you can uncheck that.  IF you can, that will provide for two different display screens.  If you can't uncheck that, you're stuck.

---

