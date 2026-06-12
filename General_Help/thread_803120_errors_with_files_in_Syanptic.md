---
title: "errors with files in Syanptic"
date: 2008-05-22
forum: General Help
---

### Post by chewit on 2008-05-22
There is file in Synaptic called "hwtest-gtk", which is currently in the "not installed (residual config)" section of synaptic.

When I tell the package to completely remove. I get two messages, which will not let me remove it

"E: hwtest-gtk: subprocess post-removal script returned error exit status 2"

and the second message is shown in my attachment. 

Would you explain what I need to do to fix this. If you can fix via the terminal, that will be fine.

---

### Post by vibinlakshman on 2008-05-22
My first impression is that , uninstall open office and reinstall it , if there is an error in installing it , first install ur choice and try installing open office .. Let me see what error u r getting nw...

---

### Post by EXCiD3 on 2008-05-22
You can try that with uninstalling open office but you should also try the Synaptic > Fix Broken Packages option from the menu. This sometimes helps.

---

### Post by chewit on 2008-05-22
> **EXCiD3 said:**
> You can try that with uninstalling open office but you should also try the Synaptic > Fix Broken Packages option from the menu. This sometimes helps.

There are no broken packages according to Synaptic.

---

### Post by EXCiD3 on 2008-05-22
See what this does:
```
dpkg --configure -a
```

---

### Post by chewit on 2008-05-22
I ran that command, the output was this:

Setting up openoffice.org-writer2latex (0.5-6) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...
unopkg failed.
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-writer2latex; however:
  Package openoffice.org-writer2latex is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-writer2latex
 openoffice.org

---

### Post by EXCiD3 on 2008-05-22
Try this:
```
dpkg --configure openoffice.org-writer2latex
```

---

### Post by chewit on 2008-05-22
I get this output:

Setting up openoffice.org-writer2latex (0.5-6) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...
unopkg failed.
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 openoffice.org-writer2latex

---

### Post by EXCiD3 on 2008-05-22
lol, everything i tell you to try just gives you parts of the errors you got in the first place!

I did find a launchpad bug for this, but no fixes: [https://bugs.launchpad.net/ubuntu/+source/writer2latex/+bug/219703](https://bugs.launchpad.net/ubuntu/+source/writer2latex/+bug/219703)

---

### Post by chewit on 2008-05-22
Thanks,

I have tried reinstalling writer2latex, but i get this message

E: openoffice.org-writer2latex: subprocess post-installation script returned error exit status 1
E: openoffice.org: dependency problems - leaving unconfigured

---

### Post by chewit on 2008-05-22
I have posted a comment launchpad bug report. Hopefully, it should be fixed for 8.04.1

It is not effecting OpenOffice, it still works fine.

---

### Post by EXCiD3 on 2008-05-22
Thats good to hear. I don't know enough to try to fix the problem manually. Hopefully one of the developers will take notice and comment a fix for you.

---

