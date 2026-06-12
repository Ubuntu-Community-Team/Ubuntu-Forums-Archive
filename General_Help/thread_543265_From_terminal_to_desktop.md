---
title: "From terminal to desktop"
date: 2007-09-04
forum: General Help
---

### Post by Vince329 on 2007-09-04
I downloaded adobe flash plug in to the desk top. Now how do I navigate from the terminal to the desk top? Then I would be able to follow the instructions. I have a lot to learn but I will try.

 
   1.  Click the "Download .rpm" link. A dialog box will appear asking you where to save.rpm installation the file.
   2. Save the .rpm file to your desktop and wait for the file to download completely.<
   3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user). The installer will instruct you to shut down your browser(s).
   4. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by SOULRiDER on 2007-09-04
RPM = BAD, DEB = GOOD.

You REALLY  should check this link out, it shows how to isntall software on Ubuntu, its a lot easier than you think ;)
[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Basically, if you wanna isntall flash just type:
```
 sudo aptitude install flashplugin-nonfree
``` in a console.

---

### Post by sumguy231 on 2007-09-04
.RPM files are for Red Hat-based systems - Ubuntu uses .DEB packages. You can either install it the easy way mentioned above, or if you really want to you could always download the tarball, extract it, and copy libflashplayer.so to your browser's plugins directory.

---

### Post by r4ik on 2007-09-04
Now how do I navigate from the terminal to the desk top?

cd Desktop

---

### Post by jamvegan on 2007-09-04
And if you want to explore the terminal more, Ubuntu has  a decent guide to [Basic Commands]("https://help.ubuntu.com/7.04/basic-commands/C/").

---

### Post by Vince329 on 2007-09-04
Thanks for the link. I did use synaptic but I wanted the free version.

---

### Post by Vince329 on 2007-09-04
Guess I'll go back and try the tar ball version.

---

### Post by jamvegan on 2007-09-04
> Thanks for the link. I did use synaptic but I wanted the free version.

What do you mean by free version?  If you are downloading from Adobe's website then you are getting the same Flash Player 9 that is listed in Synaptic as flashplugin-nonfree.  The reason that it is labeled as "non-free" in Ubuntu is because the software license does not fit the definition of a free software license (which has nothing to do with price, or whether you are allowed to use the compiled software, but rather with what you are allowed to do with the source code).  So, if you've already got it installed via Synaptic, you're done! :)

---

### Post by Vince329 on 2007-09-05
I thought that being non free I would have to pay for it. I went back to Snyaptic and down loaded adobe and installed it. I played around in terminal for 3 hours and never could figure out how to navigate to the tar ball version. Thanks for setting me straight with the non free bit.

---

### Post by jamvegan on 2007-09-05
> Thanks for setting me straight with the non free bit.

You're welcome.  That's been confusing people for years. :)  Which is the reason that many people prefer the term "open source" to "free software".  I like the philosophical stance that goes along with "free software", but the phrase can be ambiguous, no doubt about it.

---

