---
title: "Don't understand message in Terminal"
date: 2021-09-12
forum: General Help
---

### Post by Penfold1971 on 2021-09-12
[COLOR=#1A1A1A][FONT=Verdana]I have a very basic machine running headless. OS is Ubuntu 20.04.3.[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]I log in via Terminal on an iMac to see if there are any updates to the OS.The confusion I refer to comprises these two parts from the Terminal window :[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]*8 updates can be applied immediately.*[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]*8 of these updates are standard security updates.*[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]But when I use the command 'sudo apt-get upgrade' I get the following :[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]*The following packages have been kept back:*[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]*  linux-generic linux-headers-generic linux-image-generic*[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=Verdana]*0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.*[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]If 8 out of 8 updates are security updates and can be applied immediately, why is there the apparent contradiction '0 to upgrade …' and ' … 3 not to upgrade.'?[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]Be aware - I have virtually no expertise in these matters and simply need to keep the Ubuntu system up and running without hitch. I use it to take part in the Folding at Home project. This machine, with Ubuntu installed, has been processing FAH work units since 2012.[/FONT][/COLOR]

[COLOR=#1A1A1A][FONT=Verdana]Thanks in advance for any enlightenment.[/FONT][/COLOR]

---

### Post by ActionParsnip on 2021-09-12
Try
```

sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by GhX6GZMB on 2021-09-12
First you need to _get_ the upgrades.
Then you need to _run_ the upgrades.

```
sudo apt update
sudo apt upgrade
```

---

### Post by deadflowr on 2021-09-12
The command
```
sudo apt-get upgrade
```
does not install new packages.

Running the command ActionParsnip posted, 
```
sudo apt-get dist-upgrade
```
command will install new packages.

The linux-generic packages listed need to install new packages in order to completely satisfy the update.
This is because the linux-generic packages are dependent on the latest kernels available.

(If you run the dist-upgrade command it should output more info about what new packages will be installed.
Probably with names like linux-image-5.4.0-123-generic or something like that.
Those numbered strings package represent completely new packages.)

---

### Post by Penfold1971 on 2021-09-12
Thanks ActionParsnip 'apt-get [COLOR=#ff0000]dist[/COLOR]-upgrade' did the trick. I'd just been using 'apt-get upgrade'.

---

### Post by Penfold1971 on 2021-09-12
And thanks for that explanation, dead flower. No wonder I was stalling things.

---

