---
title: "Back-up files from WinXP using Ubuntu Live are corrupted"
date: 2013-07-19
forum: General Help
---

### Post by danidetapia on 2013-07-19
Hey everybody,

Due to some restrictions in my company laptop I informally agreed to extract some files I needed (like my timesheets and so on) using my emergency pendrive with Ubuntu Live. I copied them to another external drive and then back to my personal PC. The point is files are now corrupted. I could fixed the mailbox file already but not many XLS or PDF files. Is this a normal behavior because of what I did? Any idea how to fix these files?

Thanks in advance,

---

### Post by sudodus on 2013-07-19
Welcome to the Ubuntu Forums :-)

Normally xls files and pdf files will be copied as they are (without any changes) between different file systems. If this was what you did, there is something seriously wrong, if they were corrupted. But maybe you did also something else ...

1. Can you read the files on the pendrive or that other external drive? Are they OK?

2. What is corrupted? Some letters and special signs, or the whole files?

3. Did you edit the files somehow before copying them back to the company's computer?

-o-

One source of corruption is that writing to and from USB is very slow, and it is often buffered, so that you do not realize that it has not finished. The user interface looks like it has finished. If you unplug the pendrive before it has really finished, and without unmounting (ejecting) the drive, the file(s) will be corrupted, because they were only partially written.

Unmounting will not finish until writing has finished. A command line alternative is ```
sync
``` which will not return to prompt until all buffered write operations have finished. So to be safe, unmount and sync!

---

