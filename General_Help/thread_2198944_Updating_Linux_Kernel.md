---
title: "Updating Linux Kernel"
date: 2014-01-11
forum: General Help
---

### Post by Shadius on 2014-01-11
Hey everyone!

I'm interested in learning how to update my Linux kernel. I'm running Ubuntu 12.04, and I want to know how to find out what kernel I'm currently running, if I need to update it, and how to do so.  Also, where do I go to find what the latest Linux kernel is? Thanks for the help!

---

### Post by The Spectre on 2014-01-11
To see what Kernel you are currently using run this command in Terminal...
```
uname -a
```

The find out what the latest Linux Kernel is you can go here...
[https://www.kernel.org/](https://www.kernel.org/)

This is a good place to start for Kernel information...
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by grahammechanical on 2014-01-11
You can find out the kernel version by running the command

```
uname -a
```

or

```
uname -r
```

This is what I see

> 3.13.0-1-generic #16-Ubuntu SMP Tue Jan 7 19:44:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

My kernel is Linux 3.13.0 generic. I am using the development branch of next version of Ubuntu (14.04) that will not be released until the end of April. So, I have a kernel that is not yet available to Released versions of Ubuntu.

If everything is working as it should then you can wait until the Ubuntu developers update the kernel for you. Ubuntu 12.04 was released in April 2012 and since then it has had 3 major upgrades called point releases. Each of these point releases brings with it a newer version of the kernel that has been tested by the Ubuntu developers. The next point release to 12.04 will come towards the end of January and the beginning of February. You could also wait until the end April and upgrade to Ubuntu 14.04 and you will get the Linux kernel 3.13.0 without any trouble.

If you want to experiment, then my advice would be to put in another installation of Ubuntu and experiment with that. Something will surely break the OS and if that happens to your only Ubuntu OS then there is difficulty.

Please see this thread and see what happened when someone got the very latest Linux kernel. For me there was no problems. But others sometimes do have problems.

[http://ubuntuforums.org/showthread.php?t=2198375](http://ubuntuforums.org/showthread.php?t=2198375)

Linux kernels come from here

[https://www.kernel.org/](https://www.kernel.org/)

[https://www.kernel.org/category/releases.html](https://www.kernel.org/category/releases.html)

Installing them is not something I do.

Regards.

---

### Post by Shadius on 2014-01-11
Thank you for the information.

For comparison purposes, this is what I see when I use the Terminal to find out what kernel I'm on: 

Mine: ```
shadius@shadius-phantom:~$ uname -a
Linux shadius-phantom 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

Yours: ```
3.13.0-1-generic #16-Ubuntu SMP Tue Jan 7 19:44:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 
```

Now you said that you're using the 3.13.0-1 kernel that isn't released yet which is why it's obviously different from my kernel, and you mentioned point releases.  Where do I look for Ubuntu's point releases so I can check at which point I'm at right now?  I'd like to look at the dates to get a timeframe and keep myself updated about the point releases.

---

### Post by deadflowr on 2014-01-11
You are most likely at 12.04.3, however you're running the original kernel version for 12.04.
This here explains better, and also how to upgrade the kernel to more recent versions which come default on the upgraded point releases
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by Shadius on 2014-01-11
> **deadflowr said:**
> You are most likely at 12.04.3, however you're running the original kernel version for 12.04.
This here explains better, and also how to upgrade the kernel to more recent versions which come default on the upgraded point releases
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

So according to this:

```
shadius@shadius-phantom:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

```

I'm on 12.04.4 LTS.  You said I'm running the original kernel version of 12.04, meaning that I didn't get the 3 point releases that user grahammechanical mentioned?  If this is correct, what kernel version am I supposed to be up to if I did receive the 3 point releases? Where can I check? Just point me in the right direction.

---

### Post by deadflowr on 2014-01-11
> [COLOR=#000000]what kernel version am I supposed to be up to if I did receive the 3 point releases? Where can I check? Just point me in the right direction[/COLOR]

You're on the right kernel, so don't worry.
The point release number (12.04.4) means your running the most up to date system, even though you're not running the most up to date kernel version.
That link posted should give a reason for that.

---

### Post by Bashing-om on 2014-01-11
Shadius; Hi !

In addition to all the info provided, 
If you are running your graphics with an older ATI graphics card (2x/3x/4x series AMD cards), it will behoove you to remain on the 3.2.0-58-generic kernel.
There is good reason why Hardware Enablement Stack is not implemented in that kernel version.

[INDENT][INDENT]look before you leap
[/INDENT][/INDENT]

---

### Post by Shadius on 2014-01-11
> **deadflowr said:**
> You're on the right kernel, so don't worry.
The point release number (12.04.4) means your running the most up to date system, even though you're not running the most up to date kernel version.
That link posted should give a reason for that.

Oh okay, thank you! I'll check out that link.

> **Bashing-om said:**
> Shadius; Hi !

In addition to all the info provided, 
If you are running your graphics with an older ATI graphics card (2x/3x/4x series AMD cards), it will behoove you to remain on the 3.2.0-58-generic kernel.
There is good reason why Hardware Enablement Stack is not implemented in that kernel version.

[INDENT][INDENT]look before you leap
[/INDENT][/INDENT]

Good to know, thanks for the information. I'm not using a graphics card right now, but I plan on getting one later on. 

Thanks everyone for helping me understand this.

---

