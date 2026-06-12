---
title: "Dependency problem with 855resolution"
date: 2005-08-25
forum: General Help
---

### Post by Muffe on 2005-08-25
I have a laptop with an 1280x800 screen. I use the 855resolution program to force X.org to use 1280x800 instead of 1024x768.

I found an deb package in a Debian repository (the version I found in the Ubuntu repositories was too old), and downladed it. When I tried to install it with the *dpkg -i * command, I got a message that it was a dependency probem. The package required  libc6 >= 2.3.2.ds1-21, and I had 2.3.2.ds1-20ubuntu14 installed. I had previously installed 855resolution from source with the same libc6 version, so I knew it worked. Therefore, I forced the package to be installed.Now my screen looks wonderful, but:

The problem is that every time i try to use an apt-get install command, I get a message telling me that I have unmet dependencies. It suggest to remove the 855resolution package to solve the problem, and I can not find any way to bypass it.

Is it any way to permanently remove this warning for this package and this version only?

Thanks.

---

### Post by davmac on 2005-08-25
I had the same problem and unfortunately didn't find an elegant solution to the problem. I uninstalled 855resolution, rebuilt it from source (from [http://perso.wanadoo.fr/apoirier/](http://perso.wanadoo.fr/apoirier/)) and added a script in init.d to run it at start up.

If you find the "real" answer to this problem, I'd love to know!

Regards,

Dave MacLeod

---

### Post by Muffe on 2005-08-26
I wil probably do the same as you, it's just that I like to do it "the Ubuntu way"...

---

### Post by Muffe on 2005-08-26
I have made a walkaround to this problem. I unpacked the .deb package and changed the required version of libc6 to 2.3.2 (without that ds1-21 stuff at the end), uninstalled the old and installed the modified one with success.

If someone can host the package, please send me a PM with an email adress that I can send it to.

---

### Post by varunus on 2005-08-26
Muffe, I can host the package.  I've sent you a PM.

EDIT:  Package is now hosted.
[http://web.ics.purdue.edu/~ajgore/855resolution_0.4-2_i386.deb](http://web.ics.purdue.edu/~ajgore/855resolution_0.4-2_i386.deb)

---

### Post by savage on 2005-08-31
thank you so much varunus

---

