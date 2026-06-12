---
title: "Opera very slow to start"
date: 2013-02-22
forum: General Help
---

### Post by robc02 on 2013-02-22
Opera 12.14 on Ubuntu 12.04 amd64.

Very slow startup - over a minute and lots of hard-drive activity. Other apps not affected so I think this is an Opera problem.
This only happens on the first startup after a reboot - closing Opera and re-opening later is fine.
I have tried clearing the cache and also re-installing, neither has any noticeable effect.
I can't find any log file activity, but maybe I'm not looking in the right place?
Any ideas?

---

### Post by carl4926 on 2013-02-22
If you start it from a terminal, is there any noise?

---

### Post by robc02 on 2013-02-22
Starting from terminal I get this:

> Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory


I looked into this a few days ago. VDPAU is for Nvidia cards - I have an ATI Radeon 2100 on board.

Interestingly I just did a Kernel upgrade and after the reboot Opera started quickly. After the next reboot Opera was slow again. The same thing happened when I reinstalled Opera - OK first time then back to slow.

---

### Post by zhaozhou on 2013-02-22
You can ignore the message about the missing shared object. You can 'strace'(1) the call to opera, and paste that.


```

sudo apt-get install strace pastebinit
strace opera 2>&1 | pastebinit

```

---

### Post by stinkeye on 2013-02-22
When reinstalling your local configs remain.
ie opera still starts using the configs @ **~/.opera**

Test to see if it's caused by your local configs.
Create a folder in your home directory called **opera-test**

Then to start opera using **~/opera-test** as the personal directory 
instead of the normal ~/.opera directory, 
run in terminal...
```
opera --pd ~/opera-test
```

Starting opera normally will still use the **~/.opera** configs.
Be aware this is where your customization, mail, passwords etc are stored.

---

### Post by robc02 on 2013-02-22
> **zhaozhou said:**
> You can ignore the message about the missing shared object. You can 'strace'(1) the call to opera, and paste that.


```

sudo apt-get install strace pastebinit
strace opera 2>&1 | pastebinit

```

I've had a number of problems with pastebinit! Here's how it went:

Did "strace opera 2>&1 | pastebinit" also monitored progress using System Monitor. Opera eventually got started a minute or so later. I closed it almost immediately - its window dissappeared BUT opera was still active, according to System Monitor, for several minutes - and its lock file never closed, even after opera stopped. 

In the meantime System Monitor showed Python to be occupying ever more memory, finally reaching 1.5G, and heavy network (sending) activity. Eventually I got an error message saying that there was insufficient memory for pastebinit, so I shut the system down. 

I tried all this again and got the same results but shut down Python before getting an error message - this cut out the network activity.

Anyway, I tried a third time but piped the output of strace to gedit - the file is enormous, even compressed it is 21Meg! 

Is there anything I should look for to help me filter out the relevant from the irrelevant so that I can post it?

Thanks
Rob

---

### Post by robc02 on 2013-02-22
> Then to start opera using ~/opera-test as the personal directory
instead of the normal ~/.opera directory,
run in terminal...

Did this and Opera starts immediately. Clearly there's something in my .opera folder causing the problem!

If I can't get anywhere with the strace results I'll have to gradually build up a new .opera from my old one. 'Could be a lengthy job.

---

### Post by stinkeye on 2013-02-22
If you use the mail client try starting opera without mail.
```
opera -nomail
```

For other options see
```
opera --help
```

---

### Post by robc02 on 2013-02-24
Drat!! The problem seems to have gone away while I was testing things. I haven't actually *changed* anything - just started it using "nomail" option and had a general play around.

I bet the problem will come back before long!

It still takes a long time to close down. The only way I can quickly reopen opera is with:

```
killall opera; killall -9 opera;  rm ~/.opera/lock
```

I'm sure I shouldn't have to do that.

I'll monitor how it goes over the next few days.

Thanks for you help so far.

---

