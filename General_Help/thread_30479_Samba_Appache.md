---
title: "Samba? Appache?"
date: 2005-04-28
forum: General Help
---

### Post by dfghost on 2005-04-28
Wich one is better, Samba or Appache2?  I have both installed, but have no clue how to use them.  Could someone point me to a tut or give me some basics?  Thanks in advance.

---

### Post by Sam on 2005-04-29
They are both completly different. Samba is intended for sharing and browsing windows network, and Apache is a web server for hosting web sites.

What are your needs ?

---

### Post by shakin on 2005-04-29
[QUOTE=dfghost]Wich one is better, Samba or Appache2?  I have both installed, but have no clue how to use them.  Could someone point me to a tut or give me some basics?  Thanks in advance.[/QUOTE]

Do use Apache 2 point your browser at [http://localhost](http://localhost)

Now drop your files into /var/www to see them on your web server. Use a tool like NVU to develop web pages.

To use Samba, find the System / Administration / Shared Folders and you can setup network shares for other computers to attach to. To attach to other computers' shares, go to Places / Network Servers and browse the network to find the share you want.

---

