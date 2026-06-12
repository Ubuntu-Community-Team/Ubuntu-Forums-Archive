---
title: "Transferring contacts list"
date: 2006-11-23
forum: General Help
---

### Post by Pepandy on 2006-11-23
I could not see a better place for this question, so please point me elsewhere if it is not suitable.

I'm trying to transfer my work from a Suse 10.0 machine (with KDE 3.4.2 level b, Kaddressbook 3.4.2) onto Kubuntu 6.06 (KDE 3.5.2, Kaddressbook 3.5)  and cannot find how to transfer the list of contacts, and I mean _all_ the information for each contact.

I've tried exporting from Suse in various formats, but all I ever see at the other side on import are the names, address, e-mails etc, but not the categories I've defined nor which categories each name is in.

Also, the distribution lists are missing. I've discovered that under Kubuntu the distributions lists are supplied by a separate package, kaddressbook-plugins, and have installed that, but I cannot even see, when I start Kontact, the pane which should show them, according to the help pages.

So two questions:

1. How do I transfer the categories and distribution lists?

2. How do I manage distribution lists under Kubuntu?

Or should I be asking this question elsewhere, like kdepim?

---

### Post by kosmic on 2006-11-23
I don't use kaddressbook, but this is what I did to transfer my evolutions contacts and emails from one computer to another.

Just see if you have a .kaddressbook folder (it is an hidden directory)

if yes just copy it to a safe place.

Then copy this folder to your new installation and it should work.

The directory should be in your Home partition :)

EDIT.: maybe the kaddressbook folder is inside the .kde3 folder

---

### Post by Pepandy on 2006-11-24
After a good bit of grep'ping, I discover that the directory I need to transfer is ~/.kde/share/apps/kabc.

That solves my particular problem as I had nothing on the target machine already. But the general case still exists where the requirement would be to merge lists.

Before I did that, I found ~/.kde/share/config/kaddressbookrc which contains the list of custom categories. I don't know whether it was necessary to copy that line as well or not as I'd done it before I found the kabc directory.

---

