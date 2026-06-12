---
title: "keyboard doesnot work in VIrtualBox Guest machine"
date: 2008-04-05
forum: General Help
---

### Post by chinese_ys on 2008-04-05
Hello, Guys

I installed Virtualbox 1.5.6 not the ose version on ubuntu 8.04 beta because of the usb support issue. I could not use keyboard when I am tring to type anything in guest machine. I also found keyboard stops working even in installation process. I have a laptop installed opensuse 10.3+virtualbox 1.5.6 under which keyboard is working fine. So I guess this is a problem on the connection between ubuntu and virtualbox. 

Any idea about this?
Thanks,

---

### Post by chinese_ys on 2008-04-07
nobody had this kind of problem?

---

### Post by xmyth on 2008-04-07
I have the same problem, after upgraded to the latest hardy version.

If you uncheck the option "Enable support to enter complex characters", virtualbox will work fine.

The option located at System -> Administration -> Language Support

---

### Post by chinese_ys on 2008-04-08
thanks for the advice.

however I do need other language input which needs "Enable support to enter complex characters"

any other solution?

---

### Post by rdoolen on 2008-04-11
I have the exact same problem. I can make VB work by disabling complex characters, but I need them.

Is this a known bug? Did you read this someplace or figure it out yourself?

---

### Post by dwx1618 on 2008-04-12
Hi, I'm having the same problem, but I'm not sure how to log in to change it without first getting my keyboard and then my entire machine locked up. Help?

---

### Post by cyriver on 2008-04-17
I'm having same problem and I suspect that the keyboard is usb keyboard.

As a work around resolution, if I run VirtualBox as root, keyboard will work in VirtualBox guest OS.
This confirms that the problem is related to usb permission issue.

The real solution should be running VirtualBox as normal user. However, I've not been able to figure out.

---

### Post by dilney on 2008-04-17
I had the same problem and fixed by doing this:

In VirtualBox, go to File -> Preferences -> Input; then uncheck "Autocapture keyboard"  ([http://forums.virtualbox.org/viewtopic.php?t=572](http://forums.virtualbox.org/viewtopic.php?t=572))

---

### Post by kentxu on 2008-04-21
I can confirm this problem. If you have complex language input enabled (from preference), you won't be able to type in virtualbox. This might be also linked to a similar virt-manager problem which the keyboard will lock when you shutdown a guest machine. Especially when you set ram to very low or forgot to set ram value.  The entire Gnome will be locked without keyboard, the only key that works is ctrl-alt-1. I haven't gone back to confirm this problem though.

If you are not sure, you can create a new user account and login to see if the problem goes away, that's how I found out. 

You can disable "auto capture" feature in virtualbox preference menu as a workaround.

---

### Post by rdoolen on 2008-04-21
Disabling 'auto capture' doesn't help me. I can only get it to work two ways.

1. If I disable complex characters and restart X (maybe reboot)
2. launch as ssh -XC localhost VirtualBox

---

### Post by chinese_ys on 2008-04-25
I solved this problem by installing scim-bridge-client-qt in ubuntu 8.04(may need a reboot).

---

### Post by kentxu on 2008-04-26
> **chinese_ys said:**
> I solved this problem by installing scim-bridge-client-qt in ubuntu 8.04(may need a reboot).

This is the best solution so far. 

I first disabled "auto" capture and that worked for me on English Windows XP. However, it doesn't work on Japanese Windows XP guest. Then I installed scim-bridge-client-qt and it worked after I rebooted my machine (won't work without a reboot, reboot XWindow might be enough though).

---

### Post by raynix on 2008-05-15
> **dilney said:**
> I had the same problem and fixed by doing this:

In VirtualBox, go to File -> Preferences -> Input; then uncheck "Autocapture keyboard"  ([http://forums.virtualbox.org/viewtopic.php?t=572](http://forums.virtualbox.org/viewtopic.php?t=572))

This works great for me! Thanks!!!:KS

---

### Post by felipelavinz on 2008-07-12
Well, this is strange... I'm on Ubuntu Hardy 8.04.1, spanish and running a Windows Fundamentals (which is something like a lightweight XP SP2) guest in VirtualBox 1.6.2

I couldn't get some special characters to work (such as á é í ó...) so I thought I would try to deactivate complex characters support, but it was deactivated... so I activated it and, voila! now á é í... work on the WFLP guest

---

