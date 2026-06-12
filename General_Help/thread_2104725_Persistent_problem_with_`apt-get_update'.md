---
title: "Persistent problem with `apt-get update'"
date: 2013-01-14
forum: General Help
---

### Post by kkrishnan on 2013-01-14
Hi folks,

I've had this problem for a few weeks now, and just didn't bother to sit down and figure out what was wrong. When I run ```
sudo apt-get update
```, I get the following errors at the end:
> 
W: Failed to fetch [http://linux.dropbox.com/ubuntu/dists/precise/Release.gpg](http://linux.dropbox.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'linux.dropbox.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.I see this as two distinct problems:
1. Something wrong with PPA
2. A separate problem, of which the source is unclear. ie, the `something wicked' messages

I tried solving the PPA problems based on the solutions posted [here]("http://blog.launchpad.net/ppa/failed-to-fetch-errors-for-ppas"). However, neither ```
/etc/apt/sources.list
``` nor any list in ```
/etc/apt/sources.list.d
``` had an entry with anything other than `main' at the end of the line.

I have had less success with problem 2 and would appreciate tips for solving both.

Thanks in advance

---

### Post by I8NY on 2013-01-14
I can help solve one issue but not the other.   For the PPA issue, the location it is looking for files doesn't exists.  And from looking at it in the browser, the Precise folder (12.04) doesn't exists now.  They do have Hard, Jaunty, Karmic, Lucid, Maverick, Natty, and Oneiric versions.  So those version of Ubuntu should work fine.  There could be a stability issue or something else so they took it down but there isn't much you can do (unless you downgrade) until they put back the files for Precise Ubuntu.  Idk about your other issues but check you boot partition, sometimes that gets filled up and causes weird issues when trying to update stuff.

---

### Post by d4rk0wl on 2013-01-14
This is probably a long shot, but have you attempted:
```
sudo apt-get clean
```
and
```
sudo apt-get --fix-missing
```

I could be way off, but it is worth a shot.

Regards,
- D4rk0wl

---

### Post by kkrishnan on 2013-01-14
Hi D4rk0wl and I8NY,

Thank you for your tips. Problem 2 has mysteriously disappeared (I've been hunting for stuff posted on forums before and have tried so much stuff now that I'm not sure what fixed it). Problem 1 (with the PPA) still remains. I8NY, are you saying that there isn't any way to fix this current problem?

---

### Post by plucky on 2013-01-14
> **kkrishnan said:**
> Hi D4rk0wl and I8NY,

Thank you for your tips. Problem 2 has mysteriously disappeared (I've been hunting for stuff posted on forums before and have tried so much stuff now that I'm not sure what fixed it). Problem 1 (with the PPA) still remains. I8NY, are you saying that there isn't any way to fix this current problem?

You have to disable/delete the repository in **Software Sources** as that PPA doesn't have a repository for the Precise Release.

See [Here](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/)

Good Luck

---

### Post by kkrishnan on 2013-01-15
Hi plucky,

That seems to have fixed the issue. Thanks very much.

---

