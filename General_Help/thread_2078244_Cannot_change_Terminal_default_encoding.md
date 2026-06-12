---
title: "Cannot change Terminal default encoding"
date: 2012-10-30
forum: General Help
---

### Post by outofsync on 2012-10-30
Hi,

I'm on Precise Pangolin 12.04 LTS 

I've a lot of custom code which outputs text as ISO-8859-1 encoding to the Terminal.

I installed such encoding, and made it the default. I verified that now the desktop uses this encoding.

Also, the contents of  /etc/default/locale is LANG=es_ES.ISO-8859-1

However, when I open Terminal, the default encoding is always UTF-8. I can navigate to the Terminal menu bar, and choose ISO-8859-1 encoding, but it's an annoyance to do it everytime I open a Terminal.

How can I change the Terminal default to ISO-8859-1?

And, why is Terminal setting UTF-8 as the default?

Thanks!!

---

### Post by lykeion on 2012-10-30
If you are using gnome terminal you can set the default encoding with gconftool, like this:
```
gconftool --set --type=string /apps/gnome-terminal/profiles/Default/encoding ISO-8859-1
```

---

### Post by lykeion on 2012-10-30
...and as to why utf-8 is default, I think it's simply because it's superior. If you are in the mood for reading, you can get the whole background here:

[http://www.joelonsoftware.com/articles/Unicode.html](http://www.joelonsoftware.com/articles/Unicode.html)

---

### Post by outofsync on 2012-10-31
> **lykeion said:**
> If you are using gnome terminal you can set the default encoding with gconftool, like this:
```
gconftool --set --type=string /apps/gnome-terminal/profiles/Default/encoding ISO-8859-1
```

Worked like a charm, thanks.

---

### Post by lykeion on 2012-10-31
Glad I could help outofsync. If you set this thread to SOLVED in Thread tools menu, others can find the solutions to questions more easily.

---

