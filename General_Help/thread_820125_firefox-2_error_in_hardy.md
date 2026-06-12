---
title: "firefox-2 error in hardy"
date: 2008-06-06
forum: General Help
---

### Post by crispinb on 2008-06-06
I want to use firefox-2 sometimes, as there's no google gears for ff3 yet. But when I run it (either the hardy package or the tgz downloaded from mozilla), I get the error:

```
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 2037 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Anyone know why?

---

### Post by crispinb on 2008-06-06
As my Hardy installation is pretty stock, I assume this must be a bug with the firefox-2 package. 

Does anyone know where I should report this?

---

### Post by crispinb on 2008-06-07
Am I the only person still using firefox-2?

---

### Post by salvador_luna on 2008-06-07
Firefox 2 is running fine on my laptop.

I used this guide:

[http://ubuntuforums.org/showthread.php?t=759504](http://ubuntuforums.org/showthread.php?t=759504)

Hope it helps!

---

### Post by Bari on 2008-06-07
I have had no problem with FF2 I used synaptic to uninstall FF3 and install FF2 which it did without a hitch and keeping all the bookmarks and preferences.  Perhaps you should try to uninstall FF2 completely and let synaptic fetch a new download and install it.

---

### Post by crispinb on 2008-06-07
> **salvador_luna said:**
> Firefox 2 is running fine on my laptop.

I used this guide:

[http://ubuntuforums.org/showthread.php?t=759504](http://ubuntuforums.org/showthread.php?t=759504)

Hope it helps!

Ah, but I don't want to remove FF3, which I do use most of the time. I just want FF2 for some specific things (like offline use with google docs).

---

### Post by crispinb on 2008-06-07
> **Bari said:**
> I have had no problem with FF2 I used synaptic to uninstall FF3 and install FF2 which it did without a hitch and keeping all the bookmarks and preferences.  Perhaps you should try to uninstall FF2 completely and let synaptic fetch a new download and install it.


That's odd. I've un- and re-installed the FF2 package a couple of times. I've also used the FF2 tgz straight from mozilla's site. All cause the above problem for me. An interaction with another app, perhaps?

Does anyone know what the error in the OP means, and why FF2 might be causing it?

---

### Post by crispinb on 2008-06-07
Here's another clue: if I turn compiz off, FF2 works.

I'd rather keep compiz on, of couse. Anyone know of any incompatabilities between compiz and FF2?

---

### Post by crispinb on 2008-06-07
Well, randomly fixed rather than exactly solved.

I turned off compiz, ran FF2, which was OK. Then I turned compiz back on whilst FF2 was running, and to my surprise the latter kept going. Now the problem seems to have gone away altogether.

I'd still rather know what's going on, but for now at least this is no longer a problem.

---

