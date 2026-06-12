---
title: "Is there an application for simply adding new version of applications from PPAs"
date: 2014-10-28
forum: General Help
---

### Post by abcuser on 2014-10-28
Hi,
few years back there was Ubuntu Tweak tool that had some sort of installing applications from third party sources (like PPA). But Ubuntu Tweak tool does not include this anymore.

Is there any GUI application with list of most used PPAs, to just simply install app without having to search for PPA and manually adding it with terminal.

For example Pinta in official Ubuntu 14.04 repository is at version 1.3 which is just very old and very buggy version. There is Pinta 1.5 released which is very stable and a lot of new feature. I can add PPA from [https://launchpad.net/~pinta-maintainers/+archive/ubuntu/pinta-stable](https://launchpad.net/~pinta-maintainers/+archive/ubuntu/pinta-stable) but I have to search for this PPA and manually add it...

Also there is LibreOffice 4.2 in official Ubuntu 14.04 repository. But I get a lot of Microsoft Office files and there were a lot of fixes in LibreOffice 4.3, so I have to search the web to find out the repository: sudo add-apt-repository ppa:libreoffice/libreoffice-4-3

And this list goes on and on... So is there some GUI application to easily add the newest version of software using PPAs? Something like Ubuntu Software Center but with just new version of software from PPAs?

P.S. I know I can install Ubuntu 14.10 to get new version of applications, but I would like to use Ubuntu 14.04 because it is LTS, and I would like to use it for years, just adding new software from PPAs.
Thanks

---

### Post by Vaphell on 2014-10-28
check this out, maybe it will suit your needs

[http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html](http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html)
[https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager](https://launchpad.net/~webupd8team/+archive/ubuntu/y-ppa-manager)

---

### Post by abcuser on 2014-10-29
@Vaphell, I know this tool already and it is not what I want. Y-PPA-Manager is tool to manually add PPAs to tool. What I would like is to have a tool that already has all of the PPAs in repository and just one click to install them without searching for PPAs on the net.

---

### Post by dragonfly41 on 2014-10-29
Here is one tool I've recently started to use to manage my 14.04 server.

webmin.   [http://www.webmin.com/](http://www.webmin.com/)

It is in Ubuntu software centre. I'm not sure if the repo package is latest version 1.710.

You can see and try a working demo here.

[http://webmin-demo.virtualmin.com](http://webmin-demo.virtualmin.com)        Login user "demo" password "demo"

After local installation launch from [https://localhost:10000/](https://localhost:10000/)

and go to System > Software Packages

click on Package Tree to see packages listed.

I've started developing a custom module to manage (through templates) all my configurations,   
server admin and custom applications development.

A bit like Chef recipes.


[later edit]

If you visit the demo site note that different users are playing around with themes and languages so you might encounter a weird theme not to your liking. Don't be put off by that since the blue-theme and gray-theme are more up to date.   And you can develop your own custom theme by cloning one of the themes.   I've developed a custom ajax theme and there is also metal-theme which is worth looking at.


[another edit]

This might be an easier approach if webmin is an overkill ...

[http://www.webupd8.org/2012/12/how-to-list-packages-from-ppa.html](http://www.webupd8.org/2012/12/how-to-list-packages-from-ppa.html)

---

