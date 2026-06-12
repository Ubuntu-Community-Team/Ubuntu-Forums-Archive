---
title: "Problems with Downloading Updates"
date: 2006-07-10
forum: General Help
---

### Post by Jesus_Christ on 2006-07-10
For the past two days, there have been two individual updates that have refused to be found by the update manager. They were listed along with my other 100 or so updates, but unlike the rest, they wouldn't download, and I received this error message:

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb)
404 not found

W: Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb](http://nz.archive.ubuntu.com/ubuntu/pool/main/p/pmount/pmount_0.9.11-1ubuntu1_i386.deb)
404 not found

Obviously the links provided aren't legit, so is there anyway I can obtain these updates manually, or rectify the problem in the update manager?

---

### Post by Bil-E-daKid on 2006-07-10
Hey there!

Yeah, I use the NZ mirror as well (being from NZ and all) and sometimes encounter these messages too.

I suspect that the package lists get updated before the packages themselves have had time to sync fully to this mirror - hence Ubuntu knowing about the updates before the files themselves can be 'found'.

I normally just give it a couple of days and try again once the packages have mirrored successfully.

FYI, make sure you are not using the NZ mirror for your security updates as those are the ones you'll want to get at straight away!

(You should have security.ubuntu.com listed in your /etc/apt/sources.list for the security updates).

:-)

---

### Post by yabbadabbadont on 2006-07-10
I see the same thing happen on the US mirrors a lot.  (there are many posts about it in these forums)  When that happens, I just remove the country code from the front of the entries in sources.list and use the main repositories for a couple of days.

---

