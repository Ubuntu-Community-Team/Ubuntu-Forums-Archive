---
title: "The package must be reinstallled, no files can be found"
date: 2021-02-28
forum: General Help
---

### Post by alemanlatino on 2021-02-28
I tried to install Bleachbit for ubuntu 16.04, however the system could not install it and asks me to reinstall it saying its file cannot be found. As a result, synaptic and apt-get upgrade are blocked. I don't know how to reinstall it since the package administrator refuses to do so.  How can I fix up this mess? 
The error is: Unknown error Class systemerror. The package bleachbit needs to be reinstalled, but I can't find an archive for it
Thank You very Much

---

### Post by Impavidus on 2021-02-28
Are you sure you want to fix this? 16.04 only has 2 months of support left, so in 2 months you have to move to a more recent release. That could be 18.04, but you can also jump straight to 20.04. If you make a fresh install of a new release of Ubuntu, there's no point in fixing the old release.

If you really want to fix this, bleachbit is supposed to be in the universe repository. Make sure it's enabled.

I've never used bleachbit myself. I don't need it and it appears it makes it easy to remove too much.

---

### Post by alemanlatino on 2021-02-28
I know I have to move to another release but I would like to fix this issue. Universe is enabled and I still have this issue. What can I do? Thank You

---

### Post by CelticWarrior on 2021-02-28
There's really no point in troubleshooting an about to be obsolete release but you should keep it fully updated until it expires anyway:
```
sudo apt update
sudo apt full-upgrade
```
Post back any errors in full.

---

### Post by alemanlatino on 2021-02-28
[LIST=1]
[*]sudo apt update
[*]OK:1 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) xenial InRelease
[*]Holen:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [109 kB]
[*]OK:3 [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) xenial InRelease
[*]OK:4 [http://ppa.launchpad.net/videolan/stable-daily/ubuntu](http://ppa.launchpad.net/videolan/stable-daily/ubuntu) xenial InRelease
[*]OK:5 [http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu](http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu) xenial InRelease
[*]OK:6 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial InRelease
[*]OK:7 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) xenial-updates InRelease
[*]Es wurden 109 kB in 15 s geholt (7.255 B/s).
[*]Paketlisten werden gelesen... Fertig                      (Package lists are being read... ready)
[*]Abhängigkeitsbaum wird aufgebaut.                      (Dependencies are being built)
[*]Statusinformationen werden eingelesen.... Fertig  (Status information is being read...ready)
[*]Alle Pakete sind aktuell.  ( All packages are updated)
[*]euclides@euclides-HP-350-G1:~$ sudo apt full-upgrade
[*]Paketlisten werden gelesen... Fertig                     (Package list is being read..ready)
[*]Abhängigkeitsbaum wird aufgebaut.                     (Dependencies are being built)
[*]Statusinformationen werden eingelesen.... Fertig   (Status information is being read...ready)
[*]E: Das Paket bleachbit muss neu installiert werden, es kann jedoch kein Archiv dafür gefunden werden. (The package bleachbit must be reinstalled, but I can't find an archive for it)
[/LIST]

---

### Post by deadflowr on 2021-02-28
What does
```
apt-cache policy bleachbit
```
show?

---

### Post by alemanlatino on 2021-02-28
[HTML]apt-cache policy bleachbit
bleachbit:
  Installiert:           4.2.0-0
  Installationskandidat: 4.2.0-0
  Versionstabelle:
 *** 4.2.0-0 100
        100 /var/lib/dpkg/status
     1.10-1 500
        500 http://de.archive.ubuntu.com/ubuntu xenial/universe i386 Packages[/HTML]

---

### Post by deadflowr on 2021-02-28
What does this do?
```
sudo apt install --reinstall bleachbit
```

---

### Post by alemanlatino on 2021-02-28
[HTML]sudo apt install--reinstall bleachbit
E: Ungültige Operation install--reinstall  (INVALID OPERATION)
[/HTML]

---

### Post by deadflowr on 2021-02-28
Need spacing between the install and --reinstall.

---

### Post by alemanlatino on 2021-02-28
```
sudo apt install  --reinstall bleachbit
[sudo] Passwort für euclides: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
E: Das Paket bleachbit muss neu installiert werden, es kann jedoch kein Archiv dafür gefunden werden. (E: The package bleachbit needs to be reinstalled but I can't find an archive for it)
```


same error

I really don't know what to do...:(

---

### Post by QIII on 2021-02-28
Is this **U**buntu 16.04, or a different flavor (i.e.: Kubuntu, Xubuntu).  Is it an Ubuntu deriviative?

---

### Post by deadflowr on 2021-02-28
Try
```
cd Downloads
apt download bleachbit
```
Does anything download?

---

### Post by CelticWarrior on 2021-02-28
It seems that none of the Ubuntu repositories is enabled: Main, Universe, Restricted, Multiverse.
Please open Software & Updates to check. It's recommended to have all the above selected.

---

### Post by alemanlatino on 2021-02-28
```
 cd Downloads
euclides@euclides-HP-350-G1:~/Downloads$ apt download bleachbit
E:  Es konnte keine Quelle gefunden werden, um Version »4.2.0-0« von  »bleachbit:i386« herunterzuladen. (E: no source could be found to  download bleachbit.i386 version 4.2.0)
```

I have them all

Ubuntu 16.04

Ubuntu 16.04

Does it mean I have no option, but to upgrade to Ubuntu 20.04???

---

### Post by QIII on 2021-02-28
I see that you have told us you have the Universe repo selected, but would you double-check to be sure that the repo is selected and have you done

```
sudo apt-get update
``` 

?

---

### Post by deadflowr on 2021-02-28
The issue is the version installed is too new and is not from the Ubuntu archives.
Not sure why it's not downloading from the Ubuntu archives as the apt-cache policy output shows no other archives from which the package is from.
For fun let's look at what the /var/lib/dpkg/status shows for it
try
```
egrep "Package: bleachbit" /var/lib/dpkg/status -A15
```

---

### Post by QIII on 2021-02-28
> **alemanlatino said:**
> Does it mean I have no option, but to upgrade to Ubuntu 20.04???

It was included in the repos for 16.04:  [https://packages.ubuntu.com/xenial/bleachbit](https://packages.ubuntu.com/xenial/bleachbit)

However, while on that point:  16.04 reaches End of Life (EOL) in April, 2021.  I'm not sure how much effort this is worth since you will need to upgrade in less than two months in any case.

---

### Post by QIII on 2021-02-28
> **deadflowr said:**
> The issue is the version installed is too new and is not from the Ubuntu archives.

Excellent catch!

---

### Post by alemanlatino on 2021-02-28
```
 egrep "Package: bleachbit" /var/lib/dpkg/status -A15
Package: bleachbit
Status: install reinstreq half-installed
Priority: optional
Section: admin
Installed-Size: 2429
Maintainer: Andrew Ziem <andrew@bleachbit.org>
Architecture: all
Version: 4.2.0-0
Config-Version: 4.2.0-0
Depends: gir1.2-gtk-3.0, gir1.2-notify-0.7, libgtk-3-0, python3, python3-chardet, python3-gi
Recommends: python3-notify, python3-scandir
Description: Removes unnecessary files
 Delete traces of your activities and other junk files to free disk
 space and maintain privacy.  BleachBit identifies and erases
 broken menu entries, cache, cookies, localizations, recent document
 lists, and temporary files in Firefox, Google Chrome, Flash, and 60

```

```
 sudo apt-get update
[sudo] Passwort für euclides: 
magdDas hat nicht funktioniert, bitte nochmal probieren.
[sudo] Passwort für euclides: 
Holen:1 http://security.ubuntu.com/ubuntu xenial-security InRelease [109 kB]   
OK:2 http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu xenial InRelease      
OK:3 http://de.archive.ubuntu.com/ubuntu xenial InRelease                      
OK:4 http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu xenial InRelease     
Holen:5 http://de.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]  
OK:6 http://ppa.launchpad.net/videolan/stable-daily/ubuntu xenial InRelease    
OK:7 http://ppa.launchpad.net/webupd8team/tor-browser/ubuntu xenial InRelease  
Es wurden 218 kB in 4 s geholt (45,7 kB/s).
Paketlisten werden gelesen... Fertig
```

---

### Post by deadflowr on 2021-02-28
Can you purge it?
```
sudo apt purge bleachbit
```

---

### Post by alemanlatino on 2021-02-28
[HTML] sudo apt purge bleachbit
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
E: Das Paket bleachbit muss neu installiert werden, es kann jedoch kein Archiv dafür gefunden werden. (E: the Package bleachbit must be reinstalled  but I can't find an archive for it)[/HTML]

no.. I can't.. :-(

---

### Post by deadflowr on 2021-02-28
Try
```
sudo rm -i /var/lib/dpkg/info/bleachbit.*
sudo dpkg --remove --force-remove-reinstreq bleachbit
```

---

### Post by alemanlatino on 2021-02-28
Thank You!! That solved the issue.
I could upgrade and open synaptic again!!
Thank You!!!!

---

