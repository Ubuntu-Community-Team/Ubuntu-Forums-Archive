---
title: "[SOLVED] dependency problem on new install of Gutsy"
date: 2008-05-19
forum: General Help
---

### Post by maljaros on 2008-05-19
My fresh install of Ubuntu 7.10 is up and running a KDE session but any attempt to add new apps with Synaptic produces some dependency problems.
E: evolution: dependency problems - leaving unconfigured
E: evolution-plugins: dependency problems - leaving unconfigured
E: gnome-control-center: dependency problems - leaving unconfigured
E: gnome-session: dependency problems - leaving unconfigured
E: gedit: dependency problems - leaving unconfigured
E: gnome-games: dependency problems - leaving unconfigured
E: gnome-panel: dependency problems - leaving unconfigured
E: nautilus: dependency problems - leaving unconfigured
and associated exit status 139 subprocess post-installation script errors relating to:
E: ubuntu-docs
E: capplets-data
E: deskbar-applet
E: eog
E: evince
E: evolution-common
E: evolution
E: evolution-plugins
E: file-roller
E: gcalctool
E: gnome-control-center
E: gnome-session
E: gdm
E: gedit-common
E: gedit
E: gnome-games-data
E: gnome-panel-data
E: gnome-system-monitor
E: gthumb
E: nautilus
E: sound-juicer
E: tomboy
E: update-manager
E: gnome-system-tools

The system runs Firefox, Konqueror and Evolution Mail with no obvious difficulty so it seems to be a Gnome problem.
Can anybody spot a common thread here and suggest where the dependency problem starts.
Thanks for your attention
Maljaros

---

### Post by ibuclaw on 2008-05-19
Can you pinpoint when the first dependancies error occurs?

Open up a terminal and type in:
```
sudo apt-get upgrade 2>&1 | grep "Depends"
```

Then scroll to the top, and that should and the first dependancy issue should be your problem package.

Have you got all sources (except backports and proposed) enabled?

If not, enable all repositories apart from the above two. If you are still getting troubles, enable the "backports" repository.

Regards
Iain

---

### Post by maljaros on 2008-05-19
Thanks for the response Tinivole.
Running the command 
sudo apt-get upgrade 2>&1 | grep "Depends"
produces no output and running Update Manager gets: 
Your system is up-to-date.
The problem occurs when I try to use Synaptic to load a new app.
The repositories that Synaptic presents under Software Sources are (enabled): Canonical Main, Open Source Universe, Restricted (drivers), Restricted multiverse, apt-build main.  
Presented as further options (but not enabled) are 
Ubuntu Source Code and Gutsy partner.
The two that you mention - backports and proposed - are not presented as options
How do I tell Synaptic about these other repositories?

---

### Post by ibuclaw on 2008-05-20
It should be viewable from the Software Sources App, else you'll probably find it commented out in the "/etc/apt/sources.list" file.

Although, if you could find the first package that produces the problems, that would be brillant. So then we could look for a way to meet it's dependancy manually.

Else, you could try force install the packages...
```
sudo apt-get install -f
```

Regards
Iain

---

### Post by maljaros on 2008-05-20
I started deleting apps with dependency problems one at a time to try to get to the source of the problem.  Synaptic would not let me remove either akiga or evolution-data-server which seemed to have a broken inter-dependency.  I think that enabling evolution database backend server (is this what you meant by backports?) could have solved the problem but had wrecked my installation to a point where KDE would not let me have a terminal.
The real problem may have been that I had two Gutsy 7.10 installs in different sectors on the same machine - so I deleted both sectors and did a clean install which appears to be working fine.  Thanks for your help, tinyvole.  Learning about the various repositories and how to access them was a worthy step forward.

---

### Post by ibuclaw on 2008-05-21
Hi, I'm glad to know that you are learning from this.

The backports that I was mentioning can be turned on/off in the "Software Sources" app.

In synaptic, go into "Settings>Repositories" and then click on the "Updates" tab.
See the attachment below.

Apt also comes with a useful feature called "Pinning", though I will not go into full detail what it is right now, but an example of what it can do is prevent an upgrade of a package to a different version number (ie: Locking the package).

Locking Versions can be done in Synaptic, "Package>Lock Verson"

Regards
Iain

---

### Post by maljaros on 2008-05-21
Thanks again Iain.
Having now destroyed the evidence I can't be sure but it may have been that EKIGA wanted an earlier version of evolution-data-server. (Hence the need for pinning I guess)
 It would have been nice to get to the bottom of the problem but I am happy that it has gone away, leaving me (thanks to your guidance) somewhat better informed.
Regards, Malcolm

---

