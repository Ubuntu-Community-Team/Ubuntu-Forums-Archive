---
title: "Virtualbox after reinstall of Ubuntu 2022.04"
date: 2023-06-17
forum: General Help
---

### Post by cscj01 on 2023-06-17
I had a nonrecoverable failure on my filesystem disk and had to reinstall Ubuntu 2022.04.  I have backups of home directories as well as most of the pertinent system directories using Timeshift.  If I reinstall Virtualbox, can I import the VMs from the backed up directories?  If so, are there things I need to be aware of to do in addition?

---

### Post by cscj01 on 2023-06-20
Bump

---

### Post by TheFu on 2023-06-21
I don't use timeshift nor virtualbox, so I don't know how/what those tools do at a level to answer questions, but since you 'bump'ed it, I figure any reply would be better than nothing.

Try it. Does it work?

Validating a backup process is best done BEFORE it is actually needed.  For example, do you export the VMs to an OVF format as part of your backups, to make importation possible?

BTW, I can't tell if you have 22.04 as the host system or just as the VM you want back. Could you clarify? That could matter for some other issues, I'd think.

---

### Post by MAFoElffen on 2023-06-22
It should work.

Form Oracle's VirtualBox Doc's:
> 
The Machine Folder. By default, each virtual machine has a directory on your host computer where all the files of that machine are stored: the XML settings file, with a . vbox file extension, and its disk images. This is called the machine folder.

What is is each machine folder, should be everything it needs... Hopefully those were backed up right?

---

### Post by cscj01 on 2023-06-26
> **MAFoElffen said:**
> It should work.

Form Oracle's VirtualBox Doc's:

What is is each machine folder, should be everything it needs... Hopefully those were backed up right?

Yes, I'll give that a go.  I had another problem that I just got repaired, so that is why this is delayed.  I'll post and close this if all goes well.  Thanks.

---

