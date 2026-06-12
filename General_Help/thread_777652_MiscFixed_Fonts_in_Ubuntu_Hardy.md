---
title: "MiscFixed Fonts in Ubuntu Hardy"
date: 2008-05-01
forum: General Help
---

### Post by dustins on 2008-05-01
Hey all,

I have just done a fresh install of Ubuntu 8.04 on my workstation.  One of the things that has always driven me nuts about Ubuntu is that bitmaped, non-antialiased fonts are not available by default.  I have looked all around and no one seems to have a common answer to the problem.  Can anyone point me in the right direction?  Thanks a million!

-- Dustin

---

### Post by simpsonsfan74 on 2008-05-01
I just ran into the solution for this the other day when trying to fix my "fuzzy fonts" problem in Hardy.

Run:
sudo dpkg-reconfigure fontconfig-config

Choose Native for the first one, Always for the second one (assuming you have an LCD monitor), and then Yes to allow bitmapped fonts.

---

### Post by dustins on 2008-05-02
Thanks, simpson!  It worked like a charm!

---

