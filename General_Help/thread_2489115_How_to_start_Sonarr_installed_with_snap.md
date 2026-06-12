---
title: "How to start Sonarr installed with snap"
date: 2023-07-18
forum: General Help
---

### Post by jgw on 2023-07-18
I installed Sonarr with snap.  Now I can't figure out how to start it.  Can anybody point me to a place that will help me with that?  (I have been looking and there are a LOT of those but .....)

Thank you................

---

### Post by Holger_Gehrke on 2023-07-18
It's a server. It should start automatically from a systemd unit. Try opening it's web control panel by going to 'localhost:8989' in your browser. At least that's what both sonarr.tv (the homepage of the project) and 'snap info solarr' tell you.

Holger

---

### Post by jgw on 2023-07-18
Thanks for the response!

I've been using sonarr for literally years, then I had a system problem and had to start all over from scratch and I have forgotten much!

I'll get it eventually.......

---

### Post by #&amp;thj^% on 2023-07-18
jgw it is also a service check with:
```
systemctl status sonarr 

```
Since the install have you logged out yet or better a reboot?

---

### Post by jgw on 2023-07-20
Thank you for the help.  

 systemctl status sonarr
Unit sonarr.service could not be found.

That was strange.  I actually have sonarr running so I am not sure what is going on but I am, hopefully forging on.  Now I have the problem of assigning a root address but I will, eventually get that one.   I want to install existing shows.  This is a re-installation but I still have the shows.  They are at mnt/3tb/TV and 'mnt' is at the root. 

Working on it.

I marked this as solved and it is not!    Not thinking..............................  Don't think solving can be reversed.

---

### Post by #&amp;thj^% on 2023-07-20
> **jgw said:**
> 
I marked this as solved and it is not!    Not thinking..............................  Don't think solving can be reversed.

Your right it's not solved, but I guess your better suited with snaps, I find them a royal pain in the......
```
 systemctl status sonarr
&#9679; sonarr.service - Sonarr Daemon
     Loaded: loaded (/lib/systemd/system/sonarr.service; enabled; preset: enabl>
     Active: active (running) since Thu 2023-07-20 07:54:54 MDT; 4h 36min ago
   Main PID: 2686 (mono)
      Tasks: 10 (limit: 18736)
     Memory: 176.7M
        CPU: 17.185s
     CGroup: /system.slice/sonarr.service
             &#9492;&#9472;2686 /usr/bin/mono --debug /usr/lib/sonarr/bin/Sonarr.exe -nobro>

Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:    --- End of inner exce>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Common.Htt>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Common.Htt>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Common.Htt>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Core.Downl>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:    --- End of inner exce>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Core.Downl>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Core.Downl>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Core.Downl>
Jul 20 12:30:29 me-Lenovo-Legion-5-15ARH05 mono[2686]:   at NzbDrone.Core.Downl>

```
The only problem I had was bolting qBittorrent to my recordings, but after I did get it, all is good.
jgw I run *0* snaps as you already know:
```
apt policy sonarr && apt depends sonarr
sonarr:
  Installed: 3.0.10
  Candidate: 3.0.10
  Version table:
 *** 3.0.10 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
        100 /var/lib/dpkg/status
     3.0.9 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.8 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.7 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.6 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.5 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.4 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.3 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
     3.0.2 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 PaI guess your bckages
     3.0.1 500
        500 https://apt.sonarr.tv/debian buster/main amd64 Packages
        500 https://apt.sonarr.tv/debian buster/main i386 Packages
sonarr
  Depends: adduser
  Depends: libsqlite3-0 (>= 3.7)
 |Depends: libmediainfo0v5 (>= 0.7.52)
  Depends: <libmediainfo0> (>= 0.7.52)
  Depends: mono-runtime (>= 5.18)
  Depends: ca-certificates-mono
  Depends: libmono-system-net-http4.0-cil (>= 4.0.0~alphI guess your ba1)
  Depends: libmono-corlib4.5-cil (>= 4.0.0~alpha1)
  Depends: libmono-microsoft-csharp4.0-cil (>= 1.0)
  Depends: libmono-posix4.0-cil (>= 4.0.0~alpha1)
  Depends: libmono-system-componentmodel-dataannotations4.0-cil (>= 4.0.0~alpha1)
  Depends: libmono-system-configuration-install4.0-cil (>= 1.0)
  Depends: libmono-system-configuration4.0-cil (>= 4.0.0~alpha1)
  Depends: libmono-system-core4.0-cil (>= 4.0.0~alpha1)
  Depends: libmono-system-data-datasetextensions4.0-cil (>= 1.0)
  Depends: libmono-system-data4.0-cil (>= 4.0.0~alpha1)
  Depends: libmono-system-identitymodel4.0-cil (>= 4.0.0~alpha1)
  Depends: libmono-system-io-compression4.0-cil (>= 3.2.1)
  Depends: libmono-system-numerics4.0-cil (>= 1.0)
  Depends: libmono-system-runtime-serialization4.0-cil (>I guess your b= 4.0.0~alpha1)
  Depends: libmono-system-security4.0-cil (>= 1.0)
  Depends: libmono-system-servicemodel4.0a-cil (>= 3.2.3)
  Depends: libmono-system-serviceprocess4.0-cil (>= 3.0.6)
  Depends: libmono-system-transactions4.0-cil (>= 1.0)
  Depends: libmono-system-web4.0-cil (>= 2.10.3)
  Depends: libmono-system-xml-linq4.0-cil (>= 3.0.6)
  Depends: libmono-system-xml4.0-cil (>= 3.12.0)
  Depends: libmono-system4.0-cil (>= 4.0.0~alpha1)
 |Depends: debconf (>= 0.5)
  Depends: <debconf-2.0>
    cdebconfI guess your b
    debconf
  Conflicts: <nzbdrone>
 |Recommends: libmediainfo0v5 (>= 18.03)
  Recommends: <libmediainfo0> (>= 18.03)
  Suggests: sqlite3 (>= 3.7)
    sqlite3:i386
  Suggests: mediainfo (>= 0.7.52)
  Replaces: <nzbdrone>
    sonarr

```
Don't let the Debian Naming fool you it's Ubuntu here, that's just the source it installed from.
Anyway Good Luck

---

