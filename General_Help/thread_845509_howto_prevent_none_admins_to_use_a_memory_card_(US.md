---
title: "howto prevent none admins to use a memory card (USB) in the system?"
date: 2008-06-30
forum: General Help
---

### Post by adhg on 2008-06-30
Hello all,

I have some users that do not have admin privileges, is it possible to prevent them to use a USB card (any memory card) to download information from the computer?

* Some users can see sensitive-information but not to take it with them and abuse it's copyrights 

thank you

---

### Post by russlar on 2008-06-30
Disable automounting of USB devices, and make sure that the non-admin users are not in the sudoers group. If they can't sudo, they can't mount, and if a usb stick doesn't mount automatically, it must be mounted manually. If a user doesn't have sudo rights, they can't mount manually.

---

### Post by adhg on 2008-06-30
mmm...great, at least the option exists :-)

"Disable automounting of USB devices," how do I do that if I may ask?

---

### Post by chrisccoulson on 2008-06-30
Yes, it should be possible to set up Policykit to stop users using removable storage devices. First of all, go to System -> Administration -> Authorizations. Scroll down to 'Mount filesystems from removable drives' on the left-hand side. Under 'Implicit Authorizations' on the right hand side, click the Edit button. In the new window, change the 'Active Console' policy to one of the 'Admin Authentication' options. This will stop normal users from mounting external filesystems via HAL.

You might also want to remove users from the 'plugdev' group. You can do this in the Users and Groups tool, by unchecking 'Access external storage devices automatically' under the 'User Privileges' tab for the user.

---

### Post by russlar on 2008-06-30
> **adhg said:**
> mmm...great, at least the option exists :-)

"Disable automounting of USB devices," how do I do that if I may ask?

Off the top of my head, I don't know. I believe it to be in the HAL, somewhere in /usr/share/hal/device-manager. most of the scripts look like they're written in python.

---

