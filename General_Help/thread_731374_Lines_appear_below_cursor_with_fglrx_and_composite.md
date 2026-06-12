---
title: "Lines appear below cursor with fglrx and composite enabled."
date: 2008-03-21
forum: General Help
---

### Post by eTronicGaming on 2008-03-21
I recently upgraded the fglrx drivers using Envy on my t60p running Ubuntu 7.10.
I finally got most issues fixed, only, when I have composite enabled, there appears to be lines below my cursor that change when I highlight text or open programs and won't go away.  The only fix is to set composite to disable or 0, but then compiz won't work as a result.  Is there a fix for this?

-Josh

---

### Post by eTronicGaming on 2008-03-25
Bump... anyone?

---

### Post by dposselt on 2008-03-28
Hi,

Fellow T60p user here (but running fedora 7) with the same problem you report. This started with fglrx versions 8.1 and 8.2, which caused my entire screen to be filled with lines and corruption when compiz (or beryl) were turned on. With the latest version (8.3), the problem is largely fixed, but I get lines around my mouse as you noted. I posted on phoronix.com about this in the ATI driver forums (a nice source of information in general if you haven't been there). So far, I have not been able to find any help for this. My sense is that it is a remnant of a bug left over from previous releases in which the driver did not support 3D rendering for screens that were not a multiple of 64 pixels (1680 / 64 /= integer...). See the driver release notes for versions 8.1 and 8.2 for the note on this.

I am waiting for the next release (due sometime in April) for a possible bugfix. Note that the problem does not occur when I use an external display with resolution that is a multiple of 64 pixels.

Hang in there, and if you find a fix, let me know.

---

### Post by eTronicGaming on 2008-05-02
I finally got it fixed!

This site helped:
[http://www.thinkwiki.org/wiki/Problems_with_fglrx](http://www.thinkwiki.org/wiki/Problems_with_fglrx)

Basically, get the ATI Catalyst Control Center, check the Anti aliasing box, and set it to at least 2x... then restart x and it works!.

---

