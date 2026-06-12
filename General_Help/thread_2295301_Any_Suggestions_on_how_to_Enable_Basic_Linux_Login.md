---
title: "Any Suggestions on how to Enable Basic Linux Logins with AD Credentials"
date: 2015-09-17
forum: General Help
---

### Post by Horned_Dragon on 2015-09-17
Hello everyone at the Ubuntu forums,

The company I work for is exploring using Linux distros for thin clients (both USB and PXE booted).  Since it sounded like a perfect excuse to finally dip my toes into the Linux Pool, I decided to look into how that might be done.  I spent a short while looking into how Windows users might be able to log directly into a Lubuntu machine using their active directory credentials and I'm hitting a bit of a wall.  I just started exploring Ubuntu and Linux as a whole, so I'd appreciate any suggestions or corrections that the community could offer.  At this stage, I'd just like a user to be able to sit down at a machine, put in their credentials, and log on. Being able to lock their screen and log back in is important, but shared folders or other features aren't really needed and I don't see their home folders being used if created.

Looks like Power broker and Centrify are both big players in this, but it looks like both they and Winbind require joining the machine to Active Directory to accomplish this task. Since this would be for thin clients via PXE boot, I imagine a lot of attempts to join the domain when users restart their machines.  I'd prefer to limit that potential strain on AD as much as possible.  Since the network is all Windows, users and groups don't have UID's or GID's.  It's my understanding that standard LDAP authentication won't work without those identifiers pulled down from AD though, and the main processes I've seen that can set that information from the Windows SSID all need to join the domain.

I guess I'm looking for a way to use AD credentials at the login screen without joining the domain and, if needed, for new users to auto-create UIDs and GIDs in the process so everything meshes.  With all of the tutorials out there, I'm confident someone has done something like this before, but I'm stuck.  If anyone has any suggestions, I'd greatly appreciate any input.

Thanks for reading that book of a post, and have a good one.

---

