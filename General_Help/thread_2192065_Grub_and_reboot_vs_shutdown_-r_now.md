---
title: "Grub and reboot vs shutdown -r now"
date: 2013-12-05
forum: General Help
---

### Post by walth on 2013-12-05
I have a media center pc that I generally admin from cli running standard Ubuntu 13.10.  Generally I like to reboot it by simply typing 
```
sudo reboot
```

The issue I'm having is afterwards it just sits at the Grub screen.  After which I have to get up and find the keyboard and hit enter.  

However If I enter 
```
sudo shutdown -r now
```
I don't even see the Grub screen and it boots normally with no issues as expected. 

Is this to be expected?  I've been typing sudo reboot for quit a while and never had this happen until just recently.  Is there a way to fix this?

Thanks

---

### Post by efflandt on 2013-12-06
Strange, according to "man reboot" without --force it should do the same thing:> When called with --force or when in runlevel 0 or 6, this tool  invokes the reboot(2) system call itself and directly reboots the system.  Otherwise this simply invokes the shutdown(8) tool with the appropriate arguments.Note that if you are doing this from another computer you may want to end the command line with **&** to make sure that shutdown continues after your remote terminal disconnects. I seem to remember complete shutdown not completing from an ssh unless I did "sudo shutdown -h now &", although the only computer I do that on is a very old SuSE 8.2 box.

So you might try this to see if it works any differently: **sudo reboot &**

I know that worked on a Raspberry Pi via ssh ($35 ARM credit card size computer that boots special Debian wheezy version from SD).

---

### Post by jeremy1701 on 2013-12-07
I thought the same things as efflandt, 'reboot' should do the same thing as 'shutdown -r now'. You could try the --verbose option to see if you get any additional information. 

> --verbose
    Outputs slightly more verbose messages when rebooting, useful for debugging problems with shutdown.

---

