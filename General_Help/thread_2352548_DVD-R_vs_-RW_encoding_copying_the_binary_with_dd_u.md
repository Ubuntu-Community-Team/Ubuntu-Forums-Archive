---
title: "DVD-R vs -RW encoding: copying the binary with dd utility"
date: 2017-02-13
forum: General Help
---

### Post by haplorrhine on 2017-02-13
I want the security of a read-only medium.  I want to edit (partition resizing namely) and test the contents of a DVD-R before finalizing the write.  I've yet to open a pack of DVD-RWs, hoping that the solution is interchangeable data encoding at the binary level.

sudo dd if=/dev/DVD-RW of=/dev/DVD-R

Has anyone done this?  Could someone test it for me before I open the packaging?

---

### Post by haplorrhine on 2017-02-14
I couldn't find much relevant information, so I just gave it a go.  It turns out that dd will accept as an input file the /dev/sr0 file where the DVD mounts, but as an output file it will warn that it is read-only.  Alternatively, you can use dd to write the DVD to a system file and then use growisofs to write that system file to a blank DVD.

WIth written DVD-RW:
dd if=/dev/sr0 of=/blank/text/file

Now replace DVD-RW with blank DVD-R or DVD+R

growisofs -dvd-compat -Z /dev/sr0=/blank/text/file

I used DVD+R rather than DVD-R.  I don't know whether DVD+R holds more  data, but growisofs completed writing before it could throw the  out-of-space warning. Even if you do receive this warning, it might not matter if the unwritten data is simply zeroed extra disk space.

Alas, my DVD-RW was not seen by GParted, so partition resizing on a DVD-RW is still an issue.

---

