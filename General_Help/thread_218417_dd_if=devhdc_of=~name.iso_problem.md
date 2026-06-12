---
title: "dd if=/dev/hdc of=~/name.iso problem"
date: 2006-07-18
forum: General Help
---

### Post by jordilin on 2006-07-18
While recording a data cd to an iso file by means of the command 
```
dd if=/dev/hdc of=~/name.iso
```
at the output I obtain:
> 1290056+0 records in
1290056+0 records out
segment violation

I get a segment violation error. But, the iso file is created flawlessly, because I can then burn the iso image without any problem. Anyone has tried this wonderful command and has had the same "issue"? In fact it is not an issue because I get what I want, but this segment violation worries me!!

---

### Post by jordilin on 2006-07-18
No one has tried this command? Put a cd and run it!! Just to see if I'm not the only one

---

### Post by king20878 on 2006-07-18
if you "dd if=/something_other_than_your_cdrom" do you get the same error?

---

### Post by schilcha on 2006-07-18
Here's what I get:
```
$ dd if=/dev/hdc of=~/name.iso
dd: reading `/dev/hdc': Input/output error
321216+0 records in
321216+0 records out
164462592 bytes (164 MB) copied, 120.091 seconds, 1.4 MB/s

```
I guess, the i/o error is caused by cd, which is in a rather bad state. Still, no segmentation violation. 

Im not a programmer, but I guess, a segmentation violation is somewhat similar to a segfault. I really can't believe, that there's such a bug in dd. However, I've seen segfaults on various commands (ls, ps, ...) on a machine with defect memory -- try running memtest (e.g from the install/live cd) to rule out this possibility. 

Good Luck!

---

### Post by jordilin on 2006-07-19
It seems I've found the problem. If I use my Desktop with my language which is Catalan gives segment violation, but if I use the Desktop with English (I switched at the entry login) there's no output error at all. In any case, when I use Catalan, I get the error but the output is the same, so it's not a very big issue.

---

