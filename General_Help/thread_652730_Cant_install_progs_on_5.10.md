---
title: "Cant install progs on 5.10?"
date: 2007-12-29
forum: General Help
---

### Post by BruceWayne on 2007-12-29
I cant install anything on 5.10. It keeps giving me this-

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

Any suggestions? Its driving me nuts. :(

---

### Post by Ripfox on 2007-12-29
Why are you using 5.10 is my question...

[http://ubuntuforums.org/showthread.php?t=132835](http://ubuntuforums.org/showthread.php?t=132835)

> sudo apt-get update

---

### Post by BruceWayne on 2007-12-29
i get this in response to that...

Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper ReleaseIgn cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages
Fetched 1B in 0s (2B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/dapper/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/dapper/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Hallvor on 2007-12-29
You are better off with a clean reinstall.

---

### Post by Sef on 2007-12-29
Breezy Badger, 5.10, is no longer supported.   Either update to Dapper Duck, 6.06, or download the current version of Ubuntu, Gutsy Gibbon, 7.10.  To download it, go to [ubuntu.com]("http://ubuntu.com").

---

