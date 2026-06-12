---
title: "can't update with terminal, only update manager"
date: 2014-07-09
forum: General Help
---

### Post by Buntu Bunny on 2014-07-09
I'm no Ubuntu whiz, but I do like to try to keep my hand at it. For awhile now, I get the following when trying to update via the command line.
```

buntu_bunny@buntu_bunny-CM1740:~$ sudo apt-get update && sudo apt-get dist-upgrade

<snip>


Err http://ppa.launchpad.net precise/main Sources                       
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found

<snip>

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Well, I tried Cinnamon a few years ago but removed it. Or thought I did, so I ran

```
sudo apt-get --purge autoremove cinnamon
```

It came back

```
Package cinnamon is not installed, so not removed
The following packages will be REMOVED:
  gir1.2-unique-3.0* libtommath0* linux-headers-3.2.0-53*
  linux-headers-3.2.0-53-generic* linux-headers-3.2.0-54*
  linux-headers-3.2.0-54-generic* linux-headers-3.2.0-55*
  linux-headers-3.2.0-55-generic* linux-headers-3.2.0-56*
  linux-headers-3.2.0-56-generic* linux-headers-3.2.0-57*
  linux-headers-3.2.0-57-generic* linux-headers-3.2.0-59*
  linux-headers-3.2.0-59-generic* linux-headers-3.2.0-60*
  linux-headers-3.2.0-60-generic* linux-headers-3.2.0-61*
  linux-headers-3.2.0-61-generic*
0 upgraded, 0 newly installed, 18 to remove and 0 not upgraded.
After this operation, 541 MB disk space will be freed.

```

I ran sudo apt-get update again, but got the same "failed to fetch" messages.

I can update without problem with Update Manager, but I would like to fix this if possible.

---

### Post by Buntu Bunny on 2014-07-09
Okay, I think I got it. I was sitting there staring at my post when it occurred to disable the cinnamon ppa. I went to other software sources in Update Manager and unchecked 

ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main
ppa.launchpad.net/gwendal-lebihan-dev/cinnamon-stable/ubuntu precise main (Source Code)

I ran apt-get again and success!

I may never win any geek awards, but at least I can figure out a thing or two on occasion. ;)

---

### Post by deadflowr on 2014-07-09
Yeah the cinnamon devs decided a little while ago to stop maintaining a cinnamon-stable ppa.
For whatever reason.

Others have taken up the cause
[http://www.webupd8.org/2014/06/new-cinnamon-stable-ubuntu-ppas-ubuntu.html](http://www.webupd8.org/2014/06/new-cinnamon-stable-ubuntu-ppas-ubuntu.html)

as well, the devs do still have a ppa for nightly builds
[https://launchpad.net/~gwendal-lebihan-dev/+archive/ubuntu/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/ubuntu/cinnamon-nightly)

---

### Post by Buntu Bunny on 2014-07-09
Well, it's fun to be able to try out different desktop environments, because that way everyone can find their Linux niche. I appreciate the links deadflowr, I may want them someday.

---

