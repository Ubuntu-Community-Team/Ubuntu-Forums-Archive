---
title: "Dell Laptop will not suspend"
date: 2013-05-06
forum: General Help
---

### Post by tgross35 on 2013-05-06
Hi all,

I have a Dell Latitude laptop, working fine for a long time. However, I recently updated to 13.04, and now my computer fails to suspend, no matter what. Closing the lid doesn't work, clicking suspend from the system menu doesn't work, and sudo pm-suspend doesn't work. When I try suspend or closing the lid, my screen shuts off and it password locks my computer, but the computer is still clearly working, fan and power light on (normally when suspending the fan would shut off and the power light would do a slow flash.) A simple key press or swipe on the mouse pad will turn the screen back on. When I try pm-suspend, I get a black screen showing a blinking underscore for about 20 seconds, then my computer will return to the state it was and the terminal command will end. I need to be able to suspend, my computer travels and needs to be able to go a few days without power. Any suggestions, please let me know.

Thanks

---

### Post by montag dp on 2013-05-06
I had some problems hibernating with the Ubuntu 13.04 kernel.  There were also some problems with increased power usage. 

It's probably worth a try using an older kernel if it was working fine for you before.  Here is what I did:

1) Add the following line to /etc/apt/sources.list:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security-main

2) sudo apt-get update

3) Install linux kernel, headers, etc. for version 3.5.0-28-generic using synaptic

4) When booting, select "Advanced options" and the added kernel.

---

### Post by icarus128 on 2013-05-06
I also see this with my Thinkpad w520.  This was working this morning but around Lunch I got an update that simply said something like "Ubuntu Base" with not technical details.  I installed this update and I get exactly the behavior the OP described.

In my pm-suspend.log I see this every time:

> 
/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: not executable.
Mon May  6 18:08:51 EDT 2013: performing suspend
Mon May  6 18:09:12 EDT 2013: Awake.
Mon May  6 18:09:12 EDT 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


---

### Post by tgross35 on 2013-05-06
> **montag dp said:**
> I had some problems hibernating with the Ubuntu 13.04 kernel.  There were also some problems with increased power usage. 

It's probably worth a try using an older kernel if it was working fine for you before.  Here is what I did:

1) Add the following line to /etc/apt/sources.list:

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security-main

2) sudo apt-get update

3) Install linux kernel, headers, etc. for version 3.5.0-28-generic using synaptic

4) When booting, select "Advanced options" and the added kernel.

Got the first two steps, but would you mind elaborating on what to install? I am not familiar with synaptic.

---

### Post by tgross35 on 2013-05-07
I don't believe it. I closed my laptop lid today and viola, thing actually goes on standby. I haven't changed anything, I guess it was just inconsistent for some reason; I'll leave the thread open for anyone else who is having the issue.

---

### Post by icarus128 on 2013-05-07
That's bizarre, the exact same thing happened to me this morning.  Nothing at all has changed.

---

### Post by montag dp on 2013-05-07
> **tgross35 said:**
> Got the first two steps, but would you mind elaborating on what to install? I am not familiar with synaptic.Sorry, I was kind of in a rush when I typed that the first time.  You'll want to open synaptic and search for `3.5.0-28'.  Then mark the f

linux-headers-3.5.0-28-generic
linux-headers-3.5.0-28
linux-image-3.5.0-28-generic

However, if everything is working fine now, there's probably no reason to install this kernel.

---

