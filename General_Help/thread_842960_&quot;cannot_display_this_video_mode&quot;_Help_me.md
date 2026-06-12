---
title: "&quot;cannot display this video mode&quot; Help me fix this please."
date: 2008-06-27
forum: General Help
---

### Post by bad sneakers on 2008-06-27
I can't install ubuntu until I know how to fix this.

From my monitor's(dell E173FP)manual:
This means that the monitor cannot synchronize with the signal that it is receiving from the computer. Either the signal is too high or too low for the monitor to use. See Specifications for the Horizontal and Vertical frequency ranges addressable by this monitor. Recommended mode is 1280x1024 @ 60Hz.

Monitor specs:
Horizontal scan range	
31 kHz to 80 kHz (automatic)

Vertical scan range	
56 Hz to 76 Hz (automatic)

Optimal preset resolution	
1280 x 1024 at 60 Hz

Highest preset resolution	
1280 x 1024 at 75 Hz

What do I have to do to make it work?

---

### Post by bad sneakers on 2008-06-27
btw I have this problem with every linux distribution i've tried.

---

### Post by bad sneakers on 2008-06-28
^

---

### Post by bad sneakers on 2008-06-29
^

---

### Post by cocopuffz on 2008-06-29
Try "gksudo displayconfig-gtk"

This should in theory set up your xorg file with all the supported display modes. You should try "autodetect" then see if you can add the exact res you prefer. 

mine for example. "plug & play (1440x900)" in the list for generic monitors

---

### Post by bad sneakers on 2008-06-29
Didn't work.

Gtk-WARNING **: cannot open display:

---

### Post by bad sneakers on 2008-07-01
No one knows? Could someone recommend a forum where I could get some help with this?

---

### Post by bad sneakers on 2008-07-02
^

---

### Post by bad sneakers on 2008-07-03
^

---

### Post by bad sneakers on 2008-07-03
^

---

### Post by bad sneakers on 2008-07-04
bump... again.

---

### Post by bad sneakers on 2008-07-05
Does anyone actually read this forum?

---

### Post by hansdown on 2008-07-05
> **bad sneakers said:**
> Does anyone actually read this forum?

Hi bad sneakers. My first instinct was to answer no,but I see that 107 people have viewed Your post. Perhaps they like me are unable to answer Your question correctly. Please be patient, someone will help, I'm sure.

---

### Post by Bubba64 on 2008-07-06
All we an do is assume you are running a desktop CD that is not installed and your not able to get a working screen resolution. Tell us if your dual booting, and what program is installed and which CD your are trying, and what the computer is and the drivers. :)

---

### Post by bad sneakers on 2008-07-06
> **Bubba64 said:**
> All we an do is assume you are running a desktop CD that is not installed and your not able to get a working screen resolution. 

That's correct. And I'm using the 8.04 ubuntu cd.

---

### Post by greenco on 2008-07-09
I am having the same problem!!!
I am running WinXP (SP2) on a desktop system and I am trying to boot from the Umbuntu 8.04 CD, that I made from the downloaded ISO file. I select the option to try the demo, without installing anything and after it starts to load the OS and it gets to a black screen that says:

1:Analog Input
Cannot display this video mode

The boot process hangs at this point. I have lowered my screen resolution and it doesn't help. I sure would like to get past this problem.

---

### Post by bad sneakers on 2008-07-11
Bump

---

### Post by avtolle on 2008-07-11
[https://help.ubuntu.com/community/BootOptions#When%20installing](https://help.ubuntu.com/community/BootOptions#When%20installing) take a look at the vga=xxx boot option. You could try the one that is given first to see if it works, that is vga=771.

---

### Post by bad sneakers on 2008-07-14
bump

---

### Post by bad sneakers on 2008-07-16
^

---

### Post by bad sneakers on 2008-07-20
bump

---

### Post by bad sneakers on 2008-07-24
^

---

### Post by bad sneakers on 2008-07-29
bump

---

### Post by SunnyRabbiera on 2008-07-29
Hmm, shame no one has given you answers for this yet.
But did you try the alternate install CD?

---

### Post by bad sneakers on 2008-07-29
Nope. And I'm on dial-up, so I can't download it. It wouldn't solve my problem anyway. I could probably install with the disc I have; I just wouldn't be able to use the OS once it's installed.

---

### Post by bad sneakers on 2008-07-31
bump

---

### Post by bad sneakers on 2008-08-01
bump

---

### Post by bad sneakers on 2008-08-01
This is ridiculous.

---

### Post by bad sneakers on 2008-08-02
> **bad sneakers said:**
> This is ridiculous.

---

### Post by bad sneakers on 2008-08-06
If it's impossible to configure xorg or whatever to work with my monitor, let me know so I can stop wasting my time bumping this thread.

---

### Post by perlluver on 2008-08-06
You might be able to get more help at [http://www.linuxquestions.org](http://www.linuxquestions.org).

---

### Post by bad sneakers on 2008-08-11
^

---

### Post by bad sneakers on 2008-08-11
^

---

### Post by dc_atkinson on 2010-02-24
I have the same problem with the same Dell monitor.   Did you get anywhere with this problem???

---

