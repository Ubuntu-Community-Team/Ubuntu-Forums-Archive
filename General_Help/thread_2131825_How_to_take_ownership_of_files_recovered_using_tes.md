---
title: "How to take ownership of files recovered using testdisk"
date: 2013-04-02
forum: General Help
---

### Post by patagriff on 2013-04-02
I recovered filed from a deleted partition using testdisk. The program was easy to use and did exactly what it promised. HOWEVER, the recovered files are now in folders that are owned by root. How can I take ownership of these photos, videos and mp3's so I can deleted, copy, or edit them?

I don't know how to change permissions when I'm not root. I realize I can do this in a terminal, but I don't know the commands.

Thanks in advance for the usual timely and knowledgeable advice.

Patagriff, locked myself out in Tacoma

---

### Post by papibe on 2013-04-02
Hi patagriff.

To change ownership of a file back to you:
```
sudo chown youruser:youruser  file
```
Or to change recursively all files and directories (probably what you need):
```
sudo chown -R youruser:youruser  directory/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by patagriff on 2013-04-02
What do I put inplace of youruser? My user name?

---

### Post by patagriff on 2013-04-02
Thanks. It worked perfectly the first try. You are a gentleman and a scholar.

---

