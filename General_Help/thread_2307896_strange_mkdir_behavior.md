---
title: "strange mkdir behavior?"
date: 2015-12-29
forum: General Help
---

### Post by maclenin on 2015-12-29
After opening the terminal inside thunar at /home/user/Desktop/test and running...
```
mkdir a b c
mkdir old
mv a/ b/ c/ old/
rm -r old
mkdir old
```
...this result / path appeared in thunar after executing the final (second) *mkdir old* command (without error in the terminal):
```
[no folder icon] /home/user/Desktop/test/old
```
When I clicked the path, an "open with" window appeared. The *old* directory did not open.

I had to close and re-open /home/user/Desktop/test within thunar to yield the "expected" result:
```
[folder icon] old
```

Thanks for any thoughts!

---

### Post by cogier2 on 2015-12-29
Fascinating. I don't think this is a Thunar issue as it happened to me in a terminal (Linux Mint 17.3 Cinnamon), but only the very first time I did it. I have been unable to reproduce it since.

---

### Post by maclenin on 2015-12-30
Indeed! I don't think it's a thunar issue either. Perhaps, it's connected to the timing of the deletion of the previous *old* directory - too soon before re-mking it? Something that needed to refresh didn't refresh properly?

Still curious as to why it might have occurred....

Thanks, again, for any insights!

---

