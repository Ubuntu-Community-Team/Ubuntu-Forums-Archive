---
title: "Handling server permissions"
date: 2014-04-18
forum: General Help
---

### Post by jason58 on 2014-04-18
Greetings!

I've been fighting this for a couple months now, so it'd be really awesome if someone could help me figure out.

What I'm trying to accomplish is to have the owner of a directory and its contents be something other than the server user (in this case www-data), yet still allow the server to read/write to said directory. Here's what I've tried:


[LIST=1]
[*]Add the user to the www-data group
[*]Set all files/folders chown to user:www-data
[*]Set all directories to 775 permission
[*]Set all files to 664 permission
[/LIST]

This almost works. For some crazy reason though, specific to Wordpress, I still cannot install/update plugins or the wordpress core -- any moment wherein www-data would need to create a directory and create/modify/delete files. If, however, I chown www-data -R the entire directory, it works. This absolutely baffles me! 

I'm also gone the ACL route:


[LIST=1]
[*]Install acl, add to fstab, remount
[*]Setfacl -Rdm g:www-data:rwx root-site-folder
[*]Find root-site-folder -type f -exec setfacl -m g:www-data:rw {} \;
[/LIST]

I even tried adding an acl for www-data as a user as well as a group. No difference.

I absolutely must be missing some simple permissions concept here. I actually got it to work on one site, but I have absolutely no idea why it worked on that one and not 4 others. Someone please shed some light on this! It's driving me bonkers! Hahah!

Thank you!

---

### Post by SeijiSensei on 2014-04-18
I've taken the opposite approach from you.  I have a user and group that own the entire wordpress tree and placed the Apache user in the group.  Then I have 770 permissions on the directories in the wordpress tree, and 660 permissions on the files themselves.  My installation was automatically updated a couple of times recently without incident.

---

