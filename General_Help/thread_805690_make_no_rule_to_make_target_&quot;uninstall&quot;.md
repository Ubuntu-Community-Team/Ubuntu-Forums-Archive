---
title: "make: no rule to make target &quot;uninstall&quot;"
date: 2008-05-24
forum: General Help
---

### Post by mrwawa on 2008-05-24
Hi all,

I am relatively green on Linux, though I have been working with it on and off for six years.  I know that's sad, but at any rate . . .

I have installed a genetics program, CBrother, that I wish to uninstall.  I ran make make install in the folder after I unzipped the file. Do I run sudo make uninstall from the same folder?  I have tried that and I get the message "make no rule to make target "uninstall". Stop."

In addition, how does one "recover" the install notes?  Are they saved in the unzipped folder?

Thanks for any help,

Wade

---

### Post by gsmanners on 2008-05-24
A lot of apps don't bother with uninstall rules. That's where packaging comes in or at least use checkinstall. Speaking of checkinstall, you may be able to use that to package your app, then use dpkg -r to uninstall it. Depending on how the install works, you may be able to do this without needing to uninstall first.

---

