---
title: "Hardware error or Software error?"
date: 2008-02-19
forum: General Help
---

### Post by go7Ul1ai on 2008-02-19
Hello,
I am getting very worried about my laptop as regularly Firefox stops responding, and tonight Pidgin stopped responding and so did numerous other applications. It got so bad that tonight when applications stopped responding, I couldn't do anything at all, I couldn't even do anything on the panels, It was scary. I am wondering if this could be a hardware error/fault/problem?
But I was dual booting with Vista until I decided to reinstall Ubuntu over Vista so it was just Ubuntu installed, back when I was dual booting everything was fine with Ubuntu. Do you think it was just bad luck that time on installing, just a bad install?
Should I reinstall Ubuntu? I have checked for memory errors using the Ubuntu Live CD mem test and i've used memtest.org's memtester. Also, I put in my Vista Recovery disk and it wouldn't let me check for memory faults, so I typed in on the command line 'chkdsk', it scanned some files and at the end it said 'Failed to transfer logged messages to the event log with status 50', what does this mean and does this mean I have a hardware fault?

I am really worried and don't know what to do, please someone help me.

Lee x

---

### Post by go7Ul1ai on 2008-02-19
Please help :( I don't know what to do

---

### Post by mrsteveman1 on 2008-02-19
So the memtest check returned no errors?


Is the computer running hot? If the system is really, really hot, it can become unstable like you said.


Are there any weird errors in dmesg when the system is running?


I would definitely do a fresh installation of ubuntu to remove any possible software problems. Also might be worth it to check the disk for bad sectors using UBCD, since the windows chkdsk isn't all that useful.

---

### Post by go7Ul1ai on 2008-02-20
> **mrsteveman1 said:**
> So the memtest check returned no errors?


Is the computer running hot? If the system is really, really hot, it can become unstable like you said.


Are there any weird errors in dmesg when the system is running?


I would definitely do a fresh installation of ubuntu to remove any possible software problems. Also might be worth it to check the disk for bad sectors using UBCD, since the windows chkdsk isn't all that useful.

Thanks for the reply, I just did a fresh install so I'm hoping things are better. My system wasn't hot at the time of writing or time of errors etc, I keep it in a well ventilated place and theres no dust in the hardware etc.
What is UBCD and I don't know what dmesg is?

Lee x

---

### Post by go7Ul1ai on 2008-02-20
Thanks or the replies everyone

---

### Post by mrsteveman1 on 2008-02-20
[UBCD]("http://www.ultimatebootcd.com/") is a boot cd intended for diagnosing system problems, it includes a large number of programs that can't be run in linux, and it also includes a lot of the common ones that do run in linux.

In particular there are a lot of disk testing programs on the disc that should help determine if the disk has bad sectors or other damage. 

It's quite useful, and it can actually be run from a USB stick so you dont have to carry around CDs (which i hate).

Usually problems like this happen because the system is hot, or because the ram is bad, or because the hard drive is bad. I'm guessing that reinstalling ubuntu will fix the problem but definitely you should look into that disk and make sure its OK, at the least install smartmontools and check it like this:

```
sudo smartctl -H /dev/sda
```

---

