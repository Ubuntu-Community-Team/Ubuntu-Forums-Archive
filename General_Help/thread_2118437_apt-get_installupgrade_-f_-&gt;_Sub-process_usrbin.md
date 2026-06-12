---
title: "apt-get install/upgrade -f -&gt; Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2013-02-21
forum: General Help
---

### Post by Tricky12321 on 2013-02-21
I get this error on trying to run those commands in the terminal

```
sudo apt-get upgrade
sudo apt-get install -f
```

```
tricky@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1496 kB of archives.
After this operation, 0 B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "da:en",
    LC_ALL = (unset),
    LC_TIME = "da_DK.UTF-8",
    LC_MONETARY = "da_DK.UTF-8",
    LC_ADDRESS = "da_DK.UTF-8",
    LC_TELEPHONE = "da_DK.UTF-8",
    LC_NAME = "da_DK.UTF-8",
    LC_MEASUREMENT = "da_DK.UTF-8",
    LC_IDENTIFICATION = "da_DK.UTF-8",
    LC_NUMERIC = "da_DK.UTF-8",
    LC_PAPER = "da_DK.UTF-8",
    LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing poppler-data (--configure):
 package poppler-data is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 poppler-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
tricky@ubuntu:~$ 

```

```
 tricky@ubuntu:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages have been kept back:
  linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1496 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "da:en",
    LC_ALL = (unset),
    LC_TIME = "da_DK.UTF-8",
    LC_MONETARY = "da_DK.UTF-8",
    LC_ADDRESS = "da_DK.UTF-8",
    LC_TELEPHONE = "da_DK.UTF-8",
    LC_NAME = "da_DK.UTF-8",
    LC_MEASUREMENT = "da_DK.UTF-8",
    LC_IDENTIFICATION = "da_DK.UTF-8",
    LC_NUMERIC = "da_DK.UTF-8",
    LC_PAPER = "da_DK.UTF-8",
    LANG = "da_DK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
dpkg: error processing poppler-data (--configure):
 package poppler-data is not ready for configuration
 cannot configure (current status `half-installed')
Errors were encountered while processing:
 poppler-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

this happend after i tryed to remove my Danish language pack for my ubuntu. and now i can't reinstall it because of my ubuntu saying that i need to repair my software center, or something like that.

in other words is there a way that i can reinstall or remove this part of my old language pack so i can see my ubuntu in pure english and not half Danish and half English

I used Wubi to install ubuntu and i selected Danish in the install menu.

---

### Post by schragge on 2013-02-21
Well, it's clear what's going on here, but I don't know how to repair it in Ubuntu, sorry. :( On Debian, I'd *sudo dpkg-reconfigure locales*, but I guess this won't work in Ubuntu, since Ubuntu uses language-packs and probably doesn't have the package *locales*. Still, you can try it.

[highlight]Update 1.[/highlight]
Oh wait, Ubuntu *does* have the package [locales](http://packages.ubuntu.com/quantal/locales). So, definitely try
```

sudo dpkg-reconfigure locales

```disable *da_DK.UTF-8*, and enable *en_US.UTF-8*

[highlight]Update 2.[/highlight]
On the other hand, *locales* in Ubuntu doesn't contain */usr/sbin/update-locale*. You probably need to edit */etc/locale.gen* manually, then
```
sudo locale-gen
```

[highlight]Update 3.[/highlight]
Also edit */etc/default/locale* if this file is present

---

### Post by Tricky12321 on 2013-02-21
This fixed my first problem. now my linux turned danish again. and i get error codes in danish so you would not propperly understand them. so now next problem is that i need to remove the language package from the terminal, because all of my software is broken, no system settings because of broken packages.

but anyhow, you might get some information from my danish error code anyway so here it is. i can translate it using google translate but that would still get pretty bad...

```
root@ubuntu:~# apt-get install -f
Indlæser pakkelisterne... Færdig
Opbygger afhængighedstræ        
Læser tilstandsoplysninger... Færdig
Retter afhængigheder... Færdig
0 opgraderes, 0 nyinstalleres, 0 afinstalleres og 2 opgraderes ikke.
1 ikke fuldstændigt installerede eller afinstallerede.
0 B/1.496 kB skal hentes fra arkiverne.
Efter denne handling, vil 0 B yderligere diskplads være brugt.
dpkg: error processing poppler-data (--configure):
 pakken poppler-data ikke klar til konfiguration
 kan ikke konfigurere (nuværende status 'half-installed')
Ingen apportrapport skrevet da MaxReports (maks rapporter) allerede er nået
                                                                           Der opstod fejl under behandlingen:
 poppler-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:~# 
```

TRANSLATE IN GOOGLE TRANSLATE!!!!!

```
root @ ubuntu: ~ # apt-get install-f
Reading package lists ... finished
parse
Reading state information ... finished
Dishes dependencies ... finished
0 upgraded, 0 reinstalled, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
0 B/1.496 kB retrieved from the archives.
After this operation, the 0 B of additional disk space will be used.
dpkg: error processing poppler-data (- configure):
  package poppler-data is not ready for configuration
  can not configure (current status 'half-installed')
No apportrapport written as MaxReports (max reports) has already been reached
                                                                            Error occurred while processing:
  poppler data
E: Sub-process / usr / bin / dpkg returned an error code (1)
root @ ubuntu: ~ #
```

---

### Post by schragge on 2013-02-21
Well, the offending package is *poppler-data*, so try to forcibly remove it, then reinstall
```

dpkg -r --force-remove-reinstreq poppler-data
dpkg -i --force-configure-any /var/cache/apt/archives/poppler-data*.deb

```

---

### Post by Tricky12321 on 2013-02-22
Thanks all works now, you guys are great!

---

