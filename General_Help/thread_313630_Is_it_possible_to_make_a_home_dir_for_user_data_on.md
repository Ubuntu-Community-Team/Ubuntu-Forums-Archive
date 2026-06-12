---
title: "Is it possible to make a /home dir for user data only in 6.10"
date: 2006-12-06
forum: General Help
---

### Post by MrEinstein on 2006-12-06
Hello
I want to separate the ./xxxxx files from the directory that the user see as his /home directory.

The goal is that an inexperienced user should not have to se all these ./xxxxxx directories and eventually delete/rename one when using the system regardless witch program he uses.

Regards

---

### Post by steve.horsley on 2006-12-06
Sorry, but I don't understand. What do you mean by "all these ./xxxxxx directories"? Users home directories are normally pretty empty apart from Desktop.

---

### Post by bscbrit on 2006-12-06
I'm not sure I understand, but are you referring to the 'hidden' files whose names all begin with a '.' e.g. .azureus or .mozilla?  If so, you do not have to see them.  Simply deselect 'Show Hidden Files (or Ctrl-H) and they disappear from view.  If I've misunderstood, can you please tell me again what you are trying to achieve?

---

### Post by strabes on 2006-12-06
Sorry for the non-answer but any file that begins with a period is hidden, meaning they should not show up in nautilus unless you have enabled showing hidden files. Press Ctrl + H to toggle showing of hidden files.

Another solution would be to make a separate (preferably ext3) data partition on your HDD and then mount it in fstab.

[edit]: man you guys are fast. got to the hidden files thing before me

---

### Post by MrEinstein on 2006-12-06
Thanks for the answers all.
What i meant was that the users users should not be able to see any hidden directories in their home dir even if they have enabled showing hidden files by mistake.

(We are trying to modify Kubuntu for use by pople with no experience in Linux.)

Regards

---

### Post by bscbrit on 2006-12-06
No, there is no simple way to do what you want.  The OS must have somewhere to store user-specific data and it uses hidden files in each users' area for this purpose.  Making them read-only will also not help protect your users - if they cannot be written to then the programs that want to use them will not work correctly.  I suppose you could find some way of disabling the Ctrl-H / Show Hidden Files options so at least users are not aware that the hidden files even exist but nothing will stop them from deleting a hidden file/directory if they insist on doing so.  

An alternative strategy might be to make a backup of a correctly configured user area and give each user an icon that will allow them to restore that backup and their defaults if they _do_ make a mistake at sometime.

---

### Post by MrEinstein on 2006-12-06
Thank´s for the tip.
I will try to make a script that copies a std config.

Is it possible to make a dir structure as follows:
~.mozilla              dr-x------
~.mozilla/firefox      drwx------
~.mozilla/thunderbird  drwx------
etc.
The idea would be that the user can´t delete the directories that he/she can see at the first level in his/her home directory.

regards

---

### Post by bscbrit on 2006-12-06
In theory your suggestion should work, but in practice you need to try it.  Some programs will probably accept it and others will not.  I suggest that you create a test user on your system and then change the attributes on each hidden directory as you have proposed.  Back it up to another area just that  you can restore it again if the subsequent testing breaks it. Use the system for a day or two and see what problems, if any, you have.  If everything seems to work, then try to break it in the same way that an inexperienced user might do by accident. Try deleting things etc.  You will always be able to quickly recover by restoring your back up, which will allow you time to develop a quick script that will do the same thing for your users. :-D

---

### Post by MrEinstein on 2006-12-07
Thank you for the advice, i will try to make it work.

Regards

---

### Post by mvaniersel on 2006-12-07
On a side note, I think it would be great if all configuration dot-files were stored in their own special subdirectory.

For example, /home/username/.mozilla would become /home/username/.settings/mozilla

It would clean up the home directory considerably, and I often browse my home directory from windows XP using ext2ifs, and then there is no way to hide dot-files. Also, this would allow you to set .settings read-only, as proposed above, to prevent accidental deletion.

But I guess this requires modifying a large number of programs.

---

