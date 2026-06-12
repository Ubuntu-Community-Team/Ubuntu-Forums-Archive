---
title: "com0com replacement for ubuntu (virtual serial ports)"
date: 2008-07-06
forum: General Help
---

### Post by kaligus on 2008-07-06
I am developing/maintaining some software for an antique medical device which uses serial ports to communicate with the techs running the show.

On windows I use software called com0com & hub4com to intercept both sides of the conversation and human intervention to segregate the device from the computer later.

What I need now is to have a virtualbox running a custom deploy of windows 2000 talking to that device to be logged in the same manner.

I can run the software perfectly fine and it communicates both directions, I have tried ttysnoop and ttylog but both only seem to catch half of the conversation or worse yet break the communication completely.

Does anyone have any ideas?

Longer notes about some things that would be super nice to have :lolflag: which are not in com0com to start with.

It would be nice if I could set the baud in virtualbox, and have that change logged and propigated as it is when there is no middleman.

If I could have the middleman record all changes to baud, DTR, CTS, etc. without interfering with the process that would be sweet.  

It would be nice to be able to break a signal (drop DTR/CTS/ser-in/ser-out) to simulate the all too often loose cable.

It would be nice if I could log when a new device with a differing baud rate was plugged in to see if my auto-baud system is working correctly, as well as watch that process at the signal level.

It would be really good to have the middleman segregate in versus out automatically so I dont have to tear over the logs one character at a time.

It would be nice if this solution would also butter my morning toast :)

---

### Post by kaligus on 2008-07-12
bump... and...

Since there doesn't seem to be a virtual serial port app, any recommendations as to where to start looking to write one?

The device drivers I have written previously are all for 8 antiques and embedded applications, but I am willing to give it a shot.

Google comes up with an annoyingly large number of possibilities, thus the desire for recommendations :)

THANKS !

---

### Post by ollet on 2008-11-06
Does anyone know a solution to this problem?

I posted a thread on the same subject yesterday. ([http://ubuntuforums.org/showthread.php?t=972187]("http://ubuntuforums.org/showthread.php?t=972187"))

Is it possible to somehow use two ptyp/tty pairs?

---

### Post by moberhuber on 2008-12-01
You may want to look at Tibbo VSPDL, [http://www.tibbo.com/vspdl.php](http://www.tibbo.com/vspdl.php) -- seems pretty new, and is available for download right now (beta version). Not sure about the license at this point, or whether they want to make it available commercially only in the future.

There are other commercial alternatives, such as [http://www.ttyredirector.com/](http://www.ttyredirector.com/).

Remserial ([http://lpccomp.bc.ca/remserial/](http://lpccomp.bc.ca/remserial/), GPL) may also do what you want, using Unix PTY's. It transmits the serial data in "raw form" to a network socket; STTY-like setup of terminal parameters must be done when creating the port, changing them later like described in RFC 2217 does not seem to be supported. You should be able to run two remserial instances to create a virtual nullmodem like com0com, except that you'll need to set up port speed etc in advance.

Socat ([http://www.dest-unreach.org/socat/](http://www.dest-unreach.org/socat/), also GPL) is like an extended variant of Remserial with many many more options, including a "PTY" method for redirecting the PTY to something else, which can be another instance of Socat. For Unit tets, socat is likely nicer than remserial because you can directly cat files into the PTY. See the PTY section on the manpage [http://www.dest-unreach.org/socat/doc/socat.html#EXAMPLE_ADDRESS_PTY](http://www.dest-unreach.org/socat/doc/socat.html#EXAMPLE_ADDRESS_PTY). A patch exists under "contrib" to provide RFC2217 support for negotiating serial line settings: [http://www.dest-unreach.org/socat/contrib/socat-rfc2217.html](http://www.dest-unreach.org/socat/contrib/socat-rfc2217.html)

---

