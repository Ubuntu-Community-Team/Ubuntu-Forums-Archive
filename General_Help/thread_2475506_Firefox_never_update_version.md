---
title: "Firefox never update version"
date: 2022-05-30
forum: General Help
---

### Post by cam17 on 2022-05-30
On my 20.04.4LTS version Firefox has in the software update list a description of "updated never" That is the version on I have installed and Firefox has updated from 90 version to 100. What does that description explain in the software update?

---

### Post by TheFu on 2022-05-30
Try running these commands, in order.  If the first one fails. STOP!  Post the exact command and a few lines above/below the errror - -- AS TEXT, not images.
```
sudo apt update
sudo apt full-upgrade
```

Please.

You can see the exact version of firefox installed like this:
```
$ dpkg -l 'firefox*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait>
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version                         Architecture D>
+++-=================-===============================-============-=>
ii  firefox           100.0.2+build1-0ubuntu0.20.04.1 amd64        S>
ii  firefox-locale-en 100.0.2+build1-0ubuntu0.20.04.1 amd64        E>
```

That's the way you should post the command and output. Please.  By using forum code tags so the columns line up here.  Adv Reply + the "#" button in the advanced editor menu is how. Use it like you would for bold or quote or underline....

---

### Post by cam17 on 2022-05-31
Here is the results of the command line for the firefox dpkg -l 'firefox*

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version                         Architecture Description
+++-=================-===============================-============-============>
ii  firefox           100.0.2+build1-0ubuntu0.20.04.1 amd64        Safe and eas>
un  firefox-esr       <none>                          <none>       (no descript>
ii  firefox-locale-en 100.0.2+build1-0ubuntu0.20.04.1 amd64        English lang

I did not perform the updates as the question is why is it showing Firefox as not being updated yet it updates in Ubuntu software? what does the description "update never" mean?

---

### Post by Impavidus on 2022-05-31
I never use Ubuntu Software and I don't know how Ubuntu Software tries to determine when a package on the system was last updated from the repositories. It could try from the log files or it could remember when it installed the update. The former will fail if the logs were cleared, the latter will fail if another tool installed the update. Ubuntu Software is just one of the front-ends to the package manager. The heavy work is done by other tools, that can also be called from other GUI applications like update manager and synaptic or directly from the command line. Ubuntu Software would normally not be aware of what those other tools do; each tool only knows about the state of the system at the moment you run the tool.

---

### Post by ActionParsnip on 2022-05-31
[https://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=focal&section=all](https://packages.ubuntu.com/search?keywords=firefox&searchon=names&suite=focal&section=all)

According to the packages, you have the newest version in the repos

---

### Post by TheFu on 2022-05-31
Might you have multiple versions of firefox installed, perhaps using different packaging tools - snap, flatpak, appimage and APT?  The APT version is the current, non-ESR firefox. It matches what is on my system.

If you type 'which firefox', you may see a different answer than /usr/bin/firefox.  Also, if you start firefox using a menu, the menu entry is controlled by the .desktop file. Inside that file, it can point to a program/script **anywhere** on the box.  I'd use **locate .desktop |grep firefox** to find all the firefox related .desktop files.  On my 20.04 system, there is only 1, but if I was using snap and flatpak packages, I could have 3+ of those files.

---

### Post by cam17 on 2022-06-13
When I look at both Ubuntu software and software GUI and click on the GUItab installed neither shows Firefox. More importantly what is the difference between the 2 versions ?

I did not istall Firefox it was the default and i didn't change it.

---

### Post by vanadium on 2022-06-13
It is indeed as was mentioned already: Software center is what it is. The label "Proprietary" also is not quite appropriate. Ignore this information.

---

