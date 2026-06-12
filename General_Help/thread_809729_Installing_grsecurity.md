---
title: "Installing grsecurity"
date: 2008-05-27
forum: General Help
---

### Post by ShinHadoken on 2008-05-27
I'm running hardy, and I need to know how to install the grsecurity2 patch. Also, if I install this, will I need SElinux? If so, how do I install that?
 
Thanks,
 
SH

---

### Post by ShinHadoken on 2008-05-27
bump

---

### Post by ShinHadoken on 2008-05-28
bump

---

### Post by ShinHadoken on 2008-05-28
please help me!!!

---

### Post by HalPomeranz on 2008-05-28
What functionality are you looking for by installing grsecurity?  The standard Ubuntu installation with AppArmor gives you a lot of what grsecurity can do for you...

---

### Post by ShinHadoken on 2008-05-28
Got this from the "[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421")" sticky from this forum:

> Hardened kernels are modifications to the Linux kernel that add additional security measures. This could include:

[LIST=1]
[*]The randomization of ports, memory addresses, process ID's, and other information that is typically predictable. This can thwart off many types of common attacks.
[*]Identify and prevent buffer overflow attacks from resulting in compromise by killing compromised processes (PaX bundled with grsecurity, or Redhat's Exec-Shield combined with prelink randomization). Edgy and higher contain GCC stack protection enforced in most applications, but is unable to respond to several kinds of attacks that a kernel-layer enforcer could. Likewise, PaX and friends have weakness that GCC stack protection helps cover, so the two work great as a duo.
[*]Hiding information that Linux usually allows everyone to see, including all running processes on the system, load averages, CPU info, IP addresses, etc. Obscuring this information can help keep attackers "in the dark" so to speak.
[*]More aggressive enforcement of buffer overflow protection than what Ubuntu's standard gcc stack protector can do.
[*]Adding additional restrictions on the capabilities of regular users that prevent channels of attack.
[*]Additional permissions systems that allow finer-grained tuning of various aspects of Linux.
[/LIST]

These techniques combined have been shown to be very effective in the real world in guarding against unknown attacks. For example, many administrators of hardened kernel servers either report or even prove that their hardened systems were invulnerable to newly discovered security holes, or that the severity of a breach was significantly reduced.

The most common hardened kernel patch is called "grsecurity2" ([http://grsecurity.org/](http://grsecurity.org/)), which does everything on this list.

If Ubuntu + AppArmor gives me this, then I guess I'll go that route. But, how do I configure it? Also, I've heard that Hardy has support for SElinux. Is this the same/better than AppArmor?

---

### Post by ShinHadoken on 2008-05-28
*sigh* hello? anyone there?

---

### Post by HalPomeranz on 2008-05-29
> **ShinHadoken said:**
> *sigh* hello? anyone there?

My friend, you should remember that people who post to these forums are doing so out of kindness and may have other things going on in their lives.  This kind of posting does not motivate people to help you very much.

The main thing that grsecurity has going for it is the PaX kernel-based stack protection implementation, which can help protect against many kinds of memory overflow attacks.  However, if you happen to be using a 64bit kernel you get kernel-based stack protection for free.  It's also possible to enable kernel-based stack protection in 32bit kernels without grsecurity on some 32bit processors (see [http://en.wikipedia.org/wiki/Nx_bit#Linux](http://en.wikipedia.org/wiki/Nx_bit#Linux)), although I don't know if the stock Ubuntu kernel has this enabled by default (probably not).

Application privilege control is was AppArmor gives you, so you don't need grsecurity for that.  The other stuff (memory address randomization, PID randomization, "hiding" process info, etc) is at best a second-order security improvement and not nearly as important, IMHO.

> If Ubuntu + AppArmor gives me this, then I guess I'll go that route. But, how do I configure it? Also, I've heard that Hardy has support for SElinux. Is this the same/better than AppArmor?

I believe others answered your SELinux vs. AppArmor question in another thread ([http://ubuntuforums.org/showthread.php?t=809167](http://ubuntuforums.org/showthread.php?t=809167)), so I won't belabor the point here.  Information on how to configure and use AppArmor is included in the AppArmor FAQ ([http://developer.novell.com/wiki/index.php/Apparmor_FAQ](http://developer.novell.com/wiki/index.php/Apparmor_FAQ)).  This document also includes more commentary on the AppArmor vs. SELinux debate.

Btw, if you still decide you want to go with grsecurity, you'll want to read the documentation at [http://www.grsecurity.net/](http://www.grsecurity.net/)

---

### Post by ShinHadoken on 2008-05-29
> My friend, you should remember that people who post to these forums are doing so out of kindness and may have other things going on in their lives. This kind of posting does not motivate people to help you very much.

 
Sorry, I didn't mean to sound rude, I just know how easily things can get lost in the General Help forum, and I was tired of saying bump.
 
Thanks for the info, I'll read it over and make my decision from there.
 
Thanks!!
 
SH

---

