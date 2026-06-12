---
title: "Mailman and Virtual Domain Help"
date: 2007-12-30
forum: General Help
---

### Post by koltz on 2007-12-30
I am running 7.10 server and needed to install Mailman.  I followed the directions as posted on Ubuntu's site, but have one problem.  I have the Mailman virtual domain pointed to lists.example.com for the website, but when I click to add a user, it goes to server.example.com.  I have been searching for where I need to change this setting, but no luck yet.  Any help would be greatly appreciated.

Thanks,

Corey

---

### Post by yanny on 2008-01-19
I'm not quite sure if I can help you, though I've got the similar problem and fixed it. 

I have added my virtual domain in etc/hosts. Maybe you should add lists.example.com behind 127.0.0.1, so that it looks like:


127.0.0.1       localhost lists.example.com

---

