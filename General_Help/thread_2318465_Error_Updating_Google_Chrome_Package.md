---
title: "Error Updating Google Chrome Package"
date: 2016-03-26
forum: General Help
---

### Post by HunterDX77M on 2016-03-26
Hey Everyone,

I recently started seeing an error message in the title bar, with a red exclamation point that says:

The update information is outdated. This may be caused by network problems or by a repository that is no longer available. Please update manually by selecting 'Show Updates' from the indicator menu and watching for any failing repositories.

The options below that in the menu are 'Show Updates', 'Show Notifications' (which a check mark next to it), and 'Preferences'.

Clicking 'Show Updates' just brings up a small window that says "The software on this computer is up to date".

Clicking 'Show Notifications' just checks/unchecks the check mark next to it and has no other noticeable behavior.

Clicking 'Preferences' opens up the Software & Updates preferences window.

There is an entry that is checked in the Other Software tab that is 
[http://dl.google.com/linux/chrome/deb/stable](http://dl.google.com/linux/chrome/deb/stable) main

I have tried apt-get update and apt-get upgrade, but that does not resolve the issue. When I run apt-get update I see the following in the output.

```

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

```

Is there a way to repair this without having to uninstall and reinstall Google Chrome?

Thanks for any advice.

---

### Post by verymadpip on 2016-03-26
Hi there.
I believe that Google have "ditched" (someone else can explain it in a much more pleasant & accurate way I'm sure) 32 bit Chrome.
I think I had the same error & somehow had the 32 bit repo enabled.  I did actually uninstall & reinstall Chrome to fix that, using the 64 bit specific repo:
[http://askubuntu.com/questions/510056/how-to-install-google-chrome](http://askubuntu.com/questions/510056/how-to-install-google-chrome)

 (Now I have a different sources.list issue which I'll save for my own thread, if I can't fix that by myself).

---

### Post by grahammechanical on 2016-03-26
The ditching by Google of Linux 32 bit Chrome should not affect users of Chrome 64 bit. And it doesn't except for that error message. Here is the reason why Google are ditching 32 bit Linux Chrome and two ways to stop that error message from occurring.

 [http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

[http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu)

[http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html](http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html)

Regards

---

### Post by HunterDX77M on 2016-03-26
> **grahammechanical said:**
> The ditching by Google of Linux 32 bit Chrome should not affect users of Chrome 64 bit. And it doesn't except for that error message. Here is the reason why Google are ditching 32 bit Linux Chrome and two ways to stop that error message from occurring.

 [http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)

[http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu](http://www.omgubuntu.co.uk/2016/03/fix-failed-to-fetch-google-chrome-apt-error-ubuntu)

[http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html](http://www.webupd8.org/2016/03/fix-failed-to-fetch-google-chrome_3.html)

Regards


Ah, thank you! :)

Both for the helpful background information and the fix.

---

