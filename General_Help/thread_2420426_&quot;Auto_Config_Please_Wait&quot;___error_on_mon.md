---
title: "&quot;Auto Config Please Wait&quot;   error on monitor then blank - no OS"
date: 2019-06-05
forum: General Help
---

### Post by anneranch on 2019-06-05
Yet another Ubuntu failure - for so far unknown reason.
**I am not complaining,just looking for help to fix it!**
Everything starts normal , but then I get flash of this message on otherwise black screen

"Auto Config 
 Please wait"

1.Only ONE of three OS on my system fails this way
2. There is nothing wrong with my monitor - works peachy. 
3. Used "grub" recovery and it did not fix it! 
4. I know which OS on which device is failing this way.
5. There is "grub"  something (?) which seems to be chain of files "grub" executes. SO far I have not found how to interpret / read it.
    Planning to compare it between broken and working OS.

 
Reinstalling failing  OS IS NOT an option - I want to fix this on CURRENT version of otherwise perfectly working  Ubuntu 16,04 !

I can download "clean Ubuntu 16"  on USB drive - would that help to "recover " the failing one - without installing it?
I have plenty of disk space to make copies - too late for real OS  backup. 

Any other ideas how to recover from this will be appreciated.

Cheers

---

### Post by dino99 on 2019-06-05
what journalctl/dmesg says ?

---

### Post by anneranch on 2019-06-05
Huh ?
I cannot get the OS to start. 
But I could look into dmesg  when I use "grub" . Not sure if that is legal command then. I'll try it.

---

### Post by anneranch on 2019-06-05
Well I did try it. 
I am not sure "how far" was the load, but I got about 5 pages of messages. 
Of course I cannot print it while in this debug mode. 


Unless I have an idea what message I am looking for it really does not help to solve the problem.
I just run same "dmesg" after successfully starting another OS and it looks pretty normal. 


The "auto config"  is a hardware function of the monitor.
It can be initialized  , pressing a button, anytime.

It apparently does complete , message goes away, but the monitor continues to be blank / black. 
I have no other means to make sure the OS is actually running. 

I am really at loss how to fix this. 

Ideally if I could reinstall the faulty OS but ONLY reinstall what is corrupted. 
Of course that would be done only with all current hard drives removed , with exception of the failing OS. 
I had a bad experience before trying to "upgrade" from 16 to 18. 

Thanks  for your help, appreciate your  assistance to solve this.

---

