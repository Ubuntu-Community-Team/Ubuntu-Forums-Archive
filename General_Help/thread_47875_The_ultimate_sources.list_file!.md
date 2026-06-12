---
title: "The ultimate sources.list file!"
date: 2005-07-10
forum: General Help
---

### Post by rjpa on 2005-07-10
Hi,

As I'm a new user of Ubuntu 5.04 I've seen that it's possible to use apt-get.
So I wonder, how should "the ultimate sources.list file" look like? Could you post yours? I want to be able to install the latest updates, apps, games etc. Including the Backports.

Thanks in advance.

Rasmus

---

### Post by Leif on 2005-07-10
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by debian_n00b on 2005-07-10
Hi there. I'm fairly new to Ubunto myself as well. Have been searching, but havn't come across much along the line that you speak. From what I can tell, you will want to pull packages from official Ubuntu sources wen possible over all others for fear of breaking the system if you stray. Then there is the unofficial backports included in the distributed sources list on cd which require uncommenting to activate. I would suggest then adding maybe some pure Debian sources, stable or testing maybe, and of course Marillat as well. But remember, you should pin all other repositories other than official Ubuntu sources to a rather low value so as to only grab those packages when they just arn't available otherwise. But if you must grab packages from alsewhere when Ubuntu makes them available, you will need to add the "-t repository_name" switch when installing to override the pin.
But then again, being a Ubuntu n00b, I could be completely, entirely and overwhelmingly sickenly wrong.

---

### Post by XDevHald on 2005-07-10
[QUOTE=rjpa]Hi,

As I'm a new user of Ubuntu 5.04 I've seen that it's possible to use apt-get.
So I wonder, how should "the ultimate sources.list file" look like? Could you post yours? I want to be able to install the latest updates, apps, games etc. Including the Backports.

Thanks in advance.

Rasmus[/QUOTE]
 The mirrors that I have for the main and universe are VERY good mirrors and are always up 100% no matter what. Use these to stay fully up to date and always get packages that you might find that other mirrors don't have.

I've had no issues, why should you...

>  deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary main restricted
deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted
deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary universe
deb-src [http://mirrors.xmission.com/ubuntu](http://mirrors.xmission.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


---

### Post by emperor on 2005-07-10
[QUOTE=Leif][http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")[/QUOTE]

You will need to remove the "us." in the list in the ubuntuguide as there are some broken packages in the "us" repo's" lately!

---

### Post by Norrad on 2005-07-10
[QUOTE=emperor]You will need to remove the "us." in the list in the ubuntuguide as there are some broken packages in the "us" repo's" lately![/QUOTE]
 Jeez, its more like 90% of the repos ae broken, it's been driving me nuts.

---

### Post by pt123 on 2005-07-10
[QUOTE=debian_n00b] some pure Debian sources, stable or testing maybe, and of course Marillat as well. But remember, you should pin all other repositories other than official Ubuntu sources to a rather low value so as to only grab those packages when they just arn't available otherwise[/QUOTE]

How do you "pin" the other repositories or set a low value ?

Also I get public key incorrect problems with Marillat

---

### Post by emperor on 2005-07-11
[QUOTE=pt123]How do you "pin" the other repositories or set a low value ?
[/QUOTE]

You will need to create an  "/etc/apt/preferences" file. See the following link for an example:
[http://jaqque.sbih.org/kplug/apt-pinning.html]("http://jaqque.sbih.org/kplug/apt-pinning.html")

After updating my "sources.list" per the wiki, I found that I no longer needed the problematic "Marillat" repo.

---

