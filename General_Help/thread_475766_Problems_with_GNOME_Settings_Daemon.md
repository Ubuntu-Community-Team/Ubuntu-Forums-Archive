---
title: "Problems with GNOME Settings Daemon"
date: 2007-06-16
forum: General Help
---

### Post by GhentK on 2007-06-16
At startup, Ubuntu tries to load GNOME Settings Daemon, eventually gives up and tells me that the daemon didn't reply. Now, I'm not sure what the daemon is, but it definitely doesn't show up in my package manager; only the development package does.

I would imagine that it's a conflict between different packages (I installed some in a session yesterday, and in the next new session, the error occurred), but how do I find this conflict or reinstall the package?

Thanks in advance. :)

---

### Post by dbbolton on 2007-06-16
> **GhentK said:**
> At startup, Ubuntu tries to load GNOME Settings Daemon, eventually gives up and tells me that the daemon didn't reply. Now, I'm not sure what the daemon is, but it definitely doesn't show up in my package manager; only the development package does.

I would imagine that it's a conflict between different packages (I installed some in a session yesterday, and in the next new session, the error occurred), but how do I find this conflict or reinstall the package?

Thanks in advance. :)
could you post the contents of ~/.xsession-errors ?

---

### Post by GhentK on 2007-06-16
Sure. Had to zip it up to upload it though.

---

### Post by dbbolton on 2007-06-16
> **GhentK said:**
> Sure. Had to zip it up to upload it though.
hmm, i looked over it, and didn't see anything related to your problem.

could you go to a terminal and type ```
gnome-settings-daemon
``` and post the output here?

---

### Post by GhentK on 2007-06-17
"You can only run one xsettings manager at a time; exiting"

The error message at startup is: > There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

---

### Post by dbbolton on 2007-06-17
> **GhentK said:**
> "You can only run one xsettings manager at a time; exiting"

The error message at startup is:
ok, i'm going to agree with your original post and say that you have a package issue. two questions:

1. do you remember which packages you installed just before the error occurred?
2. have you checked for broken packages?

---

### Post by GhentK on 2007-06-17
1. The following are the only ones, I think: libdvdcss2, totem-xine, gxine, libxine-extracodecs,  gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, and w32codecs.

2. Yes, none.

---

### Post by dbbolton on 2007-06-17
> **GhentK said:**
> 1. The following are the only ones, I think: libdvdcss2, totem-xine, gxine, libxine-extracodecs,  gstreamer0.10-ffmpeg, gstreamer0.10-plugins-bad, gstreamer0.10-plugins-bad-multiverse, gstreamer0.10-plugins-ugly, gstreamer0.10-plugins-ugly-multiverse, and w32codecs.

2. Yes, none.
ok, try this

```
sudo aptitude reinstall gnome-control-center
```

---

### Post by GhentK on 2007-06-18
That worked like a charm. Thanks a lot for helping me out. :D

---

### Post by dbbolton on 2007-06-18
> **GhentK said:**
> That worked like a charm. Thanks a lot for helping me out. :D
no problem

---

### Post by GhentK on 2007-06-19
Okay, I found the conflict.

Last night, I wasn't able to watch DVDs (the menu didn't work properly), so I reinstalled "libdvdnav4", and it worked. When I just booted my computer, the GNOME settings daemon couldn't start again, so it must be those two packages conflicting.

Has anyone had this problem?

---

### Post by dbbolton on 2007-06-19
> **GhentK said:**
> Okay, I found the conflict.

Last night, I wasn't able to watch DVDs (the menu didn't work properly), so I reinstalled "libdvdnav4", and it worked. When I just booted my computer, the GNOME settings daemon couldn't start again, so it must be those two packages conflicting.

Has anyone had this problem?
i've never heard of anything quite like this. since you've narrowed it down to a conflict between two official ubuntu packages, you should file a ticket on [http://launchpad.net](http://launchpad.net)

---

