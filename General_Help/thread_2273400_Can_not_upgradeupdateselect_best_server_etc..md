---
title: "Can not upgrade/update/select best server etc."
date: 2015-04-13
forum: General Help
---

### Post by pantera989 on 2015-04-13
Hi guys, I'm looking at purchasing a new low power system to run Ubuntu on, in the mean time I'm running it in Virtual Box to get myself familiar with it again. I'm running an older version as it's an ISO I had lying around (11.04). 

I'm having problems with updating, it get the following message when I run apt-get update:

```
Ign http://nz.archive.ubuntu.com natty InRelease
Ign http://nz.archive.ubuntu.com natty Release.gpg
Ign http://nz.archive.ubuntu.com natty Release
Ign http://nz.archive.ubuntu.com natty/main TranslationIndex
Ign http://nz.archive.ubuntu.com natty/universe TranslationIndex
Err http://nz.archive.ubuntu.com natty/main amd64 Packages
  404  Not Found
Err http://nz.archive.ubuntu.com natty/universe amd64 Packages
  404  Not Found
Ign http://nz.archive.ubuntu.com natty/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com natty/main Translation-en
Ign http://nz.archive.ubuntu.com natty/universe Translation-en_NZ
Ign http://nz.archive.ubuntu.com natty/universe Translation-en
W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
riley@riley-VirtualBox:~$ sudo sed 's@http://in\.archive\.ubuntu\.com/@http://archive.ubuntu.com/@' -i /etc/apt/sources.list
riley@riley-VirtualBox:~$ sudo apt-get update
Ign http://nz.archive.ubuntu.com natty InRelease
Ign http://nz.archive.ubuntu.com natty Release.gpg
Ign http://nz.archive.ubuntu.com natty Release
Ign http://nz.archive.ubuntu.com natty/main TranslationIndex
Ign http://nz.archive.ubuntu.com natty/universe TranslationIndex
Err http://nz.archive.ubuntu.com natty/main amd64 Packages
  404  Not Found
Err http://nz.archive.ubuntu.com natty/universe amd64 Packages
  404  Not Found
Ign http://nz.archive.ubuntu.com natty/main Translation-en_NZ
Ign http://nz.archive.ubuntu.com natty/main Translation-en
Ign http://nz.archive.ubuntu.com natty/universe Translation-en_NZ
Ign http://nz.archive.ubuntu.com natty/universe Translation-en
W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/natty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/natty/universe/binary-amd64/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I've tried some trouble shooting I could find in these forums, but nothing seemed to work, I tried changing the download servers, I tried using the "select best server" which failed. I'm not having any problems accessing any websites, or downloading files and the host computers Internet is working fine.

---

### Post by dino99 on 2015-04-13
dont try to awake a dead release, that does not work indeed ):P

---

### Post by slickymaster on 2015-04-13
You're getting that message because 11.04 is EOL (End-of-Life) since October 28, 2012, and the repositories for older releases that are not supported (like 11.04, 11.10 and 13.04) get moved to an archive server.

Please have a read at the [Forums Staff recommendations on EOL Ubuntu releases]("http://ubuntuforums.org/showthread.php?t=2229730") sticky.

---

### Post by pantera989 on 2015-04-13
Thanks for the reply, from what I can tell there is no way to upgrade to a  new release, and I need to create a fresh install from a  supported release?

---

### Post by slickymaster on 2015-04-13
> **pantera989 said:**
> Thanks for the reply, from what I can tell there is no way to upgrade to a  new release, and I need to create a fresh install from a  supported release?
There are ways, but I would only recommend them if we're talking about production environments which you want to keep as stable as possible. Reinstalling is usually easier and faster, especially if you would have to upgrade through several releases, which would be your case.

---

### Post by pantera989 on 2015-04-14
Thanks for the help guys, downloaded a new distro and got it all back up and running.

---

