---
title: "Thunar stopped sorting files according to my preferences"
date: 2014-03-14
forum: General Help
---

### Post by EnglishElectricAndy on 2014-03-14
I don't know if I've inadvertently changed a setting somewhere but Thunar no longer seems to sort files according to the preference I thought I'd set i.e sort by name in ascending order.

Specifically, the files are photos that are titled by date formatted as yyyy-mm-dd e.g. 2008-06-30. I recently tried to add some files with 2007 in the titles but, no matter what I try, Thunar insists on placing these after files numbered 2009 which were put in the folder during a previous session. I've tried disabling the last active view option in the file manager settings, this did not have any effect.

If anyone could point me towards a solution I'd be very grateful.

---

### Post by Toz on 2014-03-14
Are you viewing the files in Detailed List mode (View-> View as Detailed List or Ctrl+2)? If so, click on the "Name" header to change the sort direction. If you are not in Detailed List mode, change to it, change the sort direction, then return to your previous view mode. 

Does this help?

---

### Post by EnglishElectricAndy on 2014-03-14
Thanks for your reply, sadly it seems to make no difference which mode I view the files in. Files with titles starting with 2006 or 2007 or 2008 placed in the folder today will not merge in any numerical order with files starting with 2008 or 2009 placed there previously. This is the first time I've encountered this difficulty and I cannot think of what I might have changed to cause this.

---

### Post by JKyleOKC on 2014-03-14
It sounds as if your View -> Arrange Items submenu may be set to "modification date" rather than "Sort by Name"...

---

### Post by EnglishElectricAndy on 2014-03-15
Thanks, I did double-check this and 'Sort by Name' in 'Ascending' order were selected as my preferences. In the 'View detailed List' mode I configured columns to disable modification date, all to no effect.

I have found what I consider to be a workaround rather than a solution, and that was to batch select the misbehaving files, batch rename them by deleting the first two digits of the filename (i.e. 20) then repeating the batch rename adding back in the same characters. Lo and behold, everything merged into correct order. However this is a manual operation to achieve what used to happen automatically so I'm reluctant to mark the thread as solved at the moment.

Any further input/suggestions would be welcome.

Edit: 'apt-cache policy thunar' reports the installed version matches the candidate version.

---

### Post by JKyleOKC on 2014-03-15
> **EnglishElectricAndy said:**
> Any further input/suggestions would be welcome.

Edit: 'apt-cache policy thunar' reports the installed version matches the candidate version.They've been making some changes lately, and I've been running on an advanced version (4.10) of XFCE for quite some time via a PPA added to my list of sources. I've not noticed any anomalies in the display, but I don't have anything similar to your setup. Here's what I get from the policy report:```
jk@mehitabel:~$ apt-cache policy thunar
thunar:
  Installed: 1.6.3-0ubuntu1~ppa0.12.04.1
  Candidate: 1.6.3-0ubuntu1~ppa0.12.04.1
  Version table:
 *** 1.6.3-0ubuntu1~ppa0.12.04.1 0
        500 http://ppa.launchpad.net/xubuntu-dev/xfce-4.10/ubuntu/ precise/main i386 Packages
        100 /var/lib/dpkg/status
     1.2.3-3ubuntu2 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/universe i386 Packages
jk@mehitabel:~$ 

```

I figured that you already had the proper sort settings, but felt it worth mentioning since we so often miss the most obvious things when a problem pops up!

You can see from my listing that there's quite a difference in version numbers between the "official" version and the one in the PPA...

---

