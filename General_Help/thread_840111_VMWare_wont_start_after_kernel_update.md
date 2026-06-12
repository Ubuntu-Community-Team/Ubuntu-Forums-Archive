---
title: "VMWare wont start after kernel update"
date: 2008-06-25
forum: General Help
---

### Post by armandop on 2008-06-25
I downloaded vmware-server-1.0.6-91891 and installed it using one of the vmware-howtos on this site with kernel 2.6.24.18 installed.

Everything was working fine and I had setup my winXP partition, but suddenly it stopped working. I'm blaming it on the latest kernel update to 2.6.24.19. I've tried going back to the previous kernel but still it doesn't work.

Anyone have any clues ?

When I click on VMWare console I get the mouse pointer to change to the vmware Icon and vmware starts loading on the taskbar, but then it dissapears with no error message.

Let me know where I can find the vmware log so I can get an idea why it stopped working,

Thanks.

---

### Post by ubnewbie2 on 2008-06-25
> **armandop said:**
> I downloaded vmware-server-1.0.6-91891 and installed it using one of the vmware-howtos on this site with kernel 2.6.24.18 installed.

Everything was working fine and I had setup my winXP partition, but suddenly it stopped working. I'm blaming it on the latest kernel update to 2.6.24.19. I've tried going back to the previous kernel but still it doesn't work.

Anyone have any clues ?

When I click on VMWare console I get the mouse pointer to change to the vmware Icon and vmware starts loading on the taskbar, but then it dissapears with no error message.

Let me know where I can find the vmware log so I can get an idea why it stopped working,

Thanks.

If you run vmplayer from a prompt, you'll probably see something like

```
 vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

```

Do as it says (put a sudo in front of the command), and it will do what it needs to do, ask a few questions, recompile bits maybe, and it will then work again.

One thing, you'll need to install the kernel headers if you don't already have them.  You can install them using synaptic.

---

### Post by armandop on 2008-06-25
Solved!

I did 'vmware' from the terminal and then ran '/usr/bin/vmware-config.pl' accepted all defaults and vmware is working again.

Do you know why I have to recompile vmware after every kernel update, but the other Ubuntu apps work fine ?

---

### Post by ubnewbie2 on 2008-06-25
> **armandop said:**
> Solved!

I did 'vmware' from the terminal and then ran '/usr/bin/vmware-config.pl' accepted all defaults and vmware is working again.

Do you know why I have to recompile vmware after every kernel update, but the other Ubuntu apps work fine ?

Yes.  VMWare has to "virtualise" hardware like the mouse, keyboard, USB, network, CDROM, screen and HD.  Some of this involves modules/drivers that need to be compiled to work with the particular kernel that you are running.  

It's a bit unfortunate, but at least vmware provide the script to fix it.  Maybe they should build a nice GUI for it that they can launch whenever vmplayer detects the problem.

---

### Post by bodhi.zazen on 2008-06-25
vor-ubuntu has a nice how-to for a similar issue and the nvidia driver, you may be able to adapt it to vmware.

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

