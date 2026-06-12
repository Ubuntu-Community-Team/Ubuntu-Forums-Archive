---
title: "VLC Removed itself from system and will not re-install"
date: 2013-07-16
forum: General Help
---

### Post by 2defmouze on 2013-07-16
:confused:Hi all.. hope I am posting in the correct section - If not please let me know where this would be more appropriate.

The other day I was letting the software updater on my Ubuntu 13.04 system do it's thing, when I noticed a message about removing unneeded packages and saw something involving VLC media player. At the time I thought nothing of it and wasn't paying it much attention so I let it finish up and found shortly after that VLC had been removed from the system. Cannot reinstall using the Software Center or Terminal. Via Software Center I can find it and hit Install, when after a few seconds I am given this message:
```
The following packages have unmet dependencies:


vlc: Depends: vlc-nox (= 2.0.6-1) but 2.0.6-1 is to be installed
     Depends: libavcodec-extra-53 (>= 6:0.8.6) but 6:0.8.6ubuntu2 is to be installed
     Depends: libavutil-extra-51 (>= 6:0.8.6) but 6:0.8.6ubuntu2 is to be installed
     Depends: libc6 (>= 2.15) but 2.17-0ubuntu5 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.11-0ubuntu1 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.3-1ubuntu1 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.4+dfsg-0ubuntu9.2 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.4+dfsg-0ubuntu9.2 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.7.3-1ubuntu1 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.7.dfsg-13ubuntu2 is to be installed

```

Trying to install in Terminal using sudo apt-get install vlc:
```
sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.0.6-1) but it is not going to be installed
       Depends: libvlccore5 (>= 2.0.0) but it is not going to be installed
       Recommends: vlc-plugin-notify (= 2.0.6-1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.6-1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

So here I am at a loss. I've tried Googling the issues in various ways and haven't come up with anything that works. Any suggestions are much appreciated. I'm computer literate enough to figure most things out but just don't have much experience beyond the basics with Linux issues. Thanks in advance!
On a related note.. apparently my PS3 Media Server up and disappeared from the system without warning as well. Terminal is seeming to link the two together so maybe that will help.. I am seeing these messages sporadically in terminal, related to PS3MS:
```

The following package was automatically installed and is no longer required:
  ps3mediaserver-multiarch
Use 'apt-get autoremove' to remove it.
```
And
```
The following packages have unmet dependencies:
 ps3mediaserver : Depends: vlc but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

Again.. much thanks for any assistance.

---

### Post by Bashing-om on 2013-07-16
2defmouze; Hi !

Try this:
Disable all PPAs and third-party repos, reducing things to simplest terms;
Attack the dependency situation thus:
```

sudo apt-get update
sudo apt-get purge vlc
sudo rm /var/cache/apt/archives/vlc
sudo apt-get install vlc

```
Then maybe run:
```

sudo apt-get -f install

```
[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by 2defmouze on 2013-07-16
> **Bashing-om said:**
> 2defmouze; Hi !

Try this:
Disable all PPAs and third-party repos, reducing things to simplest terms;
Attack the dependency situation thus:
```

sudo apt-get update
sudo apt-get purge vlc
sudo rm /var/cache/apt/archives/vlc
sudo apt-get install vlc

```
Then maybe run:
```

sudo apt-get -f install

```[INDENT][INDENT]worth a shot
[/INDENT]
[/INDENT]



You are a lifesaver!! :)

In being greedy I wanted to give it a go without the disabling all PPA's and 3rd party repos step.. so instead I used Synaptic Package Manager to remove the VLC install which showed as a weird and unmatching version number to the current available one.

The next steps did not work out, but running
sudo apt-get -f install vlc
..solved the problem! Afterwards I was able to reinstall PS3 Media Server as well without issue.

Huge thanks for that my friend!!! :KS

---

### Post by Bashing-om on 2013-07-16
2defmouze; Hey, Great !
Glad ya got it resolved........open source, we are all in this together.
Now would be a great time to make sure all is up-2-date:
```
sudo apt-get update
sudo apt-get upgrade

```
and should be good to go.

Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

