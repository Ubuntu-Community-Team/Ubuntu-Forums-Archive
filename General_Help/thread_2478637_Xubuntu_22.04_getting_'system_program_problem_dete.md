---
title: "Xubuntu 22.04 getting 'system program problem detected' at startup."
date: 2022-08-31
forum: General Help
---

### Post by JimLS on 2022-08-31
Initial install went ok and I did not get this message.  Am setting it up for mythtv and started getting this as I was configuring mythtv with the Mythbuntu control program.  I looked in the system log to see what I could see but didn't find anything although I don't really know what I am looking for.  What should I be doing or looking for?

---

### Post by Bashing-om on 2022-08-31
JimLS; Hello -

1st of all we want to know that the system is fully updated; and that the package manager is in  a consistent state.
run in terminal:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```

Now if all is clean proceed to "look" at what might be at fault.

what shows:
```

dpkg -l mythtv
apt policy mythtv

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by JimLS on 2022-09-01
Did the update, upgrade, etc.  That had been done recently but there were a few upgrades.  No other messages of note. The issue still happened.

For the others:
```


myth@myth-14:~$ dpkg -l mythtv
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  mythtv         <none>       <none>       (no description available)
myth@myth-14:~$ apt policy mythtv
mythtv:
  Installed: (none)
  Candidate: 2:32.0+fixes.202208131732.e5c974e402~ubuntu22.04.1
  Version table:
     2:32.0+fixes.202208131732.e5c974e402~ubuntu22.04.1 500
        500 https://ppa.launchpadcontent.net/mythbuntu/32/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/mythbuntu/32/ubuntu jammy/main i386 Packages
     2:32.0+fixes.202204231837.daa4e7e447~ubuntu22.04.1 500
        500 https://ppa.launchpadcontent.net/mythbuntu/32/ubuntu jammy/main amd64 Packages
        500 https://ppa.launchpadcontent.net/mythbuntu/32/ubuntu jammy/main i386 Packages
     2:32.0+fixes.20220325.f69ce764b7-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/multiverse amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu jammy/multiverse i386 Packages
myth@myth-14:~$


```
Now thinking this may be due to partial setup of mythtv and it may go away when it is complete.

---

### Post by Bashing-om on 2022-09-01
JimLS - Well well well --- Not

The dpkg output says that mythtv is NOT installed.

Am I being real dense ? is not the app - mythtv a must to be installed ?

so - let's see what happens when it is installed:
```

sudo apt update
sudo apt upgrade
sudo apt install mythtv

```

[INDENT]seems the logical thing to do
[/INDENT]

---

### Post by JimLS on 2022-09-01
That's very strange.  I have myth backend and frontend in my programs menu and they run when selected.  I used Mythbuntu Control Program to set things up which was supposed to install mythtv.  But after I checked that they run I used apt to install mythtv and it said it was a new program.  It appeared to be using the version I selected in MCP.  So it seems it was partly installed?  I will see how things go from here.  If they are still giving me trouble I may just start over with an clean install.

---

