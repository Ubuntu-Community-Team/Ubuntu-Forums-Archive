---
title: "Having issues installing from terminal or software center"
date: 2014-06-24
forum: General Help
---

### Post by robert105 on 2014-06-24
Hi, I am fairly new to the Ubuntu system, I have Ubuntu 12.04 solely installed since my Vista crapped out. I have had no issues so far but now anytime I want to install anything either from terminal or software center I keep getting the error that I have bad/broken package files and nothing will install for me. I've tried all I could find from searching fixes but nothing seems to work, I just went in recovery mode and had that to remove broken packages but still no prevail in installing anything. For instance I try to install Synaptic Package Manager and I get this..

The following packages have unmet dependencies:
 synaptic : Depends: libept1.4.12 but it is not installable
            Depends: libvte9 (>= 1:0.24.0) but it is not installable
            Recommends: rarian-compat but it is not installable
E: Unable to correct problems, you have held broken packages.

I get this same type of message no matter what I try to install. Any help any at all would be greatly appreciated please!.

Thanks :)

---

### Post by Bashing-om on 2014-06-24
robert105; Hi Welcome to the forum.

The place to start the troubleshooting procedure is to see what the package manager reports.
Post back the out puts - between code tags - of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Then we can look for the cause.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by robert105 on 2014-06-24
[COLOR=#000000][FONT=Ubuntu Mono]Okay I did the update and upgrade which took forever and a day it seemed for the upgrade then after the [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get -f install I got:

```
[/FONT][/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-de language-pack-kde-en
  gir1.2-ubuntuoneui-3.0 language-pack-de-base language-pack-kde-zh-hans
  libcggl language-pack-kde-en-base firefox-globalmenu
  language-pack-kde-de-base libubuntuoneui-3.0-1 language-pack-zh-hans-base
  language-pack-de libcg language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.


[COLOR=#000000][FONT=Ubuntu Mono]
```

If this is done correctly, this is what I have to go on. Not sure what it all means though.

[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-06-24
Is the problem fixed? We will not know until you try to install something. The presence of packages that are no longer needed is not connected to the problem you are having. 

Regards.

---

### Post by robert105 on 2014-06-24
Wow seems to be fixed it allowed me to install the Synaptic Package Manager from the Software Center. I will try to install something from Terminal now and see *fingers crossed*

---

### Post by robert105 on 2014-06-24
YES! This resolved my issue, my hats off too you! Thank you. I can now again install both from terminal and software center. Again many thanks!

"Okay now am not sure if I am suppose to close this as Solved of if a forum mod does so."

---

### Post by deadflowr on 2014-06-24
[How to mark a thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by robert105 on 2014-06-25
Thank you! :)

---

