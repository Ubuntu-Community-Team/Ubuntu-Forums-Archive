---
title: "Trouble with Compiling/Installing Source"
date: 2007-11-13
forum: General Help
---

### Post by thegreatmuka on 2007-11-13
I have always had difficulty compiling, building, and installing source. I started with Linux a few months ago on Debian, then switched to Kubuntu feisty, and have recently upgraded to gutsy. I've never compiled the kernel myself, but I don't think this necessarily should inhibit me from using source programs.

In specific, I can recall two issues with pthreads, when trying to compile/install gyachi and recently with linuxdc++. I've tried to get help at the gyachi forums, but I could never track down the problem. That was before the upgrade (gyachi 1.0 has a gutsy .deb package, so I didn't need to compile myself). My LinuxDC++ randomly exits after use for a minute or two (doesn't even give me a crash dialog), so I thought I'd try compiling and installing the source code to see if I got the same thing.

I followed the instructions here ([http://ubuntuforums.org/showthread.php?t=193984](http://ubuntuforums.org/showthread.php?t=193984)) and got up to
```
scons release=1 PREFIX=/usr/local
```at which point it gives me:
```
client/CriticalSection.h:100: error: no matching function for call to &#8216;pthread_mutex_t::pthread_mutex_t(NULL)&#8217;
/usr/include/bits/pthreadtypes.h:73: note: candidates are: pthread_mutex_t::pthread_mutex_t()
/usr/include/bits/pthreadtypes.h:73: note:                 pthread_mutex_t::pthread_mutex_t(const pthread_mutex_t&)
scons: *** [build/client/AdcCommand.o] Error 1
scons: building terminated because of errors.
```

I'm at a loss for what to do. I have build-essential installed, I have g++, I can't pinpoint any other things to try.

I upgraded from feisty rather than doing a clean install and I'd really prefer to not have to reinstall from scratch, especially since that didn't seem to help when I came from Debian (it was the reason I installed Ubuntu in the first place). I'm on a Dell Dimension E310 (shush :( ) which *did not* come with Ubuntu. Used GNOME with Debian, am using KDE now. If there's any other relevant information that is needed, I'd be glad to give it.

---

### Post by geraldm on 2007-11-13
The error is in a header file, where it was expected to use a prototype that was not defined
when the compiler needed it to be defined.  Just locate where the definition is, and get 
it included.  
Scons makes it easier by suggesting /usr/include/bits/pthreadtypes.h
When you look into that file you find these lines:
#if !defined _BITS_TYPES_H && !defined _PTHREAD_H
# error "Never include <bits/pthreadtypes.h> directly; use <sys/types.h> instead."
#endif

So, try including the header sys/types.h prior to where the error is.
And, when successful, send the package maintainer a patch and/or note about the trouble.

Gerald

---

### Post by thegreatmuka on 2007-11-14
How exactly do I go about doing that?

Maybe this should be moved...

---

### Post by thegreatmuka on 2007-11-16
I don't really like just bumping, but I'm still kind of confused as to where to go from here.

---

