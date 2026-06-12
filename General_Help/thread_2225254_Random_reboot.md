---
title: "Random reboot"
date: 2014-05-20
forum: General Help
---

### Post by Ertai87 on 2014-05-20
My computer (Ubuntu 12.04) just randomly rebooted while I was in the middle of doing something.  I did not hit anything (as far as I know) that would cause a reboot, such as the power button or anything of that sort.  I do not appear to have had a power failure either, and even if I did, I'm using a laptop so it shouldn't have caused my computer to fail.

Anyway, I'm wondering what happened.  Everything seems to be working fine now, although I had to manually disconnect and reconnect to my wifi network after the computer restarted to get that to work.  I'm wondering if this is something seriously worth looking into.  This is the first time it's happened.

On reboot, the computer didn't give me any sort of "your computer has experienced a fatal error" dialog or anything of that sort, for any who are interested in that.  I don't know how to use the Ubuntu console well, but dmesg didn't appear to have any useful information after reboot; it seems to just output messages from the after the reboot, although I'm not super familiar with dmesg so perhaps there are some flags I should have used.

Before the reboot, I was doing some websurfing and playing Hearthstone (via Wine).  Nothing I haven't done on multiple occasions before without difficulty.

Thanks.

---

### Post by Gyokuro on 2014-05-20
Hi

Could be a hardware problem (always make sure your laptop fan is clean, RAM/HD are ok) but could be a software problem and as you have not posted that much someone can only guess but could you post what you have in:

/var/crash

command is: ls -l /var/crash

you do this either you search for terminal or press the key combination CTRL+ALT+T to open the terminal and enter above command in it: ls -l /var/crash and post via a screen shot what you have or not. Do not worry a lot of people are here which are able to help you and ask whatever question you may have.

---

### Post by Ertai87 on 2014-05-21
ls -l /var/crash:

```
total 0
-rw------- 1 whoopsie whoopsie 0 May 20 14:08 _usr_bin_nm-connection-editor.1000.uploaded
```

This computer is less than a month old, so I hope it's not a hardware issue.  That said, I may have had a hardware issue with this same model of computer before (the one I'm currently using is a loaner from Best Buy while they fix my other one which was having a blinking screen within 2 weeks of purchase), so it's not out of the question I guess.

---

### Post by Gyokuro on 2014-05-22
Hi

Thanks - only your network manager editor crashed (not bad but I have expected something else). Which GPU drivers get used (NVidia, Ati, Intel) in your system?

---

### Post by Ertai87 on 2014-05-22
I don't know how to get you meaningful data to answer that question, but the non-meaningful answer is that I'm using an Additional Driver for some sort of ATI GPU.  There are 3 versions for it: The "standard" one, "standard with updates", and "experimental".  I need to use "experimental" so that a game I play will render graphics properly, so I'm using that one.

As a side note, since you're mentioning the network manager crashing: Since this happened, it seems that I have to disconnect from my Wifi and reconnect to it semi-regularly once I boot my computer or wake it up from sleep (I have to reconnect once, and then it's fine, but I seem to have to reconnect each time).  Wondering if this is related somehow.

---

