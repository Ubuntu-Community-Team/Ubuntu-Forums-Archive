---
title: "Headphones not working in 16.04"
date: 2018-02-04
forum: General Help
---

### Post by faiuwle on 2018-02-04
I had this same problem in 14.04, never found a solution.  When I plug in headphones, sound does not work.  The headphones work fine in Windows (using the same jack) and with other devices.  Previously my headphones were working, but the last time I logged in, they didn't, I also tried rebooting a couple times, but it was still broken.  I recently updated my software, if that has something to do with it.  I don't know if it's related, but when I log in with headphones plugged in there is a "volume muted" symbol on the upper right side of the screen, but if I click on the actual volume control it is not muted.  If I unplug the headphones and plug them back in again I get a non-muted volume symbol in the upper right, but the sound still doesn't work.  I don't know what this symbol means.

---

### Post by ajgreeny on 2018-02-04
With your headphones plugged in have a look at the settings in pulseaudio-volume-control from the **Volume icon on panel -> Sound Settings ->Output devices tab** where you should see both speakers and headphones listed in the drop-down menu.

Speakers and headphones are always set separately when using pulseaudio, and on all my systems retain whatever setting they were at when last shut down, meaning my speaker volume is always muted but headphones are always at the volume I need when I have them plugged in.

---

### Post by faiuwle on 2018-02-04
I don't see speakers listed, and I don't see a drop-down.  This is what I see:

[IMG]https://i.imgur.com/QK8IKxj.png[/IMG]

---

### Post by Alxl on 2018-02-04
Now click on 'Input'   to see that part.
And when you plug in your external devise you should be able to chose what you want

---

### Post by faiuwle on 2018-02-04
That's just my microphone?  That's all there is, there's an entry for the microphone.  Why would the headphones be on that tab?

---

### Post by ajgreeny on 2018-02-04
Unfortunately the window you see for **Sound settings** looks quite different to mine; can you check you have pavucontrol installed with ```
dpkg -s pavucontrol
```
Can you also tell us your computer hardware, including the headphones.
What happens and what do you see if you click on the **Headphones/Built in audio** entry showing on your screenshot?

---

### Post by faiuwle on 2018-02-05
dpkg says pavucontrol is not installed.  Should I install it?

My computer is an ASUS K55VD laptop.  My headphones are made by Sennheiser, model number HD202II.

Nothing special happens if I click that - I think it is meant to be a selection in a list of items which contains only the headphones item.

---

### Post by ajgreeny on 2018-02-05
Yes, install pavucontrol and try again to set the volumes as in my post #2.

---

### Post by faiuwle on 2018-02-05
Ok, I installed it.  This did not change the interface of the sound settings, but I can run pavucontrol from the command line and get the interface I think you are talking about.  It looks basically exactly the same as the sound settings except with a different interface.

---

### Post by ajgreeny on 2018-02-07
Does it show both speakers and headphones now in a drop-down box/menu?

How are the headphones connected, using a jack plug or USB?

---

### Post by faiuwle on 2018-02-28
Ok, it sound briefly worked after I installed pavucontrol, but then I rebooted my computer and it once again does not work.  The headphones are listed in pavucontrol.  They are plugged in with a jack.

---

### Post by faiuwle on 2018-03-01
Ok, weird, it is randomly working again.  Does anyone have any idea why it is randomly working and not working, and how to make it so that it always works?

---

### Post by faiuwle on 2018-05-23
Once again, the headphones do not work.  Is there any solution to this?

---

### Post by ppianpak on 2018-06-12
I have the same problem on Dell XPS 15.
The problem occurs now and then, and I don't know the reason.
Usually I fix it by
> rm -rf ~/.config/pulse
sudo alsa force-reload
sudo shutdown -h now
But today it does not work anymore. :-(

---

### Post by cerberuz on 2018-09-22
My advice is to update the linux kernel inside ubuntu 16.04.
I once clicked on install updates which did modifications to the operating system
and also updated the kernel to a newer version, that was also the reason why
my headphones didn't work, speaker audio was fine tough.
After I followed this guide:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus)

about how to update the linux kernel to the very newest available version and rebooted once
the headphones work fine again.

I used this command:
apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04

---

