---
title: "automatic group ownerhsip"
date: 2008-04-16
forum: General Help
---

### Post by whaley on 2008-04-16
Greetings!

Question regarding setting group permissions.  Hypothetically, if I have a directory at /var/foo that is owned by the group bar, how can I make it so that all directories and files created undearneath /var/foo also have a group owner of bar?  It looks as though all files/directories created will always receive user:user ownership of the user that created them (e.g. whaley:whaley and not whaley:bar).      

How can I make it so the ownership is always user:bar?  Is this even possible? 

I want to accomplish this without manually using chgrp -R.  

Thanks in advance :)

---

### Post by carrett on 2008-04-16
A quick googling does not bode well: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/635762.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/635762.html)

---

### Post by whaley on 2008-04-16
Turns out my google-fu was weak, but yours was slightly stronger, but not quite strong enough.  From the link you pasted, I found a link within that page that was relevant: [http://www.linuxjournal.com/article/7727]("http://www.linuxjournal.com/article/7727")

From the article:

> setgid and Directories

What about directories? Well, setuid has no effect on directories, but setgid does, and it's a little non-intuitive. Normally, when you create a file, it's automatically owned by your user ID and your (primary) group ID. For example, if biff creates a file, the file has a user owner of biff and a group owner of drummers, assuming that drummers is biff's primary group, as listed in /etc/passwd.

Setting a directory's setgid bit, however, causes any file created in that directory to inherit the directory's group owner. This is useful if users on your system tend to belong to secondary groups and routinely create files that need to be shared with other members of those groups. For example, if the user animal is listed in /etc/group as being a secondary member of drummers but is listed in /etc/passwd has having a primary group of muppets, then animal has no trouble creating files in the extreme_casseroles/ directory, whose permissions are set to drwxrwx--T. However, by default, animal's files belong to the group muppets, not to drummers, so unless animal manually reassigns his files' group ownership (chgrp drummers newfile) or resets their other permissions (chmod o+rw newfile), other members of drummers cannot read or write animal's recipes.

If, on the other hand, biff or root sets the setgid bit on extreme_casseroles/ (chmod g+s extreme_casseroles), when animal creates a new file therein, the file has a group owner of drummers, exactly like extreme_casseroles/ itself. All other permissions still apply; if the directory in question isn't group-writable to begin with, the setgid bit has no effect, because group members are not able to create files inside it. 

So to do this I ran the following command from /var/foo

```
find . -type d | xargs chmod 2775 
``` 

The permissions were previously just 775 for all directories (or rwxrwxr-w for those who don't grok the octal version).  Just adding the leading 2 to indicate the setgid be set does what I need.

Thanks mon! :)

---

