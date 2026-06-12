---
title: "Problem with apt repository keys"
date: 2023-10-14
forum: General Help
---

### Post by skorakora on 2023-10-14
Soo long time ago i did something that broke my server, and after that I have this problem. Today I want to fix this once and for all.

I tried to add gpg keys, but it still throws the same error

Problem is: when I run apt update I got NO_PUBKEY errors, even when I try to add those keys with gpg.

This is what I got after typinng "sudo apt update"
:
```


[FONT=monospace][COLOR=#000000]Get:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease [270 kB] [/COLOR]
Get:2 https://download.docker.com/linux/ubuntu jammy InRelease [48.9 kB]                                                                  
Get:3 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease [109 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu jammy-security InRelease [110 kB]
Ign:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Err:2 https://download.docker.com/linux/ubuntu jammy InRelease 
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EA0A9C3F273FCD8 
Ign:3 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease 
Get:6 https://repo.jellyfin.org/ubuntu jammy InRelease [6,636 B] 
Ign:4 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease 
Ign:5 http://gb.archive.ubuntu.com/ubuntu jammy-security InRelease 
Ign:6 https://repo.jellyfin.org/ubuntu jammy InRelease 
Reading package lists... Done 
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]GPG error: http://gb.archive.ubuntu.com/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]GPG error: https://download.docker.com/linux/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7EA0A9C3F273FCD8 [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]The repository 'https://download.docker.com/linux/ubuntu jammy InRelease' is not signed. [/COLOR]
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]Updating from such a repository can't be done securely, and is therefore disabled by default. [/COLOR]
[COLOR=#b26818]N: [/COLOR][COLOR=#000000]See apt-secure(8) manpage for repository creation and user configuration details. [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]GPG error: http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]GPG error: http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]GPG error: http://gb.archive.ubuntu.com/ubuntu jammy-security InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]GPG error: https://repo.jellyfin.org/ubuntu jammy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49023CD01DE21A7B [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'universe/binary-amd64/Packages' as repository 'https://repo.jellyfin.org/ubuntu jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?) [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'universe/i18n/Translation-en' as repository 'https://repo.jellyfin.org/ubuntu jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?) [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'universe/i18n/Translation-en_US' as repository 'https://repo.jellyfin.org/ubuntu jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?) [/COLOR]
[COLOR=#ffff54]**W: **[/COLOR][COLOR=#000000]Skipping acquire of configured file 'universe/cnf/Commands-amd64' as repository 'https://repo.jellyfin.org/ubuntu jammy InRelease' doesn't have the component 'universe' (component misspelt in sources.list?)[/COLOR]

[/FONT]


```

I have tried to add key [FONT=monospace][COLOR=#000000]871920D1991BC93C[/COLOR] by running [/FONT]```
[FONT=monospace][COLOR=#000000]sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 871920D1991BC93C[/COLOR][/FONT]
```[FONT=monospace] (and other ways to add the key)
But it did change anything. It still says NO_PUBKEY. It throws the same error for everything I try to install, so there is the same key issue with docker in log (this is clean docker install)


EDIT:
I have disabled systemd-resolved, enabling it breaks my network as this server works as a router as well.
I can start it temorarly to just download keys, as symlink in /etc/resolv.conf points to systemd-resolved. I have adguard installed and running on port 82
With systemd-resolved inactive everyting works fine but when activated I am unable to acess adguard on 192.168.0.1:82 and my custom DNS server (ping with direct ip works, but it fails with domain name)
The issue with keys was long before making my server as a router so this is not a reson of this problem. I am just adding this to save some time with troubleshooting.
[/FONT]

---

