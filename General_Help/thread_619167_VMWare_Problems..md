---
title: "VMWare Problems."
date: 2007-11-21
forum: General Help
---

### Post by chrispche on 2007-11-21
--
chrispche@chrispche-desktop:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
Unable to alloc client: Cannot open file "/home/chrispche/.vmware/preferences": Permission denied.



VMware Server Error:
VMware Server unrecoverable error: (vmui)
Unable to alloc client: Cannot open file "/home/chrispche/.vmware/preferences": Permission denied.

A log file is available in "/tmp/vmware-chrispche/ui-7085.log".  Please request support and include the contents of the log file.  
To collect files to submit to VMware support, run vm-support.
We will respond on the basis of your support entitlement.
--

This is what I get when I try to run VMWare as the user chrispche. If I sudo vmware I can run it fine. Any idea whats going on?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
Hi, chrispche

Change the permission of the folder and file will fix that.
This command will change owner of the directories and files under to your user.

```

sudo chown chrispche:chrispche -R /home/chrispche/.vmware/

```

And you will be able to run vmware without sudo.

---

### Post by chrispche on 2007-11-21
Sorry explain what just happened there? Thank you it worked. But what did it all mean?

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
I had this problem sometime ago.

```

Unable to alloc client: Cannot open file "/home/chrispche/.vmware/preferences": Permission denied.

```
This line means that you don't have the permission to open the "preferences" file.
I don't know exactly why this happened, but I think it happened the first time I opened vmware, maybe some bug in the installer, but I'm not sure though.

The .vmware folder somehow assigned to user root, so basically, the command I gave to you, is to change the permission of that folder and all the files inside to be owned by you, since it's located in your "home" directory, it should owned by you.

---

### Post by chrispche on 2007-11-21
I see, where might you suggest I learn about such things? Is that huge tome the official Ubuntu book a good investment?

---

### Post by dabl on 2007-11-21
> **chrispche said:**
> Is that huge tome the official Ubuntu book a good investment?

NO, but *Beginning Ubuntu Linux* by Keir Thomas _is_ a good investment, IMHO.  :)

---

### Post by Milk &amp; Toast &amp; Honey on 2007-11-21
Actually, I never really read something like books / bible for linux yet, so I can't suggest any book to read.
I learn this by doing, I do read some tutorial (part-by-part) in internet, but I can't remember the links.

If you read books that specifically for Ubuntu, I *think* most part of the book will cover only Ubuntu distro specifically.
But if you really want to learn linux in common usage, I suggest you read the books that don't have *any distro name* in their cover.

Also, I learn a lot from the "man" command.
```

man <program_name>

```
For example, you can try
```

man chown

```
to see the "manual" or description of what the "chown" command / program does.

---

