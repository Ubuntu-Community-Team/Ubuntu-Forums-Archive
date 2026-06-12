---
title: "Cannot Remove a User Account in Ubuntu 14.04.1"
date: 2014-09-04
forum: General Help
---

### Post by em3raldxiii on 2014-09-04
[SIZE=5]**[COLOR=#006400]SOLVED[/COLOR]**[/SIZE]

Summary:

1.  Attempted to remove a user using the User Accounts dialogue.
2.  Error message:  **[SIZE=3]> [COLOR=#800000]Cannot delete user - running '/usr/sbin/userdel' failed: Child process exited with code 16[/COLOR][/SIZE]**


3. The issue was solved with this command in a terminal:
> sudo userdel -rf [COLOR=#0000cd]username[/COLOR]

4. There was one error output, but it did not prevent the user from being deleted:  
> userdel: [COLOR=#0000cd]username[/COLOR] mail spool (/var/mail/[COLOR=#0000cd]username[/COLOR]) not found

Backstory:

After a fresh install of Ubuntu 14.04.1 where I had preserved the /home directory on another partition, I created users for my family.  I used new usernames for them so that the new install would not be gibbled up with configuration files in the old ~/ directories.  However, I accidentally used the same username for one of my children.  Upon attempting to log into that user (which I had specified no login password for when I created it), it would not log in - the screen went black for a moment, then it returned to the login screen with the "bonk bonk" login prompt sound.  I tried moving the ~/ directory to a backup for that user, and create a new home folder with the right username, but that had no effect.  I created a new user with a new username and specified a simple password (by the way, the algorithm that says a password is "not good enough" is too obnoxious - I seriously don't need a heavily obfuscated password for regular users on my home PC).  Anyway ... that worked fine.  Then to delete the old user, I had to issue the ]sudo userdel -rf [COLOR=#0000CD]username [/COLOR]command[COLOR=#0000CD].[/COLOR]

---

