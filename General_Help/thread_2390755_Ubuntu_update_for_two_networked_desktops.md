---
title: "Ubuntu update for two networked desktops"
date: 2018-05-02
forum: General Help
---

### Post by pushbike06 on 2018-05-02
Problem 1:
I have two desktop PC's connected to the internet via a router (common arrangement). Both PC's have 16.04 LTS as system. From the Desktop using System / Details / Check for updates  I can regularly update PC 1 but when I try to update PC 2 it returns "System up to date". Some days later it will respond to the same request with an update. The PC1 has a number of applications installed whereas PC 2 has only Firefox, Thunderbird and Ubuntu Software. If I try to update PC 2 via Ubuntu Software it also returns with "System up to date".
Problem 2:
I also have on the same router network a netbook loaded with Lubuntu I think the latest version, unable to find where Lubuntu version is listed, and I use Software Updater to check for updates. Everytime I use it the response is "Failed to download repository information check your internet connection" This message repeats when I "Try again" until I give up and select "OK" to try and close it down  then it lists the updates and will down load and I presume update.

---

### Post by Impavidus on 2018-05-02
(Best to make separate threads for separate problems)

For problem 1: Maybe [phased updates](https://wiki.ubuntu.com/PhasedUpdates)? Both computers get the same updates, but not at the same time (for the non-critical updates).

For problem 2: What's the output of```
sudo apt-get update
```

---

### Post by pushbike06 on 2018-05-02
Impavidus,
The following test was carried out from admin login not my user login where I use Software Updater.
The response to sudo apt-get update is:
Hit:1 [http://mirror.aarnet.edu.au/pub/ubuntu/archive](http://mirror.aarnet.edu.au/pub/ubuntu/archive) xenial InRelease
Get:2 [http://mirror.aarnet.edu.au/pub/ubuntu/archive](http://mirror.aarnet.edu.au/pub/ubuntu/archive) xenial-updates InRelease [109 kB]
Hit:3 [http://mirror.aarnet.edu.au/pub/ubuntu/archive](http://mirror.aarnet.edu.au/pub/ubuntu/archive) xenial-backports InRelease
Get:4 [http://mirror.aarnet.edu.au/pub/ubuntu/archive](http://mirror.aarnet.edu.au/pub/ubuntu/archive) xenial-security InRelease [107 kB]
Ign:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal InRelease
Ign:6 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal Release
Ign:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources.diff/Index
Get:8 [http://mirror.aarnet.edu.au/pub/ubuntu/archive](http://mirror.aarnet.edu.au/pub/ubuntu/archive) xenial-updates/main i386 Packages [708 kB]
Ign:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources
Ign:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources
Ign:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources
Ign:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources
Ign:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources
Err:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal/partner Sources
  404  Not Found [IP: 91.189.91.15 80]
Get:10 [http://mirror.aarnet.edu.au/pub/ubuntu/archive](http://mirror.aarnet.edu.au/pub/ubuntu/archive) xenial-updates/universe i386 Packages [575 kB]
Fetched 1,499 kB in 5s (275 kB/s)
Reading package lists...
W: The repository 'http://archive.canonical.com/ubuntu quantal Release' does not have a Release file.
E: Failed to fetch [http://archive.canonical.com/ubuntu/dists/quantal/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/quantal/partner/source/Sources)  404  Not Found [IP: 91.189.91.15 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by tinylagarto on 2018-05-02
You have to remove Quantal from your sources. You are mixing 16.04 with sources from an older release and I guess unsupported. 
You can do this by editing /etc/apt/sources.list with an editor as root.

---

### Post by pushbike06 on 2018-05-02
ivanovnegro2
Thanks for your help problem 2 solved.

---

### Post by Impavidus on 2018-05-03
Great. If you're also satisfied with my explanation for problem 1, could you mark this thread as solved? Thread tools (near top of page) &#8594; mark as solved.

---

### Post by pushbike06 on 2018-05-03
Impavidus
Historically I have had problem 1 and I decided to source the updates PC 1 and PC 2 from different servers. I thought that the server identified the two PC's as just one i.e. that  a flag was set when a system was up to date. This is probably incorrect and that phased updates where in play. Any way I set PC 2 to the same server as PC 1, main server, and got an immediate update of about 90Mb. It seems the local server was not capable of providing updates. So I will mark this thread as solved.

---

