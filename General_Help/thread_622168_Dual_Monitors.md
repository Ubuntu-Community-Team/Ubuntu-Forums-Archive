---
title: "Dual Monitors?"
date: 2007-11-24
forum: General Help
---

### Post by theyain on 2007-11-24
I am trying to help my roomie use Ubuntu (7.04) but we have a major problem.  Several in fact.


His laptop is broken. The main LCD screen doesn't work (the LED regulator died and now it just doesn't work at all), so need to use the secondary monitor (VGA port, LCD) as the main.  But if you have tried running dual screens on Ubuntu during its earlier releases, then you would know that the secondary screen just screws up greatly.


Is there ANY way to set it up so that the attached monitor is the main Monitor?  Or does my friend have to go back to using the dreaded Windows?

And NO I am not afraid to use the command line.  ^_^

Second problem:  I updated his computer through the command line (ctrl alt f2) and after I updated I could no longer access the Repoz.

Third problem: Anyone know how to detach a monitor from a laptop with out screwing over the laptop?

---

### Post by theyain on 2007-11-24
Bump for help.

---

### Post by theyain on 2007-11-25
Hello?  Hello?  Anyone?

---

### Post by Tenken on 2007-11-25
I was just working on a Gateway laptop that also had a broken monitor, plugging in the second monitor and keeping the lid of the laptop closed defaulted to the secondary monitor. With that setup there is not reason to remove the lid either, you just need a external keyboard and mouse.

For your your second question check to make sure all the repos aren't commented out in your /etc/apt/sources.list file.

---

### Post by theyain on 2007-11-25
You haven't seen the monitor then.

The monitor its self is no longer attached to the rest of the laptop (except for the sole while that connects it to the motherboard).  The monitor is placed under the rest of the laptop.

---

### Post by theyain on 2007-11-27
Bump

---

### Post by Tenken on 2007-11-27
If the laptop has an nvidia card you could disable the monitor with the nvidia settings tool, hit Alt+F2 and type gksu nvidia-settings.

---

### Post by theyain on 2007-11-27
I got an error saying it could not be displayed

---

### Post by Tenken on 2007-11-27
Try checking Synaptic to see if the program is installed, I think it installs by default if it is an nvidia card.

If you aren't sure what type of card it is, do this in a terminal:

```
lspci
```

or if the output it too long

```
lspci -v | less
```

and you should be able to find what type of card the laptop is running

---

### Post by theyain on 2007-11-30
Silly me I just realized that you told me to hit alt F2.  

I can't do anything GUI Based.  I can't see the main screen, and the second screen just flashes constantly.  Everything I do is in the tty1-6.

---

### Post by markyb86 on 2007-11-30
What kind of laptop is it? The screens are different on all but usually easy to remove.

---

### Post by theyain on 2007-11-30
Sony Vaio - its about 4 years old now.

---

### Post by markyb86 on 2007-11-30
pry the piece of plastic above the keyboard up, and you should have screws for the hinges of the screen, you can take the lcd off by unplugging its video and its power cord. then you can reapply the screws and the plastic cover.

---

### Post by Tenken on 2007-11-30
> Silly me I just realized that you told me to hit alt F2.

I can't do anything GUI Based. I can't see the main screen, and the second screen just flashes constantly. Everything I do is in the tty1-6.

If you feel comfortable enough you can try editing your xorg.conf and removing the screen/display manually. I've only had minimal experience with this so then only advice I can give you is to make sure you back up your old configuration first :).

```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.backup
```

---

### Post by theyain on 2007-11-30
I've edited my xorg.conf before, so no worry there.  I'll make double copies, mainly because I have screwed myself over by accidentally coping over the backup.

Anyone have and Idea how to edit xorg so that The secondary monitor is used as the main monitor?

And thanks MarkyB. I just wanted reassurance.  You wouldn't believe how much dust was in there X(  By the time I had removed all the dust, the pile had grown to the size of my hand.

---

### Post by markyb86 on 2007-11-30
I know the dust feeling, my computer sits on the floor and sucks in at least 10lbs of dust a day!

---

### Post by theyain on 2007-11-30
Yeah, dust isn't fun.

---

