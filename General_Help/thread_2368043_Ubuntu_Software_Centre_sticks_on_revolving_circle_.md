---
title: "Ubuntu Software Centre sticks on revolving circle (16.04LTS)"
date: 2017-08-06
forum: General Help
---

### Post by davehk on 2017-08-06
Hi,

As of yesterday,  by Ubuntu Software Centre sitcks on the revolving arrow screen whenever I click any of the three tabs. I first noticed problems trying to install the latest version of Virtualbox by double-clicking on the downloaded .deb file. SW centre opens, I click Install and after asking for authorization is then immediately went back to the SW screen with the "remove" icon displayed, but it hadn't done anything. Now if I do that, I get the same blank area with the revolving arrow as above.

I've already tried

sudo apt purge gnome-software ubuntu-software
sudo apt autoremove (which seemed to clean everything up as expected)
sudo apt install gnome-software ubuntu-software

but it's made no difference. (.....thinks - perhaps I need to reboot).

OK, rebooted and SW centre GUI now seems to be working (though I've not tried to install anything via the GUI).

However, it still won't install VB from the deb archive - I click on "install", it briefly say "installing" and then jumps back to "install" again, without doing anything. I wonder if it's a problem with the .deb archive (I re-downloaded it which made no difference)?


Thanks.

---

### Post by Autodave on 2017-08-06
I gave up on that awhile ago and went back to using [I]synaptic.

sudo apt-get install synaptic
[/I]
That will install under *System.*

---

### Post by davehk on 2017-08-06
Yes, first thing I did after installing Xenial was to install synaptic! It installed under System Tools -> Administration on my system.

Can't seem to work out how to use it to install a downloaded .deb archive, though I know I've done it on 12.04!

---

### Post by westie457 on 2017-08-06
Install 'gdebi' and its dependencies using synaptic package manager, close synaptic.
Right-click the deb select 'Open with' > 'Gdebi Package Installer'


Or using the terminal > cd (to where the deb file is located)
```
sudo dpkg -i <name-of-file>.deb
```

---

### Post by davehk on 2017-08-06
Yes, thanks - in fact I just remembered about dpkg -i.

I decided to add the repository and let synaptics handle it - which worked fine.

Thanks for help.

---

