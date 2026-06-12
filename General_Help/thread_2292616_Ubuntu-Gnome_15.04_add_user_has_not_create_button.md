---
title: "Ubuntu-Gnome 15.04 add user has not create button"
date: 2015-08-29
forum: General Help
---

### Post by RobertoRecordo on 2015-08-29
Trying to add user to system. I am using the system tool => users dialogue.
I unlock and enter my password, give a user-name and passwords ( and see the verification check)

All that is available is an "enterprise" button, not the "create"  button as per
[https://help.ubuntu.com/stable/ubuntu-help/user-add.html](https://help.ubuntu.com/stable/ubuntu-help/user-add.html)

When I click the enterprise button the screen says "Enterprise login allows an existing centrally managed account to be used on this device."
then there are fields to fill in for domain, user-name and password. This is not useful to me, there is no centrally managed account.

What is this? Does it have anything to do with the fact that there is a home folder in a remoter partition with this username? To explain, I did a full install on 15.04, after backing up home folders to remote partitions. Ubuntu is mounting folders user1 & user2 , but created an "official" empty home folder tor the me.   

I googled for others having problems with adding users to GNOME 15.04 but I found none.

Help? How can I add a user?

-Rob

---

### Post by RobertoRecordo on 2015-08-29
I threshed around trying different things. 
I discovered that creating a password in the add user dialogue box causes the "add" button at the top right to be greyed out.
Changing the password selection to "allow user to create password at first login" (paraphrase) makes the "add" button active.
Is it a bug?

Marking this as closed,

---

