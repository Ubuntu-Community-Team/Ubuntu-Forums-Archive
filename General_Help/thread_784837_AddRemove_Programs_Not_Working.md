---
title: "Add/Remove Programs Not Working"
date: 2008-05-06
forum: General Help
---

### Post by Junior Varsity on 2008-05-06
Well, my Ubuntu was downloading updates and it was in the middle of installing and configuring when my computer froze and I had to shut it down by holding the power button. Now when I went in the installer to try and install a few programs it gives me this error: 

[IMG]http://i29.tinypic.com/s5xt2b.png[/IMG]

I went into terminal and tried to enter just that: dpkg-configure -a and dpkg-configure-a. None of it works. Can someone please help me fix what's going on? Thank you. :)

---

### Post by jman0591 on 2008-05-06
When in doubt stick a "sudo" in front of a command.  This will allow it to be run as root, and should fix your problem, and many others when you just forget to put it it.  So enter "sudo dpkg-configure -a", without quotes of course, into the terminal, and it should ask you for your password then go and do its business.  Hope this helps.

---

### Post by Junior Varsity on 2008-05-06
I tried before and It gave me an error. Let me try again and I'll paste the results.

Edit: Results:

sudo: dpkg-configure: command not found

---

### Post by HotShotDJ on 2008-05-06
> **jman0591 said:**
> When in doubt stick a "sudo" in front of a command.ACK!  While in this particular case, the "sudo" advise was absolutely correct, you should NOT just "stick a "sudo" in front of a command" unless you are sure you know what and why you are doing it.  In addition to fixing up your problem with dpkg, it can also be used to modify and delete system files, install trojans & root kits, and all manner of mischief.  When in doubt, run as root (sudo)?  Please.  No.  When in doubt, ask a trusted source (such as ubuntuforums.org).

---

### Post by HotShotDJ on 2008-05-06
> **Junior Varsity said:**
> sudo: dpkg-configure: command not foundyou left out a space between dpkg and -configure...

---

### Post by Junior Varsity on 2008-05-06
Yay so far so good, ish.

 sudo dpkg -configure-a
dpkg: unknown option -o

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

Now what?

---

### Post by HotShotDJ on 2008-05-06
> **Junior Varsity said:**
> Now what?I'm sorry.  That was my fault... I should have been paying better attention.  Here is the command:

```
sudo dpkg --configure -a
```Don't forget a space after dpkg and after --configure

---

### Post by Junior Varsity on 2008-05-06
THANK YOU SO MUCH. Okay now its downloading a package and hopefully it'll install correctly. Thank you both!

---

### Post by jman0591 on 2008-05-06
My apologies.  The "when in doubt stick the sudo in" was meant as more of a joke than anything else, as in you will be surprised how many times forgetting it is the origin of your problem (for me at least).  However I see how this could be taken the wrong way.

---

