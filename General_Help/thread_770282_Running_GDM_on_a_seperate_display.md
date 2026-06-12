---
title: "Running GDM on a seperate display"
date: 2008-04-27
forum: General Help
---

### Post by mrmonday on 2008-04-27
Hey all,

I've recently done a clean install of hardy on my desktop, and would like to set up VNC with a GDM login window, rather than the current desktop. I've looked at [https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c](https://help.ubuntu.com/community/VNC#head-a2254fc1fe04cd6bacc05b7277c2b76a65ccb36c), but the instructions seem to be for feisty/gutsy, and don't work on hardy. I've also tried the tightvnc methods, but that doesn't start GDM, that just starts a new X session which I can VNC to. I guess all I need is the command to launch gdm to put in my ~/.vnc/xstartup...

So far I've tried the following, but to no success:

```

gdm #does nothing
/usr/lib/gdm/gdm[greeter|login] #both give a message about the wrong version of the GDM daemon running
/etc/init.d/gdm [start|restart] #does nothing 

```

Any ideas?

Note for admins/mods if they read this: I was unable to add tags to this post, as it complains that they should be at least 3 characters... X, VNC and GDM are all <= 3 ;)

---

### Post by mrmonday on 2008-04-30
*bump*

An update: What I actually want to do is have VNC run at start up so I can VNC in and have control of :0 (the default X desktop)...

So far the closest I've managed to do is ssh in, start a VNC server on :1, then use that to start Xnest on :2, but viewed on :1... Not the nicest solution (they keyboard map gets messed up in Xnest too)... I also tried tunneling X over ssh, but that was horribly slow.

Once again - any ideas?

---

