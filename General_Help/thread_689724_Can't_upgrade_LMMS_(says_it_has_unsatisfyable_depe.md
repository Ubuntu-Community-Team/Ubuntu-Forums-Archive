---
title: "Can't upgrade LMMS (says it has unsatisfyable dependencies but it doesn't!)"
date: 2008-02-06
forum: General Help
---

### Post by Envergure on 2008-02-06
LMMS appears in the Synaptic as version 0.3.0 when in reality 0.3.1 is out.  I downloaded the .deb from [[COLOR="Blue"]**here**[/COLOR]]("http://ftp.ubuntulinux.org/ubuntu/pool/universe/l/lmms/") (lmms_0.3.1-1ubuntu1_i386.deb) but when I try to run it the deb installer says "error:  some dependancy can't be satisfied:  libc6," but the synaptic says it's there, and it is.

---

### Post by Don Gatto on 2008-02-07
Hello,

this might be because you have the proper packages, but not the proper version. Open the package with the Archive Manager, and open the control archive inside it. Jump in the . directory, open the file named control. There you'll see which version of libc6 do you need.
(Alternatively, you could force-installing it with ```
sudo dpkg -i lmms_0.3.1-1ubuntu1_i386.deb
```, but this might break packages. Anyway, Synaptic could tell you then the unsatisfied dependencies.)

---

### Post by Envergure on 2008-02-07
Alright, I need version 2.7-1 and I only have version 2.6.1-1, which the Synaptic insists is the latest version.

I reloaded the package list and as it was dowlnoading I opened up the "view progress of single files" thing and several of the stati (statuses) read "Failed".  I bet that's the source of the problem.

---

### Post by Don Gatto on 2008-02-08
So you can't upgrade your libc6? Could you give me some examples of those which has been failed?

About the downloading: everybody recommends searching for packages at packages.ubuntu.com, the latest lmms pack is available there too.

---

### Post by Envergure on 2008-02-08
I can't see what failed, they go by too quickly.

Here's the output from doing it in the terminal:```

christopher@christopher-desktop:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Translation-en_CA                  
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_CA
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy Release 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates Release              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security Release             
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy-security/multiverse Packages
Fetched 4B in 1s (3B/s)  
Reading package lists... Done
christopher@christopher-desktop:~$
```

The ones that say "Ign" are the same ones that failed the other way.

The packages database has the same version as I already do.

How often is the package list on the servers updated?

---

### Post by Don Gatto on 2008-02-11
I think "Ign" stands for Ignored (or similar).
You should check your /etc/apt/sources.lst file, if you have a backup, you should restore it (you can make a copy of the current one too). (You could post the file here if you want me to see it.)
I was curious and tried to see ca.archive.ubuntu.com, but it was unavailable, that should be the problem. You should "jump back" to the repositories of packages.ubuntu.com (by either setting it in Synaptic or by editing sources.list).

---

### Post by zvacet on 2008-02-11
You have problems,because you are trying to install Hardy packages in Gutsy.

---

### Post by tophue on 2008-02-14
so does 0.3.31 only work on hardy? I dont want to have to switch to hardy just to update this software if I dont have to. Anyone know to do this?

---

