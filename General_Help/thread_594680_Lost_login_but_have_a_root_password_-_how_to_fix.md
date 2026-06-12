---
title: "Lost login but have a root password - how to fix"
date: 2007-10-28
forum: General Help
---

### Post by aussiedaddy on 2007-10-28
Feisty.  User changed their password (I think) but can't remember the new one.  Anyhow they can't login.  If I try to login as root it clearly can authenticate me (if I use wrong password I get a different message, but with correct password I get message that root cannot login from this screen.  Having read around in this forum I now understand why that is.  People no doubt have their opinions as to whether this is a good thing or not.  I made the assumption that as long as I had a root password I could easily fix any user problem such as the above, but unless I can login as root its no use.  From these forums I now know how to enable login as root - but I can't login as anyone else to do that as only one user was created.  In the future I can solve by always creating a dummy user that enables me to get in and fix things, but I am hoping that there is a way to fix things in this instance.  Any help would be most appreciated.

Clearly I am new to this way of doing things but to me sudo is convenient but it strikes me as a lessening of security if you only login as root when necessary and logout again as soon as that need ceases, and the arrangement is at the present time a significant problem for me.  I'll read more about the arguments but I will certainly consider enabling root login on future installs.

---

### Post by figjam on 2007-10-28
Are you at the console?

If you are, then do this:

Press Ctrl+Alt+F1

You will be dropped to a screen where you can log in as root.

Once logged in, then do 

passwd <username>

This will allow you to set a new password for the <username>

Once done, you can press Ctrl+Alt+F9 to return to your X session.

Hope this helps.

---

### Post by #Reistlehr- on 2007-10-28
Go to the Recovery Image or w/e it's called. The one listed in grub under the first linux install. It will load you to a root prompt. It's the same as booting with an init 1 in your boot line.

---

