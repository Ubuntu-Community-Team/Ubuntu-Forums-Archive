---
title: "Allocate disk space for users of multisite app"
date: 2013-08-11
forum: General Help
---

### Post by ola3 on 2013-08-11
I am developing an app that will run as  a multisite app on a linux cloud hosting service but i want each site to have a predefined limited amount of disk space it can consume just as in some SaaS software. The amount disk space can be adjusted up or down based on user's requirements. So for each site the user/owner cannot consume more than their allocated space per time. 

In this setup also, a user may have a dedicated IP, ftp access. Makes me think the allocation should be done at hardware level but all sites share the same code base so I need them on same computer.

I do not know if this can be achieved by this approach but I am open to any suggestions. 
Please ask for any clarifications.
It may also be obvious from my question that I am a Linux noob.

Thanks for any help, it will be more appreciated than you could imagine.

---

### Post by mcduck on 2013-08-12
I doubt you would be able to do it on hardware level (or at least that would be pointlessly complicated way). :)

On the other hand, operating system/ file system level is definitely a plausible way. Most Linux filesystems have support for disk space quotas. This should work: [http://www.thegeekstuff.com/2010/07/disk-quota/]("http://www.thegeekstuff.com/2010/07/disk-quota/")

---

### Post by ola3 on 2013-08-16
thanks mcduck for the reply. sorry i cldnt reply earlier too, been away. the link was helpful though. I have now been able to move to configuring each user's directory as a virtual host directory using webmin. I am just wondering if webmin may be used to provide each of the users a login/admin interface for creating such things as email and ftp accounts just like we do on cpanel with shared hosts. anybody pls??

---

