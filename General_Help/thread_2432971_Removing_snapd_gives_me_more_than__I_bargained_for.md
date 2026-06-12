---
title: "Removing snapd gives me more than  I bargained for"
date: 2019-12-11
forum: General Help
---

### Post by Robbyx on 2019-12-11
Ub 18.04 LTS

I have been having some error messages which led me to assume from other answers, that it was connected with snap. I therefore decided to remove it.

I followed this advice 



> To remove snap first you might want to remove all the snap programs to free up storage space. To do so here is a small script.

    #!/bin/sh
    set -eu

    snap list --all |
        while read snapname revision; do
            snap remove "$snapname" --revision="$revision"
        done

Afterwards remove snap using

sudo apt autoremove --purge snapd

[https://askubuntu.com/questions/1193482/how-to-remove-snap-from-ubuntu-18-04-before-and-after-install/1193569](https://askubuntu.com/questions/1193482/how-to-remove-snap-from-ubuntu-18-04-before-and-after-install/1193569)

The result was that not only was snap removed but so was my access to all settings, and I had no sound. I therefore restored a backup of the OS and now have snap installed but I also have sound, settings, etc. 

Taking into account the surprising removal of essential operations, how should I set about removing snap?

---

### Post by #&amp;thj^% on 2019-12-11
I do this **_very early_** in my installs, so a lot of configs  and settings don't get in the way.
My method is as follows:
```
sudo rm -rf /var/cache/snapd/
```
Then:
```
sudo apt autoremove --purge snapd gnome-software-plugin-snap
```
And finally:

```
rm -fr ~/snap

```
Don't forget to use "sudo" i was being lazy. ;)
This will completely remove snap, snapd, all installed snap packages and their data, and never again suggest snap packages in the software store.

---

### Post by Robbyx on 2019-12-11
As I am not removing snap, very early in the installation, do you think that I am likely to get the same problems from your purge settings that I got from the one I quoted in my  post above?

---

### Post by kansasnoob on 2019-12-12
> **Robbyx said:**
> As I am not removing snap, very early in the installation, do you think that I am likely to get the same problems from your purge settings that I got from the one I quoted in my  post above?

Start by running:

```
snap list
```

Or maybe:

```
snap list --all
```

That will list all installed snaps. Maybe good idea to compare the output of those two commands to see if there's any difference. Anyway all wanted snap apps will be removed in the process so will need to be reinstalled via apt or some other source like .deb. I like to use synaptic (package manager) to parse the availability of packages in the repos.

I had always just used "snap list" on fairly fresh installs of Bionic which would typically remove:

```
core                  16-2.41                     7713  stable    canonical&#10003;  core
core18                20191001                    1192  stable    canonical&#10003;  base
gnome-3-26-1604       3.26.0.20190830             92    stable/…  canonical&#10003;  -
gnome-3-28-1804       3.28.0-10-gaa70833.aa70833  71    stable    canonical&#10003;  -
gnome-calculator      3.34.0+git1.822e4b58        501   stable/…  canonical&#10003;  -
gnome-characters      v3.32.1+git2.3367201        317   stable/…  canonical&#10003;  -
gnome-logs            3.34.0                      81    stable/…  canonical&#10003;  -
gnome-system-monitor  3.32.1-3-g0ea89b4922        100   stable/…  canonical&#10003;  -
gtk-common-themes     0.1-22-gab0a26b             1313  stable/…  canonical&#10003;  -
```

And the only packages I'd need to reinstall from apt were 'gnome-calculator' and 'gnome-system-monitor' but I don't run the standard out-of-box Ubuntu desktop. My initial reasoning was that the snap versions of packages would take 3 to 5 seconds to open/load even on fast hardware.

---

### Post by Robbyx on 2019-12-12
I followed your advice and reinstalled calc and sys monitor. I also needed to install the sound. It all seems to have worked. I assume that all the other items that appeared in your snap list were specific to snap ie:

Core and Core18 (not in synaptic]=M)
gnome-3-26-1604 &1804    M
GTK & GTK2-common-themes  M

---

