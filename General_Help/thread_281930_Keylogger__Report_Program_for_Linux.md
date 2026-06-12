---
title: "Keylogger / Report Program for Linux?"
date: 2006-10-21
forum: General Help
---

### Post by EagleX on 2006-10-21
I'm wondering if there is a program that will work on Ubuntu that logs keystrokes, and reports on user activity.

I recently switched over to Ubuntu from Windows, and I'm very impressed so far. However, my parents would like to be able to see what I am doing online. I respect this, and so have been looking for something that works on Linux.

They have been using eBlaster and Spector Pro, but I haven't found anything of that nature of Linux. Does such a thing even exist? I've found software like DansGuardian, but that's not exactly what I'm looking for.

If you know of something that fits this profile, please post a link to where I can download it, and instructions for installing it!

Thanks! :)

---

### Post by cmost on 2006-10-21
It's great that you respect your parents' wishes to monitor your online activity.  Considering that it's extremely easy to circumvent most key logging systems, you are to be commended for cooperating.

There is an overall lack of sophisticated key logging / report generating systems similar to Spectre Pro, Net Nanny, etc., that monitor e-mail, chat software, programs run, and generate screenshots.  This is likely due to the fact that Linux is not yet in widespread use, or, software venders are simply acting as though it isn't a viable alternative to the Borg (a.k.a. Microsoft.) Nevertheless, there ARE rudimentary key loggers available for Linux.  Here's what I could find:

LKL is a userspace keylogger that runs under Linux on the x86 architechture. LKL sniffs and logs everything that passes through the hardware keyboard port (0x60). It translates keycodes to ASCII with a keymap file.
Link:
[http://sourceforge.net/projects/lkl/](http://sourceforge.net/projects/lkl/)

A hardware keylogger such as KeyGhost Pro might also be a satisfactory solution.  These are nice because they are operating system independent and will work equally well under Windows or Linux.  Find out more about it here:

Link:
[http://www.keyghost.com/kgpro.htm](http://www.keyghost.com/kgpro.htm)

Good luck!  Here's hoping you'll get to keep Ubuntu; it rocks!

---

### Post by EagleX on 2006-10-21
> **cmost said:**
> It's great that you respect your parents' wishes to monitor your online activity.  Considering that it's extremely easy to circumvent most key logging systems, you are to be commended for cooperating.

There is an overall lack of sophisticated key logging / report generating systems similar to Spectre Pro, Net Nanny, etc., that monitor e-mail, chat software, programs run, and generate screenshots.  This is likely due to the fact that Linux is not yet in widespread use, or, software venders are simply acting as though it isn't a viable alternative to the Borg (a.k.a. Microsoft.) Nevertheless, there ARE rudimentary key loggers available for Linux.  Here's what I could find:

LKL is a userspace keylogger that runs under Linux on the x86 architechture. LKL sniffs and logs everything that passes through the hardware keyboard port (0x60). It translates keycodes to ASCII with a keymap file.
Link:
[http://sourceforge.net/projects/lkl/](http://sourceforge.net/projects/lkl/)

A hardware keylogger such as KeyGhost Pro might also be a satisfactory solution.  These are nice because they are operating system independent and will work equally well under Windows or Linux.  Find out more about it here:

Link:
[http://www.keyghost.com/kgpro.htm](http://www.keyghost.com/kgpro.htm)

Good luck!  Here's hoping you'll get to keep Ubuntu; it rocks!

Thank you very much! The LKL looks closer to what I need.

This might not be possible, but could Ubuntu run a Windows based program (eBlaster, Spector Pro, Net Nanny, etc.) through Wine? I've successfully managed to run a number of Windows programs with Wine (Dreamweaver, IE, to name a few). I know Wine has it's limitations, but would something like this be possible?

---

### Post by aysiu on 2006-10-21
You can try this, too:
[http://pykeylogger.sourceforge.net/wiki/index.php/Main_Page](http://pykeylogger.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by toocrazy on 2007-05-16
I like the lkl, but it lacks of keymaps files, anyone knows where I can find a portuguese keymap to use with it?

Cumps and Tks

---

### Post by edpl on 2007-07-23
For linux you can buy hardware keylogger (for example [www.keelog.com](www.keelog.com)). I use that one from yesterday and I think this is good solution. You don't need no additional software.

--
sorry for my english ;)

---

