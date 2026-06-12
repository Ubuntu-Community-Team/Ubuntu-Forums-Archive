---
title: "Software updater startup problem 12.10"
date: 2012-10-22
forum: General Help
---

### Post by stroudwaterboy on 2012-10-22
Now I have got 12.10 going at last (raid problem).

When I try to run software updater I get the following.

W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Now I am sure that I need to remove CD-ROM from the list of sources the problem is that the only option I get once this comes up is close and try as I might I cannot see anywhere else to change the settings.

---

### Post by 2F4U on 2012-10-22
If you can't do it through the GUI you can also edit the sources list /etc/apt/sources.list directly with an editor and administrative privileges.

---

### Post by grahammechanical on 2012-10-22
On 12.10 we find Software sources in the System Settings under the power/cog menu.

Once you open Software Sources go to the Other Software tab. Do you see any reference to the CD-Rom?

I have this:

cdrom:[Ubuntu 12.10_Quantal Quetzal_-Alpha amd64 (20120829)]/ quantal main restricted.

I installed this particular 12.10 from the Alpha release. You may have something similar but different.

Is there a tick mark against this or other references to cdrom? If so uncheck them.

That might solve the problem of those errors messages. We only need a CD-Rom as a software source if we need to install or update from the CD-Rom.

Regards

---

### Post by jerrrys on 2012-10-22
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by stroudwaterboy on 2012-10-22
Thank you all for your help, as I stated the main problem is that you cannot change the software sources from the app if CD-rom is ticked for some reason even with a live CD available! In the end I discovered that when trying to edit  /etc/apt/sources.list I right clicked and the software sources screen opened!

Again thanks for the help, now I just need to find out why Firefox opens 24 instances every time I click on it, some interesting bugs this tme.

---

