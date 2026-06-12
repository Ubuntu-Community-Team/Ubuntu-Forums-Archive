---
title: "Sound/Headphones?"
date: 2005-10-08
forum: General Help
---

### Post by Door on 2005-10-08
Hi! I'm a newbie, obviously. Does anybody have any idea how to make it so that the sound from my laptop speakers is muted when I use headphones?
Any response much appreciated.

---

### Post by QuantumCowboy on 2005-10-23
I have the same problem.  I'm runnning 5.04 on an HP zv5000, and my speakers stay on even when I plugthe headphones in.  On my sound control, there are three selectors: Master, Headphone, and PCM.  Adjusting headphone only changes the headphone volume level, leaving the speakers unaffected.  The PCM slider and Master slider change the volume of both the headphones and the speaker!  Thus if I put PCM to 0, regardless of where the Headphones volume is, there is no sound from either.

Is there some fix for this?  I work in the library on my laptop quite a bit, and if I can't listen to my music....  I've been using Ubuntu for a few months and really like it, and I have most of the quirks ironed out; but a lot of these little things are adding up.  As much as I hate Micro$oft, if Linux doesn't become significantly more automatic soon, I just don't think it will be worth the trouble and the stack of minor inconveniences.

Somebody please help, I don't want to go back to the dark side!

Thanks,
QC

---

### Post by QuantumCowboy on 2005-10-23
Found this on a [Gentoo website]("http://www.purplefrog.com/~thoth/zv5000/"):

> 
nforce-audio 0292 ebuild is bad
Use ALSA. The rest of this section is only of historical interest.

One freaky feature of this laptop is that plugging in headphones does not mute the speakers under the nforce-audio drivers. Recent nforce-audio drivers eliminate the ability to control speaker volume independently of headphone volume.

The 0261 driver had separate parameters for vol (could mute the speakers) and pcm (controlled speaker and headphones). 0292 has only vol which controls speakers and headphones. There is no way to turn off the speakers while leaving the headphones working. 0301 is similarly defective, so I have masked both of them using /etc/portage/package.mask. I had to retrieve the purged 0261 nforce-audio from the viewcvs.gentoo.org portage attic and install it in a PORTDIR_OVERLAY to get things working the way I wanted. 

Looks like its a strange hardware problem with the Linux nForce driver in general, not so much with Ubuntu.  Could someone please explain what this means and how I should go about fixing my system?

Thanks,
QC

---

### Post by davebgimp on 2006-06-06
I have the same issue with my Lenovo 3000 N100 laptop. The speakers do not mute when headphones are plugged in.

---

### Post by pimpaulogy on 2006-07-07
Well, not sure if this will be helpful because I am guessing most of you have done this already and I am new to this whole Linux thing, but I was also having the same problem with my HP Compaq nc8230.  Turns out, Ubuntu didn't have the "switch" enabled by default to recognize the headphones when I plug them in to mute the main speakers.  To fix it, openned up the Volume Control for the Intel ICH6 driver, click the switches tab, and put a check mark next to Headphone Jack Sense, and that did the trick.  Like I said, not sure how helpful this would be but here you go.

---

### Post by davebgimp on 2006-07-08
Yeah, I've also found out that manually disabling the laptop speakers does the trick. In my case, turning off "external amplifiers" from Kmix (I use Kubuntu) does the job.

> **pimpaulogy said:**
> Well, not sure if this will be helpful because I am guessing most of you have done this already and I am new to this whole Linux thing, but I was also having the same problem with my HP Compaq nc8230.  Turns out, Ubuntu didn't have the "switch" enabled by default to recognize the headphones when I plug them in to mute the main speakers.  To fix it, openned up the Volume Control for the Intel ICH6 driver, click the switches tab, and put a check mark next to Headphone Jack Sense, and that did the trick.  Like I said, not sure how helpful this would be but here you go.

---

### Post by transpine on 2006-07-25
Oh, Thanks for help.
I just solved this problem by checking "Headphone Jack Sense" at Volume control.
This site, Ubuntuforums.org is Awsome!!

---

### Post by JPMaximilian on 2006-09-07
There is no option for me to turn on headphone jack sense.  I'm running 6.06 on an acer travelmate 2440.  How do I go about disabling the speakers?  I don't know how to use kmix.

---

### Post by kristiank10 on 2007-10-20
> **davebgimp said:**
> Yeah, I've also found out that manually disabling the laptop speakers does the trick. In my case, turning off "external amplifiers" from Kmix (I use Kubuntu) does the job.

I mute external speakers by explicitly muting "front" in kmix. Your solution sounds better :)
External amplifiers? Where do you find external amplifiers in kmix? 

thx

---

### Post by prog101 on 2007-12-07
SOLVED

The following fix should work; it works on my Toshiba A135-S7404.

1. Remove volume control icon from the top panel.

2. Edit file alsa-base: sudo nano /etc/modprobe.d/alsa-base
Add/edit the following line:
options snd-hda-intel model=lenovo

3. Remove sound module
sudo modprobe -r snd-hda-intel

4. Add sound module
sudo modprobe snd-hda-intel

Sound should work from internal speakers and get muted when headphones are used (headphone jack sense)

5. You may add the volume control icon again back to the top panel.

cheers!

---

### Post by oreja on 2008-02-04
I found solution that works with Amilo Pro V3515  (Fujitsu - Siemens).

You have to add 2 lines to your /etc/modprobe.d/alsa-base file

#add this lines
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto  position_fix=1 enable=yes


and restart laptop. I hope it helps.

---

