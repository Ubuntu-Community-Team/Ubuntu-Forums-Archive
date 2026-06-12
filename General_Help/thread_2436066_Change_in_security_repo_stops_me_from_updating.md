---
title: "Change in security repo stops me from updating"
date: 2020-01-30
forum: General Help
---

### Post by t0p on 2020-01-30
I'm running Lubuntu 19.10.  I have added Kali repos and installed some Kali tools through the script Katoolin.  I have used Katoolin for a while without problem.  Until a few days ago. Now, when I try to run **apt-get update** I get this error:

```
t0p@pluto:~$ sudo apt-get update
Hit:1 [http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu](http://ppa.launchpad.net/bookworm-team/bookworm/ubuntu) eoan InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan InRelease               
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security InRelease [97.5 kB]
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-backports InRelease             
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) eoan-updates InRelease [97.5 kB]     
Hit:6 [http://ftp.hands.com/kali](http://ftp.hands.com/kali) kali-rolling InRelease   
Reading package lists... Done                    
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Origin' value from 'Kali' to 'Ubuntu'
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Label' value from '' to 'Ubuntu'
N: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Version' value from '' to '19.10'
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Suite' value from 'kali-rolling' to 'eoan-security'
E: Repository 'http://security.ubuntu.com/ubuntu eoan-security InRelease' changed its 'Codename' value from 'kali-rolling' to 'eoan'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
E: Repository 'http://archive.ubuntu.com/ubuntu eoan-updates InRelease' changed its 'Origin' value from 'Kali' to 'Ubuntu'
E: Repository 'http://archive.ubuntu.com/ubuntu eoan-updates InRelease' changed its 'Label' value from '' to 'Ubuntu'
N: Repository 'http://archive.ubuntu.com/ubuntu eoan-updates InRelease' changed its 'Version' value from '' to '19.10'
E: Repository 'http://archive.ubuntu.com/ubuntu eoan-updates InRelease' changed its 'Suite' value from 'kali-rolling' to 'eoan-updates'
E: Repository 'http://archive.ubuntu.com/ubuntu eoan-updates InRelease' changed its 'Codename' value from 'kali-rolling' to 'eoan'
N: This must be accepted explicitly before updates for this repository can be applied. See apt-secure(8) manpage for details.
t0p@pluto:~$ 

```

I deleted  the kali repos, through the katoolin script, hoping that would solve the problem.  But the next step in removing katoolin involves **sudo apt-get update** and I get the same error as above.

What should I do to deal with this? How do I "explicitly accept" these changes? I have read the apt-secure man-page and am none the wiser.  Can someone explain it a bit slower to me?   Cheers.

---

