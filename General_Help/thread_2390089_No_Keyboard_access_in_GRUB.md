---
title: "No Keyboard access in GRUB"
date: 2018-04-25
forum: General Help
---

### Post by flyingsolo on 2018-04-25
My desktop is dual boot Ubuntu and Windows 10 with a USB connected old iMac keyboard which has worked well for ages.
However, recently it seems to have lost functionality during the booting process so that I can no longer use arrow down to select the Win 10 option at the GRUB screen; I have no idea what made this change.
I've read that USB keyboard access may need to be set in the BIOS but that screen also requires a keyboard entry (del) to access it and the keyboard is the issue.
Is it likely the BIOS needs tweeking and how do I get access when the keyboard won't respond to entries?

I should also say that I do successfully log in to Ubuntu since it is top of list in grub and the keyboard does work once the OS boots.

Thanks,

---

### Post by flyingsolo on 2018-04-28
I've only heard crickets so far.
Hopefully I've explained my problem well enough but to rephrase it, I can't selet any of the boot options offered except the default top one which is Ubuntu, because the keyboard is not recognized during the booting process as it used to be. Consequently, I can't log into Win 10 partition. Once Ubuntu loads, the keyboard is recognized and can be used.

I haven't found this explained in my searches so far. Advice?
Thanks in advance.

---

### Post by flyingsolo on 2018-08-18
Still trouble shooting this. I did get to view BIOS settings by disconnecting CPU fan on start. However, it listed all USB ports active and detected the presence of the keyboard and mouse. 
Nonetheless, the keyboard was still inactive at BIOS.
I'm thinking next to try clearing the CMOS (battery removal method). Not being any sort of expert at this, are there potential problems I may create by resetting BIOS? 
Maybe I just need a bit of hand-holding to give me confidence! ;)

---

### Post by him610 on 2018-08-18
Hello flyingsolo from Nova Scotia, Canada,

You don't need to clear CMOS, or reset the BIOS. You originally stated you have a USB keyboard which means your BIOS recognizes it, and it  means  there is nothing to (re)set there. You may need to consider replacing your keyboard; sometimes the contacts get worn and no longer provide a good connection. Walmart sells decent wireless Logitech keyboard/mouse combos for as low as $20. 

Hope this helps.

---

### Post by flyingsolo on 2018-08-18
Thanks for the advice but I seem to have solved it (finally) on my own. 
(Luckily, a very rainy day today so had nothing better to do!)

Initially, I did try a different working keyboard from another system with no success.
So I did proceed to clear the CMOS after reading elsewhere that it should be safe to do so. This did fix it and allow keyboard access during restart & so allow selecting the Win 10 installation. However, it failed again on a restart. So, next I just replaced the CMOS battery (6 y old afterall) and now all seems good again.
I still don't know if this was all precipitated by a bad (old) CMOS battery or maybe there was a power surge or power interruption disrupting the system. 

I realize none of this is really an Ubuntu issue, so maybe not appropriate for these forums, but when you're faced with a new problem, you don't really know where the answer may be. Hopefully someone else may find this thread of use for a similar issue.

---

### Post by him610 on 2018-08-19
flyingsolo,

Thanks for sharing your experience, and your solution. I have never had a case of defective or old CMOS battery even in systems 10+ years old; it is something I hardly ever consider. A few years ago, I did have one system that would sometimes fail to boot which would require resetting the CMOS then it would boot right up.

---

