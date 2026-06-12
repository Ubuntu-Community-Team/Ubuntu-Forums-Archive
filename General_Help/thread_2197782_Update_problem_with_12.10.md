---
title: "Update problem with 12.10"
date: 2014-01-05
forum: General Help
---

### Post by alhamra_g on 2014-01-05
Dear All

Since last year:lolflag: I mean 2 weeks ago;), I have had a problem with updating my ubuntu 12.10. I get this message and I can't update the OS. would you please guide me how can I solve it?

```
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by grier-devon on 2014-01-05
Well with the PPA those are probably broken now so just remove them and then I would just remove those "cd" which can be done through software and driver. After removing the error's try sudo apt-get update in the terminal.

---

### Post by Bucky Ball on 2014-01-05
Welcome. You want to kill any PPA starting with: 

```
http://ppa.launchpad.net/joe-nationnet/
```

Open Software Sources (or you can get there via Update Manager>Settings) and go to 'Other Software' tab and untick anything with 'joe-nationnet' in it. Those PPAs are not being found.

```
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
```

Then:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by alhamra_g on 2014-01-05
> **Bucky Ball said:**
> Welcome. You want to kill any PPA starting with: 

```
http://ppa.launchpad.net/joe-nationnet/
```

Open Software Sources (or you can get there via Update Manager>Settings) and go to 'Other Software' tab and untick anything with 'joe-nationnet' in it. Those PPAs are not being found.

```
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-amd64/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/joe-nationnet/ppa/ubuntu/dists/quantal/main/binary-i386/Packages  404  Not Found
```

Then:

```
sudo apt-get update
sudo apt-get upgrade
```

Tnx my friend.
It's done. now only this error can be seen.
```
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download. They have been ignored, or old ones used instead.
```

what is this CD-Rom?

---

### Post by grahammechanical on 2014-01-05
cdrom? Compact Disk Read Only Memory. It is the cd or dvd disk that you used to install Ubuntu with. It can also be used as a repository of software. You will see it listed in Software Sources>Other Software.  There is a tick box called Cdrom with Ubuntu 12.10 'Quantal Quetxal.' You have have that box ticked.

Regards.

---

### Post by alhamra_g on 2014-01-05
> **grahammechanical said:**
> cdrom? Compact Disk Read Only Memory. It is the cd or dvd disk that you used to install Ubuntu with. It can also be used as a repository of software. You will see it listed in Software Sources>Other Software.  There is a tick box called Cdrom with Ubuntu 12.10 'Quantal Quetxal.' You have have that box ticked.

Regards.

Yep, I did untick it and every thing is OK now. Should I leave them untick for ever?

---

### Post by Bucky Ball on 2014-01-05
> **alhamra_g said:**
>  Should I leave them untick for ever?

Yes, unless you need to use the CD to get things from as a source. In that case, put CD in, tick these entries again, and run update. That scenario is unlikely though.

---

### Post by alhamra_g on 2014-01-06
Thank you all very much.

---

### Post by Bucky Ball on 2014-01-06
You're welcome. ;) Please mark thread as 'Solved' to help others by following the link in my signature and post a new thread for any future support issues. Enjoy!

---

