---
title: "Apt-get?"
date: 2004-11-18
forum: General Help
---

### Post by Tarisutan on 2004-11-18
Hey everyone how can I add more repositories with more up to date packages because the ubuntu repositories suck..they don't have much and there out of date. Are there other ubuntu repositories or can i use debian repositories? and how can i add repositories?

---

### Post by dataw0lf on 2004-11-18
Well, besides the fact that I have no idea what you're talking about in regards to Ubuntu's repos being outdated,  edit /etc/apt/sources.list
Or just use synaptic.
dataw0lf

---

### Post by jdong on 2004-11-18
Exactly *what*'s wrong with Ubuntu Warty repositories?!??

If you really want bleeding edge software, add Hoary repos. I should throw in a warning that we've already seen one breakage with Sed in Hoary. Another example why you shouldn't live on the bleeding edge...

---

### Post by voth on 2004-11-18
[QUOTE=jdong]Exactly *what*'s wrong with Ubuntu Warty repositories?!??

If you really want bleeding edge software, add Hoary repos. I should throw in a warning that we've already seen one breakage with Sed in Hoary. Another example why you shouldn't live on the bleeding edge...[/QUOTE]
 For the new linux users you may want to list a few of those repositories and a nice step by step instructions to add them to the /etc/apt/sources.list

My problem isn't so much out of date, it's more to the fact that the one used by default lacks a multitude of applications.

---

### Post by jdong on 2004-11-18
There are plenty of Howto's of how to enable the **universe** repository, which encompasses virtually all the packages in Debian Sid.

---

### Post by voth on 2004-11-18
In case anyone is interested.

**USING APT**
Update the package lists available in the repositories:
Code:
> apt-get update

This will compare your RPM database against the updated lists. You can upgrade your system with the latest packages with:
Code:
> apt-get upgrade

You can add new software by typing:
Code:
> apt-get install <name of package>

If you want to install the lastest version of grip:
Code:
> apt-get install grip

Or search for software in the local repository meta-data:
Code:
> apt-cache search <keyword>

Code:
> apt-cache show <name of package>

If you're looking for grip but you don't know if your repositories have it or not:
Code:
> apt-cache search grip

From time to time you may want to save some diskspace:
Code:
> apt-get clean

Remember to update your local repository often before upgrading or installing software,
so that you can enjoy the latest and greatest.

For more info:
Code:
> man apt-get

/etc/apt/apt.conf (APT configuration where you can, for example, disable the GPG key check by changing 'true' x 'false')

/etc/apt/sources.list (APT list of local repositories where you can add or delete repositories)

[I]Be sure to read /etc/apt/sources.list.d/mirror-select.list which has been automatically configured by the Ubuntu apt mirror selector
Run "apt-get mirror-select" to reselect mirrors for that file.[/I]

---

### Post by jdong on 2004-11-18
Cut-and-pasted from a Fedora article? ;)
 
 apt-get mirror-select is an apt4rpm function; Debian apt and thus Ubuntu apt do NOT have this option.
 
 
 Also, apt-get dist-upgrade can sometimes offer a more complete upgrade than just apt-get upgrade.

---

### Post by Tarisutan on 2004-11-19
As far as i can tell it is out of date, firefox and thunderbird are both older versions.

---

### Post by TravisNewman on 2004-11-19
The repositories are at the state they are because the applications worked, and they KNEW that they worked, without any major errors. You won't get any application upgrades through apt until the next version is released, unless you want to live bleeding edge and use the testing version. They do this because releasing Firefox 1.0 COULD HAVE broken a lot of stuff, and in Hoary it was a bit broken, but has since been fixed. Nothing but security updates will come out for Warty. This isn't stopping you from doing it manually though.

Sorry if I sound a bit flustered, but this has been deliberated over and over, and it doesn't seem like anyone is taking the suggestions from my signature... Faq/Wiki/Search

---

