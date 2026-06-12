---
title: "[SOLVED] Too much access to Windows (permissions not respected)"
date: 2007-12-16
forum: General Help
---

### Post by techiebiker on 2007-12-16
Ubuntu 7.10 connecting to shares on Windows XP Pro SP2.

Home network does not have a DC. Each Windows computer (2 x XP Pro, 1 x W2K) is set up with the same local user accounts with the same passwords. 

One XP box has folders shared. The shares are, User1, User2, User3 and AllUsers. From each Windows box if User1 is logged in User1 can access User1 and AllUsers shares. If User2 is logged in User2 can access User2 and AllUsers shares, etc.

In Ubuntu when I access the Windows network and navigate to the XP box that shares folders all shares are visible. When I click on a share I am asked for user name and password. When I enter same, e.g., User1 & user1pwd, I am able to access ALL SHARES on the Windows box!!!!

What's going on here? Anyone have any idea?

I know that when I had Ubuntu 6.10 on the Ubuntu box it only allowed access to shares the user had permission for. At first I thought 7.10 was a great leap forward because it accessed the Windows network and shares MANY times faster than 6.10 did. Then I found out it didn't seem to care about security.

What's happening here?

---

### Post by sciurus on 2007-12-18
Ubuntu can only do what Windows allows it to do. Turn of "Simple file and print sharing" in Windows and configure the permissions for the network share the way you want in Windows.

---

### Post by danwood76 on 2007-12-18
XP file permissions are fairly weak, and the drive needs to be formatted NTFS for them to work at all.

---

### Post by techiebiker on 2007-12-19
Okay, my bad. At some point I changed the User1 (my account) group membership to the Administrators group. Removed it from admin group and everything's back to what it should be.

Don't remember when or why I changed the group membership. Do it very occasionally and then remove the account from the group when I log off. At least that's usual practice.

I crashed my bicycle end of July and suffered TBI (traumatic brain injury). Recovery went well and everything seems to be fine. Every once in a while I'm discovering that I seem to forget a few things that I wouldn't have before.

---

