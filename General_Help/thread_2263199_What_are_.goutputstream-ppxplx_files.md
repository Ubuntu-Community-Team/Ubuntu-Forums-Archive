---
title: "What are .goutputstream-ppxplx files?"
date: 2015-01-30
forum: General Help
---

### Post by Martin_McGlensey on 2015-01-30
I have many 0 byte files in my home directory. The root name is .goupputstream  followed by 5 letters. Each file has a different set of letters and creation date. Does anybody know where these come from? How can I get rid of them? Should I delete them?

Thanks

---

### Post by Impavidus on 2015-01-30
Sounds like a bug that was present in 12.04, but no longer in 14.04. I believe it's safe to delete those files. They were created when you shutdown the computer without first logging off.

---

### Post by Bashing-om on 2015-01-30
Martin_McGlensey; Yep;

confirmation:
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)

seems the fix is worse than the bite. The procedure in 12.04 is just to delete the .goutputstream files .

[INDENT][INDENT]not always a perfect world
[/INDENT][/INDENT]

---

