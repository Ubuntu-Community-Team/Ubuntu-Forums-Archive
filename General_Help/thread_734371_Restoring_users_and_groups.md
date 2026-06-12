---
title: "Restoring users and groups"
date: 2008-03-24
forum: General Help
---

### Post by Audiosears on 2008-03-24
Hey all,

I ran across an error trying to uninstall a package the other day, finding out that the process hung and wiped out /etc/passwd, /etc/group, /etc/shadow and possibly other files needed to establish user and group permissions, which then tanked just about everything and gave the dreaded 'gdm user cannot be found' on boot.

I was able to restore the files from a backup using the LiveCD, and things are running fine again save for the fact that users OTHER than root do not show up in the "Users and Groups" manager that comes with Ubuntu.  All the groups show up properly.

I use an account called systemsadmin for administration, and I can log in and su / sudo properly from there.

I restored the following files into /etc so far:

group
group-
gshadow
gshadow-
passwd
passwd-
shadow
shadow-

Observations:

1) I had a large list of users and groups that also translate into samba accounts, and all samba shares are working normally again.  Group access to file shares is based off group membership (i.e. membership in 'public' allows you to map \\server\public).  Similarly, anyone with a home directory, based on access by the user/owner, still works fine.

2) The sudoers file was unaffected, and I can gain su / sudo access or log in as root normally.

3) If I go to "groups" in the Users and Groups manager, I can see all the groups, but available membership only shows the root user as well.

Questions:

1) The permissions on the files I restored could be wrong, but I'm not sure what they originally were - I'm thinking chown 640 for the above list?  I can seem to access them fine, save for not being able to see the full user list.

2) Should I restore other files besides the above list?  Not sure if there's a directory other than /etc I should be worried about...

3) How do the files with the '-' suffix work against the files without them?  Are the files without '-' parsed on boot and turned into the '-' files, then locked?

Any help is greatly appreciated, and I thank you in advance.

---

### Post by Audiosears on 2008-03-27
<bump>

it seems as though I can manually edit any of the files and Samba picks up the changes after some time, but I really need to get the user manager back up if possible.

I did not see any other user/ group management utils in add/remove programs - does anyone else use another app that might work better?

---

### Post by Audiosears on 2008-06-11
<bump>

I just installed Hardy without any hitches, just on the off chance that it might affect the problem, but to no avail.

I can still manually edit the files, but there may be other files whose permissions got blown out that I still need to fix.  Any ideas?

---

