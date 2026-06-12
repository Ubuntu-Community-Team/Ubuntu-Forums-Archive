---
title: "Error &quot;Could not inialize the package information.&quot;"
date: 2013-01-02
forum: General Help
---

### Post by mhwittek on 2013-01-02
Hello All,
I am new to Ubuntu, and I received this following error that I am not sure what is causing it.:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


Any Ideas?

Thanks,
Mike W.

---

### Post by plucky on 2013-01-02
> **mhwittek said:**
> Hello All,
I am new to Ubuntu, and I received this following error that I am not sure what is causing it.:
'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


Any Ideas?

Thanks,
Mike W.

Welcome to the forum!

open A Terminal [CTRL+ALT+T]

and run ```
sudo rm /var/lib/apt/lists/* -vf
``` and then run ```
sudo apt-get update
```

The first command deletes all the index files in the /var/lib/apt/lists/ directory and the second command reloads the index files from the net.

Good Luck

---

### Post by mhwittek on 2013-01-02
Hello Plucky,
Thanks for the information. The information did fixed most of issue. I can run Software Update again. But during the "sudo apt-get update" command it stated that there were two issues that were not corrected. Now I get this new error window that is titled "Failed to download software repository information", and the body of the error reads as follows: Check your Internet Connection.

*in window:* W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

My Internet connection is working just fine. I would guess I would not be able to post this otherwise. 

Thanks for the help. 

Regards,
Mike Wittek

---

### Post by plucky on 2013-01-03
> W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)/dists/oneiric/main/binary-i386/Packages Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


That error means that for some reason, the Installation CDrom has been ticked as a source in your **Software Sources** list.

Open the **Settings** button in the **Update Manager** and un-tick the CDrom as a source.

Good Luck

---

### Post by ibjsb4 on 2013-01-03
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

And welcome to the forums  :)

---

