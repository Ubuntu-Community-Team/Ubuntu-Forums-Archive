---
title: "system startup is not working as expected"
date: 2013-05-15
forum: General Help
---

### Post by BcRich on 2013-05-15
I switched my computer on today as per normal, but unplugged my wifi dongle and my system has been in this boot sequence with lots of numbers and system info displayed on the screen for hours please see the pic i've linked to. does anybody know why it's doing this and if it's ok for me to simply hit the reset button and try rebooting with the wifi dongle attached? is it doing some sort of file system check? [http://ubuntuone.com/6UdUIgvj9QpuoLNPF3fOVw](http://ubuntuone.com/6UdUIgvj9QpuoLNPF3fOVw)

---

### Post by Nolix on 2013-05-15
What verision of Ubuntu are you using?
Was that the first bootup or has this happened after a specific update, ect

---

### Post by BcRich on 2013-05-16
Thanks for the reply Nolix, I'm using Kubuntu Raring and this is unrelated to updates or a distro upgrade. Kubuntu seems to have a problem with initializing my desktop whenever my wifi dongle is unplugged, this is the most extreme situation i've seen thus far as usually it gets to the login screen (at the very least). I got tired of waiting so I rebooted (cold) and with the dongle plugged in everything went along as normal. I'm just a little concerned that maybe there might be some bad sectors on my HDD after this, so I ran an fsck but this didn't turn anything up. do you perhaps have any suggestions for further maintanence :)

---

### Post by Nolix on 2013-05-16
> **BcRich said:**
> Thanks for the reply Nolix, I'm using Kubuntu Raring and this is unrelated to updates or a distro upgrade. Kubuntu seems to have a problem with initializing my desktop whenever my wifi dongle is unplugged, this is the most extreme situation i've seen thus far as usually it gets to the login screen (at the very least). I got tired of waiting so I rebooted (cold) and with the dongle plugged in everything went along as normal. I'm just a little concerned that maybe there might be some bad sectors on my HDD after this, so I ran an fsck but this didn't turn anything up. do you perhaps have any suggestions for further maintanence :)

It was a good call running fsck just in case, I would suggest looking into your BIOS settings, particularly your boot sequence, it may have something to do with it. If that's not the case it may have something to do with your x.org conf file. Beyond that I have no Idea.

---

### Post by BcRich on 2013-05-16
Cool 8-) Thanks 4 the suggestions I sincerely appreciate it :) I'll have a look around and see wut i can come up with.

---

