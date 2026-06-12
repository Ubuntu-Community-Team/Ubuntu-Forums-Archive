---
title: "[Solved] Does Ubuntu Mate (software boutique) include 3rd party PPA's?"
date: 2016-06-18
forum: General Help
---

### Post by soft22dvd3 on 2016-06-18
Ubuntu Mate Software Boutique has software not available on regular Ubuntu repositories (Google Chrome, App Grid, Skype).

On the Ubuntu Mate forum someone said it includes PPA's (I assume 3rd party):
"They are usually PPAs from developers."
[https://ubuntu-mate.community/t/the-software-boutique-will-be-avaible-for-other-ubuntu-flavors/4478](https://ubuntu-mate.community/t/the-software-boutique-will-be-avaible-for-other-ubuntu-flavors/4478)


However when I check PPA's it does not list any third party, only archive.ubuntu and archive.canonical. I used these commands:
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```


1. If Ubuntu Mate does include 3rd party software sources, how can I see them?
2. If it does not include 3rd party software sources, how am I able to install apps like Google Chrome, App Grid, and Skype from Software Boutique?

---

### Post by vasa1 on 2016-06-18
Maybe when you choose to install Google Chrome, for example, the ppa will be added.

---

### Post by ajgreeny on 2016-06-18
vasa1 is correct; when you download the .deb package for Chrome it will automatically add the repository to your software sources.  Skype is available from the **Canonical-Partner** repos which you can enable in software-sources ->Other Software tab.  I had no idea what App-grid is but you can add the ppa at [https://launchpad.net/~appgrid/+archive/ubuntu/stable](https://launchpad.net/~appgrid/+archive/ubuntu/stable) to enable that, if you want to, though having searched I now know it is an alternative to software-centre.

You do not tell us if you have added any PPAs with the command **sudo add-apt-repository ppa:---**, eg ```
sudo add-apt-repository ppa:libreoffice/ppa
```
If you have not added any manually they certainly will not be showing by default in any package manager application, not even **apt-get**.

---

### Post by soft22dvd3 on 2016-06-18
Thanks for the replies!
> **ajgreeny said:**
> 
If you have not added any manually they certainly will not be showing by default in any package manager application, not even **apt-get**.
I have not added any PPAs. These 3rd party apps show up by default in the Software Boutique of a fresh install of Ubuntu Mate 15.10 (software boutique is the only software store in Ubuntu Mate). I assume it is the same with Software Boutique Ubuntu Mate 16.04.

---

### Post by Dennis N on 2016-06-18
You don't necessarily need to add PPAs to your system for the Software Boutique to show and fetch that software - the source would be hard coded in the S.B. application.
Examples:
For Chrome, the Boutique knows the source as [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) so it downloads the .deb, then installs it.
Skype comes through the Canonical Partner Repository. So it would download the .deb from there and install it even without Partners being enabled in your sources list. No reason why it can't do that.

---

### Post by vasa1 on 2016-06-18
> **Dennis N said:**
> You don't necessarily need to add PPAs to your system for the Software Boutique to show and fetch that software - the source would be hard coded in the S.B. application.
Examples:
For Chrome, the Boutique knows the source as [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) so it downloads the .deb, then installs it. ...
IIRC, when I installed Chrome from the website, the ppa was automatically added. I, as a user, didn't explicitly add it.

It would be interesting to know what OP's */etc/apt/sources.list.d* looks like before and after installing Google Chrome via the boutique.

I'm also guessing that the ppa is necessary for subsequent updates to Google Chrome.

---

### Post by Dennis N on 2016-06-18
> I'm also guessing that the ppa is necessary for subsequent updates to Google Chrome
And updates for anything else not from the Ubuntu repos, unless the software has the ability to check for and install it's own updates, like Firefox.

---

### Post by lah7 on 2016-06-18
As developer of the Software Boutique, I can confirm the software **does** indeed add third party repositories depending on the application. Repositories are only added or removed if the user clicks **Install, Reinstall **or** Remove**. If desired, you can see which PPA or source is being used with the **More** button, as mentioned already.

**Dennis N** is right that the applications are hard coded to the Boutique. Think of this as a hand picked selection of software ready for a one-click install and not as a fully fledged software center replacement. Although some new planned features in future will give it basic functionality to perform a package search.

[I addressed the same topic at the Ubuntu MATE Community.]("https://ubuntu-mate.community/t/does-ubuntu-mate-software-boutique-include-3rd-party-ppas/6935/7?u=lah7")

---

### Post by ajgreeny on 2016-06-18
> **lah7 said:**
> As developer of the Software Boutique, I can confirm the software **does** indeed add third party repositories depending on the application. Repositories are only added or removed if the user clicks **Install, Reinstall **or** Remove**. If desired, you can see which PPA or source is being used with the **More** button, as mentioned already.

**Dennis N** is right that the applications are hard coded to the Boutique. Think of this as a hand picked selection of software ready for a one-click install and not as a fully fledged software center replacement. Although some new planned features in future will give it basic functionality to perform a package search.

[I addressed the same topic at the Ubuntu MATE Community.]("https://ubuntu-mate.community/t/does-ubuntu-mate-software-boutique-include-3rd-party-ppas/6935/7?u=lah7")

Thanks for that info lah7; it is good to be put right about something I do not know and have never used, ie Mate or the Software-Boutique.

---

### Post by soft22dvd3 on 2016-06-18
> **lah7 said:**
> As developer of the Software Boutique, I can confirm the software **does** indeed add third party repositories depending on the application. Repositories are only added or removed if the user clicks **Install, Reinstall **or** Remove**. If desired, you can see which PPA or source is being used with the **More** button, as mentioned already.

**Dennis N** is right that the applications are hard coded to the Boutique. Think of this as a hand picked selection of software ready for a one-click install and not as a fully fledged software center replacement. Although some new planned features in future will give it basic functionality to perform a package search.

[I addressed the same topic at the Ubuntu MATE Community.]("https://ubuntu-mate.community/t/does-ubuntu-mate-software-boutique-include-3rd-party-ppas/6935/7?u=lah7")

Thank you so much for the detailed answer!

---

