---
title: "'held  back dependencies'"
date: 2015-11-09
forum: General Help
---

### Post by UncleMonty on 2015-11-09
```
sudo apt-get install spotify-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 spotify-client : Depends: libnspr4-0d but it is not installable
                  Recommends: libavcodec53 but it is not installable or
                              libavcodec52 but it is not installable or
                              libavcodec-extra-53 but it is not installable or
                              libavcodec-extra-52 but it is not installable
                  Recommends: libavformat53 but it is not installable or
                              libavformat52 but it is not installable or
                              libavformat-extra-53 but it is not installable or
                              libavformat-extra-52 but it is not installable
E: Unable to correct problems, you have held broken packages.
```

I am using ubuntu 14.04. I went to synpatic package manager - can't find anything under 'broken' and 'fix broken package' also failed (as did apt-get upgrade and update). Any other options please?

---

### Post by UncleMonty on 2015-11-09
Okay fixed broken packages is now offering the following error message: 

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

---

### Post by QDR06VV9 on 2015-11-09
What is the output of this from terminal.
```
sudo apt-get -f install -s
```
Please use code tags when copying from terminal it helps us to read it better.

---

### Post by UncleMonty on 2015-11-10
What are code tags, sorry?

```
sudo apt-get -f install -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by slickymaster on 2015-11-10
> **UncleMonty said:**
> What are code tags, sorry?

```
sudo apt-get -f install -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

Regarding code tags, see this: [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

As for your issue, apparently it's fixed. If so, please mark the thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by QDR06VV9 on 2015-11-10
Just for more information only.
How to Install Spotify in Ubuntu
[http://howtoubuntu.org/how-to-install-spotify-in-ubuntu](http://howtoubuntu.org/how-to-install-spotify-in-ubuntu)

---

### Post by UncleMonty on 2015-11-10
Thanks, it's fixed! :)

---

