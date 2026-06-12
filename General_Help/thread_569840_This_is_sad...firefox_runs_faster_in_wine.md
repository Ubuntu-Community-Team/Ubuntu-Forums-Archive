---
title: "This is sad...firefox runs faster in wine"
date: 2007-10-07
forum: General Help
---

### Post by peabody on 2007-10-07
I just tried the windows version of Firefox in wine and I can say without a doubt that it runs faster than Ubuntu's native Firefox.

Now before anyone gets their panties in a bind, I'll state for the record that firefox is quite usable in Feisty.  Until I tried out windows firefox, I was happy with it.  But now that I've observed what I have, I'm dying to answer the folllowing...How on earth is it possible that firefox would run faster via a complex software compatibility layer to another operating system than through the native libraries?  That should be some kind of red flag to the people developing the Ubuntu build of firefox.  Something is fishy...there's just no good excuse for a non-native binary with, in theory, exponentially more function call overhead to run faster than the native build.

---

### Post by kerry_s on 2007-10-07
ubuntu does not develop firefox. firefox is built for windows. linux is just supported.

---

### Post by peabody on 2007-10-07
> **kerry_s said:**
> ubuntu does not develop firefox. firefox is built for windows. linux is just supported.

That's not true, Firefox has had a linux version since day one and it's largely been Linux users that have pushed firefox as an alternative to IE for Windows users.  Ubuntu has access to the complete source code.  I've heard plenty of talk in threads here ([http://ubuntuforums.org/showthread.php?t=494942&highlight=firefox+faster+wine](http://ubuntuforums.org/showthread.php?t=494942&highlight=firefox+faster+wine)) about speed issues regarding firefox, including suggestions on how to speed it up by tweaking the build process.

It wouldn't surprise me that certain things would be faster in Wine firefox (flash, no control over that, it's closed source).  However, simple things like smoothness and speed of scrolling seem like they should be well within the developers control.

---

### Post by Meomix on 2007-10-07
really? i found running programs under wine a nightmare to control, looks fishy that firefox is faster on a almost dead wagon though.

---

### Post by kerry_s on 2007-10-07
i'm trying it now under wine and it is not faster.

---

### Post by AliTabuger7 on 2007-10-07
What kind of hardware are you using? Judging by what I've seen of wine, the GUI lacks resource heavy elements like rounded corners and such. Furthermore, it is possible that whatever "scrolling" quality differences that you are seeing are because of the setting "smooth scrolling".

Still, it wouldn't surprise me. The windows version would undoubtedly get more development attention.

---

### Post by greymongrey on 2007-10-07
Have you ever tried running the version of Firefox that doesn't need installing? I run a SeaMonkey version, and it is very fast.

---

### Post by peabody on 2007-10-07
> **Meomix said:**
> really? i found running programs under wine a nightmare to control, looks fishy that firefox is faster on a almost dead wagon though.

I've had the opposite experience actually.  It's AMAZING to me what Wine is able to run these days.  I remember the 0.3 days when wine barely ran anything.  Now  I keep throwing things at it and it just keeps on running them.

---

### Post by por100pre1 on 2007-10-07
Any extensions, many themes? :-k 

Try a new profile:

```
firefox -ProfileManager
```

I'm not denying Firefox is slow... :(

---

### Post by kerry_s on 2007-10-07
> **kerry_s said:**
> i'm trying it now under wine and it is not faster.

it's actually not that bad when you do the usual tweaks. i really only notice the java script for site menus being a little slow. oh, and trying to put attachments.

---

### Post by Meomix on 2007-10-07
> **peabody said:**
> I've had the opposite experience actually.  It's AMAZING to me what Wine is able to run these days.  I remember the 0.3 days when wine barely ran anything.  Now  I keep throwing things at it and it just keeps on running them.

really, i could barely get a media player to run under wine
i needed to install a special  "hacked directx" for the dam player to work, was horrific trying to find the wine plugin [-(

---

### Post by kerry_s on 2007-10-07
> **Meomix said:**
> really, i could barely get a media player to run under wine
i needed to install a special  "hacked directx" for the dam player to work, was horrific trying to find the wine plugin [-(

damn, it's still crap just segfaulted on me, wouldn't work after that, so i just removed it, not worth trying again. :mad:

---

### Post by jrharvey on 2007-11-30
Firefox for wine is DEFINATELY faster than the native ubuntu. I am not sure how this can be but I noticed it a while back. It is very weird but I wonder if acts the same way that it does in windows. Can it get viruses like in windows?

---

### Post by santiagoward2000 on 2007-11-30
> **greymongrey said:**
> Have you ever tried running the version of Firefox that doesn't need installing? I run a SeaMonkey version, and it is very fast.

Hey! What do you mean by "doesn't need installing"? How does it work? Where can I try it?

---

### Post by urosh2 on 2008-01-28
> **jrharvey said:**
> Firefox for wine is DEFINATELY faster than the native ubuntu. I am not sure how this can be but I noticed it a while back. It is very weird but I wonder if acts the same way that it does in windows. Can it get viruses like in windows?

I agree with you. It is faster in wine and it's a shame. Maybe windows platform is better than Linux.

---

