---
title: "Flashing the Nokia 770 in Ubuntu environment"
date: 2007-05-28
forum: General Help
---

### Post by al4ie on 2007-05-28
Hi guys, hope someone can help me. I totally borked my 770 yesterday running the Synaptic package manager. I have recently moved over to Ubuntu, and cannot find a flasher utility for the Nokia 770 to run under Ubuntu anywhere. I can't seem to get any of these guys to work: [http://tablets-dev.nokia.com/d3.php](http://tablets-dev.nokia.com/d3.php) - although it should be noted I am an Ubuntu n00b. I'm running the IE86 build. Any and all help much appreciated.

---

### Post by Jussi Kukkonen on 2007-05-28
I assume you mean the i386 Ubuntu version? In that case, use the flasher-3.0 executable like this:
```
sudo ./flasher-3.0 --reboot --flash --fiasco RX-34_2007SE_3.2007.10-7_PR_COMBINED_MR0_ARM.bin
```
replace the name of the image file with the one you want to use.

---

### Post by al4ie on 2007-05-30
ah dude, thank you. I can see this is the right way, but I get a command not found error?

cd Desktop
alfie@Alfies:~/Desktop$ sudo ./flasher-3.0 --reboot --flash --fiasco SU-18_2006SE_3.2006.49-2_PR_F5_MR0_ARM.bin
sudo: ./flasher-3.0: command not found


( I changed directory to desktop where the BIN file is).

Thanks.

---

### Post by ikonia on 2007-05-30
check the permissions on the file, it needs to be executable by your user.

---

### Post by al4ie on 2007-05-30
yup, I am the user...-

---

### Post by fanatik on 2007-05-30
is the flasher-3.0 command in your Desktop folder too? as ./flasher-3.0 says run flasher from the current directory. paste the output of:

**$ ls -l**

when in your Desktop directory, so we can see permissions of the relevant files.

---

### Post by al4ie on 2007-05-30
I get this:

flasher-3.0
SU-18_2006SE_3.2006.49-2_PR_F5_MR0_ARM.bin
alfie@Alfies:~/Desktop/flasher 770$ 

(thanks again for the help, much appreciated this end)

---

### Post by al4ie on 2007-05-30
hang about, it's working now!!!

Will feedback when done.

---

### Post by al4ie on 2007-05-30
Ah dude, that totally worked. I think it was because I had the bin and flasher just on the desktop rather than in a folder. Once I popped them into their own it was all steam ahead.

Thanks again for the help.

alf.

---

