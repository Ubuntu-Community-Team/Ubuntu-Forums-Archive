---
title: "Problem when updating the repositories."
date: 2013-03-22
forum: General Help
---

### Post by Silky Jackson on 2013-03-22
When I try and run a software update this message comes back.

W:Failed to fetch [http://ppa.launchpad.net/upubuntu-com/shell/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/upubuntu-com/shell/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/upubuntu-com/shell/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/upubuntu-com/shell/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.


I also noticed that when I go to details in my system settings the button that tells you if you need to update or not is gone. The number under Ubuntu on the same panel is hard to read but it looks to say 13.04. It should say 12.10. 

Any ideas as to what I did to cause this problem.

---

### Post by sanderj on 2013-03-22
Start the Ubuntu Software Source, click Edit -> Software Source, go to the tab Other Sources. There, unselect the problematic PPA sources you mention above.

HTH

---

### Post by Silky Jackson on 2013-03-22
Thank you, that seemed to help. I played around to much when I first installed Ubuntu and now problems are showing up. Linux is still pretty new to me so I don't want to make things worse.

---

### Post by ibjsb4 on 2013-03-22
Like sanderj said, needs to be removed.  There is no quantal package for this ppa.

[http://ppa.launchpad.net/upubuntu-com/shell/ubuntu/dists/](http://ppa.launchpad.net/upubuntu-com/shell/ubuntu/dists/)

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

