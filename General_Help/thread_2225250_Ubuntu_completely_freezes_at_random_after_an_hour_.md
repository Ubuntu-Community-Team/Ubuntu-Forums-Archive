---
title: "Ubuntu completely freezes at random after an hour or so of use"
date: 2014-05-20
forum: General Help
---

### Post by kbjr on 2014-05-20
This is not a new install, I have been using ubuntu on this machine for almost 2 years. This problem, however, just started yesterday. After logging in and using the computer for about an hour or so, the whole machine completely freezes. Mouse and keyboard do nothing, cannot pull up a tty, cannot ping the machine from another; Just completely frozen. The only thing I can do is hard reboot the machine.

Ubuntu 12.04 32-bit
Kernel: 3.5.0-49-generic

I tried rebooting into ubuntu with a back-version of the kernel (as far back as 3.5.0-45), but the same thing still happened.
I also ran memtest for a while (not very long, but a while) and didn't get any errors.

I will be happy to provide any other info needed.

---

### Post by Gyokuro on 2014-05-20
Hi

Could be an overheating problem, dying PSU, bad hard disk sectors,... for a quick RAM test you should either let memtest run for a while or in case you have more then two RAM sticks you can use always one - work with each one some time and if it freezes again you know which one is bad and sometimes it's good to clean your machine of all the dust which you have collected over the time. Maybe something interesting got logged in /var/log/syslog. Maybe you find something interesting in it and can post it here?

---

### Post by kbjr on 2014-05-20
Hi

I have dumped a copy of syslog here ([https://www.dropbox.com/s/sbfab1jqgdjixxx/syslog.1](https://www.dropbox.com/s/sbfab1jqgdjixxx/syslog.1)). I'm actually starting to think that this might have something to do with VirtualBox. I have been running a dev VM for work lately, and the freeze only seems to occur at times when this VM is running. The computer has been running (admittedly mostly idle) for a little over an hour now with no problem.

---

### Post by kbjr on 2014-05-20
Also, to respond to the other things you mentioned:

I don't think its overheating, the case stays pretty cool all the time, and the fans don't kick up which they are "supposed" to do if the temp gets too high.
The PSU is new, only about 4-5 months old, so I hope its not that >_<
Like I said in the original post, I did run memtest for a while, ran through 6 tests before I stopped it, no errors.
The case could use a cleaning; There is a fair amount of dust in there ... I will try that.

edit:

Also, this is a dual boot machine, and I have never had this happen on windows (and I do much more system intensive things over there).

---

### Post by tgalati4 on 2014-05-20
Besides cleaning, it's a good idea to reseat cards, RAM, and all connectors.  Run it for several hours without a VM to make sure it is stable, then start your VM and note the time.  It's possible that your VM has an issue and needs to be scrapped.  What OS is running in your VM?

---

### Post by kbjr on 2014-05-20
It's an ubuntu VM, running through [vagrant]("http://www.vagrantup.com/")/virtualbox. I'll check all the connections when I open it up for cleaning.

edit:
specifically, it is the vagrant precise32 box (ubuntu 12.04 32-bit)

---

### Post by Gyokuro on 2014-05-22
Have you solved your freeze problems as I have to admit I'm not a fan of virtualbox and prefer KVM which is much more reliable (virtualbox experience of the past).

---

