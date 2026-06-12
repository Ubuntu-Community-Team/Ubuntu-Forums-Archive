---
title: "Root login to server"
date: 2024-03-12
forum: General Help
---

### Post by julian-s1965 on 2024-03-12
Hi I logged into the server of a new client. His website files are on the server but I cannot see them logged in as root user. I run the ls command and only can view a snap folder and a single txt file.  No signs of web files. Should root user not be able to see everything ?

---

### Post by TheFu on 2024-03-12
> **julian-s1965 said:**
> Hi I logged into the server of a new client. His website files are on the server but I cannot see them logged in as root user. I run the ls command and only can view a snap folder and a single txt file.  No signs of web files. Should root user not be able to see everything ?

No. You are seeing a normal Ubuntu install for desktops AND servers. Ubuntu doesn't use the root user.  Many distros are setup that way.
On Ubuntu, you are expected to use **sudo** for any ad-hoc needs.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) explains the original ways.  I haven't noticed any differences in my ubuntu servers with regards to sudo use and non-root use.  If I need to run things as root, that's handled via either systemd "unit files" or from one of the 3 cron methods available for the root userid - just like on any other Linux.

Canonical knew that neophyte users often get into problems with easy access to root, so they've just never setup Ubuntu Server to work that way. Of course, you can, if you know how, make the root user a security risk like all the other Linux systems out there that don't force sudo.  **It isn't needed.**

I don't know if these forums still have the same rules, but telling someone how to setup direct root ssh and direct root logins was against forum policy. I believe it is still frowned upon, but a moderator would know for sure.

---

