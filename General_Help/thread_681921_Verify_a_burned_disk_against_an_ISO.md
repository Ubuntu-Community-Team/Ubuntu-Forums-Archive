---
title: "Verify a burned disk against an ISO?"
date: 2008-01-29
forum: General Help
---

### Post by dorkdork777 on 2008-01-29
Hello all,

I downloaded an ISO of Linux Mint (an Ubuntu-based distro, AFAIK), and burnt it to a CD-R at the lowest speed I could (9.4x). It came out with an error, telling me to try a lower speed. I tried again - same problem. None of my burns had ever had this problem before, so what I'd like to know is this:

Is there a way to verify a disk to see if it's a perfect copy of an ISO?

I have searched for this problem, and all I could find was unanswered questions and complicated instructions involving the command line ([like this]("http://www.g-loaded.eu/2006/10/07/verify-a-burned-cddvd-image-on-linux/")). I prefer GUIs, but I'm fine with pasting a few instructions into the command line.

Thanks a lot for reading; hope you guys have a solution! (You always seem to! :))

---

### Post by TBerben on 2008-01-29
Most burning applications should offer you to verify the burnt data for you (I know K3B does)

---

### Post by HermanAB on 2008-01-29
Use md5sum.

---

### Post by dorkdork777 on 2008-01-29
I just used CD/DVD Creator to burn this CD, and it didn't offer me the option to verify. I suppose it would be easiest to install K3B and re-burn it, verifying it this time. Thanks a lot! :)

---

### Post by Zwack on 2008-01-29
md5sum -b /some/path/to/your/file.iso
md5sum -b /dev/cdrom

The two numbers should be the same.

Z.

---

### Post by bodhi.zazen on 2008-01-29
+1 K3b, it is the most reliable that way.

+1 md5sum if you prefer the command line.

---

