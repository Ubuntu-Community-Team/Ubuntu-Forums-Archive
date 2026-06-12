---
title: "How can I manually get an unsupported scanner to work?"
date: 2006-09-12
forum: General Help
---

### Post by Roasted on 2006-09-12
I'm told there's a way. I have an all-in-one Epson Stylux CX4800, which isn't supported by Linux. The printer works fine, however the scanner I cannot get to work. How can I get around this barrier?

---

### Post by Anduu on 2006-09-12
Have you tried xsane?

It is in the repos.

---

### Post by canadianwriterman on 2006-09-12
You would also need the backend for Epson, which can be found at:

[http://www.sane-project.org/lists/sane-backends-external.html]("http://www.sane-project.org/lists/sane-backends-external.html")

It's a bit tricky to get it working, but I got the scanner on my Canon all-in-one working great with Xsane.

Also, you may never get the scanner working WITH the printer. Xsane will be a separate program for scanning and will work independently of the printer.

---

### Post by Roasted on 2006-09-12
xsane doesn't recognize it. And I came across a site that didn't have my scanner listed as natively compatible with Linux, so I had no idea what I could do to get it to work.

btw what's this mean? I found my scanner in that link.



Stylus CX4800 	USB 	0x04b8/0x0819 	Good 	all-in-one
overseas version of the PX-A650

---

### Post by Roasted on 2006-09-18
hi

---

### Post by Roasted on 2006-09-21
Okay. I'm about to blow my top. This is getting ridiculous. It shouldn't take hours upon hours of research and asking questions to get a scanner to work.

For once, I don't know what a backend is. I assume it's some kind of driver? For two, I need a backend for my scanner. For three, I have no idea what to do with the backend. I believe I got a backend earlier but it was an RPM file, and I couldn't open it.

Can someone help before I go back to windows?

---

### Post by Quicky on 2006-09-22
Sounds like a pain in the backend.

---

### Post by PriceChild on 2006-09-22
[http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX4800](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX4800) says that your printer and scanner should work just fine.

Are you sure that xsane doesn't do the job for you?

---

### Post by mannheim on 2006-09-22
The "backend" that you need for this Epson scanner is the "epkowa" backend. It **is** in the ubuntu repositories, but is not installed by default: it is part of the package "libsane-extras".

So go to Synaptic (or the command line) and intall the **libsane-extras** package from the Universe repository. Then you should be all set to go: start up xsane again, and it should find your scanner.

---

### Post by buellman on 2006-09-22
After you installed libsane-extras you maybe need to run xsane as root aka sudo.
There was a problem mentioned in [this]("http://ubuntuforums.org/showthread.php?t=140229") thread and on [Launchpad]("https://launchpad.net/distros/ubuntu/+source/xsane/+bug/37499"). But maybe it will just work :-)

Greets. Buellman

---

### Post by Roasted on 2006-09-22
> **PriceChild said:**
> [http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX4800](http://www.linuxprinting.org/show_printer.cgi?recnum=Epson-Stylus_CX4800) says that your printer and scanner should work just fine.

Are you sure that xsane doesn't do the job for you?

I don't know what to tell you. I try to open xsane and it says no devices available.

---

### Post by moopere on 2006-09-22
> **Roasted said:**
> Okay. I'm about to blow my top. This is getting ridiculous. It shouldn't take hours upon hours of research and asking questions to get a scanner to work.

Yep, you are right.  I'd complain long and loud to Epson about this.  Its their product, they should support it out of the box with clear instructions and software/drivers.

Get on to them - nothing will change if we don't let the manufacturers know.

Cheers,
Craig

---

### Post by Roasted on 2006-09-22
Okay on another forum some dude hooked me up with the sane backends. It's a tar.gz file. I extracted it to the desktop. How do I install it from here? I tried apt-get install as well as cd Desktop THEN apt-get install and couldn't get it to work. Any leads? I did this before but it's been a while, and the book I wrote this information in was ruined when my basement flooded a few weeks ago. :(

---

### Post by mannheim on 2006-09-22
Roasted,

Have you installed libsane-extras from the repositories, as suggested above?

(Don't install from the tar file you've got: install the ubuntu package from the repositories, using Synaptic.)

---

### Post by Roasted on 2006-09-22
Okay. I installed them. But when I open xsane, it does the same thing (no devices available). 

Hmm?

---

### Post by buellman on 2006-09-22
> **Roasted said:**
> Okay. I installed them. But when I open xsane, it does the same thing (no devices available). 

Hmm?
Have you tried sudo xsane?

Greets. Buellman

---

### Post by Roasted on 2006-11-16
Haven't messed with my scanner in a while. Still haven't gotten it running.

I used synaptic. The libsane-extras are now installed. Xsane does nothing, just says no devices available. The printer is turned on. Even sudo xsane in the terminal doesn't help.

:(

---

### Post by nix4me on 2006-11-16
Scanner support has always been troublesome in linux.  File a bug with both Ubuntu and Xsane/sane.

nix4me

---

### Post by Roasted on 2006-11-17
But am I doing everything right then? Like, SHOULD it work with what I have set up, it just isn't?

---

