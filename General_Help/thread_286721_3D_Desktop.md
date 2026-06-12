---
title: "3D Desktop??"
date: 2006-10-28
forum: General Help
---

### Post by johann_p on 2006-10-28
I must admit that all those threads discussing how to enable a 3D desktop are quite confusing. From what I understand, Xgl is really a bad choice: I tested the Xgl+Beryl configuration and playing movies slows down to a crawl, 3D acceleration in windows is lost. Not going to do that.

So the alternative seems to be AIXGL, but I do not see how to do this best. It seems it needs tweaking of X config settings etc.

I wish there was a way to simply configure an *additional* session type that would allow to run Beryl/GNOME or Beryl/KDE under AIXGL. Or Compiz/GNOME or Compiz/KDE under AIXGL. But with the option to switch back to a stable non-3D session if necessary.

Would that be possible?

---

### Post by Architeuthis on 2006-10-28
> So the alternative seems to be AIXGL, but I do not see how to do this best. It seems it needs tweaking of X config settings etc.


I dont know much about beryl and compiz and xgl etc. But i know aiglx is included in the xorg version shipped in ubuntu 6.10. I hope this can be of use for you.

---

### Post by bulldog on 2006-10-28
I use Beryl and Emerald with Dapper 6.06,and even it's Alpha,it works fine.

You can set your desired manager by using the Beryl settings manager and switch back to metacity if you want.

Have to say I use a nVidia 6800 Ultra graphics and a Dual Core AMD 4600.

But no problems so far.:D

---

### Post by johann_p on 2006-10-28
I have to admit that this is all a bit too complex for me. I know that AIXGL is "included", but obviously it needs to get *enabled* somehow. 

What I am looking for is a foolproof step by step howto for doing this:
- enable AIXGL just for a session, not for gdm and every session
- run whatever is needed to enable 3D effects or (more important) window-speedup within this session

Maybe I am totally misunderstanding something here, but what I thought was: AIXGL and Xgl are the underlying X-server technologies to make those fancy new effects and window managers possible; Compiz and  Beryl are window managers (enhancements?) that use those technologies.

So what I want is: enable AIXGL for a new session type, e.g. "GNOME-AIXGL" so that I can choose to log in into such a 3D-enhanced session. 

How would one need to go about doing this?

---

### Post by galileon on 2006-10-28
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

this worked for me, but note i installed my nvidia beta driver from nvidia.com, ie by hand

---

