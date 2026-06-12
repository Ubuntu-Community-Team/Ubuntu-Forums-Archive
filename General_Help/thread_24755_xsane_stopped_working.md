---
title: "xsane stopped working"
date: 2005-04-08
forum: General Help
---

### Post by jeremy on 2005-04-08
A few days ago xsane was updated in the repository, and since then I cannot scan.

Xsane opens as usual, and finds my epson perfection 1200 photo, but when I try to scan (or get a preview) xsane hangs for a minute or two, the gives an error "Error during read: Error during device I/O".

I have checked the scanner on another PC, works perfectly. I have reinstalled all the xsane bits using synaptic. I have also rebooted, and tried running xsane as root. Still the same.

If anyone else is having a similar problem, or has any  suggestions, please post.
Thanks

---

### Post by jeremy on 2005-04-15
I am still having this problem, even after a fresh install of hoary release. If anyone has any suggestions I would be most grateful.

---

### Post by bin on 2005-04-16
Same problem with Epson 1260 until I remembered that the Epson has a longish warm up time. When you start xsane there's a panel that shows Standard Options and the Lamp Warmup Time is set to -1 . I've just changed that to 5 and it works fine.

in light

bin

---

### Post by jeremy on 2005-04-16
bin
Many thanks for your reply, however, in my 'standard options' window there is no 'lamp warmup time' setting.

---

### Post by Bob D. on 2005-04-16
I have the same problem here as well. Epson 1660 Photo scanner. Xsane seems to see as a Epson GT8300 (?), but it used to work OK.

I can't see a setting for chnaging the warmup time either.

Bob

---

### Post by jeremy on 2005-04-16
I have made a bug report at [http://bugzilla.ubuntu.com/show_bug.cgi?id=9818](http://bugzilla.ubuntu.com/show_bug.cgi?id=9818)

---

