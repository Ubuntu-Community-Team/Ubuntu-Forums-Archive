---
title: "Firefox questions [Resolved]"
date: 2007-05-13
forum: General Help
---

### Post by daverave999 on 2007-05-13
There are a couple of things I miss from the Windows version of Firefox and I was wondering if it is possible to have them in the Linux version, or if anyone could tell me why they are absent.

The address bar would behave like a google "i'm feeling lucky" search if you didn't type an url, whereas now it doesn't. Surely I can enable this or make a workaround? I found it most useful.

Also, no backspace as back? Any reason for that?

---

### Post by rsambuca on 2007-05-13
I am not sure about the backspace thing as I have never used it, but as far as the address bar thing, it seems to work fine for me in both ubuntu and windows.  I am using FF 2.0.0.3 in both and have a shared folder so cookies, cache, bookmarks, etc are the same.  To be honest, I haven't noticed a difference between the two.

---

### Post by skwishybug on 2007-05-13
I just learned this one:

To set the backspace to act as a back button, type in about:config into the address line.
In Filter type in "backspace" and then change the value to 0

Works perfectly.

---

### Post by daverave999 on 2007-05-13
Thanks skwishybug! That's one sorted...

Am I the only one who is experiencing this address bar thing then?

---

### Post by aysiu on 2007-05-13
In about:config, go to keyword.URL and change the string to ```
http://www.google.com/search?ie=UTF-8&oe=UTF-8&btnI=&q=
```

---

### Post by daverave999 on 2007-05-14
Thank you!

[/EDIT] It appears it was my fault in the first place for using OpenDNS...

---

