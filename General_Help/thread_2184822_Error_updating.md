---
title: "Error updating"
date: 2013-10-30
forum: General Help
---

### Post by miguel6 on 2013-10-30
I was typed:

```
sudo apt-get update
```

after I was prompted with a window asking me to install update. I clicked it and got this error.


[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_009_zpsa72a841e.png~original[/IMG]

Now up at the top right I have this error icon indicator. I'm trying to get rid of it and fix this but don't know how.

[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_010_zps263d526d.png~original[/IMG]

Terminal says it's having an error with a package I believe. Here it is.

```
mig@mig-G55VW:~$ sudo apt-get install -f[sudo] password for mig: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-zeitgeist-2.0 tor tor-geoipdb torsocks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  librhythmbox-core8
The following NEW packages will be installed:
  librhythmbox-core8
0 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
8 not fully installed or removed.
Need to get 0 B/819 kB of archives.
After this operation, 1,776 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 176010 files and directories currently installed.)
Unpacking librhythmbox-core8 (from .../librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/librhythmbox-core.so.8.0.0', which is also in package librhythmbox-core7 3.0.1-0~13.10~ppa1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
mig@mig-G55VW:~$
```

Any help is appreciated. 

SIDE NOTE: instead of making another thread I will just quickly ask here. Is increase/decrease volume causing a stutter in the audio a known bug ? Or when I open the sound settings my mouse freezes and it takes awhile to open the window.

---

### Post by ian-weisser on 2013-10-30
> **miguel6 said:**
> 
Unpacking librhythmbox-core8 (from .../librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb (--unpack):
 [COLOR=#ff0000]trying to overwrite '/usr/lib/librhythmbox-core.so.8.0.0', which is also in package librhythmbox-core7 3.0.1-0~13.10~ppa1[/COLOR]


Your biggest problem is that two different PPA packages provide the same library file. They shouldn't do that.

1) Disable one (or both) PPAs in your Software Sources control panel (Software Center -> Edit -> Software Sources)

2) Delete the package from your local cache with: **sudo apt-get clean core8_3.0.1-1ubuntu2~ppa0_amd64.deb **

3) Try updating again: **sudo apt-get update && sudo apt-get upgrade**  

Post any error messages here.

---

### Post by miguel6 on 2013-11-02
> **ian-weisser said:**
> 
1) Disable one (or both) PPAs in your Software Sources control panel (Software Center -> Edit -> Software Sources)


Which packages are you refeering too ? When I go to [COLOR=#000000](Software Center -> Edit -> Software Sources) there are on packages that suggest any connection to [/COLOR][COLOR=#FF0000]*/usr/lib/librhythmbox-core.so.8.0.0' *[/COLOR][COLOR=#000000]or[/COLOR][COLOR=#FF0000][I]librhythmbox-core7 3.0.1-0~13.10~ppa1

[/I][/COLOR]Here are the packages that I am able to disable.

[[IMG]http://i1141.photobucket.com/albums/n591/iLuvlunchtime/Selection_011_zps2179a71c.png~original[/IMG]]("http://s1141.photobucket.com/user/iLuvlunchtime/media/Selection_011_zps2179a71c.png.html")

---

### Post by ian-weisser on 2013-11-02
If you really don't know (and don't know how to figure it out), then disable ALL of your PPAs.

Here is one way to figure out which PPA is causing the problem:
Disable all PPAs, and get your package manager working again.
Re-enable one PPA at a time. After each, run **sudo apt-get update && sudo apt-get upgrade**
When your package manager breaks again, you know that the PPA you just re-enabled is the problem.

Another way is to browse those PPA URLs until your find both packages (they may be from different PPAs)

When you determine which PPA is the problem, make sure to notify the PPA maintainer(s) about the conflict.

Do remember that PPAs are not community-supported software. PPAs are only supported by their maintainer.

---

### Post by miguel6 on 2013-11-06
> **ian-weisser said:**
> If you really don't know (and don't know how to figure it out), then disable ALL of your PPAs.

Here is one way to figure out which PPA is causing the problem:
Disable all PPAs, and get your package manager working again.
Re-enable one PPA at a time. After each, run **sudo apt-get update && sudo apt-get upgrade**
When your package manager breaks again, you know that the PPA you just re-enabled is the problem.

Another way is to browse those PPA URLs until your find both packages (they may be from different PPAs)

When you determine which PPA is the problem, make sure to notify the PPA maintainer(s) about the conflict.

Do remember that PPAs are not community-supported software. PPAs are only supported by their maintainer.

Well, I started the process of finding out which package was breaking the package manager. After disabling all the packages the errors still persist. Doing a search on google for the package I believed was ruining things due to the 
```
[COLOR=#000000][FONT=Ubuntu Mono]Errors were encountered while processing:
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] /var/cache/apt/archives/librhythmbox-core8_3.0.1-1ubuntu2~ppa0_amd64.deb[/FONT][/COLOR]
```

I googled "librhythmbox-core8[COLOR=#000000][FONT=Ubuntu Mono]" and got to this link: [/FONT][/COLOR][http://askubuntu.com/questions/367422/need-to-resolve-dependencies-for-installation](http://askubuntu.com/questions/367422/need-to-resolve-dependencies-for-installation)

This concluded that when I installed Saucy Salamander I installed somethings someone suggested which one of them was Rhythmbox 8 when I hadn't removed Rhythmbox 7. After removing it, everything worked fine again.

Everything is updated and all is well :) Thanks for your help

---

### Post by ian-weisser on 2013-11-06
Glad to see it's working now!

---

