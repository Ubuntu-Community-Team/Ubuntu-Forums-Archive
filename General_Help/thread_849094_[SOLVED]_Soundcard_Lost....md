---
title: "[SOLVED] Soundcard Lost..."
date: 2008-07-04
forum: General Help
---

### Post by sunshine12 on 2008-07-04
Today when I started my PC then there isn't any sound.
I checked the sound settings and My soundcard is LOST, I mean it is not in the list.. Go back to windows XP, sound is not there and also soundcard is lost from the Device Manager also.....

Can't understand the problem, soundcard is C-Media Pci 8738... purchased on may 2001.

here is the screenshot when the soundcard was there (in XP)..

The second entry in soundcard options is my soundcard CMI8738.. Now there isn't that entry in the list and soundcard is lost from Ubuntu too..

---

### Post by iaculallad on 2008-07-04
What displays when you issue the terminal command below:

```
lspci | grep audio
```

---

### Post by sunshine12 on 2008-07-04
0:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)

---

### Post by sunshine12 on 2008-07-04
Thanks for reply.. it shows

0:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)

---

### Post by iaculallad on 2008-07-04
> **sunshine12 said:**
> 0:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)

And what does this displays?:

```
asoundconf list
```

---

### Post by sunshine12 on 2008-07-04
Thanks for the quick reply..

Names of available sound cards:
I82801BAICH2


Earliear it was.. I82801BAICH2 and CMI8738

---

### Post by sunshine12 on 2008-07-04
What is the life of any Soundcard?? Is it out of order or what??

---

### Post by iaculallad on 2008-07-04
> **sunshine12 said:**
> What is the life of any Soundcard?? Is it out of order or what??

That shouldn't change :confused:

Try to make I82801BAICH2 default using the terminal and retest your sound:
```

sudo asoundconf set-default-card I82801BAICH2
```

---

### Post by sunshine12 on 2008-07-04
No sound, where is my original soundcard gone??

---

### Post by sunshine12 on 2008-07-04
Can anyone have idea?? Where is my original soundcard and why suddenly xp and ubuntu can't find it??

---

### Post by jocko on 2008-07-04
I have three possible reasons, in order of severity:

1. You have accidentally inactivated it in the bios. Restart your computer, enter the bios setup (either press delete or f2 during the bios self tests, depending on your bios). Find any settings regarding pci slots or irq and see if they are all active. (can't help you very much here, every bios looks different...)

2. The card is not properly seated. Turn off the computer, unplug it, open up the case and remove the sound card. Re-seat it in the pci slot and try again.

3. Your sound card is broken. If you have a warranty you may get a replacement from the manufacturer, otherwise, buy a new one...

---

### Post by sunshine12 on 2008-07-04
Problem Solved... don't sure how? possibilities..

I have used Revo uninstaller to uninstall programs and registries, that might have created some problem!! don'
t sure though.

So, what I have done is System Restore in XP to previous state and I think it worked!!!

Screenshot of it.. second entry is my soundcard..

Thanks for replying.. Thanks a lot..

---

