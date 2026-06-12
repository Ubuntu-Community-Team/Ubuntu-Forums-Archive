---
title: "ctrl-alt-F* gives blank screen"
date: 2013-04-07
forum: General Help
---

### Post by georgecolin on 2013-04-07
I have just installed Nvidia GTX 680, and am using Nvidia Driver Version 304.84.  
I  am running kubuntu 12.04.

THE PROBLEM:    
Ctrl-Alt-F1 F2, ... now give a blank screen.  Ctrl-Alt-F7 restores my desktop environment ok.

RELATED COMMENTS:
Previously I was using an ATI card, and Ctrl-Alt-F* worked ok (though it is a few weeks since I last used these keys).

I intend running CUDA on the GPU, so I (believe that I) need to use nvidia graphics drivers rather than ubuntu's own.

I have seen this:
[http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/page2.html](http://www.linuxquestions.org/questions/linux-general-1/ctrl-alt-f1-%3D-black-blank-screen-385376/page2.html)
thread, but the suggested changes to /etc/default/grub do not work for me.
Other threads I have found are a few years old now, so I am asking here, hoping for up-to-date info for 12.xx, thanks.

---

### Post by georgecolin on 2013-04-07
Ok, I fixed this.

In additional drivers, I selected:
     'NVIDIA accelerated graphics driver (post-release updates) (version current updates)  
instead of:
     '(recommended version)'.

---

### Post by bogan on 2013-04-07
Hi!, **georg**e,

Good to hear you fixed it.

Please mark Thread as Solved.

[Go to edit thread>Advanced, edit the Prefix [ubuntu] to [Solved], Save changes.]

Chao!, **bogan**.

---

