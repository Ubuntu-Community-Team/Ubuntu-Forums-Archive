---
title: "my new kernel hangs during boot-up."
date: 2007-10-24
forum: General Help
---

### Post by Yarbo on 2007-10-24
I just compiled a new kernel using the directions [here]("http://ubuntuforums.org/showthread.php?t=311158").

I used the full kernel linux-2.6.23.1 available at kernel.org.

I was able to compile the kernel and install it, and everything seemed to be going ok while booting.  I got to a screen displaying a dialog box which said that Ubuntu was running in low-graphics mode. I figured this was okay, since I've not yet installed any drivers.

When I click OK on this dialog, the X cursor stays on the screen for a few moments, and it moves around as I move the mouse. After about 30 seconds or so the cursor disappears and I am left with a black screen. Not even a flashing cursor.


Does anyone have any ideas what might be causing this, and what I can do to troubleshoot?  I'm very new to Linux, and a lot of this still beyond me, so any help would be appreciated.

---

### Post by Yarbo on 2007-10-25
If anyone is interested as to how I was able to fix this, then read on.  Keep in mind that I am a complete newbie to Linux, and was using a lot of guides... well, google is your friend.

As it turns out, I was getting a black screen because of an improperly configured xorg.conf file.

So I ran  ```
dpkg-reconfigure xserver-xorg
```

This allowed me to go and reset the /etc/X11/xorg./conf, and I was then able to boot in and configure my video drivers!  Now my new kernel works great, and much faster too.

---

