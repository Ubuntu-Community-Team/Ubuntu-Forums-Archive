---
title: "AMD Catalyst Control Center (Administrator) not worked on Xubuntu 15.04"
date: 2015-05-06
forum: General Help
---

### Post by tanawat on 2015-05-06
I currenly using Xubuntu 15.04 x64 and I already installed driver for AMD Graphic card correctly.
AMD Catalyst Control Center worked fine but AMD Catalyst Control Center (Administrator) not worked.
I wonder why?
And how to get it work?

---

### Post by QIII on 2015-05-06
What do you mean by not working?

Is it not opening?

---

### Post by tanawat on 2015-05-07
> **QIII said:**
> What do you mean by not working?

Is it not opening?
Yes

---

### Post by QIII on 2015-05-07
OK.

Please use the terminal and issue this command:

```
sudo amdcccle
```

to see if that will invoke Catalyst in administrative mode.

If it does, we'll work on getting it to work from the icon.

If it does not and you get errors in the terminal, please copy the results by highlighting it all, then pressing CTRL+SHift+C.

Post that back here between code tags.  To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

