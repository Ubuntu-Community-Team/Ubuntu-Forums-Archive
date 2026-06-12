---
title: "Edubuntu 7.10 with Thin Clients users authenticated through AD"
date: 2008-01-30
forum: General Help
---

### Post by buddist7 on 2008-01-30
I've already got Thin Clients working successfully, users are authenticated just fine with Active Directory.

The problem lies in the Thin Client Manager.  It works fine with local (to the 

When a user logs in with an AD login the same functionality of a regular user such as viewing the process list, sending messages, blanking the screen, executing commands, or disconnecting don't work.  Oddly enough I can view the screen with the x11vnc in the screen viewer section of the Thin Client Manager.  

These AD user's processes in the output of 'ps aux' are numeric uids when all the local users are their login name.  Im sure there is some correlation with that.  

I am looking for any suggestions for better integration of the AD users to behave just like local accounts.

---

