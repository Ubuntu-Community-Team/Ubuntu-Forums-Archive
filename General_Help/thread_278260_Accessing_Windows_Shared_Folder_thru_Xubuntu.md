---
title: "Accessing Windows Shared Folder thru Xubuntu"
date: 2006-10-16
forum: General Help
---

### Post by textguru on 2006-10-16
I need to access windows shared folder from xubuntu desktop. Hope you could help me. In ubuntu, there is an option from the dropdown menu but on xubuntu it doesn't have. Hope you can help.

---

### Post by textguru on 2006-10-17
Hey guys,

Need this badly. I need to transfer files from xubuntu to windows shared folder.

---

### Post by anaconda on 2006-10-17
> In ubuntu, there is an option from the dropdown menu
what do you mean by that?

if I understand correctly that means that in ubuntu you had your windows shared folder mounted already(that is why it is in the places menu), and in xubuntu you don't have it mounted.

You just need to mount your share, and copy the files..

here is a link for you.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by textguru on 2006-10-17
What I mean was this, I wanted to access Windows Shared folders from the network file server. In ubuntu, there is a dropdown menu Places and there you have Connect to (Remote) Server...

How about on Xubuntu? how can I connect to remote server especially on Windows server share?

---

### Post by hvc123 on 2006-10-17
i never use the GUI,

install samba and run gnome-terminal

mkdir [whateveryoulike]

smbmount //[ipaddressoftarget/sharename /newdiryoumadeearlier

done, as long as you have permissions

---

### Post by D10 on 2006-10-17
If you want a gui install Linneighborhood.

---

### Post by textguru on 2006-10-17
> **D10 said:**
> If you want a gui install Linneighborhood.

How to install Linneighborhood?:confused:

---

### Post by textguru on 2006-10-17
> **hvc123 said:**
> i never use the GUI,

install samba and run gnome-terminal

mkdir [whateveryoulike]

smbmount //[ipaddressoftarget/sharename /newdiryoumadeearlier

done, as long as you have permissions

Do I really need to install samba? As far as I know, I need to install samba if I need to share a directory to any windows users.

---

### Post by Iowan on 2006-10-17
You'll probably need **smbfs** and **smbclient**.  I think they come on Ubuntu - but I couldn't say about Xubuntu

---

### Post by MacHaddock on 2007-10-31
> **textguru said:**
> What I mean was this, I wanted to access Windows Shared folders from the network file server. In ubuntu, there is a dropdown menu Places and there you have Connect to (Remote) Server...

How about on Xubuntu? how can I connect to remote server especially on Windows server share?

Yes I would love to know this to. Is there a way to got that menu in xubuntu perhaps?

---

