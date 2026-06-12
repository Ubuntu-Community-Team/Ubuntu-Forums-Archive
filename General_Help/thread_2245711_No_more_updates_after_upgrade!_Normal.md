---
title: "No more updates after upgrade! Normal?"
date: 2014-09-25
forum: General Help
---

### Post by sim085 on 2014-09-25
Hi,

I had a machine with Ubuntu Server Edition version 12. A month or so ago when I logged in on the system I had a message that I had to upgrade to version 14. I did this. However now when I login I always get:

0 packages can be updated.
0 updates are security updates.

Is this normal? Before I remember I always had packages to update! What could be wrong?

If I do apt-get update apt-get upgrade I do get some packages that need upgrading.

---

### Post by deadflowr on 2014-09-25
It's normal for like a day or two(or sometimes up to a week, or so).
But if it's saying that everytime, I would check that the updating is in proper working order.
```
sudo apt-get update
```
If it has problems, it'll bark it out.
If not, it'll simply end with a line saying something like 20kb packages fetch in 20secs, or something like that.

An error will be very pronounced.

If no errors, you can try the upgrade command to apply the updates, if any
```
sudo apt-get upgrade
```

Post back if either command produce any errors.
Post them as well, using Code Tags, please.

---

### Post by sim085 on 2014-09-25
Problem is I already did apt-get update and apt-get upgrade.

When I did apt-get upgrade it asked permission to install upgraded packages even though on login it reported there are "0 packages can be updated."

I now logged in (through SSH) and it is not giving the messages "0 packages can be updated."

When I enter apt-get update I get the following:

```

Ign http://mt.archive.ubuntu.com trusty InRelease
Ign http://mt.archive.ubuntu.com trusty-updates InRelease
Ign http://mt.archive.ubuntu.com trusty-backports InRelease
Hit http://mt.archive.ubuntu.com trusty Release.gpg
Ign http://security.ubuntu.com trusty-security InRelease
Hit http://mt.archive.ubuntu.com trusty-updates Release.gpg
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://mt.archive.ubuntu.com trusty-backports Release.gpg
Hit http://mt.archive.ubuntu.com trusty Release
Get:2 http://security.ubuntu.com trusty-security Release [59.7 kB]
Hit http://mt.archive.ubuntu.com trusty-updates Release
Hit http://mt.archive.ubuntu.com trusty-backports Release
Hit http://mt.archive.ubuntu.com trusty/main Sources
Hit http://mt.archive.ubuntu.com trusty/restricted Sources
Get:3 http://security.ubuntu.com trusty-security/main Sources [45.3 kB]
Hit http://mt.archive.ubuntu.com trusty/universe Sources
Hit http://mt.archive.ubuntu.com trusty/multiverse Sources
Hit http://mt.archive.ubuntu.com trusty/main amd64 Packages
Hit http://mt.archive.ubuntu.com trusty/restricted amd64 Packages
Get:4 http://security.ubuntu.com trusty-security/restricted Sources [14 B]
Hit http://mt.archive.ubuntu.com trusty/universe amd64 Packages
Get:5 http://security.ubuntu.com trusty-security/universe Sources [10.8 kB]
Hit http://mt.archive.ubuntu.com trusty/multiverse amd64 Packages
Get:6 http://security.ubuntu.com trusty-security/multiverse Sources [700 B]
Hit http://mt.archive.ubuntu.com trusty/main i386 Packages
Hit http://mt.archive.ubuntu.com trusty/restricted i386 Packages
Get:7 http://security.ubuntu.com trusty-security/main amd64 Packages [144 kB]
Hit http://mt.archive.ubuntu.com trusty/universe i386 Packages
Hit http://mt.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://mt.archive.ubuntu.com trusty/main Translation-en_GB
Hit http://mt.archive.ubuntu.com trusty/main Translation-en
Get:8 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Hit http://mt.archive.ubuntu.com trusty/multiverse Translation-en_GB
Hit http://mt.archive.ubuntu.com trusty/multiverse Translation-en
Get:9 http://security.ubuntu.com trusty-security/universe amd64 Packages [48.9 kB]
Hit http://mt.archive.ubuntu.com trusty/restricted Translation-en_GB
Get:10 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,148 B]
Hit http://mt.archive.ubuntu.com trusty/restricted Translation-en
Get:11 http://security.ubuntu.com trusty-security/main i386 Packages [136 kB]
Hit http://mt.archive.ubuntu.com trusty/universe Translation-en_GB
Hit http://mt.archive.ubuntu.com trusty/universe Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/main Sources
Get:12 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Hit http://mt.archive.ubuntu.com trusty-updates/restricted Sources
Get:13 http://security.ubuntu.com trusty-security/universe i386 Packages [48.8 kB]
Hit http://mt.archive.ubuntu.com trusty-updates/universe Sources
Get:14 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse Sources
Hit http://security.ubuntu.com trusty-security/main Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/main i386 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/restricted i386 Packages
Hit http://security.ubuntu.com trusty-security/universe Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/universe i386 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://mt.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://mt.archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/main Sources
Hit http://mt.archive.ubuntu.com trusty-backports/restricted Sources
Hit http://mt.archive.ubuntu.com trusty-backports/universe Sources
Hit http://mt.archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://mt.archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://mt.archive.ubuntu.com trusty-backports/main Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/multiverse Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/restricted Translation-en
Hit http://mt.archive.ubuntu.com trusty-backports/universe Translation-en
Fetched 498 kB in 8s (61.2 kB/s)
Reading package lists... Done

```

and apt-get upgrade:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  g++-4.6 libboost-iostreams1.46.1 libgd2-noxpm libicu48 libkadm5clnt-mit8
  libkadm5srv-mit8 libkdb5-6 liblcms1 libmpc2 libstdc++6-4.6-dev
  libtasn1-3-dev python-imaging
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.

```

(as I said I just did apt-get upgrade and when reported there are upgrades I answered yes).

---

### Post by deadflowr on 2014-09-25
You can update those kernel packages with the dist-upgrade option instead of the normal upgrade
```
sudo apt-get dist-upgrade
```

the apt-get man pages can be helpful, or better at explaining the difference than me, or here as well
[http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade](http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade)

Hope it helps.

---

### Post by Rob Sayer on 2014-09-25
If there are any error messages there I can't see them.

The kernel updates are being held back because apt-get upgrade upgrades the software packages but doesn't replace them with a new version.  This usually happens with a kernel update.

To update the kernel do:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I don't usually bother with autoremove because it may cause problems.

---

### Post by sim085 on 2014-09-25
Ok ran those commands. So should now be ok? When should I run sudo apt-get dist-upgrade?

---

### Post by deadflowr on 2014-09-25
> **sim085 said:**
> Ok ran those commands. So should now be ok? When should I run sudo apt-get dist-upgrade?

Usually when you see the output like the one you got:
> The following packages have been kept back:
It'll always list what packages. You can review them if need be, and if you are hesitant to apply them, you can always post the output in a thread on the forums for more clarity.

but for kernel packages, it's normal.

edit: I should note the system needs to be restarted for the new kernel packages to take effect.

---

### Post by Michael_McKenney on 2014-09-25
Do you need to clean up old upgrades and /boot space first?  I had the problem with doing upgrades and found /boot was full.  I used Synaptics to cleanup the old Linux-images.

---

### Post by deadflowr on 2014-09-25
> **Michael_McKenney said:**
> Do you need to clean up old upgrades and /boot space first?  I had the problem with doing upgrades and found /boot was full.  I used Synaptics to cleanup the old Linux-images.

Depends on if you have a separate boot partition. and then it depends on how fat said partition is.

---

### Post by sim085 on 2014-09-25
Thanks for the info. I restarted and now I get the number of packages that need updating :)

7 packages can be updated.
7 updates are security updates.

I'll do a quick update upgrade.

I guess that solved the problem. That said, I am relevant new to linux which is why I am asking this question; what are "linux-generic linux-headers-generic linux-image-generic"?

---

### Post by sim085 on 2014-09-25
To quick to declare victory ...

I did apt-get update and got the following ...

```

...
Hit http://mt.archive.ubuntu.com trusty-backports/universe Translation-en
Fetched 1,157 kB in 8s (131 kB/s)
W: Failed to fetch http://mt.archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by deadflowr on 2014-09-25
[http://askubuntu.com/questions/41605/trouble-downloading-updates-due-to-a-hash-sum-mismatch-error](http://askubuntu.com/questions/41605/trouble-downloading-updates-due-to-a-hash-sum-mismatch-error)

Also, the linux-generic packages are for the kernel. Instead of patching an existing kernel, you get a totally new one; while keeping the old one is it was.
I guess the reason, or a reason would be that if any problems happen with the patched up kernel(the new one) you still have an older, non-patched, functional kernel you can still boot into and use it.
Or at least that's one way to look at it...

---

### Post by sim085 on 2014-09-25
> **deadflowr said:**
> [http://askubuntu.com/questions/41605/trouble-downloading-updates-due-to-a-hash-sum-mismatch-error](http://askubuntu.com/questions/41605/trouble-downloading-updates-due-to-a-hash-sum-mismatch-error)

That is strange ... I had found this solution while looking on the forum:

```

apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

```

to me it looks similar to the solution the post you posted. Anyways, doing what is suggested in that post (delete the contents of list) made apt-get update work :) Wonder what was so different.

---

