---
title: "Anyone using gDesklets?"
date: 2005-10-29
forum: General Help
---

### Post by n1x0n on 2005-10-29
Hi :D
Anyone using gDesklets?
If yes, please help me install them... :(

niks@Niks:~$ cd Desktop/gDesklets-0.34.3
niks@Niks:~/Desktop/gDesklets-0.34.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
niks@Niks:~/Desktop/gDesklets-0.34.3$


Whats the problem?
Sorry for so "stupid" question, but i'm beginner...
Thats my last problem today... :)

Oh, another question - if there is any sense of firewall?

BIG, BIG THANKYOU!!!

---

### Post by PriceChild on 2005-10-29
you need the compiler thingy majigs... :P

```
apt-get build-essential
```

I'm a newb too so sorry if this is wrong, but i'm sure that's what you need, just not whether you need an "install" in there somewhere! :P

btw, what are gdesklets? :)

---

### Post by XDevHald on 2005-10-29
**Step 1: **
> apt-get install mawk 
**Step 2:**
> apt-get install gcc-3.4 gcc-3.4-base

**Step 3:**
> apt-get install make

---

### Post by PriceChild on 2005-10-29
What he said ;)

Sorry for any confusion :)

---

### Post by Dracontopes on 2005-10-29
[quote=n1x0n]Hi :D
Anyone using gDesklets?
If yes, please help me install them... :(

niks@Niks:~$ cd Desktop/gDesklets-0.34.3
niks@Niks:~/Desktop/gDesklets-0.34.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
niks@Niks:~/Desktop/gDesklets-0.34.3$


Whats the problem?
Sorry for so "stupid" question, but i'm beginner...
Thats my last problem today... :)

Oh, another question - if there is any sense of firewall?

BIG, BIG THANKYOU!!![/quote]

If you want a firewall you can try Firestarter. Install it with this command:
```
sudo apt-get install firestarter
```
Or search for the package in Synaptic, which has a nice GUI.

gDesklets is/was in the repositories also I thought? (I installed is yesterday)

---

### Post by n1x0n on 2005-10-29
niks@Niks:~$ cd Desktop/gDesklets-0.34.3
niks@Niks:~/Desktop/gDesklets-0.34.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
niks@Niks:~/Desktop/gDesklets-0.34.3$


Nothing :/
I've installed gcc, mawk & make :(

BTW. [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

---

### Post by n1x0n on 2005-10-29
niks@Niks:~$ cd Desktop/gDesklets-0.34.3
niks@Niks:~/Desktop/gDesklets-0.34.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
niks@Niks:~/Desktop/gDesklets-0.34.3$


Nothing :/
I've installed gcc, mawk & make :(

BTW. [http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

:D :D :D
sudo apt-get install gdesklets :D

---

### Post by dbott67 on 2005-10-29
[quote=n1x0n]sudo apt-get install gdesklets :D[/quote] 
That's what I was going to say! :)  gDesklets is in the repos... or just run Synaptic and search for gDesklets.

-Dave

---

### Post by Efwis on 2005-10-29
i'm a little confused here, are you tryign to install the gDesktlets widgets or the gDesklets base program??

I know that gDesklets is alread in the repos. You can get the entire system in synaptic.

system>administration>synaptic program manager

click on search type in gdesklets after it finds it install both gdesklets and gdesklets-data

If you use the add programs in the applications menu you only get the core program you don't get the widgets themselves installed.

you now have gdesklets installed on your system. if I recall correctly, the version in synaptic is the same one you would currently download from the project page itself. The only thing you may want to do is install other widgets.

---

### Post by Dracontopes on 2005-10-29
If you want to install new widgets then just go to [http://gdesklets.gnomedesktop.org/]("http://gdesklets.gnomedesktop.org/") and drag a download link to the gDesklets main program and it will install automatically!

To manually start the deamon just issue the command ***gdesklets*** from a terminal.

(If you want to have gdesklets started everytime you start your computer then start **gnome-session-properties** from a terminal. Then go to the last tab and add the command **gdesklets** there.)

---

### Post by zeca_pedra on 2005-11-01
[QUOTE=Dracontopes]If you want to install new widgets then just go to [http://gdesklets.gnomedesktop.org/]("http://gdesklets.gnomedesktop.org/") and drag a download link to the gDesklets main program and it will install automatically!

To manually start the deamon just issue the command ***gdesklets*** from a terminal.

(If you want to have gdesklets started everytime you start your computer then start **gnome-session-properties** from a terminal. Then go to the last tab and add the command **gdesklets** there.)[/QUOTE]

Yep, nice and easy! But how about if you're running Xfce42? In my case I've a clean and fast install of Breezy with Xfce and no Gnome nor Kde, just Xfce42. I love it, it's smooth, fast, flexible but... I don't know how to set apps to autostart when I loggin.

Any help it's highly appreciated!
Zeca

---

