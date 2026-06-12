---
title: "Laptop Repair - HUGE SECURITY RISK"
date: 2022-12-15
forum: General Help
---

### Post by brett-h-l on 2022-12-15
I have to take my laptop in to a local tech shop for repair.  I am concerned about data security.  My home partition is NOT encrypted.  I created a "technician" user account with admin privileges but when I login to the "technician" account I can view all files and folders on my account?  This is stupid.  This is a security flaw.  What can I do?  The technician will require admin privileges but my data will be exposed.

Edit:
Okay, I realized that I can change my home directory "others" access permission to "none".  This should be set to none by default.  What were they thinking?

Edit Again:
This will not work.  A "tech" account with admin privileges would simply change my account "others" access permission back to "access files" using sudo.

---

### Post by Tadaen_Sylvermane on 2022-12-15
Backup your personal files and remove them from the system. Easy. Put them back when you get the machine back. It is not a security flaw for an admin to have total access as that is the very definition of "administrator".

---

### Post by dragonfly41 on 2022-12-15
In fact instead of keeping Ubuntu inside your internal hard drive I would advocate installing Ubuntu on a separate SSD in a USB container. But the laptop requires USB 3.0 port not the slower USB 2.0 port.

My approach would be:

Purchase an SSD to replace your internal hard drive (keep that HDD for use as a future backup media in a container).

Purchase a second SSD which you can plugin to your laptop USB 3.0 port for Ubuntu usage.

Look to Crucial.com for ideas.

---

### Post by HermanAB on 2022-12-15
Err… Go to iFixit and repair the laptop yourself.

---

### Post by grahammechanical on 2022-12-15
> but when I login to the "technician" account I can view all files and  folders on my account?  This is stupid.  This is a security flaw.  What  can I do?  The technician will require admin privileges but my data will  be exposed.

It is not stupid. It is what happens when we give another user administrator privileges. What needs fixing on this laptop? Is it hardware related? If the tech needs to load the OS then set it to autoload. Why would the tech need administrator privileges? 

I do not use encryption. So, I may be wrong. But I think that if your home folder was encrypted the OS would require it to be decrypted to finish loading the desktop environment. 

Regards

---

### Post by Impavidus on 2022-12-15
You give the tech people access to repair your OS. They can do anything on your computer, or they wouldn't be able to repair it. Even if your home directory were encrypted, they could install a backdoor to access your files the next time you decrypt them. So, do you trust the tech people? If yes, no problem. Let them fix your computer. They won't steal your files. If no, fix it yourself.

If the issue is hardware related, you may get the spare parts and install them yourself. Or maybe you can remove the harddrive before handing over the laptop.

---

