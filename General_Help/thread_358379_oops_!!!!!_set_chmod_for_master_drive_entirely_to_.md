---
title: "oops !!!!! set chmod for master drive entirely to 777"
date: 2007-02-10
forum: General Help
---

### Post by darweth on 2007-02-10
I was fixing Nvidia binary blobs for the kernel updates from a live disc.  I wanted to be able to overwrite a xorg so I decided to set 777 permissions.  The problem is I STUPIDLY set the entire drive to 777.  I did a sudo chmod -R 777 /media/ext instead of in just /media/ext/etc or LOWER.  How dumb can I get?!?!?  lol.

Upon logging into Gnome now, I get a "User's $Home/.dmrc file is being ignored. This prevents the default session from being saved. File should be owned by user and have 644 permissions. User's $Home directory must be owned by user and not writable by other users." Uh oh. I could not access the net or do anything in Gnome.

Any sudo terminal command brought a sudo: must be setuid root error. Help!


How do I restore the proper permissions for everything?  Proper Home permissions?  And make sure everything that should be read-only is set back to that.

---

### Post by darweth on 2007-02-10
Please someone help.  I am trying to fix this from a live disc.  Was setting my entire master drive to 777 the kiss of death?  Will I have to reinstall?  HELP.

---

### Post by Maestro23 on 2007-02-10
Ran a keyword search for that error. Found this thread. Might help or put you on the right path.

[http://www.ubuntuforums.org/showthread.php?t=353930&highlight=User%27s+%24Home%2F.dmrc+file+is+being+ignored](http://www.ubuntuforums.org/showthread.php?t=353930&highlight=User%27s+%24Home%2F.dmrc+file+is+being+ignored)

---

### Post by bettlebrox on 2007-02-10
It going to be near impossible to fix permissions on all the files, easier thing to do is to backup /home, unless it's on a seperate partition and reinstall.

What you could try and do is start aptitude or synaptics and reinstall all the software, that might fix permissions on most of the system files, but probably not on the parent directories. For each user's home directory you can just recursively chown each user's home directory.

---

### Post by darweth on 2007-02-10
Thanks for the help.  I have in fact decided to backup and reinstall.  :P  I suppose everyone has to cripple their Linux box ONCE in a lifetime.

---

### Post by bettlebrox on 2007-02-12
> **darweth said:**
> Thanks for the help.  I have in fact decided to backup and reinstall.  :P  I suppose everyone has to cripple their Linux box ONCE in a lifetime.
Your right! :) gotta make mistakes to learn! ;)

---

