---
title: "CD contents filenames changed!?"
date: 2006-12-09
forum: General Help
---

### Post by Tekovro on 2006-12-09
when i was on windows i burned a couple cd's with multiple video files. i named them before i burned them onto a cd, but when i play that cd on ubuntu the file names are changed! from Naruto 001.avi it got changed to _af636~1.avi is there a way to fix this?

---

### Post by kbracer on 2006-12-10
This is just a stab in the dark, but I suspect that the CD was written using the MS Joliet format instead of ISO9600. The Joliet format puts two indexes on the disk, one that allows for mixed case long filenames and one that maintains ISO9600 compatibility. I believe you are probably seeing the compatibility index when viewing the disc on Ubuntu.

---

