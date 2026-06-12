---
title: "Duplicity was not invited"
date: 2021-05-16
forum: General Help
---

### Post by jeffmorasco on 2021-05-16
I have been on Ubuntu 18.04 and decided to upgrade to 20.04. I had several desktop folders and copied those to an external hard drive in a folder called Linux desktop. Yesterday I restored several of those folders. Today I was going to restore the rest and now find that everything in the folder Linux Desktop is a duplicity-inc file. I never installed duplicity and never ran it. The other folders on that external disk appear fine.
Is this a virus of some sort? Is duplicity included automatically in 20.04 and would it then run automatically? Most importantly how can I recover my data and prevent it from happening again?
Thanks in advance for your help.
Jeff

---

### Post by grahammechanical on 2021-05-16
Ubuntu comes with a backup utility installed. I am not familiar with it but I guess that it can be configured to run periodically. It is called Déjà Dup Backup Tool in Ubuntu Software. You can loaded from Ubuntu Software or by opening Activities and searching for Utilities. In that folder is an application called Backup.

A Psychologyst once told me that everything happens for a reason. I believe him. With computer operating systems it sometimes seems as if things happen without our initiating the action. I do not believe that Linux is that intelligent. I have never experienced the behaviour from Backup that you are experiencing.

Regards

---

### Post by deadflowr on 2021-05-16
duplicity is the backend for deja-dup.
It's what actually does the backup and restore.
deja-dup is Ubuntu's default backup utility.

---

### Post by jeffmorasco on 2021-05-16
I tried using Restore and it asked for a Password. It didn't respond to my user/su password. I also tried Admin, as a guess. That  didn't work either. Since I didn't initiate the backup, I have no idea what other  pw to use.

---

### Post by deadflowr on 2021-05-16
You would have set a unique password for it during the initial backup.
It would be unrelated to any admin or login passwords.

---

### Post by jeffmorasco on 2021-05-16
I tried using Restore after your comment above. I never did an intentional backup. I never set any password. I merely copied the multiple desktop folders to an external USB 2 T drive. Now  the folder I copied them all to, has nothing but duplicity-full files. The folder I copied them to was labeled Linux Desktop. There is no longer a folder with that name.There is a new folder labeled with my old pseudonym-desktop. 
I was wondering if this could be the work of a virus as several things happened that were not commands I had given.
Does Duplicity have a default password, as I could always try that?

---

