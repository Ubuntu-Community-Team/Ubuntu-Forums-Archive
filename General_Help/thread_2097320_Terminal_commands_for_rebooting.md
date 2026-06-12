---
title: "Terminal commands for rebooting"
date: 2012-12-22
forum: General Help
---

### Post by TimmyK. on 2012-12-22
Hello everyone. A little while ago, my laptop had a crash, and I tried rebooting. First it asked me which distro to boot, then in what mode. I clicked normal, then it asked for a login. I did so, then it just let me put in a terminal command. Could someone please tell me which commands I should use to shut it down, reboot, and anything else I should do? Should I just boot normal or should I do something different? Thanks in advance.

---

### Post by haqking on 2012-12-22
> **TimmyK. said:**
> Hello everyone. A little while ago, my laptop had a crash, and I tried rebooting. First it asked me which distro to boot, then in what mode. I clicked normal, then it asked for a login. I did so, then it just let me put in a terminal command. Could someone please tell me which commands I should use to shut it down, reboot, and anything else I should do? Should I just boot normal or should I do something different? Thanks in advance.

```
sudo shutdown
sudo shutdown -r now
sudo reboot
sudo shutdown -h now
sudo poweroff
```

You can use the man pages to look up options for these commands and find which one you want or need

example:
```
man shutdown
```

---

### Post by TimmyK. on 2012-12-22
Thanks! And how would I boot normally? Just "sudo boot"?

---

### Post by haqking on 2012-12-22
> **TimmyK. said:**
> Thanks! And how would I boot normally? Just "sudo boot"?

if you can type a command then you have already booted

I dont get your question ?

---

### Post by GameX2 on 2012-12-22
> **haqking said:**
> ```
sudo shutdown
sudo shutdown -r now
sudo reboot
sudo shutdown -h now
sudo poweroff
```You can use the man pages to look up options for these commands and find which one you want or need

What's the difference between sudo shutdown -r now and  sudo reboot ?  Same for sudo shutdown & sudo shutdown -h now ?

Thanks for the precision!

---

### Post by haqking on 2012-12-22
> **GameX2 said:**
> What's the difference between sudo shutdown -r now and  sudo reboot ?  Same for sudo shutdown & sudo shutdown -h now ?

Thanks for the precision!

poweroff can usually be done without sudo depending on the system.

Shutdown -r and reboot are the same thing (symlinks)

use the man pages to find extra options 

Peace

---

### Post by coldcritter64 on 2012-12-22
> **TimmyK. said:**
> Thanks! And how would I boot normally? Just "sudo boot"?
I think you mean "reboot normally" and "sudo reboot" would do it, it was one command in haqking's previous post, so yes.

---

### Post by sudodus on 2012-12-22
I think the critical part is how to avoid hard reset (the power button or the electric plug or remove the battery depending on what computer it is). Because hard reset can shut off the system before important things have been written to the hard disk drive.

When your computer won't respond to normal key presses or mouse actions, try to press a key sequence while pressing

***alt + SysRq*** all the time

***r e i s u b***  (slowly, maybe one key each second)

This shuts down the run levels and performs necessary writes to disk if possible at all, and it works most of the time.

After such a reboot, the computer is likely to boot normally.

If not it might be possible to repair the root file system. Boot from another drive (from a repair file system or from the Ubuntu install drive), avoid mounting anything on the hard drive and run
```
sudo e2fsck -f /dev/sdxy
```
where x is the drive letter, often a, and y is the partition number on that drive, often 1, 5 or 6, e.g. /dev/sda6

---

### Post by TimmyK. on 2012-12-22
Sorry, I'm getting a little confused. Do I just type in the command you gave me and reboot? Am I in a terminal mode or something?

---

### Post by sudodus on 2012-12-22
> **TimmyK. said:**
> Sorry, I'm getting a little confused. Do I just type in the command you gave me and reboot? Am I in a terminal mode or something?
***alt+SysRq  reisub*** works in linux independent of graphical or text screen mode. It is a hot-key sequence.

But if your system is up and running normally, you can use
```
sudo reboot
``` to reboot and
```
sudo poweroff
``` to poweroff (shutdown, including power).

---

### Post by TimmyK. on 2012-12-22
Ok, I know this will seem like a dumb question, but how do I type in alt+SysRq reisub? Does is have to be in the terminal or just anywhere? Do I hold down the alt key while typing that in or is it a terminal command?

---

### Post by sudodus on 2012-12-22
When your computer won't respond to normal key presses or mouse actions, try to press a key sequence while pressing
 
 ***alt + SysRq*** all the time
 
 ***r e i s u b*** (slowly, one key each time for about one second)

See this link [[COLOR="Red"]https://en.wikipedia.org/wiki/Magic_SysRq_key[/COLOR]]("https://en.wikipedia.org/wiki/Magic_SysRq_key")

---

### Post by TimmyK. on 2012-12-22
OK, I completely forgot about the SysRq key. So hold down Alt + SysRq and slowly type in r e i s u b? And this won't clear all my data, will it? (Sorry if you are rolling your eyes, I just need to make absolutely sure of everything!) Thanks.

---

### Post by sudodus on 2012-12-22
> **TimmyK. said:**
> OK, I completely forgot about the SysRq key. So hold down Alt + SysRq and slowly type in r e i s u b? And this won't clear all my data, will it? (Sorry if you are rolling your eyes, I just need to make absolutely sure of everything!) Thanks.
On the contrary, in a locked system ***it is likely to save data***, that might be destroyed by a hard reset.

Did you read the link? It explains more than can be written in this conversation. And you can find more links about the same subject in order to understand how it works.

---

