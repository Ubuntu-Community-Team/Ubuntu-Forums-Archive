---
title: "preserve permissions while zip folders"
date: 2019-10-22
forum: General Help
---

### Post by mood86 on 2019-10-22
Hello,
[COLOR=#242729][FONT=Arial]How can I preserve permissions while compressing a folder using zip under Ubuntu?

[/FONT][/COLOR]

---

### Post by spjackson on 2019-10-22
Welcome to the forums.

The zip and unzip commands in the zip package are from Info-Zip and these normally preserve permissions where possible. An alternative would be to use a compressed tar, if that would meet your needs.

---

### Post by TheFu on 2019-10-22
> **mood86 said:**
> Hello,
[COLOR=#242729][FONT=Arial]How can I preserve permissions while compressing a folder using zip under Ubuntu?

[/FONT][/COLOR]

The Unix-way would be to use **tar** and **gzip** from a root/sudo elevated account:

```
$ sudo tar czvf some-filename.tgz  relative-path-to-directory/
```

tar should only be used for 500MB and less.  For larger needs, use a real backup tool.

As for zip and unzip or any other program running on any Unix, ownership and groups outside the current userid can only be maintained by either using root or sudo.  Looking through the zip manpage, I don't see any mention at all about maintaining permissions, so every implementation could be different.

---

