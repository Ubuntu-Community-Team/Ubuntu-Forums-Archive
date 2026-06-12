---
title: "General question for Flash Player 9"
date: 2007-02-28
forum: General Help
---

### Post by jellystones on 2007-02-28
So even though I know how to compile programs from source, or install binaries, I've been withholding from installing flash-player 9 because I want the Ubuntu flavoured version (I.e, the version that you can get through the synaptic package manager).

Will Flash be released soon for a quick download through the package manager? Also is there really any point in waiting for it? For some reason I have this notion that packages downloaded through the package manager are optimized for Ubuntu.....is this a silly way of thinking?

Thanks
Martin

---

### Post by openix on 2007-02-28
Hi,

Version 9 is already in the repositories,

sudo apt-get install flashplugin-nonfree

---

### Post by 23meg on 2007-02-28
It's very easy to install, and Ubuntu can't make any modifications on it, since it's closed source, so it won't be "Ubuntu flavoured" in any case.

---

### Post by jellystones on 2007-02-28
> **23meg said:**
> It's very easy to install, and Ubuntu can't make any modifications on it, since it's closed source, so it won't be "Ubuntu flavoured" in any case.

Thanks for the quick reply...so for the open source packages, are those ever tweaked for Ubuntu?

---

### Post by jellystones on 2007-02-28
> **openix said:**
> Hi,

Version 9 is already in the repositories,

sudo apt-get install flashplugin-nonfree

Oh I assumed that the package manager showed all of the available packages. I guess not. Thanks!

---

### Post by 23meg on 2007-02-28
> **jellystones said:**
> Thanks for the quick reply...so for the open source packages, are those ever tweaked for Ubuntu?

Some are, some are not. System critical parts such as the kernel almost always are. You can find out whether or not a certain package has been by looking at the changelog.

---

### Post by JasonRivers on 2007-03-02
when I try and install this using "apt-get install flashplugin-nonfree" it tries to install flash player 7, from macromedia, and give this error:

automatic installation failed due to network problems or upstream changes

i'm guessing this is because its now Adobe, and not Macromedia.

so I tried the download from the Adobe website and it asks where firefox is installed (one would assume the /usr/share/firefox directory) but it's not working.

any idea's how I can install flash 9?

Jay

---

### Post by SpikeyB on 2007-03-02
I did it by installing Automatix and then using Automatix to install Swiftfox.  Flash came with Swiftfox and works in Firefox too.

---

### Post by JasonRivers on 2007-03-02
thanks, I managed to install it from the adobe download the install directory is /usr/lib/firefox incase anyone else needs it :)

Jay

---

