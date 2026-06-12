---
title: "Problems Uninstalling Transmission"
date: 2014-04-29
forum: General Help
---

### Post by Romeu_Tristo on 2014-04-29
Hi,

I'm new to Linux. I've installed it for the first time one week ago so my knowledge about it is still very basic.

Basically I want to uninstall the "Transmisson" (I prefer using qBittorrent). So, I went to the Software Center and clicked on the button "Remove from my system". I've uninstalled another programs like this, with success. The thing is that in this case, when this process is over a new "Qtransmission bittorrent client" appears on my installed software. And if I try to uninstall this one, the first "Transmission" appears again. It's like the command to unistall "Transmission" activates the installation of "Qtransmission bittorrent cliente" and vice-versa. I don't even know if there's a difference between this two applications. The name and the image icon changes, but it seems that their basically the same.

Can someone help me? Thanks in advance

---

### Post by bapoumba on 2014-04-29
```
Description-en: lightweight BitTorrent client
 Transmission is a set of lightweight BitTorrent clients (in GUI, CLI
 and daemon form). All its incarnations feature a very simple, intuitive
 interface on top on an efficient, cross-platform back-end.
 .
 This is just a metapackage depending on one of the front-end
 alternatives
Description-md5: ad4c3a4546931273694cb4f642f5341d
Homepage: http://www.transmissionbt.com/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: lubuntu-desktop

```
Transmission is a meta-package, if you uninstall it, it does not remove the other packages it depends upon.
Are you running out of space ? Could you install the other client of your choice keeping transmission ? transmission-gtk is part of ubuntu-desktop dependencies.

---

### Post by Romeu_Tristo on 2014-04-29
Thanks for quick response!
I'm not running out of space, but normally I like to uninstall programs I don't use because in the long run it makes a big difference.
But is there a way to uninstall it? Or should I just keep it, and why?

---

### Post by vasa1 on 2014-04-30
> **Romeu_Tristo said:**
> ...
But is there a way to uninstall it? Or should I just keep it, and why?
You should be able to uninstall it but I'd suggest keeping it until you get more confident with Linux and are sure about how the other torrent manager works.

One nice way to figure out the potential consequences of any action is to run a simulation. So, in a terminal, run *apt-get purge -s transmission** and examine the output carefully. If you have doubts about the output, just ask!

Notes: 
[LIST]
[*]There's no need for *sudo* when it's just a simulation (*-s*).
[*]One proposed deletion could be "lubuntu-desktop". That appears frightening but isn't. That entry refers to a metapackage which is just a list of files that Lubuntu will look at if, when the next version of Lubuntu comes around, you choose to do an upgrade as opposed to a clean install. See [www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html) and [https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop) for more on the effect of removing "lubuntu-desktop".
[*]If you're interested in removing software, you may encounter a situation in which something else is installed in place of the software you remove. That's because the OS determines that you need at least one software of that category: easy example is your web browser. I don't think you can delete all your web browsers (if you have more than one). The system won't allow it.
[/LIST]

---

### Post by Romeu_Tristo on 2014-04-30
I was now able the uninstall Transmisson. After using the simulation command I saw on the terminal that in order to delete all the packages I should use "*apt-get autoremove"* so I did "*sudo apt-get autoremove transmission" *and it worked. Problem solved, and learned some command line stuff on the way :D

Thanks for all the help. Glad to verify that Linux comunity is as helpful as I've heard it would be!

---

### Post by vasa1 on 2014-04-30
> **Romeu_Tristo said:**
> ... to delete all the packages I should use "*apt-get autoremove"* so I did "*sudo apt-get autoremove transmission" *and it worked. ...
I think *sudo apt-get autoremove* is enough. I'm not sure there's any benefit to adding a package name. Anyone?

---

### Post by bapoumba on 2014-04-30
> **vasa1 said:**
> I think *sudo apt-get autoremove* is enough. I'm not sure there's any benefit to adding a package name. Anyone?
apt-get autoremove <package> removes a package and its dependencies [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)
transmission being a metapackage, my guess is that it got removed along with its dependencies.

If I get this [http://packages.ubuntu.com/trusty/transmission](http://packages.ubuntu.com/trusty/transmission) and that [http://packages.ubuntu.com/trusty/transmission-qt](http://packages.ubuntu.com/trusty/transmission-qt) correctly, the autoremove should have removed all deps that were not deps of other packages, including transmission-qt.

Now I'm not sure how it will turn out in the future, as transmission-qt is a dep of ubuntu-desktop [http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop) wwhich may now turn apt-get to complain as the ubuntu-desktop deps are not satisfied, or more probably will install it again on the next update/upgrade.

---

### Post by vasa1 on 2014-04-30
On re-reading the first post, it seems to be a case of the operating system insisting on having at least one torrent client installed. When OP tried to remove transmission-gtk, transmission-qt was installed and vice versa. This is similar what I (and others) experienced when trying to remove a web browser.

I don't know how off-topic we're getting here, but I use *apt-get purge <package>* to remove a package (and its config files (outside ~/)) rather than *apt-get autoremove <package>* because the latter doesn't remove the config files (outside ~/). Dependencies that are no longer needed are automatically suggested for deletion the next time I run *sudo apt-get update && and sudo apt-get upgrade*.

---

### Post by bapoumba on 2014-05-01
:)
Yes, we are drifting a bit and learning at the same time, so I say it is OK for now.

I always use apt-get autoremove on its own, without adding a specific package name. I looked at the help page because I did not know it could work with <package_name>.

Now removing packages with or without purge really depends on what you are trying to do. Sometimes it is good to remove config files, sometimes it is good to keep them.

I'm always cautious and, at least on my systems, do not remove metapackages. Can lead to surprises during the next upgrade if you do not read the actions that are going to be applied and say yes, OK, just do it. I've helped several persons in the last few days where I suspect metapackages go removed and then deps autoremoved, leading to loosing gedit and other such details :)

---

### Post by spode2 on 2014-07-07
This problem has had me wondering if I am going mad. I have installed Qbittorrent and would like to remove Transmission/QTransmission but I am not allowed to. Nothing tells me that, so I wasted time going round in circles. 

Is there really no safe way of removing or hiding this unwanted software?

---

### Post by monkeybrain20122 on 2014-07-07
install synaptic and use it to manage your packages. for example, if you open synaptic and search for transmission you will see transmission-common and transmission-gtk, those are the one installed and you would uninstall them and it will show you what change will be made before it prompts you to go ahead. It is much faster and a lot more capable than the bloated  software centre.

---

### Post by ian-weisser on 2014-07-08
> **spode2 said:**
> Is there really no safe way of removing or hiding this unwanted software?

You can safely uninstall (almost) anything you wish.

Open a terminal. This command will happily and safely remove most traces of Transmission from your system.
```
sudo apt-get autoremove transmission-common
```

The transmission-gtk package is recommended by the ubuntu-desktop metapackage.
Removing transmission will also remove the ubuntu-desktop metapackage (just the package, not the desktop itself!)
Your desktop will be unaffected *until* you upgrade to a newer release of Ubuntu (like 14.10 or 15.04).

When you upgrade to a newer release of Ubuntu, you will automatically receive upgrades to your existing packages, regardless of whether you have a *-desktop metapackage installed or not. The ubuntu-desktop metapackage ensures that obsoleted packages get removed and new packages get installed to match the latest release. So you may wish to reinstall ubuntu-desktop (which will reinstall Transmission!) before you upgrade to the next release of Ubuntu.

Reinstalling ubuntu-desktop in the future is trivial from the terminal:
```
sudo apt-get install ubuntu-desktop
```

---

