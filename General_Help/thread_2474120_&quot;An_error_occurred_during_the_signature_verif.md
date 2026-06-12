---
title: "&quot;An error occurred during the signature verification.&quot; in apt-update after adding key"
date: 2022-04-22
forum: General Help
---

### Post by yahyamousavi70 on 2022-04-22
the server I work on is a Debian 9.13 OS and "mysql Ver 14.14 Distrib 5.7.34,". I tried downloading package information from all configured sources with the following command:


```

sudo apt update

```


then I faced to the following error:
```

Hit:1 http://security.debian.org stretch/updates InRelease
Hit:2 http://packages.cloud.google.com/apt google-cloud-monitoring-stretch-all InRelease
Hit:3 http://packages.cloud.google.com/apt cloud-sdk-stretch InRelease
Hit:4 http://packages.cloud.google.com/apt google-compute-engine-stretch-stable InRelease
Ign:5 http://deb.debian.org/debian stretch InRelease
Hit:6 http://repo.mysql.com/apt/debian stretch InRelease
Hit:7 http://packages.cloud.google.com/apt google-cloud-packages-archive-keyring-stretch InRelease
Hit:8 http://deb.debian.org/debian stretch-updates InRelease
Hit:9 https://packages.cloud.google.com/apt google-cloud-logging-stretch-all InRelease
Hit:10 http://deb.debian.org/debian stretch-backports InRelease
Hit:11 http://deb.debian.org/debian stretch Release
Get:12 https://packages.sury.org/php stretch InRelease [6,839 B]
Err:6 http://repo.mysql.com/apt/debian stretch InRelease
  The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
Err:12 https://packages.sury.org/php stretch InRelease
  The following signatures were invalid: EXPKEYSIG B188E2B695BD4743 DEB.SURY.ORG Automatic Signing Key <deb@sury.org>
Fetched 6,839 B in 1s (5,504 B/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
10 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repo.mysql.com/apt/debian stretch InRelease: The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://packages.sury.org/php stretch InRelease: The following signatures were invalid: EXPKEYSIG B188E2B695BD4743 DEB.SURY.ORG Automatic Signing Key <deb@sury.org>
W: Failed to fetch http://repo.mysql.com/apt/debian/dists/stretch/InRelease  The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
W: Failed to fetch https://packages.sury.org/php/dists/stretch/InRelease  The following signatures were invalid: EXPKEYSIG B188E2B695BD4743 DEB.SURY.ORG Automatic Signing Key <deb@sury.org>
W: Some index files failed to download. They have been ignored, or old ones used instead.

```


then for fixing the issue of expired signatures I did a long journey, and faced to some problems , so I thought maybe I did something wrong, so I explain the setps I followed in details. after reseacrh I conculded to update expired keys as the following:


```

sudo apt-key list

```


then I saw this:


```

/etc/apt/trusted.gpg
--------------------
pub   dsa1024 2003-02-03 [SCA] [expired: 2022-02-16]
      A4A9 4068 76FC BD3C 4567  70C8 8C71 8D3B 5072 E1F5
uid           [ expired] MySQL Release Engineering <mysql-build@oss.oracle.com>


pub   rsa3072 2019-03-18 [SC] [expired: 2021-03-17]
      1505 8500 A023 5D97 F5D1  0063 B188 E2B6 95BD 4743
uid           [ expired] DEB.SURY.ORG Automatic Signing Key <deb@sury.org>


/etc/apt/trusted.gpg.d/debian-archive-bullseye-automatic.gpg
------------------------------------------------------------
pub   rsa4096 2021-01-17 [SC] [expires: 2029-01-15]
      1F89 983E 0081 FDE0 18F3  CC96 73A4 F27B 8DD4 7936
uid           [ unknown] Debian Archive Automatic Signing Key (11/bullseye) <ftpmaster@debian.org>
sub   rsa4096 2021-01-17 [S] [expires: 2029-01-15]


/etc/apt/trusted.gpg.d/debian-archive-bullseye-security-automatic.gpg
---------------------------------------------------------------------
pub   rsa4096 2021-01-17 [SC] [expires: 2029-01-15]
      AC53 0D52 0F2F 3269 F5E9  8313 A484 4904 4AAD 5C5D
uid           [ unknown] Debian Security Archive Automatic Signing Key (11/bullseye) <ftpmaster@debian.org>
sub   rsa4096 2021-01-17 [S] [expires: 2029-01-15]


/etc/apt/trusted.gpg.d/debian-archive-bullseye-stable.gpg
---------------------------------------------------------
pub   rsa4096 2021-02-13 [SC] [expires: 2029-02-11]
      A428 5295 FC7B 1A81 6000  62A9 605C 66F0 0D6C 9793
uid           [ unknown] Debian Stable Release Key (11/bullseye) <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/debian-archive-buster-automatic.gpg
----------------------------------------------------------
pub   rsa4096 2019-04-14 [SC] [expires: 2027-04-12]
      80D1 5823 B7FD 1561 F9F7  BCDD DC30 D7C2 3CBB ABEE
uid           [ unknown] Debian Archive Automatic Signing Key (10/buster) <ftpmaster@debian.org>
sub   rsa4096 2019-04-14 [S] [expires: 2027-04-12]


/etc/apt/trusted.gpg.d/debian-archive-buster-security-automatic.gpg
-------------------------------------------------------------------
pub   rsa4096 2019-04-14 [SC] [expires: 2027-04-12]
      5E61 B217 265D A980 7A23  C5FF 4DFA B270 CAA9 6DFA
uid           [ unknown] Debian Security Archive Automatic Signing Key (10/buster) <ftpmaster@debian.org>
sub   rsa4096 2019-04-14 [S] [expires: 2027-04-12]


/etc/apt/trusted.gpg.d/debian-archive-buster-stable.gpg
-------------------------------------------------------
pub   rsa4096 2019-02-05 [SC] [expires: 2027-02-03]
      6D33 866E DD8F FA41 C014  3AED DCC9 EFBF 77E1 1517
uid           [ unknown] Debian Stable Release Key (10/buster) <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/debian-archive-jessie-automatic.gpg
----------------------------------------------------------
pub   rsa4096 2014-11-21 [SC] [expires: 2022-11-19]
      126C 0D24 BD8A 2942 CC7D  F8AC 7638 D044 2B90 D010
uid           [ unknown] Debian Archive Automatic Signing Key (8/jessie) <ftpmaster@debian.org>


/etc/apt/trusted.gpg.d/debian-archive-jessie-security-automatic.gpg
-------------------------------------------------------------------
pub   rsa4096 2014-11-21 [SC] [expires: 2022-11-19]
      D211 6914 1CEC D440 F2EB  8DDA 9D6D 8F6B C857 C906
uid           [ unknown] Debian Security Archive Automatic Signing Key (8/jessie) <ftpmaster@debian.org>


/etc/apt/trusted.gpg.d/debian-archive-jessie-stable.gpg
-------------------------------------------------------
pub   rsa4096 2013-08-17 [SC] [expired: 2021-08-15]
      75DD C3C4 A499 F1A1 8CB5  F3C8 CBF8 D6FD 518E 17E1
uid           [ expired] Jessie Stable Release Key <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/debian-archive-stretch-automatic.gpg
-----------------------------------------------------------
pub   rsa4096 2017-05-22 [SC] [expires: 2025-05-20]
      E1CF 20DD FFE4 B89E 8026  58F1 E0B1 1894 F66A EC98
uid           [ unknown] Debian Archive Automatic Signing Key (9/stretch) <ftpmaster@debian.org>
sub   rsa4096 2017-05-22 [S] [expires: 2025-05-20]


/etc/apt/trusted.gpg.d/debian-archive-stretch-security-automatic.gpg
--------------------------------------------------------------------
pub   rsa4096 2017-05-22 [SC] [expires: 2025-05-20]
      6ED6 F5CB 5FA6 FB2F 460A  E88E EDA0 D238 8AE2 2BA9
uid           [ unknown] Debian Security Archive Automatic Signing Key (9/stretch) <ftpmaster@debian.org>
sub   rsa4096 2017-05-22 [S] [expires: 2025-05-20]


/etc/apt/trusted.gpg.d/debian-archive-stretch-stable.gpg
--------------------------------------------------------
pub   rsa4096 2017-05-20 [SC] [expires: 2025-05-18]
      067E 3C45 6BAE 240A CEE8  8F6F EF0F 382A 1A7B 6500
uid           [ unknown] Debian Stable Release Key (9/stretch) <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/google-cloud-packages-archive-keyring.gpg
----------------------------------------------------------------
pub   rsa2048 2021-03-01 [SC] [expires: 2023-03-02]
      7F92 E05B 3109 3BEF 5A3C  2D38 FEEA 9169 307E A071
uid           [ unknown] Rapture Automatic Signing Key (cloud-rapture-signing-key-2021-03-01-08_01_09.pub)
sub   rsa2048 2021-03-01 [E]


pub   rsa2048 2020-12-04 [SC] [expires: 2022-12-04]
      59FE 0256 8272 69DC 8157  8F92 8B57 C5C2 836F 4BEB
uid           [ unknown] gLinux Rapture Automatic Signing Key (//depot/google3/production/borg/cloud-rapture/keys/cloud-rapture-pubkeys/cloud-rapture-signing-key-2020-12-03-16_08_05.pub) <glinux-team@google.com>
sub   rsa2048 2020-12-04 [E]
so as it is shown here the three key are expired:


pub   dsa1024 2003-02-03 [SCA] [expired: 2022-02-16]
      A4A9 4068 76FC BD3C 4567  70C8 8C71 8D3B 5072 E1F5
uid           [ expired] MySQL Release Engineering <mysql-build@oss.oracle.com>


pub   rsa3072 2019-03-18 [SC] [expired: 2021-03-17]
      1505 8500 A023 5D97 F5D1  0063 B188 E2B6 95BD 4743
uid           [ expired] DEB.SURY.ORG Automatic Signing Key <deb@sury.org>


pub   rsa4096 2013-08-17 [SC] [expired: 2021-08-15]
      75DD C3C4 A499 F1A1 8CB5  F3C8 CBF8 D6FD 518E 17E1
uid           [ expired] Jessie Stable Release Key <debian-release@lists.debian.org>

```


so I tried the following command:


```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4A9406876FCBD3C456770C88C718D3B5072E1F5

```


result:


```

Executing: /tmp/apt-key-gpghome.8n1JFs3V5i/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys A4A9406876FCBD3C456770C88C718D3B5072E1F5
gpg: failed to start the dirmngr '/usr/bin/dirmngr': No such file or directory
gpg: connecting dirmngr at '/tmp/apt-key-gpghome.8n1JFs3V5i/S.dirmngr' failed: No such file or directory
gpg: keyserver receive failed: No dirmngr

```


so after research, I did the following:


```

sudo apt install dirmngr --install-recommends

```


result:


```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  dbus-user-session libpam-systemd pinentry-gnome3 tor
The following NEW packages will be installed:
  dirmngr
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
2 not fully installed or removed.
Need to get 597 kB of archives.
After this operation, 1,114 kB of additional disk space will be used.
Get:1 http://deb.debian.org/debian stretch/main amd64 dirmngr amd64 2.1.18-8~deb9u4 [597 kB]
Fetched 597 kB in 0s (7,412 kB/s)
Selecting previously unselected package dirmngr.
(Reading database ... 68920 files and directories currently installed.)
Preparing to unpack .../dirmngr_2.1.18-8~deb9u4_amd64.deb ...
Unpacking dirmngr (2.1.18-8~deb9u4) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up dirmngr (2.1.18-8~deb9u4) ...
Setting up google-fluentd (1.8.7-1) ...
Conffile /etc/google-fluentd/google-fluentd.conf has been modified. Remain untouched.
Conffile /etc/google-fluentd/baseline/google-fluentd.conf has been modified. Remain untouched.
Job for google-fluentd.service failed because the control process exited with error code.
See "systemctl status google-fluentd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript google-fluentd, action "start" failed.
&#9679; google-fluentd.service - LSB: data collector for Treasure Data
   Loaded: loaded (/etc/init.d/google-fluentd; generated; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2022-04-21 16:26:02 UTC; 9ms ago
     Docs: man:systemd-sysv-generator(8)
  Process: 21302 ExecStart=/etc/init.d/google-fluentd start (code=exited, status=1/FAILURE)


Apr 21 16:26:02 marketing-vm systemd[1]: Starting LSB: data collector for Treasure Data...
Apr 21 16:26:02 marketing-vm google-fluentd[21302]: Starting google-fluentd 1.8.7: Disabled via metadata ... (warning).
Apr 21 16:26:02 marketing-vm google-fluentd[21302]: google-fluentd ... failed!
Apr 21 16:26:02 marketing-vm systemd[1]: google-fluentd.service: Control process exited, code=exited status=1
Apr 21 16:26:02 marketing-vm systemd[1]: Failed to start LSB: data collector for Treasure Data.
Apr 21 16:26:02 marketing-vm systemd[1]: google-fluentd.service: Unit entered failed state.
Apr 21 16:26:02 marketing-vm systemd[1]: google-fluentd.service: Failed with result 'exit-code'.
dpkg: error processing package google-fluentd (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of google-fluentd-catch-all-config:
 google-fluentd-catch-all-config depends on google-fluentd (>= 1.3.0); however:
  Package google-fluentd is not configured yet.


dpkg: error processing package google-fluentd-catch-all-config (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 google-fluentd
 google-fluentd-catch-all-config
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I ran the following command after research and the result after that:


```

admin@marketing-vm:~$ systemctl status google-fluentd.service
Failed to connect to bus: No such file or directory

```


how ever previous command returned an error but it seems that required dirmngr was installed succesfully and I assumed this is something related to google cloud server and I ingnored research about it. but if you know what should I do regarding it I will be appreciate it. but let's continue as it is not my main issue then I tried the following command again


```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A4A9406876FCBD3C456770C88C718D3B5072E1F5

```


result:


```

Executing: /tmp/apt-key-gpghome.q3eZMOsbBP/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys A4A9406876FCBD3C456770C88C718D3B5072E1F5
gpg: key 8C718D3B5072E1F5: 4 duplicate signatures removed
gpg: key 8C718D3B5072E1F5: 60 signatures not checked due to missing keys
gpg: key 8C718D3B5072E1F5: "MySQL Release Engineering <mysql-build@oss.oracle.com>" 33 new signatures
gpg: Total number processed: 1
gpg:         new signatures: 33

```


and


```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 15058500A0235D97F5D10063B188E2B695BD4743

```


result:


```

Executing: /tmp/apt-key-gpghome.NYzCNLi5bV/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 15058500A0235D97F5D10063B188E2B695BD4743
gpg: key B188E2B695BD4743: 1 signature not checked due to a missing key
gpg: key B188E2B695BD4743: "DEB.SURY.ORG Automatic Signing Key <deb@sury.org>" 3 new signatures
gpg: Total number processed: 1
gpg:         new signatures: 3

```


and


```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 75DDC3C4A499F1A18CB5F3C8CBF8D6FD518E17E1

```


result:


```

Executing: /tmp/apt-key-gpghome.shHWXIw0ob/gpg.1.sh --keyserver keyserver.ubuntu.com --recv-keys 75DDC3C4A499F1A18CB5F3C8CBF8D6FD518E17E1
gpg: key CBF8D6FD518E17E1: 12 signatures not checked due to missing keys
gpg: key CBF8D6FD518E17E1: "Jessie Stable Release Key <debian-release@lists.debian.org>" 10 new signatures
gpg: Total number processed: 1
gpg:         new signatures: 10

```


then when I ran sudo apt update I just saw only one remaining signature issue:


```

Hit:1 http://packages.cloud.google.com/apt google-cloud-monitoring-stretch-all InRelease
Ign:2 http://deb.debian.org/debian stretch InRelease
Hit:3 http://deb.debian.org/debian stretch-updates InRelease
Hit:4 http://deb.debian.org/debian stretch-backports InRelease
Hit:5 http://security.debian.org stretch/updates InRelease
Hit:6 http://packages.cloud.google.com/apt cloud-sdk-stretch InRelease
Hit:7 http://packages.cloud.google.com/apt google-compute-engine-stretch-stable InRelease
Hit:8 http://repo.mysql.com/apt/debian stretch InRelease
Hit:9 http://packages.cloud.google.com/apt google-cloud-packages-archive-keyring-stretch InRelease
Hit:10 http://deb.debian.org/debian stretch Release
Hit:11 https://packages.cloud.google.com/apt google-cloud-logging-stretch-all InRelease
Get:12 https://packages.sury.org/php stretch InRelease [6,839 B]
Err:8 http://repo.mysql.com/apt/debian stretch InRelease
  The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
Get:14 https://packages.sury.org/php stretch/main amd64 Packages [356 kB]
Fetched 363 kB in 2s (149 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repo.mysql.com/apt/debian stretch InRelease: The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
W: Failed to fetch http://repo.mysql.com/apt/debian/dists/stretch/InRelease  The following signatures were invalid: EXPKEYSIG 8C718D3B5072E1F5 MySQL Release Engineering <mysql-build@oss.oracle.com>
W: Some index files failed to download. They have been ignored, or old ones used instead.

```


maybe I was wrong but I did the following based on the log again:


```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8C718D3B5072E1F5

```


result:


gpg: key 8C718D3B5072E1F5: 4 duplicate signatures removed
gpg: key 8C718D3B5072E1F5: 60 signatures not checked due to missing keys
gpg: key 8C718D3B5072E1F5: "MySQL Release Engineering <mysql-build@oss.oracle.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
so I searched about it and I followed the instructions on the following documentation:


[https://dev.mysql.com/doc/refman/8.0/en/checking-gpg-signature.html](https://dev.mysql.com/doc/refman/8.0/en/checking-gpg-signature.html)


based on of what was recommened as here which was reported same issue:


[https://ubuntuforums.org/showthread.php?t=2415997](https://ubuntuforums.org/showthread.php?t=2415997)


as following:
```

sudo nano /home/admin/mysql_pubkey.asc

```


and I copy and paste the PGP PUBLIC KEY BLOCK mentioned in the documentation there. and saved it. then:


```

gpg --import /home/admin/mysql_pubkey.asc

```


result:


```

gpg: /home/admin/.gnupg/trustdb.gpg: trustdb created
gpg: key 467B942D3A79BD29: public key "MySQL Release Engineering <mysql-build@os                                                                                                                     s.oracle.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1

```


I do not know why the key 467B942D3A79BD29 is different from what document says which is 3A79BD29 . any way now when I run ```
 sudo apt-key list 
``` I see the following keys:


```

/etc/apt/trusted.gpg
--------------------
pub   rsa3072 2019-03-18 [SC] [expires: 2024-02-16]
      1505 8500 A023 5D97 F5D1  0063 B188 E2B6 95BD 4743
uid           [ unknown] DEB.SURY.ORG Automatic Signing Key <deb@sury.org>
sub   rsa3072 2019-03-18 [E] [expires: 2024-02-16]


pub   rsa4096 2021-12-14 [SC] [expires: 2023-12-14]
      859B E8D7 C586 F538 430B  19C2 467B 942D 3A79 BD29
uid           [ unknown] MySQL Release Engineering <mysql-build@oss.oracle.com>
sub   rsa4096 2021-12-14 [E] [expires: 2023-12-14]


/etc/apt/trusted.gpg.d/debian-archive-bullseye-automatic.gpg
------------------------------------------------------------
pub   rsa4096 2021-01-17 [SC] [expires: 2029-01-15]
      1F89 983E 0081 FDE0 18F3  CC96 73A4 F27B 8DD4 7936
uid           [ unknown] Debian Archive Automatic Signing Key (11/bullseye) <ftpmaster@debian.org>
sub   rsa4096 2021-01-17 [S] [expires: 2029-01-15]


/etc/apt/trusted.gpg.d/debian-archive-bullseye-security-automatic.gpg
---------------------------------------------------------------------
pub   rsa4096 2021-01-17 [SC] [expires: 2029-01-15]
      AC53 0D52 0F2F 3269 F5E9  8313 A484 4904 4AAD 5C5D
uid           [ unknown] Debian Security Archive Automatic Signing Key (11/bullseye) <ftpmaster@debian.org>
sub   rsa4096 2021-01-17 [S] [expires: 2029-01-15]


/etc/apt/trusted.gpg.d/debian-archive-bullseye-stable.gpg
---------------------------------------------------------
pub   rsa4096 2021-02-13 [SC] [expires: 2029-02-11]
      A428 5295 FC7B 1A81 6000  62A9 605C 66F0 0D6C 9793
uid           [ unknown] Debian Stable Release Key (11/bullseye) <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/debian-archive-buster-automatic.gpg
----------------------------------------------------------
pub   rsa4096 2019-04-14 [SC] [expires: 2027-04-12]
      80D1 5823 B7FD 1561 F9F7  BCDD DC30 D7C2 3CBB ABEE
uid           [ unknown] Debian Archive Automatic Signing Key (10/buster) <ftpmaster@debian.org>
sub   rsa4096 2019-04-14 [S] [expires: 2027-04-12]


/etc/apt/trusted.gpg.d/debian-archive-buster-security-automatic.gpg
-------------------------------------------------------------------
pub   rsa4096 2019-04-14 [SC] [expires: 2027-04-12]
      5E61 B217 265D A980 7A23  C5FF 4DFA B270 CAA9 6DFA
uid           [ unknown] Debian Security Archive Automatic Signing Key (10/buster) <ftpmaster@debian.org>
sub   rsa4096 2019-04-14 [S] [expires: 2027-04-12]


/etc/apt/trusted.gpg.d/debian-archive-buster-stable.gpg
-------------------------------------------------------
pub   rsa4096 2019-02-05 [SC] [expires: 2027-02-03]
      6D33 866E DD8F FA41 C014  3AED DCC9 EFBF 77E1 1517
uid           [ unknown] Debian Stable Release Key (10/buster) <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/debian-archive-jessie-automatic.gpg
----------------------------------------------------------
pub   rsa4096 2014-11-21 [SC] [expires: 2022-11-19]
      126C 0D24 BD8A 2942 CC7D  F8AC 7638 D044 2B90 D010
uid           [ unknown] Debian Archive Automatic Signing Key (8/jessie) <ftpmaster@debian.org>


/etc/apt/trusted.gpg.d/debian-archive-jessie-security-automatic.gpg
-------------------------------------------------------------------
pub   rsa4096 2014-11-21 [SC] [expires: 2022-11-19]
      D211 6914 1CEC D440 F2EB  8DDA 9D6D 8F6B C857 C906
uid           [ unknown] Debian Security Archive Automatic Signing Key (8/jessie) <ftpmaster@debian.org>


/etc/apt/trusted.gpg.d/debian-archive-jessie-stable.gpg
-------------------------------------------------------
pub   rsa4096 2013-08-17 [SC] [expired: 2021-08-15]
      75DD C3C4 A499 F1A1 8CB5  F3C8 CBF8 D6FD 518E 17E1
uid           [ expired] Jessie Stable Release Key <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/debian-archive-stretch-automatic.gpg
-----------------------------------------------------------
pub   rsa4096 2017-05-22 [SC] [expires: 2025-05-20]
      E1CF 20DD FFE4 B89E 8026  58F1 E0B1 1894 F66A EC98
uid           [ unknown] Debian Archive Automatic Signing Key (9/stretch) <ftpmaster@debian.org>
sub   rsa4096 2017-05-22 [S] [expires: 2025-05-20]


/etc/apt/trusted.gpg.d/debian-archive-stretch-security-automatic.gpg
--------------------------------------------------------------------
pub   rsa4096 2017-05-22 [SC] [expires: 2025-05-20]
      6ED6 F5CB 5FA6 FB2F 460A  E88E EDA0 D238 8AE2 2BA9
uid           [ unknown] Debian Security Archive Automatic Signing Key (9/stretch) <ftpmaster@debian.org>
sub   rsa4096 2017-05-22 [S] [expires: 2025-05-20]


/etc/apt/trusted.gpg.d/debian-archive-stretch-stable.gpg
--------------------------------------------------------
pub   rsa4096 2017-05-20 [SC] [expires: 2025-05-18]
      067E 3C45 6BAE 240A CEE8  8F6F EF0F 382A 1A7B 6500
uid           [ unknown] Debian Stable Release Key (9/stretch) <debian-release@lists.debian.org>


/etc/apt/trusted.gpg.d/google-cloud-packages-archive-keyring.gpg
----------------------------------------------------------------
pub   rsa2048 2021-03-01 [SC] [expires: 2023-03-02]
      7F92 E05B 3109 3BEF 5A3C  2D38 FEEA 9169 307E A071
uid           [ unknown] Rapture Automatic Signing Key (cloud-rapture-signing-key-2021-03-01-08_01_09.pub)
sub   rsa2048 2021-03-01 [E]


pub   rsa2048 2020-12-04 [SC] [expires: 2022-12-04]
      59FE 0256 8272 69DC 8157  8F92 8B57 C5C2 836F 4BEB
uid           [ unknown] gLinux Rapture Automatic Signing Key (//depot/google3/production/borg/cloud-rapture/keys/cloud-rapture-pubkeys/cloud-rapture-signing-key-2020-12-03-16_08_05.pub) <glinux-team@google.com>
sub   rsa2048 2020-12-04 [E]

```


but still I face same result when I run sudo apt update


```

Hit:1 http://packages.cloud.google.com/apt google-cloud-monitoring-stretch-all InRelease
Ign:2 http://deb.debian.org/debian stretch InRelease
Hit:3 http://security.debian.org stretch/updates InRelease
Hit:4 http://packages.cloud.google.com/apt cloud-sdk-stretch InRelease
Hit:5 http://deb.debian.org/debian stretch-updates InRelease
Hit:6 http://packages.cloud.google.com/apt google-compute-engine-stretch-stable InRelease
Hit:7 http://deb.debian.org/debian stretch-backports InRelease
Hit:8 http://packages.cloud.google.com/apt google-cloud-packages-archive-keyring-stretch InRelease
Hit:9 http://deb.debian.org/debian stretch Release
Hit:10 http://repo.mysql.com/apt/debian stretch InRelease
Hit:11 https://packages.cloud.google.com/apt google-cloud-logging-stretch-all InRelease
Hit:12 https://packages.sury.org/php stretch InRelease
Err:10 http://repo.mysql.com/apt/debian stretch InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C718D3B5072E1F5
Reading package lists... Done
Building dependency tree
Reading state information... Done
26 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repo.mysql.com/apt/debian stretch InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C718D3B5072E1F5
W: Failed to fetch http://repo.mysql.com/apt/debian/dists/stretch/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8C718D3B5072E1F5
W: Some index files failed to download. They have been ignored, or old ones used instead.

```


I also tried


```

gpg --delete-key 8C718D3B5072E1F5

```


result:


```

gpg (GnuPG) 2.1.18; Copyright (C) 2017 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


gpg: key "8C718D3B5072E1F5" not found: Not found
gpg: 8C718D3B5072E1F5: delete key failed: Not found

```


and


```

 gpg --keyid-format=long --with-fingerprint --list-keys 8C718D3B5072E1F5

```


result:


```

gpg: error reading key: No public key

```


i will appreciate it if you can help me to solve this issue

---

