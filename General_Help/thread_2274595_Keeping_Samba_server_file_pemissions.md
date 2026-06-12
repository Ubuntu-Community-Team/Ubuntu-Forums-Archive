---
title: "Keeping Samba server file pemissions"
date: 2015-04-20
forum: General Help
---

### Post by mongr31 on 2015-04-20
I'm running into a situation where I have a Samba server hosting a directory that I need to have full permissions on at all times. It's just running on a VM, so security isn't an issue. I can't seem to figure out how to keep the file permissions consistent. Every time something gets added it has different permissions and prevents me from modifying those files. Is there a way to have Samba keep the permissions at 777 or do I need to run incron or something that will scan for changes real time and chmod them as needed?

---

### Post by nerdtron on 2015-04-21
Maybe you can force all files saved on the samba directory to be owned by a single user. For example, if user1 and user2 saves their files on the samba share, all the files will be automatically owned by user1.

You can add this to your samba conf:
*[I]force user* = user1[/I]

Or look for the answer section here: [http://askubuntu.com/questions/97669/i-cant-get-samba-to-set-proper-permissions-on-created-directories](http://askubuntu.com/questions/97669/i-cant-get-samba-to-set-proper-permissions-on-created-directories)

---

