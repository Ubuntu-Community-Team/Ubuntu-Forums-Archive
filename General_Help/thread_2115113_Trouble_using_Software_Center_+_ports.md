---
title: "Trouble using Software Center + ports"
date: 2013-02-11
forum: General Help
---

### Post by Gattison on 2013-02-11
Hello, Unbuntforums.org,

  I'm new here, but have been using ubuntu for over a year now.  I love it, and have been pretty successful at troubleshooting, until now.

  (Of course, if I put this in the wrong section, or if I repeated a previously asked question, I apologize for being a newb to the forum.)

  I was using qbittorent, but then I tried to fiddle with my VPN and I'm not sure what I did, but now things just aren't working the same.

  My qbittorent stopped working after that, it would display how many people I was connected to, but no downloads would begin, they would just sit there stalled.

  After that I uninstalled qbittorrent and then attempted to reinstall it from Ubuntu Software Center, but now that is not working properly either.  I try to download anything and I get this message:

"This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

  I'm still using Ubuntu 10.10, and I'm still earning linux/Ubuntu, so I'm not sure if I need to finally upgrade to 11.whatever, or if there's a way to continue using 10.10 after it is no longer officially supported.

  Any guidance that someone could provide me in resolving this issue would be greatly appreciated.

Thanks in advance,
Gattison

---

### Post by unheeding on 2013-02-12
10.10 went EOL (End of Life) in April of last year.  I'm pretty sure that this means that the packages are no longer available in the main repositories.  Try a "sudo apt-get install qtorrent" from the command line and see what it spits out.

Your best bet is to upgrade to a supported version.  10.04 is still supported for a few months because it is a LTS (long-term support) release, but maverick is no longer on on packages.ubuntu.com, so I think you might be out of luck.

It looks like qtorrent isn't in the repositories for the newer releases... might I suggest Transmission?  It is great, and has GUI and CLI interfaces.

---

### Post by Gattison on 2013-02-12
Thanks a lot for your response, unheeding.

I wasn't a big fan of 11.04 or whatever it was, so i may switch back down to 10.04... but like you said, if it only has a few months left on that as well, I may have to just suck it up and start using a newer version.

I tried "sudo apt-get install qbittorrent" and this was my response:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qbittorrent : Depends: libboost-filesystem1.42.0 (>= 1.42.0-1) but it is not installable
               Depends: libboost-system1.42.0 (>= 1.42.0-1) but it is not installable
               Depends: libtorrent-rasterbar6 (>= 0.15.8+svn.r6088) but it is not going to be installed
E: Broken packagesI'm just guessing but it looks like this basically confirms what unheeding said.  (If I'm assuming wrong, please correct me).

Additionally:

While I appreciate unheeding's help, it still doesn't explain why my qbittorrent stopped working before I worsened things with my troubleshooting.  I have the feeling I accidentally changed something when I messed with my VPN, and when I tried to return to defaults... I don't know.

As for Transmission, if I have to, I'll switch back to Transmission (which I also cannot download from the 10.10 Software Center), but qbittorrent had an extra bell and whistle or two that I liked, so if I can, I'd love to be able to continue using it.

---

### Post by unheeding on 2013-02-12
I found [a PPA](https://launchpad.net/~hydr0g3n/+archive/ppa) for qtorrent, it has packages for most Ubuntu releases.  The dependencies might be a little bit trickier to get, I bet that you could change your apt sources to point at the 10.04 repositories (i.e. change everything in /etc/apt/sources.list that says "maverick" to "lucid").  This may break some things, especially if you have newer packages from 10.10 that aren't compatible with older 10.04 packages.

If you just don't like Unity (the awesome (imho) desktop that was introduced in 11.04) there are plenty of options to choose from.  You can install the MATE Desktop Environment [through a PPA](http://www.noobslab.com/2012/11/install-mate-14-desktop-in-ubuntu.html).  MATE is a fork of the GNOME2 Desktop Environment you are used to from Ubuntu 10.0.  There's also the option of [Linux Mint](http://distrowatch.com/table.php?distribution=mint), which offers MATE as the default DE (there's also a variant based on [Cinnamon](http://en.wikipedia.org/wiki/Cinnamon_(user_interface)), which is a fork of GNOME3 aimed at recreating a traditional desktop).  There's also [Descent|OS](http://distrowatch.com/table.php?distribution=descentos) which also offers MATE as the DE.  Both Mint and Descent are based on Ubuntu.


Additionally, you should check out Xubuntu.  The XFCE Desktop Environment is a natural fit for people who like GNOME2's traditional desktop interface, and it can be configured to look and feel pretty much exactly like GNOME2.  You might miss some plugins, but most of the functionality is there.

---

### Post by claracc on 2013-02-12
> **unheeding said:**
>  The dependencies might be a little bit trickier to get, I bet that you could change your apt sources to point at the 10.04 repositories (i.e. change everything in /etc/apt/sources.list that says "maverick" to "lucid").  This may break some things, especially if you have newer packages from 10.10 that aren't compatible with older 10.04 packages.


I do not recommend to do this since probably you are going to mess your system with a mixture of 10.04 and 10.10 packages and libraries.

I you want to stay with 10.10, you will find the old repositories in: [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/), please, see this useful thread: [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-old-unsupported-release) to configure the updates. Then, perhaps you could add the addressed qbittorrent ppa for 10.10. But I think that staying with a non supported release is a bad idea.

I think, your best bet is to install a supported release as 12.04 LTS, you can always select the gnome fallback desktop which has a low footprint and resembles the old gnome desktop.

---

### Post by uzumakifahim on 2013-02-12
LXDE based lubuntu is also a good option if you are trying to avoid Unity and want a traditional desktop.

Good Luck.

---

