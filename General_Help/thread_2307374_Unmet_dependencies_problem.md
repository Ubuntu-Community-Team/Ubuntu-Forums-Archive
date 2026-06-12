---
title: "Unmet dependencies problem"
date: 2015-12-24
forum: General Help
---

### Post by george133 on 2015-12-24
Hello guys. I'm running Ubuntu 15.10 Wily Werewolf. Today I tried to install KDE, so I run:
```
sudo apt-get install kubuntu-destkop
```

But then I run into some errors. When I try to run command 'sudo apt-get remove --purge kubuntu-desktop', I'm getting this:
```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

After this, I tried 'apt-get -f install', and that's what I got:
```
(Reading database ... 468549 files and directories currently installed.)Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.10.20150723-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me? Thanks in advance.

---

### Post by howefield on 2015-12-24
Thread moved to the "General Help" forum.

---

### Post by slickymaster on 2015-12-24
> **george133 said:**
> Hello guys. Today I have tried to install KDE, so I run:
```
sudo apt-get install kubuntu-destkop
```

But then I run into some errors. When I try to run command 'sudo apt-get remove --purge kubuntu-desktop', I'm getting this:
[<---snip--->
After this, I tried 'apt-get -f install', and that's what I got:
```
(Reading database ... 468549 files and directories currently installed.)Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) ...
[COLOR=#FF0000][B]dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.10.20150723-0ubuntu1[/B][/COLOR]
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Can anyone help me? Thanks in advance.

The part I highlighted in red is probably the culprit. Try the following in a terminal window```
sudo apt-get purge account-plugin-google
sudo apt-get install -f
```

---

### Post by george133 on 2015-12-24
> **slickymaster said:**
> The part I highlighted in red is probably the culprit. Try the following in a terminal window```
sudo apt-get purge account-plugin-google
sudo apt-get install -f
```
This is output of first command:
```
george@Bacon:~$ sudo apt-get purge account-plugin-google
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 kde-telepathy-minimal : Depends: kde-config-telepathy-accounts (>= 15.04.0) but it is not going to be installed
 unity-scope-gdrive : Depends: account-plugin-google but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by slickymaster on 2015-12-24
Please run the following commands, one at a time, in a terminal window```

sudo dpkg -P unity-scope-gdrive
sudo dpkg -P account-plugin-google
sudo apt-get install -f
```

---

### Post by george133 on 2015-12-24
> **slickymaster said:**
> Please run the following commands, one at a time, in a terminal window```

sudo dpkg -P unity-scope-gdrive
sudo dpkg -P account-plugin-google
sudo apt-get install -f
```
Succeed without any errors, thank you. I have one question, can I install kubuntu-desktop now? Or will it still give me errors?

---

### Post by slickymaster on 2015-12-24
> **george133 said:**
> Succeed without any errors, thank you. I have one question, can I install kubuntu-desktop now? Or will it still give me errors?

Yes you can and in principle you won't get any errors. And being that the case, please don't forget to mark this thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution.

---

### Post by george133 on 2015-12-24
> **slickymaster said:**
> Yes you can and in principle you won't get any errors. And being that the case, please don't forget to mark this thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"), so other people searching the forums know that it provides a working solution.
Yeah I searched a lot to fix this problem. Someone will actually need it too :P Marked as solved

---

### Post by j-willson on 2016-09-04
Thanks you so much slickymaster. This solved a problem that has been bugging me for days.

---

### Post by pete0512 on 2016-10-17
This works on 16.04 too :) thanks it's been driving me mad for days

---

