---
title: "AbiWord Won't Launch in Gutsy Gibbon"
date: 2007-10-27
forum: General Help
---

### Post by NotPhil on 2007-10-27
AbiWord won't launch. When I tried to start it from the terminal to see what was happening, it told me,
```
Aborted (core dumped)
```
I've tried reinstalling it, but it still does the same thing. Any ideas?

---

### Post by pieisgood4589 on 2007-10-27
OK, AbiWord is still not compatible with 7.10, so the best thing to do is to use OpenOffice, which is loads better then AbiWord. (Why do you use it?) Uninstall AbiWord, but install it again once it is compatible with 7.10. Good luck! :popcorn::KS:KS:KS:KS:KS:popcorn:

---

### Post by Maestro23 on 2007-10-27
> **pieisgood4589 said:**
> OK, AbiWord is still not compatible with 7.10, so the best thing to do is to use OpenOffice, which is loads better then AbiWord. (Why do you use it?) Uninstall AbiWord, but install it again once it is compatible with 7.10. Good luck! :popcorn::KS:KS:KS:KS:KS:popcorn:

Gutsy 64-bit here:  AbiWord works fine.

---

### Post by NotPhil on 2007-10-27
> **pieisgood4589 said:**
> OK, AbiWord is still not compatible with 7.10:
Has this been reported before? I can't find any reference to it in the forums, and [Bugzilla]("http://bugzilla.abisource.com/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=AbiWord&content=aborted+ubuntu") doesn't mention it either.

I'm using the 32-bit version of Ubuntu 7.10, which I just installed through the Update Manager.

---

### Post by Maestro23 on 2007-10-27
> **NotPhil said:**
> Has this been reported before? I can't find any reference to it in the forums, and [Bugzilla]("http://bugzilla.abisource.com/buglist.cgi?query_format=specific&order=relevance+desc&bug_status=__open__&product=AbiWord&content=aborted+ubuntu") doesn't mention it either.

I'm using the 32-bit version of Ubuntu 7.10, which I just installed through the Update Manager.

Try to uninstall using synaptic, then re-install.

---

### Post by Steveway on 2007-10-27
> **pieisgood4589 said:**
> OK, AbiWord is still not compatible with 7.10, so the best thing to do is to use OpenOffice, which is loads better then AbiWord. (Why do you use it?) Uninstall AbiWord, but install it again once it is compatible with 7.10. Good luck! :popcorn::KS:KS:KS:KS:KS:popcorn:

What the heck are you talking about? Abiword works great here on Ubuntu Gutsy 7.10, it loads up in about a second.
It's perfect if you just want to write a document.
And no OOo is not "better", it's a suite wich is good but it's overkill if you don't need a fullblown suite.

---

### Post by NotPhil on 2007-10-27
> **Maestro23 said:**
> Try to uninstall using synaptic, then re-install.
I tried the complete removal option and then installed it again, but the same thing still happens. Sometimes I see a window appear and dissapear, and sometimes I don't, but it won't launch. There's nothing in /var/crash for AbiWord either.

---

### Post by NotPhil on 2007-10-28
Okay, I've tried uninstalling the version of AbiWord in the repositories and installing it through its autopackage from the AbiWord home page. This is what it told me,
```
Error: Package 'Unicode character map' was found but was 
of the wrong version and the correct version could not be located.

[IV 4.0 for @gnome.org/libgucharmap]

Error: Unable to prepare package AbiWord Word Processor.
```
libgucharmap6 is installed in Gutsy Gibbon. I tried adding libgucharmap-dev, but it didn't help. (libgucharmap4 isn't available in the repositories.) I can find references to this problem on the [Web,]("http://www.google.com/search?q=abiword+libgucharmap") but I didn't see any workarounds.

Any suggestions?

---

