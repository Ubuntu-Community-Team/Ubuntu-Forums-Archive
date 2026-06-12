---
title: "Add space to existing patition from a different drive"
date: 2008-05-22
forum: General Help
---

### Post by Leav on 2008-05-22
Hi there!

I have ubuntu 8.04 up and running perfectly on my cute little eeePC, and I love it!

I'm looking into adding a 32gb corsair flash drive permanently into my eee (a bit of modding), and I would like it to be an seamless extension of the current 4gb SDD.

Is this possible?

how do you do this?

the linux file system is confusing for me... where are things actually kept?
what happens when you mount another hard drive? how do you "tell" linux to save stuff on the new hard drive?

Thanks!
-Leav

---

### Post by warp99 on 2008-05-22
> **Leav said:**
> Hi there!

I have ubuntu 8.04 up and running perfectly on my cute little eeePC, and I love it!

I'm looking into adding a 32gb corsair flash drive permanently into my eee (a bit of modding), and I would like it to be an seamless extension of the current 4gb SDD.

Is this possible?

how do you do this?

the linux file system is confusing for me... where are things actually kept?
what happens when you mount another hard drive? how do you "tell" linux to save stuff on the new hard drive?

Thanks!
-Leav

You would have to set up the SSDs to use Logical Volume Management (LVM) that way all of your drive volumes will be seen as one by the OS. More information on setting up LVM can be found here:

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall?highlight=%28lvm%29](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall?highlight=%28lvm%29)

You may also want to do a search at [eeeuser.com]("http://www.eeeuser.com/") in the forums and the wiki to see if anyone has set this up successfully.

---

