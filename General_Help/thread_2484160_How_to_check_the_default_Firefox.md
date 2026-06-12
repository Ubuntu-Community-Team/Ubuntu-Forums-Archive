---
title: "How to check the default Firefox"
date: 2023-02-19
forum: General Help
---

### Post by satimis on 2023-02-19
Hi all,

Ubuntu 22.04[B][COLOR="#FF0000"]
[/COLOR][/B]
I'm checking the source of Firefox?  How it is installed on Ubuntu 22.04

$ apt policy firefox```

firefox:
  Installed: (none)
  Candidate: 1:1snap1-0ubuntu2
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages

```

It is not installed on repo

Is it installed on Snap or from Mozilla PPA repository ?

Please advise how to check it ?  Thanks

I need a Mozilla Firefox for testing

Regards

---

### Post by aljames2 on 2023-02-19
You can run this to see which snaps are installed.
```
snap list
```
By default, starting with 22.04, Firefox is a snap.  There are other methods to installing firefox if you are trying to move sway from the snap version.

---

### Post by TheFu on 2023-02-19
```
$ which {program name}
```
Then use your intuition to figure out how it was installed by the returned result.
```
$ which firefox
/usr/bin/firefox

$ file /usr/bin/firefox
/usr/bin/firefox: POSIX shell script, ASCII text executable

```

If there was a "snap" anywhere in that path, I'd assume it was a snap package. If no snap, then I'd check the APT information.
```
$ apt search firefox
i   firefox                       - The Firefox web browser                
p   firefox-dbg                   - Safe and easy web browser from Mozilla 
p   firefox-dev                   - Safe and easy web browser from Mozilla 
v   firefox-esr-umatrix           -                                        
v   firefox-form-history-control  -                                        
p   firefox-geckodriver           - Safe and easy web browser from Mozilla 
v   firefox-lightbeam             -                    
...

```
So, on the system I ran those commands, firefox is an APT package.
```
$ apt policy  firefox
firefox:
  Installed: 110.0+linuxmint1+vera
  Candidate: 110.0+linuxmint1+vera
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
 *** 110.0+linuxmint1+vera 700
        700 http://packages.linuxmint.com vera/upstream amd64 Packages
        100 /var/lib/dpkg/status

```
and it appears to have been created from the Ubuntu snap package, somehow.  I actually don't know how.  Oops, forget that I'd moved to Mint on that system.  On an Ubuntu 20.04 box, patched yesterday, 
```
$ apt policy firefox
firefox:
  Installed: 109.0.1+build1-0ubuntu0.20.04.2
  Candidate: 109.0.1+build1-0ubuntu0.20.04.2
  Version table:
 *** 109.0.1+build1-0ubuntu0.20.04.2 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     75.0+build3-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```
That isn't a snap package.

---

### Post by satimis on 2023-02-19
> **aljames2 said:**
> You can run this to see which snaps are installed.
```
snap list
```
By default, starting with 22.04, Firefox is a snap.  There are other methods to installing firefox if you are trying to move sway from the snap version.
Hi,

Thanks for your advice.

$ snap list```

Name                       Version           Rev    Tracking         Publisher   Notes
bare                       1.0               5      latest/stable    canonical&#10003;  base
core20                     20230126          1822   latest/stable    canonical&#10003;  base
firefox                    110.0-3           2356   latest/stable/…  mozilla&#10003;    -
gnome-3-38-2004            0+git.6f39565     119    latest/stable/…  canonical&#10003;  -
gtk-common-themes          0.1-81-g442e511   1535   latest/stable/…  canonical&#10003;  -
snap-store                 41.3-66-gfe1e325  638    latest/stable/…  canonical&#10003;  -
snapd                      2.58.2            18357  latest/stable    canonical&#10003;  snapd
snapd-desktop-integration  0.1               49     latest/stable/…  canonical&#10003;  -

```

Firefox and gnome are installed on snap

To uninstall Firefox shall I use

1)
sudo snap disable firefox
sudo snap remove --purge firefox

or

2)
sudo unmount /var/snap/firefox/common/host-hunspell
sudo snap remove firefox

Please advise.  Thanks

Regards

---

### Post by satimis on 2023-02-19
Hi all,

Further to my previous posting.

Yahoo mail running on this snap Firefox is unable attaching files to mail. It can't browse computer to select file, clicking it without response.

On this PC I have another drive running Ubuntu 22.04.  Yahoo mail running on Firefox is able to attach files to mail.

$ apt policy firefox```

firefox:
  Installed: 110.0+build3-0ubuntu0.22.04.1~mt1
  Candidate: 110.0+build3-0ubuntu0.22.04.1~mt1
  Version table:
     1:1snap1-0ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
 *** 110.0+build3-0ubuntu0.22.04.1~mt1 1001
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```
Firefox is installed on repo

Not on snap

$ snap list```

Name                     Version                     Rev    Tracking         Publisher   Notes
bare                     1.0                         5      latest/stable    canonical&#10003;  base
core                     16-2.58.2                   14784  latest/stable    canonical&#10003;  core
core18                   20230207                    2697   latest/stable    canonical&#10003;  base
core20                   20230126                    1822   latest/stable    canonical&#10003;  base
core22                   20230207                    509    latest/stable    canonical&#10003;  base
gnome-3-28-1804          3.28.0-19-g98f9e67.98f9e67  161    latest/stable    canonical&#10003;  -
gnome-3-34-1804          0+git.3556cb3               77     latest/stable    canonical&#10003;  -
gnome-3-38-2004          0+git.6f39565               119    latest/stable    canonical&#10003;  -
gnome-42-2204            0+git.0c1a50b               56     latest/stable    canonical&#10003;  -
gnome-system-monitor     42.0                        181    latest/stable/…  canonical&#10003;  -
gtk-common-themes        0.1-81-g442e511             1535   latest/stable/…  canonical&#10003;  -
gtk2-common-themes       0.1                         13     latest/stable    canonical&#10003;  -
kde-frameworks-5-core18  5.67.0                      35     latest/stable    kde&#10003;        -
vlc                      3.0.18                      3078   latest/stable    videolan&#10003;   -

```

I can't recall whether this Ubuntu 22.04 version was upgraded from Ubuntu 20.04 ?  Or installed on Ubuntu 22.04 boot USB?

Regards

---

### Post by Dennis N on 2023-02-19
> Yahoo mail running on this snap Firefox is unable attaching files to mail. It can't browse computer to select file, clicking it without response.
I depends on where the files you want to attach are on your computer. Files in your home folder should be accessible, otherwise not, with two exceptions: files in /media or /mnt.

Your other computer (in the display of post 5) has a Firefox package from a PPA, not the Ubuntu repository.

With 22.04 and 22.10, I removed the Firefox snap and install the Firefox Flatpak and be done with it. Some users like the PPA or go directly to Mozilla and get a package to manually install. I also remove snap-store (a.k.a Ubuntu Software) and install gnome-software + the flatpak plugin. You also are forced to take it's snap plugin, I believe.

---

### Post by satimis on 2023-02-19
> **Dennis N said:**
> I depends on where the files you want to attach are on your computer. Files in your home folder should be accessible, otherwise not, with two exceptions: files in /media or /mnt.

The problem here is clicking [Attach files from computer] without response.

Clicking
[Share files from Google Drive]
[Share files from Dropbox]
[Attach files from recent emails]
all having response and I can select, attach and send file

> 
Your other computer (in the display of post 5) has a Firefox package from a PPA, not the Ubuntu repository.

With 22.04 and 22.10, I removed the Firefox snap and install the Firefox Flatpak and be done with it. Some users like the PPA or go directly to Mozilla and get a package to manually install. I also remove snap-store (a.k.a Ubuntu Software) and install gnome-software + the flatpak plugin. You also are forced to take it's snap plugin, I believe.

Mozilla Support suggests me to re-install Firefox from Mozilla Firefox

Regards

---

### Post by satimis on 2023-02-20
The snap package of Firefox on Ubuntu 22.04 repo is not working correctly.

**[COLOR="#FF0000"]Problem solved as follows;[/COLOR]**

On Terminal run;```

$ sudo umount /var/snap/firefox/common/host-hunspell
$ sudo snap remove firefox

```

to remove Firefox

Following the steps on below URL to install Firefox
[B][COLOR="#FF0000"]
Installing Firefox via Apt (Not Snap)[/COLOR][/B]
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

Now attach file
-> Attach files from computer
works, able to search and select file

Regards

---

