---
title: "One more dumb question (maybe)"
date: 2008-03-26
forum: General Help
---

### Post by babyfoxx on 2008-03-26
I have 4 PC connected via a network hub, and Bellsouth DSL (Ultra). I'm the "computer guru" of the house (not really but...), and I have to "perfect Ubuntu/Linux before we'll switch over".  I'm the mom and could force a switch, but I don't want to hear any crying.

  So far it's all going well, but I'm having a shared folder/network issue. I can see and access all shared folders from Windows XP to me (Ubuntu). They can see my shared folder (Ubuntu/Linux) from Windows XP, but when they try to access it they get "unable to access.....permission denied". I know in Windows this is usually do to firewalls, but I don't have one running on Ubuntu....or do I? Is there a hidden firewall like Windows?

 I have read a few tutorials, and I'm kind of confused on which is my connection. In Network Tools I have two:
Loopback Interface (lo) & Ethernet Interface (eth0)
The IP address of (eth0) one IPv4 is normal 192....., but the other IPv6 is fe80::.....
(lo) has 2 IPv4 127... & ::1

Maybe I should download a help book?.?.

I am doing good though, WoW and Guild Wars work seamlessly. :popcorn:

---

### Post by 505 on 2008-03-26
The reason is probably that the username/password is not correct when accessing the Ubuntu machine from Windows. Take a look at the [documentation]("https://help.ubuntu.com/community/SettingUpSamba"), especially about public and private shares.

However, if you intend to switch all machines, it might not be worthwhile investing in the solution. Once all machines are Ubuntu, you can easily share files using SFTP/SSH, which makes things a lot simpler.

---

### Post by babyfoxx on 2008-03-26
Ok, I'll read that. I think it will be at least a year of dual booting before we'll switch over completely. 

I have to show them that Ubuntu will do every thing that Windows can do, and more.

---

