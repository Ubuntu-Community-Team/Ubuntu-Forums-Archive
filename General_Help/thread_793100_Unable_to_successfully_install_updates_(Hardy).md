---
title: "Unable to successfully install updates (Hardy)"
date: 2008-05-13
forum: General Help
---

### Post by TheFuzzy0ne on 2008-05-13
Hi all. I'm having trouble installing updates using aptitude, apt-get and any other package manager. The download for the first package begins, but then seems to finish after about 20%, and then the same download starts over again, and seems to repeat in an endless cycle. It doesn't appear to be an issue with directory permissions (as I believe that apt-get will notify me if it was?), and I still have over 46GB of space left, so that can't be the issue.

Here's the output for apt-get upgrade:

```

root@fuzz-comp:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
  openssh-client openssh-server
The following packages will be upgraded:
  libssl0.9.8 openssl ssh
3 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 3215kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 2 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 3 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 4 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 5 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 6 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 7 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 8 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 9 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 10 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
4% [10 libssl0.9.8 135992/2828kB 4%]                 31.4kB/s 49710d 6h26min38s

```

As you can see, the same package appears to be downloading constantly, but what you can't see is that is never completing past 30%. As you can see, I need a dist-upgrade, so here's the output for that:

```

root@fuzz-comp:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  openssh-blacklist
The following packages will be upgraded:
  libssl0.9.8 openssh-client openssh-server openssl ssh
5 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6313kB of archives.
After this operation, 4301kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 2 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 3 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 4 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 5 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 6 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 7 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 8 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 9 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
Get: 10 http://security.ubuntu.com hardy-security/main libssl0.9.8 0.9.8g-4ubuntu3.1 [2828kB]
6% [10 libssl0.9.8 409600/2828kB 14%]                 30.4kB/s 49710d 6h25min3s

```

Once again, I hit the exact same problem.

I have even tried deleting /var/cache/apt/ and recreating the directory structure to no avail. I do have apt-cacher set up on my server, but I have bypassed it and still have the same problem.

Is this a Hardy bug, or has something gone seriously wrong for me? I have been able to do updates up until now, but I've no idea what's changed...

Any input would be appreciated.

---

### Post by minaev on 2008-05-13
You can try `apt-get -f install'

---

### Post by TheFuzzy0ne on 2008-05-13
Nothing... :(

```

root@fuzz-comp:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

Thanks for your reply.

---

### Post by minaev on 2008-05-13
Now that apt-get has finished `fix-broken' operation, try to run `apt-get update' and `apt-get safe-upgrade' again.

---

### Post by Seren on 2008-05-13
Same here. It is probably related to the repositories themselves and not your installation.

---

### Post by TheFuzzy0ne on 2008-05-13
Still no joy.

I had suspected it could have been a repository problem, but I tried it again with back-ports enabled, and get exactly the same problem on a different package (libcore4 or something of that elk). I have another PC running Gutsy, but it doesn't seem to be effected.

Can anyone think of any way for me to logically troubleshoot the problem, and perhaps rule out either the repositories or my setup. Ruling out the repos would be my preference.

The problem could be the security repo as a whole. Does anyone know of any mirror servers for the security repository? My archive repos are set to use VirginMedia, but I don't think I can download security updates from them.

Thanks for such prompt responses.

---

### Post by Seren on 2008-05-13
> **TheFuzzy0ne said:**
> Still no joy.

I had suspected it could have been a repository problem, but I tried it again with back-ports enabled, and get exactly the same problem on a different package (libcore4 or something of that elk). I have another PC running Gutsy, but it doesn't seem to be effected.

Can anyone think of any way for me to logically troubleshoot the problem, and perhaps rule out either the repositories or my setup. Ruling out the repos would be my preference.

The problem could be the security repo as a whole. Does anyone know of any mirror servers for the security repository? My archive repos are set to use VirginMedia, but I don't think I can download security updates from them.

Thanks for such prompt responses.


I had the same problem, I changed my repositories to point on the main server again, and the upgrade went fine.

There is something wrong with the mirrors, you can try to switch, or wait till the mirrors are fixed.

---

### Post by TheFuzzy0ne on 2008-05-13
> **Seren said:**
> I had the same problem, I changed my repositories to point on the main server again, and the upgrade went fine.

There is something wrong with the mirrors, you can try to switch, or wait till the mirrors are fixed.

That's good enough for me, thanks! :guitar:

---

### Post by dob99 on 2008-06-19
I have this same problem and I've figured out what the issue is. It's a combination of a problem with the mirror and an (arguable) issue with apt-cacher.

The problem is the mirror (for some reason) drops the connection while you're in the middle of the download. If you were using apt-get directly (not through the apt-cacher "proxy"), it would simply reconnect and resume the download. However, apt-cacher sees that the downloaded file is the wrong size and simply throws it away. This causes the client to re-request the file and apt-cacher starts again.

The mirror I'm using is the Irish archive (run by HeaNet) and the only solution I've been able to figure out is to (as suggested above) switch back to the main repository. This is, however, far from ideal and negates the advantage of using mirrors.

Created [Bug 241350]("https://bugs.launchpad.net/ubuntu/+source/apt-cacher/+bug/241350") for the issue.

---

