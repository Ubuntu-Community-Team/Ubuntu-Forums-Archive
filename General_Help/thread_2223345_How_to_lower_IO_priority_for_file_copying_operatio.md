---
title: "How to lower I/O priority for file copying operations?"
date: 2014-05-10
forum: General Help
---

### Post by starriol on 2014-05-10
[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]Whenever I copy files from a disk to another on my personal Linux system, the OS stops responding appropriately, the UI starts behaving erratically, any movies I'm playing will freeze and continue until the file transfer is done. I don't care if the transfer takes longer, I'd like to throttle it down.[/COLOR][/FONT]
[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]
[/COLOR][/FONT]
[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]I only copy files using Dolphin normally, so I'd need this system wide or at least be able to launch Dolphin for this.[/COLOR][/FONT]

[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]
[/COLOR][/FONT]
[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]I tried "ionice -c 3 dolphin", it had the same problem.[/COLOR][/FONT]


[FONT=Lucida Grande, Trebuchet MS, Verdana, Helvetica, Arial, sans-serif][COLOR=#333333]Thanks for any ideas.[/COLOR][/FONT]

---

### Post by matt_symes on 2014-05-10
Hi

I've read about this but never used it, so....

I'm pretty sure you need to use a cgroup to limit IO; the block I/O (blkio) controller

Here's a link.

[https://www.kernel.org/doc/Documentation/cgroups/blkio-controller.txt](https://www.kernel.org/doc/Documentation/cgroups/blkio-controller.txt)

If it makes no sense, post back and we'll see if we can help you.

Kind regards

---

