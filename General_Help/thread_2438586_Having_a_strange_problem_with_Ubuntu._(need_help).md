---
title: "Having a strange problem with Ubuntu. (need help)"
date: 2020-03-14
forum: General Help
---

### Post by octoomy on 2020-03-14
I recently tried installing Ubuntu on a spare laptop I have, the thing is its throwing up an error that resulted in a kernel panic. Here is the error.
[   2.171080] Initramfs unpacking failed : LZMA data is corrupt
[   2.502733] Kernel panic - not syncing : VFS: Unable to mount root fs on unknown block
[   2.502733] CPU: 2 PID: 1 Comm: swapper/0 not tainted 5.3.0-28-generic #30~18.04.1 Ubuntu
[   2.502827] Hardware name: ASUSTeK Computer Inc. K54C/K54C, BIOS K54C.207 04/18/2012

To let you know, I upgraded this laptop to have 8 GB's of ram and it can run Ubuntu since I got it to work on a similar pc. This is a strange error. IDK why it happened. Here is the code https://drive.google.com/file/d/17KOe1MOU6R2d7II5n-NL4ghCIL7-b-Qp/view?usp=drivesdk

---

### Post by yancek on 2020-03-14
Did you verify the iso after the download with either an md5sum or sha256sum?  Seems like a bad download with corrupted files.  See the link below for an explanation.

[https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-how-to-verify-ubuntu#1-overview)

---

