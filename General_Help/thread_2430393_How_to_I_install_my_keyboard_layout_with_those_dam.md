---
title: "How to I install my keyboard layout with those damn snaps."
date: 2019-10-31
forum: General Help
---

### Post by Ferule_Bezel on 2019-10-31
I have a keyboard layout that includes some things that are common in novels, long dash, ellipsis and a few others.  I've always put it in /usr/share/X11/xkb/symbols and modified /usr/share/X11/xkb/rules/evdev.xml to include it.  With 18.04 the whole hierarchy is duplicated in the /snap/core/current directory and uneditable and for some reason.  I'm told it is a security feature.    So, how can I add my layout?  Or am I just going to have to give up on Ubuntu since they insist on breaking things with this snap nonsense,audacity, Inkscape, Nethack and now xkb?

---

### Post by HermanAB on 2019-11-01
Hmm, I have also found that Ubuntu is now a Maintainer Oriented distribution.  The actual user comes a distant second.  The last Ubuntu install, I had to spend a lot of time to disable snapd, cloud and several other services that I don't use, to speed it up and make it more user friendly.  If snapd is disabled, then the system will ignore snaps and you can then carry on as with all other Linux versions.

The result is that I now have only one machine that still runs Ubuntu - and I seldom use it.  Looking around me, four machines run OpenBSD, one Fedora, one Ubuntu (turned off) and one MacBook (This one).

So, coming back to your question about snapd: I can only say that I feel your pain, don't use it and can't help you...

If you are wondering why I mainly use a Macbook - the screen is the best.  On my Macbook Pro, I can actually see what I'm doing, which is rather important - the actual OS doesn't matter, it is UNIX, same as all the rest, it works well enough and stays out of the way.

---

### Post by vanadium on 2019-11-01
Indeed snaps introduce all kinds of complications. In 18.04, it still is quite easy to stay away from snap. Remove snapd. This will remove a few system utilities like "Character" and "System monitor", but you can simply install these back from the regular packages.

Life will become a bit more difficult in more recent versions, though still not impossible. For example, in 19.10, Chromium browser is only available as a snap. It is likely that snap will become less inevitable in the future. If that is a concern, indeed you may then need to move on to a different distribution.

---

### Post by dewdrop_world on 2019-11-02
> It is likely that snap will become less inevitable in the future. If  that is a concern, indeed you may then need to move on to a different  distribution.

If anybody from Ubuntu is reading: I use a custom keyboard layout and if it ever becomes impossible to use that layout with Ubuntu, then I will drop Ubuntu like a hot rock.

hjh

---

