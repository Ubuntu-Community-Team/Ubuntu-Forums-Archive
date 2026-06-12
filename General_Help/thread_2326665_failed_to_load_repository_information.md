---
title: "failed to load repository information"
date: 2016-06-03
forum: General Help
---

### Post by rosswmcgee on 2016-06-03
In 16.04lts the software updater tells me to check my internet connection which is fine and says failed to load repository information try again. Then sometimes a little later it says install these updates. here is the message:
```

W:The repository 'http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu xenial Release' does not have a Release file.,
W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
E:Failed to fetch [http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found, 
E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by X-RED_Tech on 2016-06-03
That PPA has nothing for 16.04, apparently. If you remove it the error message will go away.

---

### Post by vasa1 on 2016-06-03
OP: please always use code tags when pasting text you've copy from the terminal. It makes the data more readable and doesn't provide unwanted emoticons.

See the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945") for more and [http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168) for even more.

If you click on the **Reply** button or on the **Reply with quote** button, you'll see the **code tag icon** (the one with **#**) which will provide the tags in the text area for you: See the attached image titled **CODE.png**

If you don't see the code tag icon, as happens when you **Edit** your own post or when you choose **Quick Reply**, first click on **Go Advanced** just below the text area. Doing so will provide you with the code tag icon. See the attached image titled **GoAdvanced.png**

Of course, you could also add the code tags yourself by just typing :)

Thanks!

---

### Post by rosswmcgee on 2016-06-03
Still getting error after removing.


I need to re construct but editing seems not to work.

---

### Post by X-RED_Tech on 2016-06-03
> **rosswmcgee said:**
> Still getting error after removing.

If so why didn't you post it? Certainly it's a new error. If it's the same then you didn't removed the "offending" PPA...

---

### Post by rosswmcgee on 2016-06-03
It just says  failed to load repository information try again, leaves no error msg., then says software is up to date. 

The only ppa line left is this:

[http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu)

There is no ppa for xenial

I need to re-configure the updater??? But how?

this is from terminal:
W: The repository 'http://ppa.launchpad.net/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2016-06-03
How did you remove it? It seems not to've worked in any case.

Can you post the following info? ```
cat /etc/apt/sources.list

ls /etc/apt/sources.list.d/
```

---

### Post by rosswmcgee on 2016-06-03
cat /etc/apt/sources.list
```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160420.1)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```
```
rosswmcgee@rosswmcgee-OptiPlex-760:~$ 

ubuntu-mate-dev-ubuntu-ppa-xenial.list
ubuntu-mate-dev-ubuntu-ppa-xenial.list.save
rosswmcgee@rosswmcgee-OptiPlex-760:~$
```

---

### Post by ventrical on 2016-06-03
Why are the #deb-scr lines commented out ?

Regards..

---

### Post by rosswmcgee on 2016-06-03
I do not know. I want to fix this but

Do not know how.

---

### Post by ventrical on 2016-06-03
Please post this info:

Open Terminal: (ctrl+alt+t)

Enter code:

```

sudo -i gedit /usr/share/python-apt/templates/Ubuntu.info

```


and copy and paste here.

Regards..

---

### Post by oldos2er on 2016-06-03
Try ```
sudo rm /etc/apt/sources.list.d/ubuntu-mate-dev*

sudo apt update
```

---

### Post by rosswmcgee on 2016-06-03
(gedit:18398): Gtk-WARNING **: Theme parsing error: gtk-main.css:69:33: Failed to import: Error opening file: No such file or directory

---

### Post by rosswmcgee on 2016-06-03
rm: cannot remove '/etc/apt/sources.list.d/ubuntu-mate-dev*': No such file or directory


sudo apt update

Ok I was able to do that so now all that is checked in other software is Canonical  partners  software  no other options other than Cabinical partners source code.

---

### Post by ventrical on 2016-06-04
> **rosswmcgee said:**
> It just says  failed to load repository information try again, leaves no error msg., then says software is up to date. 

The only ppa line left is this:

[http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mate-dev/ppa/ubuntu)

There is no ppa for xenial

I need to re-configure the updater??? But how?

this is from terminal:
W: The repository 'http://ppa.launchpad.net/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/ppa/ubuntu/dists/xenial/main/source/Sources](http://ppa.launchpad.net/ppa/ubuntu/dists/xenial/main/source/Sources)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

I think you need to use ppa-purge:

```

sudo apt-get install ppa-purge

```

if you have already used ppa-purge my apologies .. but I did not see you mention that here.

---

### Post by rosswmcgee on 2016-06-04
I did a software update this morning all went well. So does this mean I need no soft  up date for the mate ppa? I mostly use Unity now anyway.

---

