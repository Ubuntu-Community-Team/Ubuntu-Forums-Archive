---
title: "VMware + Synergy = really odd effects"
date: 2007-08-31
forum: General Help
---

### Post by destructchaos on 2007-08-31
i'm running VMware on kubuntu feisty, using synergy as a KM switch with the server running on a windoze box and the feisty box in question running as a client.  whenever i run XP inside of VMware, i have two main problems.

1) i loose the shift and control keys, i.e. can not use them.  if i hold shift and try typing, nothing happens.  same thing for crtl.

2) the mouse is really jumpy.  i have to move it slowly to control it and even still it will randomly jump to a place on the screen that is far from where i was sending it.

additionally, when i first load up the VMware server, there is a notification in the status bar that, "You do not have VMware tools installed." despite having installed vmware-tools-kernel-modules.  is there another package i need to install?

thanks for any help you can give.

---

### Post by marx2k on 2007-08-31
you need to install vmware tool inside of windows.. its one of the options from the host dropdown menus.  id tell you but the box im on right now has virtualbox installed... but its one of those drop down menus while you have xp booted in the vmware

---

### Post by destructchaos on 2007-09-01
thanks, that fixed the mouse issue, but not the keyboard.  i still can't use the shift or control keys.  any ideas?

---

### Post by Jazkal on 2007-09-13
I'm also seeing this problem. Anyone else know what the cause/fix is?

---

### Post by bankg3 on 2007-09-18
As am I having this issue .... no one knows how to solve it?

---

### Post by nosatalian on 2007-10-13
I work at VMware (but not on workstation/server) this is a known issue.  I think the gist of it is that VMware gets keyboard input at a lower level in the OS than synergy is injecting them.  I'll ask around and check internally to see if there is a workaround/fix coming.

---

### Post by tofagerl on 2007-11-11
I am running VMware Player on Vista, with Synergy server. With VMWare installed my clients can't connect to the Synergy server. I have traced this problem to the network drivers in VMWare, as they can't connect even with VMWare not running. To fix it, I have had to uninstall VMWare, as Synergy is far more important to me than using VMWare. 

The clients as well as the VMWare image I was trying to run are all running Ubuntu btw, which is why I allowed myself to post in this forum ;p

---

### Post by klight on 2007-12-03
I've been facing the issue with synergy not passing shift or control to my VMWare client running on Gutsy.

My solution has been to switch to win2vnc on the windows "server" (in Synergy terms) and run x11vnc on the Ubuntu client.  So far this works, however the mouse and keys are a bit laggy.

---

### Post by krunge on 2007-12-03
> **klight said:**
> 
My solution has been to switch to win2vnc on the windows "server" (in Synergy terms) and run x11vnc on the Ubuntu client.  So far this works, however the mouse and keys are a bit laggy.

Have you used the -nofb option?
```
x11vnc -nofb
```

---

### Post by klight on 2007-12-05
That seems to really help.  I've also added the -noxdamge to stop the warnings about beryl/compiz.

```
x11vnc -nofb -noxdamage
```

---

### Post by sam_hatoum on 2008-04-25
I got a workaround for this...

I have:

ubuntu on my laptop with a second monitor
ubuntu on my office machine with two monitors
vmware on office machine running windows

I've installed synergy on laptop, office ubuntu, and vmware windows

and now from the laptop I can access all the screens and I can use the shift and ctrl keys on the vmware instance, since it's windows doing it, not vmware. The one problem however, is that since vmware tools are installed, it means the mouse does not appear on windows, when syergy operates it. So I've enabled mouse trails and set it to a minimum, which forces windows to render the pointer.

does the job

---

