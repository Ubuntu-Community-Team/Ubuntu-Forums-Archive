---
title: "Kmail in gnome POP email problems"
date: 2006-11-13
forum: General Help
---

### Post by threethirty on 2006-11-13
I'm trying to run Kontact in Edgy (GMONE) so that I can get my mail on my pda.  When I try and get my pop email I get this error

```
Could not start process pop3
```

any ideas?

---

### Post by rusyear04 on 2006-11-17
me too.
same thing as described above... no clue what the problem is.

---

### Post by twrock on 2006-11-19
While you are awaiting an answer to your question, may I ask a question of you? 

I prefer Gnome for my desktop, but I would like to use Kontact as a PIM and hotsync with my Palm TX pda. Is that even possible? Or will I need to use KDE instead (Kubuntu)?

Thanks.

(My apologies for hijacking your thread, but I thought that at least here were two people who have used Kmail in Gnome.)

---

### Post by bitzbox on 2006-11-19
You need to install kdebase-kio-plugins then it should work.

Martin

---

### Post by twrock on 2006-11-19
> **bitzbox said:**
> You need to install kdebase-kio-plugins then it should work.

Martin

Martin, was that answer to the original problem posted or to what I asked? (Sorry, I'm a bit dense sometimes.)

---

### Post by bitzbox on 2006-11-19
It was my answer to the original question about the POP3 error.

Martin

---

### Post by t_kiesel on 2006-11-20
HI

I have the same problems. Am new on ubuntu and just switched from suse, so don't really know yet how things work. 
I only find the following link (packages.ubuntulinux.org/edgy/kde/kdebase-kio-plugins) to download the packages, but can't open them. 
Whereelse can I download the file? How do I integrate it?

and another problem I came across: 
I safed all my folders and emails from suse kmail on a hard drive and tried to copy/paste them in the local folders of the new kmail in ubuntu. However, Kmail is not displaying the old emails. Now I found out that the old emails have the MIME Typ "message/rfc822" and the old ones the MIME Typ "text/plain". How can I change them so that Kmail can read them?

Thank you, Timo

---

### Post by bitzbox on 2006-11-20
> **t_kiesel said:**
> 
I have the same problems. Am new on ubuntu and just switched from suse, so don't really know yet how things work. 
I only find the following link (packages.ubuntulinux.org/edgy/kde/kdebase-kio-plugins) to download the packages, but can't open them. 
Whereelse can I download the file? How do I integrate it?

The best way to install packages is to use Synaptic which can be found by selecting "System/Administration/Synaptic Package Manager" from your desktop. 
Synaptic will automatically download, install and configure packages for you without all the hassle of trying to do things manually yourself. Once you've fired up Synaptic, just search for "kdebase-kio-plugins" and when Synaptic finds it, mark the package for installaion and Synaptic will do the rest.

As for your other problem, I'm sorry but I can't help with that. Hopefully, someone else will be able to help.

Martin

---

