---
title: "Ubuntu hasn't updated for 118 days"
date: 2013-03-27
forum: General Help
---

### Post by ThomasJazz on 2013-03-27
W: Failed to fetch [http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/bimsebasse/cinnamonextras/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

I get this error when I type
```
sudo apt-get update
```
My computer has been extremely slow lately and I think the lack of updating is why. How can I fix this?

---

### Post by ManamiVixen on 2013-03-27
That repository is gone now. You will have to remove it. I remember reading somewhere that the repository was closed in favor of just downloading them from the Cinnamon applets page on Cinnamon's site. All the immportant ones in the extras were merged into 1.6.7.

Once you remove the repository from your lists, update will work again. "sudo add-apt-repository --remove ppa:whatever/ppa" or edit the sources in the Software Sources window. Just search for it in the Cinnamon menu or Ubuntu Dash.

---

### Post by ThomasJazz on 2013-03-27
There are a ton of the ppa repositories in software sources, which ones do I remove?
EDIT: I removed the repository that was causing the error but when I search for updates in the UpdateManager it still says there are no updates.

---

### Post by ManamiVixen on 2013-03-27
use this link for reference:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Look for the "bimsebasse" ppa's in the "third-party software" tab and delete them. Then update again. Report back if that still dosen't work.

---

### Post by ManamiVixen on 2013-03-27
Can you post the output of "sudo apt-get update"? Also what version of Ubuntu is this?

---

