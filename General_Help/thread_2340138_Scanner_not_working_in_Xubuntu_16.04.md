---
title: "Scanner not working in Xubuntu 16.04"
date: 2016-10-16
forum: General Help
---

### Post by ardouronerous on 2016-10-16
Previous reports of the same problem, but no solution found;
[URL="https://ubuntuforums.org/showthread.php?t=2324912"]https://ubuntuforums.org/showthread.php?t=2324912
[/URL][https://ubuntuforums.org/showthread.php?t=2328712](https://ubuntuforums.org/showthread.php?t=2328712)

Link to bug report, but page is gone: [http://news.gmane.org/gmane.comp.graphics.scanning.sane.devel/cutoff=25795](http://news.gmane.org/gmane.comp.graphics.scanning.sane.devel/cutoff=25795)

My scanner is a Canon LIDE 110, Simple Scan detects it, I checked the preferences: 
[ATTACH=CONFIG]271639[/ATTACH]

but whenever I scan, I get this message, "**Failed to scan, unable to start scan**":
[ATTACH=CONFIG]271640[/ATTACH]

The scanner is not malfunctioning, I know this because I use it with Windows XP via Virtualbox, and my scanner was previously working in 14.04, it was only when I updated to 16.04 that the scanner doesn't work, and I've tested my scanner on 14.04 via Virtualbox and it works there.

Please help, thanks.

---

### Post by ardouronerous on 2016-10-16
Bump

---

### Post by ardouronerous on 2016-10-17
Bump

---

### Post by ardouronerous on 2016-10-17
My Canon LIDE 110 scanner isn't working in 16.04, it is detected but it doesn't scan, and I know it's not malfunctioning either because I've tested my scanner on Virtualbox using Windows XP and Xubuntu 14.04 and 16.04 on LiveCD, my scanner works on XP and 14.04, but not on 16.04, so it is my opinion that 16.04's xsane package is bugged.

So, how do I replace 16.04's xsane with the 14.04 version? Is there any dangers in doing this? Will this compromise my system?

---

### Post by Bucky Ball on 2016-10-17
*Threads merged.*

An attempt to fix the same problem. Better to keep it on the same thread for better support. Splitting the same issue dissipates support. Keep anything you do to try and fix this on this thread. Posting it here will serve the double purpose of bumping the thread so you don't need to do it with no additional information. Posting it elsewhere leaves this redundant.

Guess you'd use the 14.04 xsane by installing from the 14.04 repos, but a workaround at best and not a fix. Probably better to keep digging as to why the 16.04 xsane is not working for you in 16.04, though.

Do you have 'sane' installed as well as 'xsane'?

---

### Post by ardouronerous on 2016-10-17
I've double checked it in LiveCDs, by deault, 14.04 and 16.04 has sane installed not xsane, but I did install xsane to try it out, I got a 'device I/O error' when using xsane to scan though.

---

### Post by ardouronerous on 2016-10-18
After much digging around, I discovered these from Ask Ubuntu:
[ https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04]("https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04")
[ https://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10]("https://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10")

They describe a workaround to the problem, however, are these workarounds still good though? These posts were made many months ago, and if so, why haven't these fixes been included in 16.04's repos?

---

### Post by Bucky Ball on 2016-10-18
Neither link works for me, but the first one is about 16.04, so ... Aren't you using 16.04? Why would that fix be outdated?

No idea why fixes are not in 16.04. A question you would have some chance of getting answered by asking Canonical but little chance here.

---

### Post by ardouronerous on 2016-10-18
Try the links now:

[https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04](https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04)
[https://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10](https://askubuntu.com/questions/688642/network-scanner-canon-stops-after-upgrade-from-15-04-to-15-10)

If they still don't work, here's the solutions:

**sane stopped working after update to 16.04**
 > After applying these updates, it is now working properly
  libsane (1.0.26-git20160710-xenial0, 1.0.26-git20160711-xenial0)
  libsane-common (1.0.26-git20160710-xenial0, 1.0.26-git20160711-xenial0)
  sane-utils (1.0.26-git20160710-xenial0, 1.0.26-git20160711-xenial0)
     

**Network scanner (Canon) stops after upgrade from 15.04 to 15.10**
> I had the similar problem with the Canon Pixma MG5450 (MG5400 series) using Ubuntu 15.10.
Problem:

Using "Simple Scan" to scan a document failed with:

    Failed to scan
    Unable to connect to scanner

But the device was properly discovered using scanimage -L

$ scanimage -L
$ device `pixma:MG5400_C5BFDC000000' is a CANON Canon PIXMA MG5400 Series multi-function peripheral

Solution:

Download 3 packages from Debian Expirimental - Libs

    libjpeg62-turbo
        Version: 1:1.4.80-115-gfb907b2-1
    libsane-common
        Version: 1.0.26~git20151121-1
    libsane
        Version: 1.0.26~git20151121-1

(My reputation won't allow me to add more then 2 links. Otherwise i would have linked those libraries.)

Install *deb packages

# #Install the downloaded packages as root
# dpkg -i libjpeg62-turbo_1.4.80-115-gfb907b2-1_amd64.deb
# dpkg -i libsane-common_1.0.26~git20151121-1_all.deb
# dpkg -i libsane_1.0.26~git20151121-1_amd64.deb

---

### Post by ardouronerous on 2016-10-19
Bump.  I've checked the 16.04 repos, and this is what I've found:

libsane-common (1.0.25+git20150528-1ubuntu2)
libsane (1.0.25+git20150528-1ubuntu2)
sane-utils (1.0.25+git20150528-1ubuntu2)

I didn't find libjpeg62-turbo, is that even needed?

---

### Post by ardouronerous on 2016-10-20
Bump.

Can someone shed some light on how to fix this problem, please?

---

### Post by Geoffrey_Arndt on 2016-10-21
And the app "simplescan" doesn't work either?

---

### Post by ardouronerous on 2016-10-21
Simple Scan works, it detects my scanner but it doesn't scan, it gives me the error message: **Failed to scan, unable to start scan**.
I've tried xsane as well, it detects my scanner, but when I scan, it gives me a 'I/O error' message.

I've done some digging around and I've found this:
[URL="https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04"]https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04
[/URL]
It describe a workaround to the problem, however, are these workarounds still good though? These posts were made many months ago. Here's the solution:

**sane stopped working after update to 16.04**
 > After applying these updates, it is now working properly
  libsane (1.0.26-git20160710-xenial0, 1.0.26-git20160711-xenial0)
  libsane-common (1.0.26-git20160710-xenial0, 1.0.26-git20160711-xenial0)
  sane-utils (1.0.26-git20160710-xenial0, 1.0.26-git20160711-xenial0)

 I've checked the 16.04 repos, and this is what I've found:

libsane-common (1.0.25+git20150528-1ubuntu2)
libsane (1.0.25+git20150528-1ubuntu2)
sane-utils (1.0.25+git20150528-1ubuntu2)

It looks like 16.04's sane and it's dependences are outdated.

---

### Post by Bucky Ball on 2016-10-21
You have already asked about this.

[https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04](https://askubuntu.com/questions/761585/sane-stopped-working-after-update-to-16-04)

Why wouldn't it be applicable, as I have already asked??? 'sane-stopped-working-after-update-to-16-04'. Isn't that exactly your issue, or very close, you can't get your scanner to work in 16.04 but it worked fine in the last release???

Suggest you try it and get back to us with the result.

---

### Post by ardouronerous on 2016-10-21
Well, it's a trust issue for me, because in the solution, the sources of the files comes from this PPA: [https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git)

I'm very cautious when it comes to PPAs, I tend to install PPAs from trusted sources like from the official website of the software, now, I'm not sure if this Rolf Bensch is a official developer of SANE.

An anyone direct me to a official SANE PPA?

---

### Post by Bucky Ball on 2016-10-21
This is the first paragraph of Rolf's PPA page. The link to the sane snapshots is right there in the first line.

> **Rolf Bensch]Ubuntu SANE packages from SANE daily git snapshots ([http://www.sane-project.org/snapshots/](http://www.sane-project.org/snapshots/)) or cloned from git ([url]http://anonscm.debian.org/gitweb/?p=sane/sane-backends.git said:**
> ) if SANE daily git snapshot isn't available on the website.

---

### Post by ardouronerous on 2016-10-21
Looking at the links, does that mean I have to compile SANE from source? Don't think I'm that tech savy enough to compile software from source, I'm still intimated by the Terminal, even after 5 years of using Xubuntu.

Looks like I'm stuck with what I've got for now, using my scanner with Windows XP via Virtualbox, until Ubuntu updates it's repos.

---

### Post by Geoffrey_Arndt on 2016-10-21
Revised Update (launchpad clarification).

Launchpad is about as close to official as one can get . . . it's one of the more trusted PPA sources available (in your browser, just run a "whois launchpad").    

Using the PPA does not require building from source code.   If you understand the PPA basics, it takes just 5 minutes or so to do the sane packages update.    A re-start will be required.   If the system still doesn't scan (using simplescan is suggested - it uses the sane packages and others as back-end code.)

Also, remember a PPA can be installed AND removed in a matter of seconds.   Just one mouseclick will do it.

---

