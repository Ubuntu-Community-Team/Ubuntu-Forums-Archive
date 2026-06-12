---
title: "Automatically change ownership to plex:plex when copying to Plex folder?"
date: 2020-10-10
forum: General Help
---

### Post by thatotherguy2 on 2020-10-10
Plex used to be much easier to set up. Lately it seems to have permission issues with Ubuntu.

Following various online advice to get plex working on Ubuntu, I mounted my plex drive (ext4) in /opt so the "Plex" folder (and everything inside it) within can be owned by user plex: as their instructions describe. 

So, now /opt/HD/Plex is owned by the plex user and group, plex:. The only way I was able to even copy files into the folders is to add my user to the plex group and give the group write permission.

Finally, Plex works again and I can add videos to it. 

But, every time I copy anything into the Plex directory, the permissions need to be changed to plex:.  This is tedious and annoying when I forget to update the permissions.

First, is this even the right way to set up something like Plex that needs it's user to own everything it plays?

And, if so, is there any way to have Ubuntu automatically change the permissions to match the folder into which they are being copied at the time they are copied? 

Thank you

---

### Post by TheFu on 2020-10-11
**chmod g+s** on every directory you want new files and subdirectories to retain the current group with. This is called the group-set-gid-bit or permission.

>  First, is this even the right way to set up something like Plex that needs it's user to own everything it plays?
Yes. This is correct, but I'd be the owner of all files and directories, not plex.  Ownership means control that just being a member of the group doesn't provide.

The command that I would use to set this on all directories under /opt/HD/Plex is:
```

drwxrw[COLOR="#FF0000"]s[/COLOR]r-x 1303 tf   plex 61440 Oct  4 18:57 M/
drwxrwsr-x  102 tf   plex  4096 Sep 28 17:24 T/
drwxrwsr-x    4 tf   plex  4096 Aug 23  2017 V/
drwxrwsr-x    4 tf   plex  4096 Aug 23  2017 Music/

```
M is for Movies, T for TV, V for home videos, Music ... er ... 
Because 'tf' is the owner, chmod doesn't need any sudo to accomplish.
Steps:
```
sudo chown -R tf /opt/HD/Plex   # Take ownership of all media files
chgrp -R plex /opt/HD/Plex    # Ensure all files are in the plex group
find /opt/HD/Plex -type f chmod 664 {} \;   # Fix all files
find /opt/HD/Plex -type d chmod 775 {} \;   # Fix all directories
find /opt/HD/Plex -type d chmod g+s {} \;   # Fix all directories
```

From this point on, any newly added files or directories under /opt/HD/Plex/ will have the correct group and retain the setgid permission on each directory. You'll not need to do this again.  To any later lurkers, note that the OP had already added his user to the "plex" group. Without that, this will-not-work.

---

### Post by Morbius1 on 2020-10-11
Just out of curiosity is this not a viable alternative: [https://forums.plex.tv/t/proper-way-to-run-plex-as-another-user-with-systemd-ubuntu-server-16-04-lts/158853/2](https://forums.plex.tv/t/proper-way-to-run-plex-as-another-user-with-systemd-ubuntu-server-16-04-lts/158853/2)

... replace the user plex runs as from plex to you.

---

### Post by TheFu on 2020-10-11
Perhaps, but there could be some issues. I can think of multiple problems, depending on the workflows and tools involved.
[LIST]
[*]TV recording systems often run under a daemon account
[*]media downloading systems often run under a daemon account
[*]inotify tasks
[*]may desire read-only access by plex
[*]may desire read-write access by plex
[/LIST]

There are lots of different solutions possible, just depends on the desired outcome.

---

### Post by HermanAB on 2020-10-12
As shown above, the 'sticky bit' can force the user and group for you.

---

### Post by TheFu on 2020-10-12
From the chmod manpage:
```
SETUID AND SETGID BITS
       chmod clears the set-group-ID bit of a regular file if the file's group
       ID  does  not  match the user's effective group ID or one of the user's
       supplementary group IDs, unless the user  has  appropriate  privileges.
       Additional restrictions may cause the set-user-ID and **set-group-ID** bits
       of MODE or RFILE to be ignored.  This behavior depends  on  the  policy
       and  functionality of the underlying chmod system call.  When in doubt,
       check the underlying system behavior.

       For directories chmod preserves set-user-ID and **set-group-ID**  bits  un&#8208;
       less  you  explicitly specify otherwise.  You can set or clear the bits
       with symbolic modes like u+s and g-s.  To clear these bits for directo&#8208;
       ries  with a numeric mode requires an additional leading zero, or lead&#8208;
       ing = like 00755 , or =755

RESTRICTED DELETION FLAG OR STICKY BIT
       The **restricted deletion flag** or sticky bit is a single bit,  whose  in&#8208;
       terpretation  depends  on  the file type.  For directories, it prevents
       unprivileged users from removing or renaming a file  in  the  directory
       unless  they  own  the  file  or  the directory; this is called the re&#8208;
       stricted deletion flag for the directory,  and  is  [U]commonly  found  on
       world-writable  directories like /tmp[/U].  For regular files on some older
       systems, the bit saves the program's text image on the swap  device  so
       it will load more quickly when run; this is called the sticky bit.
```

People have been confusing "the sticky bit" with the "set-group-id" bit for 40+ yrs.

---

### Post by thatotherguy2 on 2020-10-14
> Yes. This is correct, but I'd be the owner of all files and  directories, not plex.  Ownership means control that just being a member  of the group doesn't provide.

Thank you. And, that's actually what I hoped to hear! It seemed odd for the user plex to be the owner.

> **chmod g+s** on every directory you want new files and  subdirectories to retain the current group with. This is called the  group-set-gid-bit or permission.

I had done this. But, it didn't seem to work. Maybe that had something to do with me not being the owner, if I understand what you posted from the chmod manpage. 

> 
Code:
sudo chown -R tf /opt/HD/Plex   # Take ownership of all media files
chgrp -R plex /opt/HD/Plex    # Ensure all files are in the plex group
find /opt/HD/Plex -type f chmod 664 {} \;   # Fix all files
find /opt/HD/Plex -type d chmod 775 {} \;   # Fix all directories
find /opt/HD/Plex -type d chmod g+s {} \;   # Fix all directories


When I got to the #Fix all files and directories section it threw and error. I looked it up and tried adding -exec like:

```
find /opt/HD/Plex -type f -exec chmod 644 {} \;
```

It seems to have worked.

> drwxrwsr-x 1303 tf   plex 61440 Oct  4 18:57 M/
drwxrwsr-x  102 tf   plex  4096 Sep 28 17:24 T/
drwxrwsr-x    4 tf   plex  4096 Aug 23  2017 V/
drwxrwsr-x    4 tf   plex  4096 Aug 23  2017 Music/

This is an example, right? Not code to type in? It looks like some output of permissions settings. I understand it shows the user as tf and the group as plex. But, I'm not sure what those numbers are or what the dates mean. Probably just extra output from whatever command produced this?

Or, do I have to set that drwxrwsr-x stuff on the folders myself?

Thanks

---

### Post by thatotherguy2 on 2020-10-14
Well, it works! So...    Thank You TheFu!!!

Plex still plays across devices AND when I copy files to the plex folder the group permissions automatically change to match. Absolutely perfect. Thank you.

---

### Post by TheFu on 2020-10-14
tf = thefu

That's my login on my plex server, sorry it wasn't clear.  If others blindly copy/pasted those lines without changing things, it will be bad. You need to fix the first command for your userid.  Many of the directories and files were probably fine, but that first command is required for all the others to actually work completely, recursively. Those commands won't harm any files already correct - that are for plex and stored in the area you've shown.  Don't do those commands in any other directories. That's a good way to a broken system.

I'm a little nervous that you don't understand the table with permissions and directories - **ls -laF** is the command to make that. It is very handy output. You should learn that stuff ASAP, since it is core to all Unix security across every platform. There's no way to skip this.  Just spend the 30 minutes and learn it.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a basic Linux book that has a chapter on users, groups and another chapter on permissions.
help.Ubuntu.com has permissions primer. I'd start there, but until you actually setup 3 userids with 4+ groups, in 3 different terminal windows and start typing chmod/chgrp/chown commands to see the impacts, you'll never actually learn it. The GUI doesn't help with these concepts. In fact, I'd say GUIs get in the way.

---

### Post by thatotherguy2 on 2020-10-18
> **TheFu said:**
> tf = thefu

That's my login on my plex server, sorry it wasn't clear.  If others blindly copy/pasted those lines without changing things, it will be bad. You need to fix the first command for your userid.  Many of the directories and files were probably fine, but that first command is required for all the others to actually work completely, recursively. Those commands won't harm any files already correct - that are for plex and stored in the area you've shown.  Don't do those commands in any other directories. That's a good way to a broken system.

I'm a little nervous that you don't understand the table with permissions and directories - **ls -laF** is the command to make that. It is very handy output. You should learn that stuff ASAP, since it is core to all Unix security across every platform. There's no way to skip this.  Just spend the 30 minutes and learn it.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a basic Linux book that has a chapter on users, groups and another chapter on permissions.
help.Ubuntu.com has permissions primer. I'd start there, but until you actually setup 3 userids with 4+ groups, in 3 different terminal windows and start typing chmod/chgrp/chown commands to see the impacts, you'll never actually learn it. The GUI doesn't help with these concepts. In fact, I'd say GUIs get in the way.

Thanks. Sorry if I sounded like an dingbat. I mostly understand permissions. I just still find lots of commands hard to memorize, especially stuff I don't use everyday. I'll definitely take the time to brush up though. Thanks for the link.

Of course I changed the owner to my username when I used the commands. Thanks for those. All I really needed to know was that I could change the owner to my username instead of plex and they'd still work. And, I knew enough to recognize output when I saw it and not try to type it in. I just thought I'd ask. Yay, I was right. 

Thanks again for your help. This plex thing has been a huge PITA for awhile. :D My kids are thrilled that plex is back.

---

### Post by ajgreeny on 2020-10-19
Brilliant!

Can you now please mark this thread as **SOLVED** from the Thread Tools menu at the top; its a great help to other forum users searching for answers.

---

### Post by kevdog on 2020-10-19
@TheFu 


Excellent demonstration and explanation.  I have to say I'm guilty sometimes for forgetting the purpose of the sticky bit.  I just don't use it all that often.  I you could give followup tutorial on smb permissions (acls) that would be great!! (jk but not really, those are even more cumbersome)

---

