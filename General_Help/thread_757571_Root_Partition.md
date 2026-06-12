---
title: "Root Partition"
date: 2008-04-17
forum: General Help
---

### Post by xaocan on 2008-04-17
A lil problem - I've got a partition that is mounted as a root partition(the owned is root) its read only for my user. How do i change the partition accessibility?

---

### Post by EvilDarkElf on 2008-04-17
Have you tried:

   [FONT="Courier New"]sudo chmod -R u=rwx path_to_folder[/FONT]

? Sudo gives you root control (it will ask for your password - that's your user's password). chmod changes file access permisions. Be carefull of using the above line, it gives read write and execute access to all users. To find out how to give it to only your user:

   [FONT="Courier New"]man chmod[/FONT]

I'm sorry if you know all this, I'm not trying to insult your intelligence, I just remember how clueless I used to be

---

### Post by mcduck on 2008-04-17
**You shouldn't change the permissions of the root partition. That _will_ break your system.**

Directories in Linux have certain permissions for a reason. Unless you are absolutely sure that you know what you are doing and what consequences it has, you shouldn't ever change them.

Users have read/write access to their own home directories, and that's where you should keep all your personal files.

If you, for some reason, really need write access to directories outside your home the correct way is not to change permissions of those directories, but instead change your own permissions, by using the 'sudo' command to run commands and programs with root privileges.

The easiest way to do this would be to just hit Alt-F2 and run the command "gksudo nautilus" to open the file manager as root user. This will give you full access to every directory and file on your system, but as it also allows you to break your system you should be really careful using it, and always remember to close the root nautilus window as soon as you do not need it any more.

edit: I read your post again, and I realized that you might not really be talking about a root partition, but instead of some extra partition that is just mounted with root privileges only? In that case, depending on what file system that partition is formatted to, you can configure the correct permissions for it in the /etc/fstab file.

---

### Post by xaocan on 2008-04-17
it didn't work but it was kinda useful thing for me to know =). I experimented with chmod but the only response i got from it was>  mode of `/dev/sda7' retained as 0777 (rwxrwxrwx)
 

what does that mean? =) any other suggestions?

PS the edit was right - it's not park of my system its just an empty partition that is formated as ext3. what exactly should i change in the  /etc/fstab file? this is that it writes about the partition that i want to use :
> UUID=711ec6cd-3dae-4c2c-b5f6-a126d624e835 /media/sda7     ext3    defaults        0       2

---

### Post by Zorael on 2008-04-17
See [this page](http://www.joomlatutorials.com/faq/view/joomla_security_tips/joomla_and_unix_file_permissions_-_explanation/60.html) for an explanation on unix permissions. 0777 or rwxrwxrw means that *everyone* (you, your group and everyone outside your group) all have read, write, and execute permissions.

That is kind of a security breach, since then people can delete your stuff. But if you're not very strict on that, I guess that's what's easiest.


edit: And yes, don't go and change the permissions on your root mount. It's *supposed* to be write-protected so that you can only allow having changes made to it consciously, since you have to supply a password for programs to get superuser privileges (which makes it writable). Else it'd be no different from l0sedows; any malicious code would be able to wipe out crucial files and your system would be hosed.

---

### Post by xaocan on 2008-04-17
That's nice that I've got read, write and execute permissions- that was the idea. The only reason why I wrote the previous post is that I still can't read, write and execute...

---

