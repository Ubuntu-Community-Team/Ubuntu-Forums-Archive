---
title: "Password in Guest account?"
date: 2013-02-01
forum: General Help
---

### Post by xycris on 2013-02-01
Hi,

I have one lappy running Ubuntu 12.04. This does not happen before until today.

A friend of mine used it logging in on the guest account since there is no password. When the computer goes idle it is suppose to go on that black out screen saver (Ubuntu default and no other options available). However, when he returned to use the lappy again, the locked screen appears and now asking for password for guest.

I suggested to leave it blank since there is no password for the Guest account but it did not accept it. Sorry, I am confused now.

Our current work around is click on the switch user button then login again and everything goes back, all the opened windows and unsaved documents.

Is there are way that disables the lock screen? It seems that when done in Guest, the other users also are affected like mine.

Thanks in advance.

Sincerely,
Xycris

---

### Post by slickymaster on 2013-02-01
By default Ubuntu 12.04 guest account is a "passwordless" account.

There's a reported bug in Launchpad concerning **_.xsession-errors from Guest session_**.
Here's the link: [Bug #1022858]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1022858")

---

