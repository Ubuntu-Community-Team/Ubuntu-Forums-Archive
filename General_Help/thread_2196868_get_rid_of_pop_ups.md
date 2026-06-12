---
title: "get rid of pop ups"
date: 2013-12-31
forum: General Help
---

### Post by trav9595 on 2013-12-31
I have ad block but some unwanted pop up sutff still loads onto my desktop sometimes where it I cant see it until I close out my browser.
Meanwhile it uses up my limited monthly 5 gigabytes.How do you block any pop ups from doing this??

---

### Post by JKyleOKC on 2014-01-01
There's not much way to keep these things from using up your limited transfer allowance, since they have to be downloaded before any blocker can identify them and prevent them from being shown.

However if you can identify the sites from which they are coming, by name, it's possible to add those site names to your /etc/hosts file with an address of 127.0.0.1 which will prevent anything at that site, including the pop-ups, from loading at all; that will save your transfer quota. This may be a cure that's worse than the problem, though, since it prevents **everything** at that site from being found. It also will slow your browser down significantly when visiting any site that attempts to load the pop-ups, since it will wait for the access attempt to time out before moving on to the next line of the original site's script.

---

### Post by vasa1 on 2014-01-01
> **trav9595 said:**
> I have ad block but some unwanted pop up sutff still loads onto my desktop sometimes where it I cant see it until I close out my browser.
Meanwhile it uses up my limited monthly 5 gigabytes.How do you block any pop ups from doing this??

I very much doubt that pop-ups, no matter how many, can use up your 5 GB.

If you want to block pop-ups, you'll have to provide more information.

---

### Post by coldraven on 2014-01-01
I use Firefox with Adblock Plus, NoScript and Ghostery and I do not get pop-ups. In Ghostery **everything** is blocked! (OK I unblocked Discus to see comments) 
For added privacy I also have RefControl and Betterprivacy installed

---

