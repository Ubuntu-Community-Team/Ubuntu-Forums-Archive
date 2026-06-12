---
title: "Setting up a group to restrict access to firefox"
date: 2007-03-22
forum: General Help
---

### Post by Boatswain on 2007-03-22
Hi all,

I'm trying to set up a user on my system with no access to firefox. So far I've set up a group called "Internet" and set up /usr/lib/firefox/firefox permissions to owner: root (read and write); group: writing(read only);others (none). I've made root and all but one of my profiles members of group: internet. The one profile that I don't want to give access to firefox can still execute firefox at this point, but if I go back to properties and clear the checkbox for "allow executing file as program" then none of the users in the "internet" group can run firefox either.

What am I missing here? I'm sure it must be a fairly straightforward process to make a user that can't access a given program, but I'm having a rough time figuring it out. Any help appreciated!

Tom

---

### Post by fragos on 2007-03-22
/usr/bin/firefox is a link to /lib/firefox/firefox and by default owner and group are both root yet you can still run it with a user login.  Looks to me like changing the group won't help much unless you change the execute privelege for other/all as no.  I'm not sure if it must be changed in both the link and the lib.

---

### Post by hikaricore on 2007-03-22
You may want to look into:

ACL: [http://gentoo-wiki.com/HOWTO_Use_filesystem_ACLs](http://gentoo-wiki.com/HOWTO_Use_filesystem_ACLs)

along with

Eiciel: [http://rofi.pinchito.com/eiciel/doc/](http://rofi.pinchito.com/eiciel/doc/)

I didn't have time to find any ubuntu/debian howtos on this, but this will atleast give you a better idea into further control of user permissions.

---

### Post by Boatswain on 2007-03-22
Thanks for the tips and the links. I got it all squared away by changing the permissions for the /usr/lib/firefox folder, and should hopefully not have any problems restricting access to the rest of the internet stuff I don't want available.

Cheers!

Tom

---

