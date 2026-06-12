---
title: "Huge performance issues... CPU activity looks like a Square waveform"
date: 2007-10-19
forum: General Help
---

### Post by sorbix on 2007-10-19
I have been having **huge** performance issues in Gutsy.  As I type this message, it takes over a second for each character to register in the text box.  Also, my CPU activity is oscillating between 100 and 0%.  This didn't happen until I upgraded to gutsy, and I have desktop effects disabled.

I know this is a very general problem that could be caused by a lot of things, but I'm hoping someone will have some hints to get this fixed.  I have a Celeron (2-something ghz) if that helps.  Please help... this message literally took 20 min to write.

---

### Post by tak1150 on 2007-10-19
OK, 1-or-2-words-answer question (i understand it takes a long time for you to type);
When you say upgrade, did you upgrade through apt-get or upgrade manager or did you do a clean install of Gutsy?

when you type
```
top
```
in your terminal, what are the top 3~5 entries in the table?

---

### Post by sorbix on 2007-10-19
The top one is usually udevd and sometimes xgl.

I did the update a few days early with the upgrade manager.

I appreciate the help.

---

### Post by tak1150 on 2007-10-19
is either udevd or xgl hogging up 100% of CPU?

---

### Post by sorbix on 2007-10-19
its hard to tell since it doesnt refresh that often, but it looks like udevd is out of control.  im looking through google for some answers right now, but if you have any tips on what it might be, i would love the help

---

### Post by sorbix on 2007-10-19
OK i just opened my system log and its getting error messages like this by the hundreds every 10 seconds or so:

device mapper: table: 254.1: linear: dm-linear: Device lookup failed
device mapper: ioctl: error adding target to table

---

### Post by sorbix on 2007-10-19
OK so I removed the evms packages as was discussed in a bug report about what I am experiencing.  It seems to have fixed the error messages in my system log and the CPU use fluxuations, but text is still taking forever to register in text boxes

---

### Post by tak1150 on 2007-10-19
You might try unplugging some devices (esp. USBs). When the Linux kernel encounters hardware that it's not sure how to handle, it does stuff like what you're experiencing sometimes. Other than that, I'm not sure what you can do. Sorry; not much of help...

---

### Post by sorbix on 2007-10-19
Thanks for your help, the CPU issues are fixed as far as I can tell.  Apparently it had something to do with evms packages trying to mount a hard drive that was already mounted or something.  But I am still trying to fix my text input issues, which seem unique to firefox.  I'm doing some testing.

EDIT: Ironically, the problem went away when I enabled desktop effects.  Go figure.

---

### Post by MrChonks on 2007-10-20
> **sorbix said:**
> 

EDIT: Ironically, the problem went away when I enabled desktop effects.  Go figure.

Thanks for posting this.  After installing xgl, I played around with the enhanced graphics and decided that it would probably be less resource intensive if I left them off.  But, what I found was the CPU was spiking every time I tried typing anything into FF.  So, I read this post, saw your edit and tried enabling desktop effects again.  That worked like a charm.  Go figure, indeed.

---

