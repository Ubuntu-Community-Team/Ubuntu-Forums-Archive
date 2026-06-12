---
title: "Amsn 0.96 RC1 won't load"
date: 2006-11-24
forum: General Help
---

### Post by Tilex on 2006-11-24
I've installed the 0.96 version of aMSN by following the instructions here:
[http://ubuntuforums.org/showthread.php?t=216689](http://ubuntuforums.org/showthread.php?t=216689)

Although the steps seem straightforward, it does not work for me, for when I launch amsn it never shows up.

So I installed the 0.95 version back and it works fine, but I want the 0.96 one.  I went on the amsn-project website and downloaded the source file.  It did not compile properly because apparently I was missing the "tcl-dev" and "tk-dev" packages even though Adept Manager tells me there are both installed.  Just in case, I re-installed tcl, tcl-dev, tk and tk-dev packages just to make sure they are installed properly.  Re-compile...same error.

So I downloaded the amsn-0.96.package (the distro-independant package) from the amsn-project website but I don't know how to open those.

Any suggestion as to how I could make aMSN work?  Thank you!8)

---

### Post by Tilex on 2006-11-24
Resolved.
I followed the instructions to install the package here:
[http://www.autopackage.org/docs/howto-install/](http://www.autopackage.org/docs/howto-install/)

Then, I had the famous "tcl not installed" error message.  It was installed, but the problem was that I had other versions of tcl and tcl-dev packages installed.  I removed all previous versions and kept only the new ones...and it works fine!

I thought I would let you know...

---

### Post by finferflu on 2006-11-24
How did you manage to keep the new packages and remove the old ones?

Thanks

---

### Post by darkteckno on 2006-11-24
Mine does not come up with an error message it just does not load

---

### Post by Tilex on 2006-11-24
> How did you manage to keep the new packages and remove the old ones?

I simply used Adept Package Manager and removed the old packages and just kept the newest versions.

> 
Mine does not come up with an error message it just does not load

You might want to download the source files and compile them.  If you didn't get any error using the package, you should not get any error by compiling it as well.  Go to [http://amsn-project.net](http://amsn-project.net) to get the instructions for compiling aMSN properly.

---

