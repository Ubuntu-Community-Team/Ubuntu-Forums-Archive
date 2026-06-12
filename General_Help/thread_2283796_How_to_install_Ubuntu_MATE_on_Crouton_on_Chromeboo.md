---
title: "How to install Ubuntu MATE on Crouton on Chromebook?"
date: 2015-06-24
forum: General Help
---

### Post by cwblanch on 2015-06-24
Hey,

I'm actually really not sure where to post this question in these forums.

But I'm curious about installing something other than Unity Ubuntu in Crouton. I've seen a few "how-to's" about how to put Ubuntu on a Chromebook, but I can't seem to find an option for installing MATE.

Sorry if I've put this in the wrong place, and thanks for the help!

---

### Post by QDR06VV9 on 2015-06-24
> **cwblanch said:**
> Hey,

I'm actually really not sure where to post this question in these forums.

But I'm curious about installing something other than Unity Ubuntu in Crouton. I've seen a few "how-to's" about how to put Ubuntu on a Chromebook, but I can't seem to find an option for installing MATE.

Sorry if I've put this in the wrong place, and thanks for the help!

Why would the install method be different?
Just get the Mate iso( i suggest the 14.04LTS)
And follow the method you were looking at.
Here is a very nice Video to help [https://www.youtube.com/watch?v=d_MuVwJq_XQ&feature=youtu.be](https://www.youtube.com/watch?v=d_MuVwJq_XQ&feature=youtu.be)
Download link and info.[URL="http://distrowatch.com/?newsid=08859"]
[/URL][http://distrowatch.com/?newsid=08859](http://distrowatch.com/?newsid=08859)

---

### Post by cwblanch on 2015-06-24
> **runrickus said:**
> Why would the install method be different?
Just get the Mate iso( i suggest the 14.04LTS)
And follow the method you were looking at.
Here is a very nice Video to help [https://www.youtube.com/watch?v=d_MuVwJq_XQ&feature=youtu.be](https://www.youtube.com/watch?v=d_MuVwJq_XQ&feature=youtu.be)
Download link and info.[URL="http://distrowatch.com/?newsid=08859"]
[/URL][http://distrowatch.com/?newsid=08859](http://distrowatch.com/?newsid=08859)

Thanks for that video. I hadn't run across it for some reason. 
I also didn't realize that GNOME is very similar to MATE visually, which is the part I like. The look Ubuntu had when I started using it.

I did all the steps but after doing all the downloading and installing it won't run.

I run ```

sudo startgnome

```

The screen goes black, as if to start and then goes back to ChromeOS saying
```

Entering /mnt/stateful_partition/crouton/chroots/trusty...

Initializing built-in extension Generic Event Extension
Initializing built-in extension SHAPE
Initializing built-in extension MIT-SHM
Initializing built-in extension XInputExtension
Initializing built-in extension XTEST
Initializing built-in extension BIG-REQUESTS
Initializing built-in extension SYNC
Initializing built-in extension XKEYBOARD
Initializing built-in extension XC-MISC
Initializing built-in extension SECURITY
Initializing built-in extension XINERAMA
Initializing built-in extension XFIXES
Initializing built-in extension RENDER
Initializing built-in extension RANDR
Initializing built-in extension COMPOSITE
Initializing built-in extension DAMAGE
Initializing built-in extension MIT-SCREEN-SAVER
Initializing built-in extension DOUBLE-BUFFER
Initializing built-in extension RECORD
Initializing built-in extension DPMS
Initializing built-in extension Present
Initializing built-in extension DRI3
Initializing built-in extension X-Resource
Initializing built-in extension XVideo
Initializing built-in extension XVideo-MotionCompensation
Initializing built-in extension SELinux
Initializing built-in extension GLX
[dix] Could not init font path element /usr/share/fonts/X11/misc, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
[dix] Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
/usr/share/bin/xinit: Xfree86_VT property unexpectedly has 0 items instead of 1
crouton: version 1-20150620222151~master:89796a99
release: trusty
architecture: armhf
xmethod: xephyr
targets: gnome
host: version 6946.58.0 (Official Build) stable-channel daisy
kernel: Linux localhost 3.8.11 #1 SMP Sat Jun 13 02:36:36 PDT 2015 armv7l armv7l armv7l GNU/Linux
freon: no
Running exit commands...
/usr/bin/xinit: connection to X server lost

waiting for X server to shut down Hangup

Unmounting /mnt/stateful_partition/crouton/chroots/trusty...

```

The only thing I, as kind of a newbie, can identify as an issue is where it says that the "property unexpectedly has 0 items instead of 1" and I have no idea what that means.

---

