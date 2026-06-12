---
title: "OpenOffice Issue"
date: 2007-05-15
forum: General Help
---

### Post by phatalbert on 2007-05-15
I'm having an issue with OpenOffice on Ubuntu Feisty.

The program won't start up for me anymore. When I run ooffice, the loading window comes up and the bar gets to about half full before it just disappears.

In the terminal window, it spits out a really long thread before ending with this.

> ** (process:8775): WARNING **: Unknown error forking main binary / abnormal early exit ...



I've tried using the synaptic package manager and reinstalling it, but it doesn't change anything.

Any ideas?

Thanks.

---

### Post by heimo on 2007-05-15
Try renaming your OOo settings directory:
```
mv ~/.openoffice.org2 ~/.openoffice.org2_old
```

---

### Post by aldeby on 2007-05-28
If you installed SCIM imput for non latin languages this fix done the job for me: 
> [http://ubuntuforums.org/showpost.php?p=2568329](http://ubuntuforums.org/showpost.php?p=2568329)
Hope it helps. It has been a very annoying bug.

---

