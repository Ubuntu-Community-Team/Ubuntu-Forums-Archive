---
title: "Transmission error with every update"
date: 2014-07-08
forum: General Help
---

### Post by el_heffe on 2014-07-08
So, don't quite remember how I installed transmission on my ubuntu 12.04 LTS server, but I did.  However, at some point in time, I have been getting errors whenever I do an update that look like this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 transmission : Depends: transmission-common (>= 2.84-0ubuntu0.12.04.1) but 2.83-0ubuntu0.12.04.2 is installed
 transmission-cli : Depends: transmission-common (= 2.84-0ubuntu0.12.04.1) but 2.83-0ubuntu0.12.04.2 is installed
 transmission-gtk : Depends: transmission-common (= 2.84-0ubuntu0.12.04.1) but 2.83-0ubuntu0.12.04.2 is installed
E: Unmet dependencies. Try using -f.
```

And this is the output of sudo apt-get install -f:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  transmission-common transmission-daemon
The following packages will be upgraded:
  transmission-common transmission-daemon
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/527 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 288580 files and directories currently installed.)
Preparing to replace transmission-common 2.83-0ubuntu0.12.04.2 (using .../transmission-common_2.84-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement transmission-common ...
Processing triggers for hicolor-icon-theme ...
Setting up transmission-common (2.84-0ubuntu0.12.04.1) ...
dpkg: dependency problems prevent configuration of transmission-daemon:
 transmission-daemon depends on transmission-common (= 2.83-0ubuntu0.12.04.2); however:
  Version of transmission-common on system is 2.84-0ubuntu0.12.04.1.
dpkg: error processing transmission-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                        Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And sudo dpkg --configure -a

```

dpkg: dependency problems prevent configuration of transmission-daemon:
 transmission-daemon depends on transmission-common (= 2.83-0ubuntu0.12.04.2); however:
  Version of transmission-common on system is 2.84-0ubuntu0.12.04.1.
dpkg: error processing transmission-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 transmission-daemon
```

I have tried manually downloading transmission-common_2.83-0ubuntu0.12.04.2_all.deb and installing it with sudo dpkg -i, and it installs no problem. 

```
$ sudo dpkg -i transmission-common_2.83-0ubuntu0.12.04.2_all.deb 
dpkg: warning: downgrading transmission-common from 2.84-0ubuntu0.12.04.1 to 2.83-0ubuntu0.12.04.2.
(Reading database ... 288580 files and directories currently installed.)
Preparing to replace transmission-common 2.84-0ubuntu0.12.04.1 (using transmission-common_2.83-0ubuntu0.12.04.2_all.deb) ...
Unpacking replacement transmission-common ...
Setting up transmission-common (2.83-0ubuntu0.12.04.2) ...
Processing triggers for hicolor-icon-theme ...
``` 
I am a bit lost as to what to do now. Thank you in advance for any help you can provide!

---

### Post by ian-weisser on 2014-07-08
Here is the current version of Transmission common for various Ubuntu releases:
```
$ rmadison -u ubuntu transmission-common
 transmission-common | 1.92-0ubuntu2         | lucid            | all
 transmission-common | 1.93-0ubuntu0.10.04.1 | lucid-updates    | all
 transmission-common | 2.51-0ubuntu1         | precise          | all
 transmission-common | 2.51-0ubuntu1.3       | precise-security | all
 transmission-common | 2.51-0ubuntu1.3       | precise-updates  | all
 transmission-common | 2.82-0ubuntu1         | saucy            | all
 transmission-common | 2.82-1.1ubuntu3       | trusty           | all
 transmission-common | 2.82-1.1ubuntu3       | utopic           | all
```

See those dkpg warnings about how your transmission-common is higher (2.83) than the newest version in Ubuntu? I don't know where you got it from, but you sure didn't get it from the Ubuntu Repositories. And it broke your system.

What to do:

1) Uninstall Transmission. All of it. Every package.
```
sudo apt-get autoremove transmission-common
```

2) Disable all non-Ubuntu Transmission sources
```
software-properties-gtk
```

3) Delete every transmission* package in /var/cache/apt/archives
```
sudo rm /var/cache/apt/archives/transmission*
```

4) Check if your package manager is working properly. If not, post the entire output here.
```
sudo apt-get upgrade && sudo apt-get update
```

5) If no errors in step 4, your package manager is fixed. Reinstall Transmission from the Ubuntu Repositories.
```
sudo apt-get install transmission-gtk
```

---

### Post by el_heffe on 2014-07-10
Yea, not sure where i got it from either- it has been several months since I last had my hands on that server.  I will work on this again when I get an opportunity (probably not for a few weeks at least, if not a few months- moving. :-| )

---

### Post by el_heffe on 2014-07-13
I was able to get into my server when I remembered what port I had forwarded to my SSH connection on the 'server'. Anyways- this is what I get:

```
sudo apt-get autoremove transmission-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 transmission : Depends: transmission-common (>= 2.84-0ubuntu0.12.04.1) but it is not going to be installed
 transmission-cli : Depends: transmission-common (= 2.84-0ubuntu0.12.04.1) but it is not going to be installed
 transmission-daemon : Depends: transmission-common (= 2.83-0ubuntu0.12.04.2) but it is not going to be installed
 transmission-gtk : Depends: transmission-common (= 2.84-0ubuntu0.12.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Not sure what to do next.  It is 12.04 'server' and I put it in quotes because IOT use crash plan I installed fluxbox, so I could VNC in on the local nework and set it up properly.  Ideas?

---

### Post by ian-weisser on 2014-07-13
Let's tell dpkg to stop trying to install it.

```
$ dpkg --get-selections | grep transmission
```

This will return a list of lines that look like:
```
transmission                    install
transmission-gtk                install
transmission-cli                install
transmission-common             install
```

A bunch of yours will say 'install'. Let's change those to 'deinstall'
Put each package on a separate line.

```
$ sudo dpkg --set-selections <return>
transmission <tab> deinstall <return>
transmission-gtk <tab> deinstall <return>
transmission-cli <tab> deinstall <return>
transmission-common <tab> deinstall <CTRL+D>
```

---

### Post by el_heffe on 2014-08-19
> **ian-weisser said:**
> Let's tell dpkg to stop trying to install it.

```
$ dpkg --get-selections | grep transmission
```

This will return a list of lines that look like:
```
transmission                    install
transmission-gtk                install
transmission-cli                install
transmission-common             install
```

A bunch of yours will say 'install'. Let's change those to 'deinstall'
Put each package on a separate line.

```
$ sudo dpkg --set-selections <return>
transmission <tab> deinstall <return>
transmission-gtk <tab> deinstall <return>
transmission-cli <tab> deinstall <return>
transmission-common <tab> deinstall <CTRL+D>
```

You were quite correct, they said install, have now changed them all to deinstall:
```
dpkg --get-selections | grep transmission
transmission                                    deinstall
transmission-cli                                deinstall
transmission-common                             deinstall
transmission-daemon                             deinstall
transmission-gtk                                deinstall
```

and then do a 
```
sudo apt-get install -f
```

and get the following: 

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  transmission-daemon
Recommended packages:
  transmission-cli
The following packages will be upgraded:
  transmission-daemon
1 upgraded, 0 newly installed, 0 to remove and 82 not upgraded.
1 not fully installed or removed.
Need to get 0 B/237 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: dependency problems prevent configuration of transmission-daemon:
 transmission-daemon depends on transmission-common (= 2.83-0ubuntu0.12.04.2); however:
  Version of transmission-common on system is 2.84-0ubuntu0.12.04.1.
dpkg: error processing transmission-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 transmission-daemon
```

Sorry for the delay- it has been a long few months where I couldn't reboot the server as I wasn't there to handle if it not booting.  Not sure where to go from here, thanks for your help!! :D

---

### Post by SeijiSensei on 2014-08-19
Have you looked in /etc/apt/sources.list and /etc/apt/sources.list.d/ to make sure you are only using the official Ubuntu repositories and not some PPA?

---

### Post by el_heffe on 2014-08-19
> **SeijiSensei said:**
> Have you looked in /etc/apt/sources.list and /etc/apt/sources.list.d/ to make sure you are only using the official Ubuntu repositories and not some PPA?

Yea, I only added the repository for handbrake.  

Marking this as solved, updated to 12.04.4 today and it seems to have fixed it.  Not really sure what made it happier, the marking it uninstall and doing the dist-upgrade, or what, but it is good now.  Just wish I could have figured out wtf happened in the first place.  C'est ve.

---

