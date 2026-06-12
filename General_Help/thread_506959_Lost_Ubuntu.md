---
title: "Lost Ubuntu"
date: 2007-07-22
forum: General Help
---

### Post by keithk50 on 2007-07-22
Upgraded my BIOS on laptop (had to be done due to battery issues) and now my Ubuntu 7.04 partition will not boot.   Even the Live CD will not run!   It has took me 3 months 'hard work' as a noob to get this OS to run.   What I do not understand is that the 'live CD' of for instance 'PC Linux' does run, and 'see's'the BIOS.   Any suggegtions.

---

### Post by bodycoach2 on 2007-07-22
> **keithk50 said:**
> Upgraded my BIOS on laptop (had to be done due to battery issues) and now my Ubuntu 7.04 partition will not boot.   Even the Live CD will not run!   It has took me 3 months 'hard work' as a noob to get this OS to run.   What I do not understand is that the 'live CD' of for instance 'PC Linux' does run, and 'see's'the BIOS.   Any suggegtions.

The BIOS upgrade may have changed the boot order. Check that, and see what boots first, second, third, and so-on.

---

### Post by keithk50 on 2007-07-22
Hi,   Thanks for the reply.     Oh my god.    Check that!!!!   I am sorry.   Pleae tell me what that is....Pleaae be gentle with me.   What was that  again.......  I love you all.

---

### Post by trak87 on 2007-07-22
The BIOS is a chip on the motherboard. When you access the BIOS you get a little text-based screen where you can enter system wide options. Usually, during boot up, you will see a little screen message saying something like, "Press F1 to enter options". You press this key intermittently during boot and you will enter the BIOS menu. There you can make changes like telling it to boot from the CD-ROM first and many other options. The keystroke for your laptop could be anything so watch the screen as you boot up for clues. It could be F1, F2, Del, F9, F10, F11, F12 or Esc. Or something else. But before testing all of that, look in your laptop manual and see which key it is. Easy.  Otherwise, just about all computer manuals are online in PDF format these days. All you have to do is go to the manufacturer's website, go into the Support area and search on your model. Then look for the manual, download it and view it. Find the key to enter the BIOS. Easy.

Once that is done, set it to boot the CD-ROM first. Then boot up with your Ubuntu install CD and then look for instructions on this forum to reinstall 'grub'. I have a feeling that may be the problem.

---

### Post by benx009 on 2007-07-22
> **trak87 said:**
> The BIOS is a chip on the motherboard. When you access the BIOS you get a little text-based screen where you can enter system wide options. Usually, during boot up, you will see a little screen message saying something like, "Press F1 to enter options". You press this key intermittently during boot and you will enter the BIOS menu. There you can make changes like telling it to boot from the CD-ROM first and many other options. The keystroke for your laptop could be anything so watch the screen as you boot up for clues. It could be F1, F2, Del, F9, F10, F11, F12 or Esc. Or something else. But before testing all of that, look in your laptop manual and see which key it is. Easy.  Otherwise, just about all computer manuals are online in PDF format these days. All you have to do is go to the manufacturer's website, go into the Support area and search on your model. Then look for the manual, download it and view it. Find the key to enter the BIOS. Easy.

Once that is done, set it to boot the CD-ROM first. Then boot up with your Ubuntu install CD and then look for instructions on this forum to reinstall 'grub'. I have a feeling that may be the problem.

some laptops (like my friend's toshiba) also give you the option to select the boot device right when you start your laptop.  helpful if you don't want to mess around in BIOS.  so, it might be just something like "press F12 to select boot device"  just press F12 (or whatever key it is), choose CD/DVD and press enter.  that should do the trick

---

### Post by keithk50 on 2007-07-22
> **trak87 said:**
> The BIOS is a chip on the motherboard. When you access the BIOS you get a little text-based screen where you can enter system wide options. Usually, during boot up, you will see a little screen message saying something like, "Press F1 to enter options". You press this key intermittently during boot and you will enter the BIOS menu. There you can make changes like telling it to boot from the CD-ROM first and many other options. The keystroke for your laptop could be anything so watch the screen as you boot up for clues. It could be F1, F2, Del, F9, F10, F11, F12 or Esc. Or something else. But before testing all of that, look in your laptop manual and see which key it is. Easy.  Otherwise, just about all computer manuals are online in PDF format these days. All you have to do is go to the manufacturer's website, go into the Support area and search on your model. Then look for the manual, download it and view it. Find the key to enter the BIOS. Easy.

Once that is done, set it to boot the CD-ROM first. Then boot up with your Ubuntu install CD and then look for instructions on this forum to reinstall 'grub'. I have a feeling that may be the problem.

Hey thanks,    I really do apriciate your reply and consideration.   I know about the BIOS and how it works.!!!!    The BIOS is set to boot from CD R0om.     Let me explain.   I have 'set up' Ubuntu run on my system and love it.    Say what you like but windows is hard to 'corrupt', Ubuntu is so easy to break.   Not Ubuntu's fault you may say but I have re-installed Ubuntu 7.04 4 times now.    Dont mind, love the distro.
But I look fdorward to a Ubuntu Desktop that will not need to be re-installed every time there is a problem,.







#

















































 reply and consideration.

---

### Post by Wim Sturkenboom on 2007-07-22
First the help:
Are CDrom and HD detected in the BIOS (CD probably is as other CD boots). Which brings me to the point that your current Ubuntu CD might be damaged. Burn a new install CD on low speed (or order a new one).
Ubuntu does not have to see your BIOS, your BIOS must see Ubuntu. If the HD is detected in the BIOS, has it been set to the same geometry as before the BIOS update?

Second let's get some things straight:
Why install 4 times? More than likely as you don't know how to fix the 'mess' that you created (no offence intended); don't worry, one day you will probably laugh about those things.
And except for microsoft, you're probably the only one who thinks that Windows is hard to corrupt :) Ubuntu is not broken, but your laptop is at this stage.

PS
please edit your previous post with all the empty lines

---

### Post by trak87 on 2007-07-22
FWIW, when I started with Linux, I reinstalled about 50 times because I didn't know how to fix things. So I think reinstalling when you get stuck is pretty normal. Reinstalling is good every major upgrade anyway.

---

