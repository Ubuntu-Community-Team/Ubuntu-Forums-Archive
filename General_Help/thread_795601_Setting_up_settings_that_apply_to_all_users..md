---
title: "Setting up settings that apply to all users."
date: 2008-05-15
forum: General Help
---

### Post by taugust04 on 2008-05-15
Hi everyone,

I've been using Ubuntu on and off for several years now, however, I'd like to setup a "demo" computer of Ubuntu 8.04 where I work for people to try it out.  I've successfully figured out how to bind the computer to Active Directory so that they can login with their network accounts onto the demo computer.

However, I'd like to apply some global settings that get applied when their home directory folder is first created when they log into the computer.  For example, the default home page in Firefox, bookmarks, desktop wall paper, appearance settings, etc.

I'm familiar on how this is done on the Mac (modifying the "/System/Library/User Template/English.lproj" folder), and on Windows (modifying the "c:\Documents and Settings\Default User" folder) so that you can configure one account, and then copy it to a "user template", so that those settings are then applied to all users when accounts are created.  Is there a similar workflow in Ubuntu?

I know this is just a general knowledge forum, however, I couldn't find the appropriate category to post this in.  I really didn't have any luck searching these forums, or on Google either, but it may just be a lack of knowledge on what keywords I should be focusing on.  Any help you can provide, or a nudge in the right direction would be greatly appreciated.

Thanks so much!

---

### Post by chrisccoulson on 2008-05-15
You can change default and mandatory keys in gconf, which will give you control over a lot of settings. A default key will apply to all users by default but will be overridden if a user changes the key in their profile.

Mandatory keys apply to all users and cannot be overridden.

You can change these in gconf-editor if you launch it as root:
```
gksudo gconf-editor
```

Not sure if is the best way to approach it though

---

### Post by pointone on 2008-05-15
/etc/skel is the template for newly created home directories.

---

