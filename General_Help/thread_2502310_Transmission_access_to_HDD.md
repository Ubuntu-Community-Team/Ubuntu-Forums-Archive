---
title: "Transmission access to HDD"
date: 2024-11-09
forum: General Help
---

### Post by tijmz on 2024-11-09
Hi all

I recently installed Ubuntu on SSD and added a 2 TB HDD to the system. I would like to use Transmission to store downloaded files on the new HDD, but unfortunately the locations to not show up in the dialog (I've used GUIs for all steps, automounting via the Disks application and accessing Transmission via its GUI, too).

I figure this is a permissions thing, but can't get it to work. What I have done so far is make sure that my user owns the respective partition on the HDD, but this does not change anything. I suspect Transmission runs as its own user, but all information I can find is about transmission-daemon and I am actually not using that.

How can I have Transmission save to a drive/partition that is different from where it has been installed?

---

### Post by tijmz on 2024-11-09
Ah, this is a classical case of spending hours on something and then right after posting to the forums, finding the solution itself. It's been a while since I have used Ubuntu and I am not sure what snap is, but apparently if an application is a snap, you need to do the following for open up its access:

> sudo snap connect transmission:removable-media

This did the trick, now to read up on what this all means :)

---

