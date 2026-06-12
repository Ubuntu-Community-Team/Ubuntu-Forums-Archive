---
title: "Log in to windows (samba) share with different user-name via files (nautilus) GUI"
date: 2014-11-10
forum: General Help
---

### Post by luddeluddis on 2014-11-10
Hi!

I have been a happy user of ubuntu gnome edition lately, for the moment 14.10. But I have an issue with files (nautilus) that has been haunting me. I have googled and searched the forum but have not seen this specific question why I try to state my problem here and see if anyone has any input.

I have a NAS where I have an admin user account. In windows 8 I can login to my shares with the admin account, and for some shares this is the only allowed user name. In windows 8 explorer asks for the credentials if the current user name is not working and I can log in as a different user (i.e. admin).

In ubuntu gnome files (former nautilus) this is not however working. If I try to log in to a share for which my current user name has no rights it only states that it cannot mount the share (because of no user rights). It doesn't ask me for a different user name. And this is my problem. I can bypass this problem by writing admin@nas/directory and then specifiy the password and everything is working fine. But this is not very smooth, especially when I try to instruct someone else less techie-savvy to do it.

Is there a way to get files to ask for credentials when logging in to a windows share with a different user name?

---

### Post by Morbius1 on 2014-11-10
It almost sounds like some point in the past you accessed the server and was prompted for a username and password and selected "Remember Forever".

From that point on it will always do that. You can go to "Passwords and Keys" and remove the saved credentials then it will prompt for credentials again - as long as you don't select "Remember Forever" again.

I don't use Unity and I'm sure there's an easy way to get to the application but for now just open a terminal and type:
```
seahorse
```
If my assumption is correct under "Passwords" should be "Login". If you select "Login" you should see something labelled "Network Password" with a network path like "smb://morbius@server"

Just right click that entry and delete it.

---

