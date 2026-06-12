---
title: "Fresh install: Ubuntu 15.10 x64 /w LVM+LUKS works perfectly until I switch to 'fgrl"
date: 2015-10-23
forum: General Help
---

### Post by AnonyUser on 2015-10-23
[FONT=verdana]
[/FONT]
[TABLE]
[TR]
[TH="align: left"]System[/TH]
[TH="align: center"]Specs[/TH]
[/TR]
[TR]
[TD="align: left"]CPU[/TD]
[TD="align: center"]intel core i3-2100[/TD]
[/TR]
[TR]
[TD="align: left"]GPU[/TD]
[TD="align: center"]ASUS HD5750[/TD]
[/TR]
[TR]
[TD="align: left"]RAM[/TD]
[TD="align: center"]4GB[/TD]
[/TR]
[TR]
[TD="align: left"]MOBO[/TD]
[TD="align: center"]P67-DS3-B3[/TD]
[/TR]
[TR]
[TD="align: left"]Keyboard[/TD]
[TD="align: center"]Skiller - sharkoon[/TD]
[/TR]
[/TABLE]

[FONT=verdana]Everything was working pretty much fine. Videos decoding well, music too - internet experience working great... desktop animations etc[/FONT]
[FONT=verdana]I also installed a few basic packages (including: Skype, Steam, Chromium, Gimp, Geany etc) without real problems.[/FONT]
[FONT=verdana]
Then I decided to switch from 'x-org' to 'fglrx' from the driver menu (instead of downloading from amd.com)

[/FONT]
[FONT=verdana]After I hit restart the Luks-promt was just frozen (or my keyboard just didn't respond anymore).

[/FONT]
[FONT=verdana]The weird thing is that every 2 reboots, I can access a different design of LUKS and enter the password* only resulting in a logcat and then a black screen. At least I can access Recovery Mode.[/FONT]
[FONT=verdana]PS I'll make a thread on the forums and link it here later.[/FONT]
[FONT=verdana]Edit: Please take lightly any grammar mistakes.[/FONT]

---

### Post by ajgreeny on 2015-10-23
15.10 does not yet work with the AMD fglrx driver so for now at least you will have to uninstall it with ```
sudo apt-get remove fglrx
```
See [http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go](http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go)

---

### Post by AnonyUser on 2015-10-24
[https://www.reddit.com/r/Ubuntu/comments/3pxw9s/warning_fresh_install_ubuntu_1510_x64_w_lvmluks/](https://www.reddit.com/r/Ubuntu/comments/3pxw9s/warning_fresh_install_ubuntu_1510_x64_w_lvmluks/)

---

