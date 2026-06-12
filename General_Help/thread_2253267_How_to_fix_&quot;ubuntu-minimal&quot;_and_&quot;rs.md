---
title: "How to fix &quot;ubuntu-minimal&quot; and &quot;rsyslog&quot; error"
date: 2014-11-18
forum: General Help
---

### Post by talialu on 2014-11-18
[FONT=arial narrow][COLOR=#000080]Hi all [/COLOR][/FONT]):P[FONT=arial narrow][COLOR=#000080], 
I need help (if possible) to resolve my bug!
After the procedure of upgrade from Ubuntu 14.04 LTS to 14.10 my system, everytime I try to do the procedure of "apt-upgrade" leave me a message of error:[/COLOR][/FONT]
 [FONT=arial][B]
rsyslog
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B][/FONT]

[COLOR=#000080][FONT=arial narrow]I try to fix in synaptic package manager but nothing, it's impossible to fix or remove and install again! 

I think I have to install again my Ubuntu but I like my system, it's approx stable and i fix my kernel with many tips now...any one have a good way to suggest me to resolve this?

(sorry in advance for my english!!)

Thx a lot[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-11-18
talialu; Hi ! Welcome to the forum.

The error condition may be from any number of things.
Let's look and see what state the package management system is in.
Post the outputs - Between Code Tags, please - of terminal  commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```
such that we see the errors and in the context that they are generated in:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
This will give direction to focus our attention.

[INDENT][INDENT]ubuntu
possibly difficult
[INDENT][INDENT][INDENT]but nothing is impossible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by talialu on 2014-11-18
ok...
I start to dgt the command "**sudo apt-get update**"

```
virtualenix@vincent-Ubuntu:~$ sudo apt-get update[sudo] password for virtualenix: 
Ign http://archive.canonical.com saucy InRelease
Ign http://ppa.launchpad.net trusty InRelease                                                
Ign http://archive.ubuntu.com utopic InRelease                                               
Trovato http://archive.canonical.com saucy Release.gpg               
Ign http://dl.google.com stable InRelease                            
Ign http://ppa.launchpad.net trusty InRelease                        
Ign http://archive.ubuntu.com utopic-updates InRelease               
Trovato http://archive.canonical.com saucy Release                   
Trovato http://dl.google.com stable Release.gpg                                             
Ign http://ppa.launchpad.net trusty InRelease                        
Ign http://archive.ubuntu.com utopic-backports InRelease             
Trovato http://archive.canonical.com saucy/partner Sources           
Trovato http://dl.google.com stable Release                                                              
Scaricamento di:1 http://ppa.launchpad.net trusty Release.gpg [316 B]                        
Ign http://archive.ubuntu.com utopic-security InRelease                                               
Trovato http://archive.canonical.com saucy/partner amd64 Packages    
Scaricamento di:2 http://ppa.launchpad.net trusty Release.gpg [316 B]                                     
Trovato http://dl.google.com stable/main amd64 Packages                                                
Ign http://archive.ubuntu.com utopic-proposed InRelease                                     
Trovato http://archive.canonical.com saucy/partner i386 Packages                            
Scaricamento di:3 http://ppa.launchpad.net trusty Release.gpg [316 B]                                      
Trovato http://dl.google.com stable/main i386 Packages                                                 
Trovato http://archive.ubuntu.com utopic Release.gpg                                                       
Trovato http://ppa.launchpad.net trusty Release                                             
Ign http://ppa.launchpad.net trusty Release                                                                        
Trovato http://archive.ubuntu.com utopic-updates Release.gpg                                                       
Trovato http://ppa.launchpad.net trusty Release                                             
Ign http://ppa.launchpad.net trusty Release                                                                        
Trovato http://archive.ubuntu.com utopic-backports Release.gpg                                                     
Trovato http://ppa.launchpad.net trusty Release                                             
Ign http://ppa.launchpad.net trusty Release                                                                        
Trovato http://archive.ubuntu.com utopic-security Release.gpg                                                      
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex                           
Trovato http://archive.ubuntu.com utopic-proposed Release.gpg         
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex      
Trovato http://archive.ubuntu.com utopic Release                      
Trovato http://archive.ubuntu.com utopic-updates Release                                                          
Trovato http://archive.ubuntu.com utopic-backports Release                                                         
Trovato http://ppa.launchpad.net trusty/main Translation-en                                                        
Trovato http://archive.ubuntu.com utopic-security Release                                                        
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex                                                  
Trovato http://archive.ubuntu.com utopic-proposed Release                                   
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex                                                  
Trovato http://archive.ubuntu.com utopic/main Sources                                       
Trovato http://archive.ubuntu.com utopic/universe Sources                                                 
Trovato http://archive.ubuntu.com utopic/restricted Sources                                               
Ign http://archive.canonical.com saucy/partner Translation-it_IT                                          
Trovato http://archive.ubuntu.com utopic/multiverse Sources                             
Ign http://archive.canonical.com saucy/partner Translation-it                           
Ign http://ppa.launchpad.net trusty/main amd64 Packages/DiffIndex                       
Trovato http://archive.ubuntu.com utopic/main amd64 Packages                            
Ign http://archive.canonical.com saucy/partner Translation-en                           
Ign http://dl.google.com stable/main Translation-it_IT                                  
Ign http://dl.google.com stable/main Translation-it                                     
Ign http://ppa.launchpad.net trusty/main i386 Packages/DiffIndex  
Trovato http://archive.ubuntu.com utopic/restricted amd64 Packages
Ign http://dl.google.com stable/main Translation-en               
Trovato http://archive.ubuntu.com utopic/universe amd64 Packages  
Trovato http://archive.ubuntu.com utopic/multiverse amd64 Packages
Trovato http://archive.ubuntu.com utopic/main i386 Packages
Trovato http://ppa.launchpad.net trusty/main amd64 Packages    
Trovato http://archive.ubuntu.com utopic/restricted i386 Packages
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com utopic/universe i386 Packages
Trovato http://archive.ubuntu.com utopic/multiverse i386 Packages
Trovato http://archive.ubuntu.com utopic/main Translation-it   
Trovato http://ppa.launchpad.net trusty/main amd64 Packages
Trovato http://archive.ubuntu.com utopic/main Translation-en
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com utopic/multiverse Translation-it
Trovato http://archive.ubuntu.com utopic/multiverse Translation-en
Trovato http://archive.ubuntu.com utopic/restricted Translation-it
Trovato http://archive.ubuntu.com utopic/restricted Translation-en
Trovato http://ppa.launchpad.net trusty/main amd64 Packages
Trovato http://archive.ubuntu.com utopic/universe Translation-it
Trovato http://ppa.launchpad.net trusty/main i386 Packages
Trovato http://archive.ubuntu.com utopic/universe Translation-en
Trovato http://archive.ubuntu.com utopic-updates/main Sources  
Trovato http://archive.ubuntu.com utopic-updates/universe Sources
Trovato http://archive.ubuntu.com utopic-updates/restricted Sources
Trovato http://archive.ubuntu.com utopic-updates/multiverse Sources
Trovato http://archive.ubuntu.com utopic-updates/main amd64 Packages
Trovato http://archive.ubuntu.com utopic-updates/restricted amd64 Packages
Trovato http://archive.ubuntu.com utopic-updates/universe amd64 Packages
Trovato http://archive.ubuntu.com utopic-updates/multiverse amd64 Packages
Trovato http://archive.ubuntu.com utopic-updates/main i386 Packages
Trovato http://archive.ubuntu.com utopic-updates/restricted i386 Packages
Trovato http://archive.ubuntu.com utopic-updates/universe i386 Packages
Trovato http://archive.ubuntu.com utopic-updates/multiverse i386 Packages
Trovato http://archive.ubuntu.com utopic-updates/main Translation-en 
Trovato http://archive.ubuntu.com utopic-updates/multiverse Translation-en
Trovato http://archive.ubuntu.com utopic-updates/restricted Translation-en
Trovato http://archive.ubuntu.com utopic-updates/universe Translation-en
Trovato http://archive.ubuntu.com utopic-backports/main Sources      
Trovato http://archive.ubuntu.com utopic-backports/restricted Sources
Trovato http://archive.ubuntu.com utopic-backports/universe Sources
Ign http://ppa.launchpad.net trusty/main Translation-it_IT
Trovato http://archive.ubuntu.com utopic-backports/multiverse Sources
Ign http://ppa.launchpad.net trusty/main Translation-it
Trovato http://archive.ubuntu.com utopic-backports/main amd64 Packages
Ign http://ppa.launchpad.net trusty/main Translation-it_IT
Ign http://ppa.launchpad.net trusty/main Translation-it              
Ign http://ppa.launchpad.net trusty/main Translation-en
Trovato http://archive.ubuntu.com utopic-backports/restricted amd64 Packages
Ign http://ppa.launchpad.net trusty/main Translation-it_IT     
Trovato http://archive.ubuntu.com utopic-backports/universe amd64 Packages
Trovato http://archive.ubuntu.com utopic-backports/multiverse amd64 Packages
Ign http://ppa.launchpad.net trusty/main Translation-it
Trovato http://archive.ubuntu.com utopic-backports/main i386 Packages
Ign http://ppa.launchpad.net trusty/main Translation-en        
Trovato http://archive.ubuntu.com utopic-backports/restricted i386 Packages
Trovato http://archive.ubuntu.com utopic-backports/universe i386 Packages
Trovato http://archive.ubuntu.com utopic-backports/multiverse i386 Packages
Trovato http://archive.ubuntu.com utopic-backports/main Translation-en
Trovato http://archive.ubuntu.com utopic-backports/multiverse Translation-en
Trovato http://archive.ubuntu.com utopic-backports/restricted Translation-en
Trovato http://archive.ubuntu.com utopic-backports/universe Translation-en                                           
Trovato http://archive.ubuntu.com utopic-security/main Sources                                                       
Trovato http://archive.ubuntu.com utopic-security/universe Sources                                                   
Trovato http://archive.ubuntu.com utopic-security/restricted Sources                                                 
Trovato http://archive.ubuntu.com utopic-security/multiverse Sources                                                 
Trovato http://archive.ubuntu.com utopic-security/main amd64 Packages                                                
Trovato http://archive.ubuntu.com utopic-security/restricted amd64 Packages                                          
Trovato http://archive.ubuntu.com utopic-security/universe amd64 Packages                                            
Trovato http://archive.ubuntu.com utopic-security/multiverse amd64 Packages                                          
Trovato http://archive.ubuntu.com utopic-security/main i386 Packages                                                 
Trovato http://archive.ubuntu.com utopic-security/restricted i386 Packages                                           
Trovato http://archive.ubuntu.com utopic-security/universe i386 Packages                                             
Trovato http://archive.ubuntu.com utopic-security/multiverse i386 Packages                                           
Trovato http://archive.ubuntu.com utopic-security/main Translation-en                                                
Trovato http://archive.ubuntu.com utopic-security/multiverse Translation-en                                          
Trovato http://archive.ubuntu.com utopic-security/restricted Translation-en                                          
Trovato http://archive.ubuntu.com utopic-security/universe Translation-en                                            
Trovato http://archive.ubuntu.com utopic-proposed/restricted amd64 Packages                                          
Trovato http://archive.ubuntu.com utopic-proposed/main amd64 Packages                                                
Trovato http://archive.ubuntu.com utopic-proposed/universe amd64 Packages                                            
Trovato http://archive.ubuntu.com utopic-proposed/multiverse amd64 Packages                                          
Trovato http://archive.ubuntu.com utopic-proposed/restricted i386 Packages                                           
Trovato http://archive.ubuntu.com utopic-proposed/main i386 Packages                                                 
Trovato http://archive.ubuntu.com utopic-proposed/universe i386 Packages                                             
Trovato http://archive.ubuntu.com utopic-proposed/multiverse i386 Packages                                           
Trovato http://archive.ubuntu.com utopic-proposed/main Translation-it                                                
Trovato http://archive.ubuntu.com utopic-proposed/main Translation-en                                                
Trovato http://archive.ubuntu.com utopic-proposed/multiverse Translation-it                                          
Trovato http://archive.ubuntu.com utopic-proposed/multiverse Translation-en                                          
Trovato http://archive.ubuntu.com utopic-proposed/restricted Translation-it                                          
Trovato http://archive.ubuntu.com utopic-proposed/restricted Translation-en                                          
Trovato http://archive.ubuntu.com utopic-proposed/universe Translation-it                                            
Trovato http://archive.ubuntu.com utopic-proposed/universe Translation-en                                            
Recuperati 948 B in 9s (99 B/s)                                                                                      
Lettura elenco dei pacchetti... Fatto
W: Errore GPG: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7274A4DAE80D6BF5
W: Errore GPG: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4A272F2B298C62A6
W: Errore GPG: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 82EB5823F4FE239D
virtualenix@vincent-Ubuntu:~$ 

```


....continue, and now this is what I have with "**sudo apt-get upgrade**"

```
virtualenix@vincent-Ubuntu:~$ sudo apt-get upgradeLettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Calcolo dell'aggiornamento... Eseguito
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
2 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Do you want to continue? [Y/n] Y
Configurazione di rsyslog (7.4.4-1ubuntu11)...
L'utente «syslog» fa già parte del gruppo «adm».
chown: impossibile accedere a "/var/spool/rsyslog": File o directory non esistente
dpkg: errore nell'elaborare il pacchetto rsyslog (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di ubuntu-minimal:
 ubuntu-minimal dipende da rsyslog; comunque:
  Il pacchetto rsyslog non è ancora configurato.


dpkg: errore nell'elaborare il pacchetto ubuntu-minimal (--configure):
 problemi con le dipendenze - lasciato non configurato
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
                                                                                                             Si sono verificati degli errori nell'elaborazione:
 rsyslog
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
virtualenix@vincent-Ubuntu:~$ 



```



.....continue with "**sudo apt-get -f install**"

```
virtualenix@vincent-Ubuntu:~$ sudo apt-get -f installLettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
2 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Configurazione di rsyslog (7.4.4-1ubuntu11)...
L'utente «syslog» fa già parte del gruppo «adm».
chown: impossibile accedere a "/var/spool/rsyslog": File o directory non esistente
dpkg: errore nell'elaborare il pacchetto rsyslog (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di ubuntu-minimal:
 ubuntu-minimal dipende da rsyslog; comunque:
  Il pacchetto rsyslog non è ancora configurato.


dpkg: errore nell'elaborare il pacchetto ubuntu-minimal (--configure):
 problemi con le dipendenze - lasciato non configurato
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
                                                                                                             Si sono verificati degli errori nell'elaborazione:
 rsyslog
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
virtualenix@vincent-Ubuntu:~$
```



....the last command "**sudo dpkg -C**"

```
virtualenix@vincent-Ubuntu:~$ sudo dpkg -C
I seguenti pacchetti sono stati estratti, ma non ancora configurati.
È necessario configurarli usando "dpkg --configure" o l'opzione di
configurazione nel menù di dselect affinché funzionino:
 ubuntu-minimal       Minimal core of Ubuntu

I seguenti pacchetti risultano parzialmente configurati. La configurazione
dovrebbe essere ritentata usando "dpkg --configure <pacchetto>" o con
l'opzione di configurazione nel menù di dselect:
 rsyslog              reliable system and kernel logging daemon


virtualenix@vincent-Ubuntu:~$ 



```


this is all!! 
Hope it's enough

---

### Post by Bashing-om on 2014-11-18
talialu; Yes ;

It is enough. We do have a problem:
> 
Ign [http://archive.canonical.com](http://archive.canonical.com) [color=red]saucy[/color] InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) [color=red]trusty[/color] InRelease

Mixing release repositories is never a good thing to do in the 1st place;
Secondly; 'suacy' is End-Of-Life and no longer has support. The software repository has been moved away.

As to what we can do now .. with mixed software versions from differing sources .. hummm .. All we can do is try and see what we can do !
Post back the contents of the sources lists files:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

AND verify the release that you have installed :
```

lsb_release -a
cat /etc/issue
uname -a

```

[INDENT][INDENT]maybe yes fixable
[INDENT][INDENT][INDENT]perhaps not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by talialu on 2014-11-18
Ok, this is the resul of the command:

....first command "**cat -n /etc/apt/sources.list**"

```
virtualenix@vincent-Ubuntu:~$ cat -n /etc/apt/sources.list     1	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     2	
     3	# newer versions of the distribution.
     4	deb http://archive.ubuntu.com/ubuntu utopic main restricted
     5	deb-src http://archive.ubuntu.com/ubuntu utopic main universe restricted multiverse #Added by software-properties
     6	## Major bug fix updates produced after the final release of the
     7	## distribution.
     8	deb http://archive.ubuntu.com/ubuntu utopic-updates main restricted
     9	deb-src http://archive.ubuntu.com/ubuntu utopic-updates main universe restricted multiverse #Added by software-properties
    10	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    11	## team. Also, please note that software in universe WILL NOT receive any
    12	## review or updates from the Ubuntu security team.
    13	deb http://archive.ubuntu.com/ubuntu utopic universe
    14	deb http://archive.ubuntu.com/ubuntu utopic-updates universe
    15	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    16	## team, and may not be under a free licence. Please satisfy yourself as to 
    17	## your rights to use the software. Also, please note that software in 
    18	## multiverse WILL NOT receive any review or updates from the Ubuntu
    19	## security team.
    20	deb http://archive.ubuntu.com/ubuntu utopic multiverse
    21	deb http://archive.ubuntu.com/ubuntu utopic-updates multiverse
    22	## N.B. software from this repository may not have been tested as
    23	## extensively as that contained in the main release, although it includes
    24	## newer versions of some applications which may provide useful features.
    25	## Also, please note that software in backports WILL NOT receive any review
    26	## or updates from the Ubuntu security team.
    27	deb http://archive.ubuntu.com/ubuntu utopic-backports main restricted universe multiverse
    28	deb-src http://archive.ubuntu.com/ubuntu utopic-backports main restricted universe multiverse #Added by software-properties
    29	deb http://archive.ubuntu.com/ubuntu utopic-security main restricted
    30	deb-src http://archive.ubuntu.com/ubuntu utopic-security main universe restricted multiverse #Added by software-properties
    31	deb http://archive.ubuntu.com/ubuntu utopic-security universe
    32	deb http://archive.ubuntu.com/ubuntu utopic-security multiverse
    33	## Uncomment the following two lines to add software from Canonical's
    34	## 'partner' repository.
    35	## This software is not part of Ubuntu, but is offered by Canonical and the
    36	## respective vendors as a service to Ubuntu users.
    37	deb http://archive.canonical.com/ubuntu saucy partner
    38	deb-src http://archive.canonical.com/ubuntu saucy partner
    39	## This software is not part of Ubuntu, but is offered by third-party
    40	## developers who want to ship their latest software.
    41	# deb http://extras.ubuntu.com/ubuntu trusty main
    42	# deb-src http://extras.ubuntu.com/ubuntu trusty main
    43	# deb http://www.mediahuman.com/packages/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
    44	# deb-src http://www.mediahuman.com/packages/ubuntu saucy main
    45	# deb http://archive.canonical.com/ trusty partner
    46	# deb-src http://archive.canonical.com/ saucy partner
    47	## Depôt MultiSystem
    48	# deb http://liveusb.info/multisystem/depot all main
    49	deb http://archive.ubuntu.com/ubuntu utopic-proposed restricted main universe multiverse
virtualenix@vincent-Ubuntu:~$ 



```

......second command "**tail -v -n +1 /etc/apt/sources.list.d/***"

```

==> /etc/apt/sources.list.d/jon-severinsson-ffmpeg-trusty.list <==# deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main
# deb-src http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main


==> /etc/apt/sources.list.d/jon-severinsson-ffmpeg-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main
# deb-src http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main


==> /etc/apt/sources.list.d/jon-severinsson-ffmpeg-trusty.list.save <==
# deb http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main
# deb-src http://ppa.launchpad.net/jon-severinsson/ffmpeg/ubuntu trusty main


==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list <==
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main


==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main


==> /etc/apt/sources.list.d/kubuntu-ppa-backports-trusty.list.save <==
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu trusty main


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list <==
# deb http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu trusty main


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu trusty main


==> /etc/apt/sources.list.d/libreoffice-libreoffice-4-3-trusty.list.save <==
# deb http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/libreoffice-4-3/ubuntu trusty main


==> /etc/apt/sources.list.d/lightdm-gtk-greeter-team-stable-trusty.list <==
# deb http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/lightdm-gtk-greeter-team-stable-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/lightdm-gtk-greeter-team-stable-trusty.list.save <==
# deb http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/lightdm-gtk-greeter-team/stable/ubuntu trusty main


==> /etc/apt/sources.list.d/me-davidsansome-clementine-trusty.list <==
# deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main


==> /etc/apt/sources.list.d/me-davidsansome-clementine-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main


==> /etc/apt/sources.list.d/me-davidsansome-clementine-trusty.list.save <==
# deb http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main
# deb-src http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu trusty main


==> /etc/apt/sources.list.d/neon-kf5-trusty.list <==
# deb http://ppa.launchpad.net/neon/kf5/ubuntu trusty main
# deb-src http://ppa.launchpad.net/neon/kf5/ubuntu trusty main


==> /etc/apt/sources.list.d/neon-kf5-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/neon/kf5/ubuntu trusty main
# deb-src http://ppa.launchpad.net/neon/kf5/ubuntu trusty main


==> /etc/apt/sources.list.d/neon-kf5-trusty.list.save <==
# deb http://ppa.launchpad.net/neon/kf5/ubuntu trusty main
# deb-src http://ppa.launchpad.net/neon/kf5/ubuntu trusty main


==> /etc/apt/sources.list.d/niko2040-e19-trusty.list <==
# deb http://ppa.launchpad.net/niko2040/e19/ubuntu trusty main
# deb-src http://ppa.launchpad.net/niko2040/e19/ubuntu trusty main


==> /etc/apt/sources.list.d/niko2040-e19-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/niko2040/e19/ubuntu trusty main
# deb-src http://ppa.launchpad.net/niko2040/e19/ubuntu trusty main


==> /etc/apt/sources.list.d/niko2040-e19-trusty.list.save <==
# deb http://ppa.launchpad.net/niko2040/e19/ubuntu trusty main
# deb-src http://ppa.launchpad.net/niko2040/e19/ubuntu trusty main


==> /etc/apt/sources.list.d/nomacs-stable-saucy.list <==
# deb http://ppa.launchpad.net/nomacs/stable/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/nomacs/stable/ubuntu saucy main


==> /etc/apt/sources.list.d/nomacs-stable-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/nomacs/stable/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/nomacs/stable/ubuntu saucy main


==> /etc/apt/sources.list.d/nomacs-stable-saucy.list.save <==
# deb http://ppa.launchpad.net/nomacs/stable/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/nomacs/stable/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-apps-saucy.list <==
# deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-apps-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-apps-saucy.list.save <==
# deb http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-apps-trusty.list <==
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-apps-trusty.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-apps-trusty.list.save <==
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-deepin-sc-trusty.list <==
# deb http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-deepin-sc-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-deepin-sc-trusty.list.save <==
# deb http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/deepin-sc/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons2-saucy.list <==
# deb http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-icons2-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-icons2-saucy.list.save <==
# deb http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-icons2-trusty.list <==
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons2-trusty.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons2-trusty.list.save <==
# deb-src http://ppa.launchpad.net/noobslab/icons2/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons-saucy.list <==
# deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-icons-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-icons-saucy.list.save <==
# deb http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list <==
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-icons-trusty.list.save <==
# deb-src http://ppa.launchpad.net/noobslab/icons/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-indicators-saucy.list <==
# deb http://ppa.launchpad.net/noobslab/indicators/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-indicators-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/indicators/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-indicators-saucy.list.save <==
# deb http://ppa.launchpad.net/noobslab/indicators/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/indicators/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-mint-trusty.list <==
# deb http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-mint-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-mint-trusty.list.save <==
# deb http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/mint/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-nitrux-os-trusty.list <==
# deb http://ppa.launchpad.net/noobslab/nitrux-os/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/nitrux-os/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-nitrux-os-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/nitrux-os/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/nitrux-os/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-nitrux-os-trusty.list.save <==
# deb http://ppa.launchpad.net/noobslab/nitrux-os/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/nitrux-os/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-potenza-trusty.list <==
# deb http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-potenza-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-potenza-trusty.list.save <==
# deb http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/potenza/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-themes-saucy.list <==
# deb http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-themes-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-themes-saucy.list.save <==
# deb http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu saucy main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu saucy main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list <==
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-themes-trusty.list.save <==
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu trusty main


==> /etc/apt/sources.list.d/noobslab-ubuntu-apps-utopic.list <==
# deb http://ppa.launchpad.net/noobslab/apps/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu utopic main


==> /etc/apt/sources.list.d/noobslab-ubuntu-apps-utopic.list.save <==
# deb http://ppa.launchpad.net/noobslab/apps/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/apps/ubuntu utopic main


==> /etc/apt/sources.list.d/noobslab-ubuntu-themes-utopic.list <==
# deb http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main


==> /etc/apt/sources.list.d/noobslab-ubuntu-themes-utopic.list.save <==
# deb http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main
# deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu utopic main


==> /etc/apt/sources.list.d/otto-kesselgulasch-lightzone-saucy.list <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/lightzone/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/lightzone/ubuntu saucy main


==> /etc/apt/sources.list.d/otto-kesselgulasch-lightzone-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/lightzone/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/lightzone/ubuntu saucy main


==> /etc/apt/sources.list.d/otto-kesselgulasch-lightzone-saucy.list.save <==
# deb http://ppa.launchpad.net/otto-kesselgulasch/lightzone/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/lightzone/ubuntu saucy main


==> /etc/apt/sources.list.d/philip5-extra-trusty.list <==
# deb http://ppa.launchpad.net/philip5/extra/ubuntu trusty main
# deb-src http://ppa.launchpad.net/philip5/extra/ubuntu trusty main


==> /etc/apt/sources.list.d/philip5-extra-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/philip5/extra/ubuntu trusty main
# deb-src http://ppa.launchpad.net/philip5/extra/ubuntu trusty main


==> /etc/apt/sources.list.d/philip5-extra-trusty.list.save <==
# deb http://ppa.launchpad.net/philip5/extra/ubuntu trusty main
# deb-src http://ppa.launchpad.net/philip5/extra/ubuntu trusty main


==> /etc/apt/sources.list.d/philip5-kubuntu-backports-trusty.list <==
# deb http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main


==> /etc/apt/sources.list.d/philip5-kubuntu-backports-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main


==> /etc/apt/sources.list.d/philip5-kubuntu-backports-trusty.list.save <==
# deb http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main
# deb-src http://ppa.launchpad.net/philip5/kubuntu-backports/ubuntu trusty main


==> /etc/apt/sources.list.d/pinta-maintainers-pinta-stable-trusty.list <==
# deb http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu trusty main


==> /etc/apt/sources.list.d/pinta-maintainers-pinta-stable-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu trusty main


==> /etc/apt/sources.list.d/pinta-maintainers-pinta-stable-trusty.list.save <==
# deb http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu trusty main


==> /etc/apt/sources.list.d/pipelight-stable-saucy.list <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu saucy main


==> /etc/apt/sources.list.d/pipelight-stable-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu saucy main


==> /etc/apt/sources.list.d/pipelight-stable-saucy.list.save <==
# deb http://ppa.launchpad.net/pipelight/stable/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/pipelight/stable/ubuntu saucy main


==> /etc/apt/sources.list.d/sialan-desktop-trusty.list <==
# deb http://ppa.launchpad.net/sialan/desktop/ubuntu trusty main
# deb-src http://ppa.launchpad.net/sialan/desktop/ubuntu trusty main


==> /etc/apt/sources.list.d/sialan-desktop-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/sialan/desktop/ubuntu trusty main
# deb-src http://ppa.launchpad.net/sialan/desktop/ubuntu trusty main


==> /etc/apt/sources.list.d/sialan-desktop-trusty.list.save <==
# deb http://ppa.launchpad.net/sialan/desktop/ubuntu trusty main
# deb-src http://ppa.launchpad.net/sialan/desktop/ubuntu trusty main


==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-trusty.list <==
# deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu utopic main # disabilitato durante l'avanzamento a utopic
# deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main


==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-trusty.list.distUpgrade <==
deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main
# deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main


==> /etc/apt/sources.list.d/team-xbmc-xbmc-nightly-trusty.list.save <==
# deb http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu utopic main # disabilitato durante l'avanzamento a utopic
# deb-src http://ppa.launchpad.net/team-xbmc/xbmc-nightly/ubuntu trusty main


==> /etc/apt/sources.list.d/teejee2008-ppa-trusty.list <==
# deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/teejee2008-ppa-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/teejee2008-ppa-trusty.list.save <==
# deb http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/teejee2008/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-saucy.list <==
# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu saucy main


==> /etc/apt/sources.list.d/tualatrix-ppa-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu saucy main


==> /etc/apt/sources.list.d/tualatrix-ppa-saucy.list.save <==
# deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu saucy main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list <==
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list.distUpgrade <==
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/tualatrix-ppa-trusty.list.save <==
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list.distUpgrade <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main


==> /etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list.save <==
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main # disabilitato durante l'avanzamento a trusty
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main


==> /etc/apt/sources.list.d/wallch-wallch-4_0-trusty.list <==
# deb http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main


==> /etc/apt/sources.list.d/wallch-wallch-4_0-trusty.list.distUpgrade <==
# deb http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main


==> /etc/apt/sources.list.d/wallch-wallch-4_0-trusty.list.save <==
# deb http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
# deb-src http://ppa.launchpad.net/wallch/wallch-4.0/ubuntu trusty main
virtualenix@vincent-Ubuntu:~$ 



```

second series of command, first "lsb_release -a"

```

virtualenix@vincent-Ubuntu:~$ lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic
virtualenix@vincent-Ubuntu:~$ 
```

.....second command "cat /etc/issue"

```
virtualenix@vincent-Ubuntu:~$ cat /etc/issueUbuntu 14.10 \n \l


virtualenix@vincent-Ubuntu:~$ 
```


....and, the last command "uname -a"

```
virtualenix@vincent-Ubuntu:~$ uname -aLinux vincent-Ubuntu 3.16.0-25-generic #33-Ubuntu SMP Tue Nov 4 12:06:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
virtualenix@vincent-Ubuntu:~$ 
```


....and now...only I hope!! 
eheh ...thx in advance for help me!!

---

### Post by Bashing-om on 2014-11-18
talialu; Mabe, just maybe
The 3rd party sources in '/etc/apt/sources.list.d ' looks to me that you have recently commented them out after the release upgrade ?
AS things STAND now, All I see is 
> 
37	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner
38	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) saucy partner

in the file ' /etc/apt/sources.list
that may not be a cause of a major problem (partner).
Comment those source lines out also and get a new status:
```

sudo apt-get update
sudo apt-get upgrade

```
IF these run clean then we can focus attention to rsyslog and  ubuntu-minimal. Hopefully, as you are running a later release, no great harm has to this time been done.

There are, as you know, Many 3rd party software sources to test before turning them back on for use in utopic .

Making progress
[INDENT][INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-11-18
> **talialu said:**
> ```

Configurazione di rsyslog (7.4.4-1ubuntu11)...
L'utente «syslog» fa già parte del gruppo «adm».
chown: impossibile accedere a "/var/spool/rsyslog": File o directory non esistente
dpkg: errore nell'elaborare il pacchetto rsyslog (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di ubuntu-minimal:
 ubuntu-minimal dipende da rsyslog; comunque:
  Il pacchetto rsyslog non è ancora configurato.
```

Looks to me like the 'rsyslog' package needs to be reinstalled.
/var/spool/syslog is provided by that package.

```
sudo apt-get install --reinstall rsyslog
```

---

### Post by Bashing-om on 2014-11-18
@ ian ; \o
As always, a pleasure to see you pop in .

[INDENT][INDENT]good things happen too
[/INDENT][/INDENT]

---

### Post by talialu on 2014-11-19
....tryed to do command "**sudo apt-get install --reinstall rsyslog**" and nothing:

```
virtualenix@vincent-Ubuntu:~$ sudo apt-get install --reinstall rsyslog
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 1 reinstallati, 0 da rimuovere e 0 non aggiornati.
2 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
E: Internal Error, No file name for rsyslog:amd64
virtualenix@vincent-Ubuntu:~$ 



```


...no news!!

---

### Post by ian-weisser on 2014-11-19
Okay, let's give apt one more try:
```
sudo apt-get update
sudo apt-get clean
sudo apt-get install --fix-broken
```

---

### Post by talialu on 2014-11-20
....the last step was not good!! 

I try the "apt-get update" and "apt-get clean" all ok, but this is what happen when i dgt the last command "apt-get install --fix-broken":

```
virtualenix@vincent-Ubuntu:~$ sudo apt-get install --fix-brokenLettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 8 non aggiornati.
2 non completamente installati o rimossi.
Dopo quest'operazione, verranno occupati 0 B di spazio su disco.
Configurazione di rsyslog (7.4.4-1ubuntu11)...
L'utente «syslog» fa già parte del gruppo «adm».
chown: impossibile accedere a "/var/spool/rsyslog": File o directory non esistente
dpkg: errore nell'elaborare il pacchetto rsyslog (--configure):
 il sottoprocesso installato script di post-installation ha restituito lo stato di errore 1
dpkg: problemi con le dipendenze impediscono la configurazione di ubuntu-minimal:
 ubuntu-minimal dipende da rsyslog; comunque:
  Il pacchetto rsyslog non è ancora configurato.


dpkg: errore nell'elaborare il pacchetto ubuntu-minimal (--configure):
 problemi con le dipendenze - lasciato non configurato
Segnalazione apport non scritta poiché il messaggio di errore indica la presenza di un fallimento precedente.
    Si sono verificati degli errori nell'elaborazione:
 rsyslog
 ubuntu-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)
virtualenix@vincent-Ubuntu:~$
```


....ok, tonight i make backup and I install again the operative system.
Many thx in advance for help ...and support...me!!

---

### Post by Bashing-om on 2014-11-21
talialu; Hello;

Just a note to check the status.

Did you (RE-)install ? OR are we still working this issue ?

[INDENT][INDENT]not done 'till the paper work is done ( :) )
[/INDENT][/INDENT]

---

### Post by talialu on 2014-11-24
....hi all,
at the end of the story I've maked the insane command...."format" and install the Ubuntu 14.04.1 LTS again....fresh installation, again little modify at kernel ...and, all work good and....at least I have the system more reactive and fast!!

Thx a lot for help and support me.

---

