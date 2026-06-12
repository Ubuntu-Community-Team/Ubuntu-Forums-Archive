---
title: "Moving Home"
date: 2008-02-13
forum: General Help
---

### Post by Robbyx on 2008-02-13
I propose to move my home directory to an ntfs format rade drive. The faq I have seen talks of ext3 format but  I assume that is not essential.

I am told that moving the home directory will make the new installation of Gutsy much easier and quicker. Why should it be quicker if I am forced to reinstall every change I made to fiesty?
 
Included in the home directory are a number of hidden directories starting with dot. They are all relate to programs that I have installed.

 If I move the home directory to a new location and then install a fresh copy of Gutsy, I assume alll those programs will not work? How does moving the home directory help with a new install?

As you can guess this all relates to a failed upgrade to Gutsy.

---

### Post by Crooksey on 2008-02-13
I would strongly not reccmomend to place /home on an ntfs partion, STRONGLY.

The linux kernel cannot natively write to ntfs partions, or work great with this filesystem.

I would use either ext3, reiserfs or xfs as the filesystem for your new /home.

Having your home directory on a diferent partion will allow you to keep most of your program settings and themes, aswell as keeping all your personal files. I have had the same /home partition for years, even if you change distro you can keep the same /home.

---

### Post by Robbyx on 2008-02-13
> **Crooksey said:**
> I would strongly not reccmomend to place /home on an ntfs partion, STRONGLY.

The linux kernel cannot natively write to ntfs partions, or work great with this filesystem.

I would use either ext3, reiserfs or xfs as the filesystem for your new /home.

Having your home directory on a diferent partion will allow you to keep most of your program settings and themes, aswell as keeping all your personal files. I have had the same /home partition for years, even if you change distro you can keep the same /home.

Thank you for the warning. How do all those dot files get used in a new installation? I assume I will have to reinstall the various programs and if there is a dot file with settings it will not over write it. Am I correct in assuming that I even with a retained home I will have to do the re installations?

---

### Post by Crooksey on 2008-02-13
Yes, re installations will be needed, but program history and settings are saved in the ~/.<filename> area. 

Think of home as your "My Documents", you dont need to back it up and replace on every install, just leave the partition unformatted.

---

