---
title: "Wine text to big"
date: 2008-04-02
forum: General Help
---

### Post by Jdm111 on 2008-04-02
When i try to use any programs on wine the text size comes up to big on the menus. I think i put the dpi resoulution up but cant  get to it to put it back. It looks like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64668&stc=1&d=1207132427[/IMG]

---

### Post by justleen on 2008-04-02
try renaming the /home/user/.wine folder, and run winecfg again to get the default back
```

/home/user/ $ mv .wine .wine_old
/home/user/ $ winecfg

```

---

### Post by Jdm111 on 2008-04-02
> **justleen said:**
> try renaming the /home/user/.wine folder, and run winecfg again to get the default back
```

/home/user/ $ mv .wine .wine_old
/home/user/ $ winecfg

```

Thanks. That worked:)

---

