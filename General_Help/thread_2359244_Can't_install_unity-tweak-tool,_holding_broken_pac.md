---
title: "Can't install unity-tweak-tool, holding broken packages"
date: 2017-04-21
forum: General Help
---

### Post by giggybyte2 on 2017-04-21
Hey everyone, 

I've been trying to get unity-tweak-tool installed for a while now. I had it a while ago but it seems to have disappeared when my ~/.cache folder got nuked.

I tried to use apt to install it and got this:

```
dustin@giggybyte:~$ sudo apt-get install unity-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-tweak-tool : Depends: unity-webapps-common but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

At this point I tried fixing it with -f:
```

dustin@giggybyte:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I tried installing the dependency manually:
```

dustin@giggybyte:~$ sudo apt-get install unity-webapps-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-webapps-common : Depends: unity-webapps-service (>= 2.3.8-0ubuntu3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Ugh, okay... how far deep down the rabbit hole does this go?
```

dustin@giggybyte:~$ sudo apt-get install unity-webapps-service
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-webapps-service : Depends: webapp-container
E: Unable to correct problems, you have held broken packages.

dustin@giggybyte:~$ sudo apt-get install webapp-container
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 webapp-container : Depends: qtbase-abi-5-5-1
                    Depends: qtdeclarative-abi-5-5-0
                    Depends: liboxideqt-qmlplugin (>= 1.8) but it is not going to be installed
                    Depends: qml-module-ubuntu-web (= 0.23+16.04.20161028-0ubuntu2) but it is not going to be installed
                    Depends: qtdeclarative5-ubuntu-ui-toolkit-plugin (>= 1.3) or
                             qtdeclarative5-ubuntu-ui-toolkit-plugin-gles (>= 1.3) but it is not going to be installed
                    Depends: unity-webapps-qml but it is not going to be installed
                    Depends: webbrowser-app (= 0.23+16.04.20161028-0ubuntu2)
E: Unable to correct problems, you have held broken packages.
dustin@giggybyte:~$ 

```

I had just installed it earlier in the week without any issues but now Ubuntu decides it hates me and of course it's not Linux if you're not spending your Friday night fixing inevitable issues.
Does anyone know what's going on here? Thanks in advance.

edit: Here's the output from a few other helpful commands:
```

dustin@giggybyte:~$ sudo apt-get update
Err:1 https://dl.winehq.com/wine-builds/ubuntu xenial InRelease
  Could not resolve host: dl.winehq.com
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:3 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Hit:4 http://repository.spotify.com stable InRelease                           
Get:5 http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu xenial InRelease [17.6 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [288 kB]
Hit:9 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease    
Get:10 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [184 kB]
Hit:11 http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu xenial InRelease  
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [160 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [188 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Hit:16 http://ppa.launchpad.net/tista/adapta/ubuntu xenial InRelease
Get:17 http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu xenial/main amd64 Packages [572 B]
Get:18 http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu xenial/main i386 Packages [572 B]
Get:19 http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu xenial/main Translation-en [344 B]
Fetched 1,152 kB in 1s (1,100 kB/s)                                            
Reading package lists... Done
W: Failed to fetch https://dl.winehq.com/wine-builds/ubuntu/dists/xenial/InRelease  Could not resolve host: dl.winehq.com
W: Some index files failed to download. They have been ignored, or old ones used instead.

dustin@giggybyte:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```

---

### Post by deadflowr on 2017-04-21
> W: Failed to fetch [https://dl.winehq.com/wine-builds/ubuntu/dists/xenial/InRelease](https://dl.winehq.com/wine-builds/ubuntu/dists/xenial/InRelease)  Could not resolve host: dl.winehq.com
W: Some index files failed to download. They have been ignored, or old ones used instead.

This means you need to fix the wine repo.
Try disabling it (the winehq repo) and then rerun the update command.
Then see what happens when you run the install commands or fix broken package commands, or upgrade commands.

---

### Post by gifford on 2017-04-21
Do you have Synaptic Package Manager installed? If so, choose custom filters and click on broken to see all that is wrong and then go to edit and choose Fix Broken Packages.

---

### Post by MilkThief on 2017-04-27
Identical issue happened to me, but without the "W: Failed to fetch..." issue.
I think this is not the true problem.

This is my output:
```

$ sudo apt-get install unity-tweak-tool
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
 unity-tweak-tool : Dipende: unity-webapps-common ma non sta per essere installato
E: Impossibile correggere i problemi, ci sono pacchetti danneggiati bloccati.
```

Then, trying to install every depending package, the final result is:

```

$ sudo apt-get -f install webapp-container
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
Alcuni pacchetti non possono essere installati. Questo può voler dire
che è stata richiesta una situazione impossibile oppure, se si sta
usando una distribuzione in sviluppo, che alcuni pacchetti richiesti
non sono ancora stati creati o sono stati rimossi da Incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
 webapp-container : Dipende: qtbase-abi-5-5-1
                    Dipende: qtdeclarative-abi-5-5-0
                    Dipende: liboxideqt-qmlplugin (>= 1.8) ma non sta per essere installato
                    Dipende: qml-module-ubuntu-web (= 0.23+16.04.20161028-0ubuntu2) ma non sta per essere installato
                    Dipende: qtdeclarative5-ubuntu-ui-toolkit-plugin (>= 1.3) oppure
                             qtdeclarative5-ubuntu-ui-toolkit-plugin-gles (>= 1.3) ma non sta per essere installato
                    Dipende: unity-webapps-qml ma non sta per essere installato
                    Dipende: webbrowser-app (= 0.23+16.04.20161028-0ubuntu2)
E: Impossibile correggere i problemi, ci sono pacchetti danneggiati bloccati.
```

I have a issue with the desktop corners I need to reset with unity tweak tool...
Please help! :cry:

---

### Post by MilkThief on 2017-04-28
:guitar:

I fixed this way:

I had several PPA on the APT configuration and I suspected one or more may cause version issues between dependencies.
Looking between PPA names I found a "backport". But how to remove its packages and substitute them with the original repo packages?


[LIST=1]
[*]*sudo apt-get install ppa-purge*
[*]*sudo ppa-purge ppa:<ppa name you want to remove and purge>/ppa*
[*]wait & cross fingers ;)
[*]*sudo apt-get install unity-tweak-tool*
[*]if [ ok ] then drink_a_beer(); else (goto $point#2; choose_another_PPA()) ;)
[/LIST]

I drunk a beer at the first cycle... \\:D/
Good luck!

**NOTE:** *you can install "Y PPA Manager". It is a good GUI tool that includes ppa-purge and can indicate wich packages are contained in every PPA. This way you know what you remove...*

---

### Post by again? on 2017-04-28
> **MilkThief said:**
> :guitar:

I fixed this way:

I had several PPA on the APT configuration and I suspected one or more may cause version issues between dependencies.
Looking between PPA names I found a "backport". But how to remove its packages and substitute them with the original repo packages?


[LIST=1]
[*]*sudo apt-get install ppa-purge*
[*]*sudo ppa-purge ppa:<ppa name you want to remove and purge>/ppa*
[*]wait & cross fingers ;)
[*]*sudo apt-get install unity-tweak-tool*
[*]if [ ok ] then drink_a_beer(); else (goto $point#2; choose_another_PPA()) ;)
[/LIST]

I drunk a beer at the first cycle... \\:D/
Good luck!

**NOTE:** *you can install "Y PPA Manager". It is a good GUI tool that includes ppa-purge and can indicate wich packages are contained in every PPA. This way you know what you remove...*

If using ppa-purge here are couple of useful commands.
All enabled repositories.
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

Enabled third party launchpad repositories in ppa-purge form.
```
for PPA_FILE in $(ls /etc/apt/sources.list.d/*.list); do cat ${PPA_FILE} | egrep -v '^#|^ *$' | grep "ppa.launchpad.net" | cut -d "/" -f4-5; done
```

---

