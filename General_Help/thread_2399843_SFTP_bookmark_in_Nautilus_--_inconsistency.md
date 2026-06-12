---
title: "SFTP bookmark in Nautilus -- inconsistency"
date: 2018-08-30
forum: General Help
---

### Post by Roasted on 2018-08-30
Hi friends. I'm tinkering with SFTP at the moment and noticed something. 

Some quick context:
Hostname of server is 'vault'
Data is located at /mnt/vault

As such my path to connect is sftp://vault/mnt/vault

I bookmarked that in Nautilus for quick access. The bookmark itself works well. The strange thing is once it's mounted, it seems to alter the path of the mounted entry. As you can see in the picture, it changes to sftp://vault/home/jason when hovering over the mounted entry on the sidebar. Yet if I hover over the actual entry I use to connect (Home Server SSH), it yields the correct path. Also attached is my bookmarks file.

Anybody have any idea why this mounted path flips when mounted?

[https://i.imgur.com/UVMAZhl.png]("https://i.imgur.com/UVMAZhl.png")

---

### Post by Roasted on 2018-08-30
This is a bit of a janky workaround, but to make it more tolerable I made a symlink that resides in my home directory on the server via "ln -s /mnt/vault vault". Thus when I go to the already-mounted-entry of the SFTP share to my server on the left side of Nautilus, I at least see this:

[https://i.imgur.com/LIPt0z0.png](https://i.imgur.com/LIPt0z0.png)

Sure, takes an extra click, but it's not much to sneeze at. Would still be interested as to why this takes place or if anyone has any other ideas.

---

