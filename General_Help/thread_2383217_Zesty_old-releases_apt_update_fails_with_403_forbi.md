---
title: "Zesty old-releases apt update fails with 403 forbidden"
date: 2018-01-22
forum: General Help
---

### Post by xrlange on 2018-01-22
I have an EOL'd Ubuntu of instance where I need a few key utilities before I can do a system switch. I have removed references to the standard repositories, switching them for old-releases.ubuntu.com:

```
root@pipeline-4199895698-vm761:/# cat /etc/apt/sources.list
## EOL upgrade sources.list
# Required
deb http://old-releases.ubuntu.com/ubuntu/ zesty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ zesty-security main restricted universe multiverse

# Optional
#deb http://old-releases.ubuntu.com/ubuntu/ zesty-backports main restricted universe multiverse
```

Then when I do a apt-get update it fails with a string of IGNOREs and ends with a summary stating HTTP 403 forbidden. This happens even if I clear the package cache. Here's an example:

```
root@pipeline-4199895698-vm761:/# rm -fr /var/lib/apt/lists/*
root@pipeline-4199895698-vm761:/# apt-get update
Ign:1 http://old-releases.ubuntu.com/ubuntu zesty InRelease
Ign:2 http://old-releases.ubuntu.com/ubuntu zesty-updates InRelease
Ign:3 http://download.opensuse.org/repositories/home:/laszlo_budai:/syslog-ng/xUbuntu_16.10 ./ InRelease
Ign:4 http://old-releases.ubuntu.com/ubuntu zesty-security InRelease
Get:5 http://download.opensuse.org/repositories/home:/laszlo_budai:/syslog-ng/xUbuntu_16.10 ./ Release [1056 B]
Ign:6 http://old-releases.ubuntu.com/ubuntu zesty Release
Get:7 http://download.opensuse.org/repositories/home:/laszlo_budai:/syslog-ng/xUbuntu_16.10 ./ Release.gpg [481 B]
Ign:8 http://old-releases.ubuntu.com/ubuntu zesty-updates Release
Get:9 http://download.opensuse.org/repositories/home:/laszlo_budai:/syslog-ng/xUbuntu_16.10 ./ Packages [87.1 kB]
Ign:10 http://old-releases.ubuntu.com/ubuntu zesty-security Release
Ign:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages
Ign:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted all Packages
Ign:13 http://old-releases.ubuntu.com/ubuntu zesty/main all Packages
Ign:14 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages
Ign:15 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages
Ign:16 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu zesty/universe all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu zesty/multiverse all Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse all Packages
Ign:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
Ign:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages
Ign:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages
Ign:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe all Packages
Ign:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main all Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu zesty-security/main all Packages
Ign:28 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse all Packages
Ign:29 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted all Packages
Ign:30 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages
Ign:31 http://old-releases.ubuntu.com/ubuntu zesty-security/universe all Packages
Ign:32 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages
Ign:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages
Ign:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted all Packages
Ign:13 http://old-releases.ubuntu.com/ubuntu zesty/main all Packages
Ign:14 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages
Ign:15 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages
Ign:16 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu zesty/universe all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu zesty/multiverse all Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse all Packages
Ign:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
Ign:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages
Ign:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages
Ign:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe all Packages
Ign:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main all Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu zesty-security/main all Packages
Ign:28 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse all Packages
Ign:29 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted all Packages
Ign:30 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages
Ign:31 http://old-releases.ubuntu.com/ubuntu zesty-security/universe all Packages
Ign:32 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages
Ign:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages
Ign:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted all Packages
Ign:13 http://old-releases.ubuntu.com/ubuntu zesty/main all Packages
Ign:14 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages
Ign:15 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages
Ign:16 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu zesty/universe all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu zesty/multiverse all Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse all Packages
Ign:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
Ign:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages
Ign:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages
Ign:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe all Packages
Ign:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main all Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu zesty-security/main all Packages
Ign:28 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse all Packages
Ign:29 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted all Packages
Ign:30 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages
Ign:31 http://old-releases.ubuntu.com/ubuntu zesty-security/universe all Packages
Ign:32 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages
Ign:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages
Ign:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted all Packages
Ign:13 http://old-releases.ubuntu.com/ubuntu zesty/main all Packages
Ign:14 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages
Ign:15 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages
Ign:16 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu zesty/universe all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu zesty/multiverse all Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse all Packages
Ign:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
Ign:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages
Ign:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages
Ign:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe all Packages
Ign:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main all Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu zesty-security/main all Packages
Ign:28 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse all Packages
Ign:29 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted all Packages
Ign:30 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages
Ign:31 http://old-releases.ubuntu.com/ubuntu zesty-security/universe all Packages
Ign:32 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages
Ign:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages
Ign:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted all Packages
Ign:13 http://old-releases.ubuntu.com/ubuntu zesty/main all Packages
Ign:14 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages
Ign:15 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages
Ign:16 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu zesty/universe all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu zesty/multiverse all Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse all Packages
Ign:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
Ign:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages
Ign:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages
Ign:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe all Packages
Ign:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main all Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu zesty-security/main all Packages
Ign:28 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse all Packages
Ign:29 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted all Packages
Ign:30 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages
Ign:31 http://old-releases.ubuntu.com/ubuntu zesty-security/universe all Packages
Ign:32 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages
Err:11 http://old-releases.ubuntu.com/ubuntu zesty/restricted amd64 Packages
  403  Forbidden
Ign:12 http://old-releases.ubuntu.com/ubuntu zesty/restricted all Packages
Ign:13 http://old-releases.ubuntu.com/ubuntu zesty/main all Packages
Ign:14 http://old-releases.ubuntu.com/ubuntu zesty/multiverse amd64 Packages
Ign:15 http://old-releases.ubuntu.com/ubuntu zesty/main amd64 Packages
Ign:16 http://old-releases.ubuntu.com/ubuntu zesty/universe amd64 Packages
Ign:17 http://old-releases.ubuntu.com/ubuntu zesty/universe all Packages
Ign:18 http://old-releases.ubuntu.com/ubuntu zesty/multiverse all Packages
Ign:19 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse all Packages
Err:20 http://old-releases.ubuntu.com/ubuntu zesty-updates/main amd64 Packages
  403  Forbidden
Ign:21 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted amd64 Packages
Ign:22 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe amd64 Packages
Ign:23 http://old-releases.ubuntu.com/ubuntu zesty-updates/universe all Packages
Ign:24 http://old-releases.ubuntu.com/ubuntu zesty-updates/main all Packages
Ign:25 http://old-releases.ubuntu.com/ubuntu zesty-updates/multiverse amd64 Packages
Ign:26 http://old-releases.ubuntu.com/ubuntu zesty-updates/restricted all Packages
Ign:27 http://old-releases.ubuntu.com/ubuntu zesty-security/main all Packages
Ign:28 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse all Packages
Ign:29 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted all Packages
Err:30 http://old-releases.ubuntu.com/ubuntu zesty-security/main amd64 Packages
  403  Forbidden
Ign:31 http://old-releases.ubuntu.com/ubuntu zesty-security/universe all Packages
Ign:32 http://old-releases.ubuntu.com/ubuntu zesty-security/multiverse amd64 Packages
Ign:33 http://old-releases.ubuntu.com/ubuntu zesty-security/restricted amd64 Packages
Ign:34 http://old-releases.ubuntu.com/ubuntu zesty-security/universe amd64 Packages
Fetched 88.6 kB in 32s (2747 B/s)
Reading package lists... Done
W: The repository 'http://old-releases.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://old-releases.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://old-releases.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/zesty/restricted/binary-amd64/Packages  403  Forbidden
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/zesty-updates/main/binary-amd64/Packages  403  Forbidden
E: Failed to fetch http://old-releases.ubuntu.com/ubuntu/dists/zesty-security/main/binary-amd64/Packages  403  Forbidden
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

What am I doing wrong that this would fail?

---

### Post by TheFu on 2018-01-22
Support for 17.04 ended earlier this month.  Move to 17.10 or load 16.04 LTS.

If you aren't willing to reload the OS every 6 months, please run only LTS releases.

---

### Post by xrlange on 2018-01-23
Hi, I said in the original post that I need to get a few utilities installed before switching. Correct me if I'm wrong, but the old-releases apt repo is for this purpose. Now, if that's true, do you know why it's not working in my situation?

---

