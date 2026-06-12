---
title: "list installed Snap programs. Ubuntu 19.10"
date: 2019-10-24
forum: General Help
---

### Post by s9032g@comcast.net on 2019-10-24
Is there a way that I can easily discover all the Snap programs that I have without looking at the source one by one.

---

### Post by slickymaster on 2019-10-24
You can  list all the Snap packages installed on your system running the following in a terminal window```
snap list
```

---

### Post by ajgreeny on 2019-10-24
Command ***snap list*** will tell you all.

---

### Post by PaulW2U on 2019-10-24
```
snap list
```

Edit: beaten by two forum staff but at least we all agreed.  :)

---

### Post by TheFu on 2019-10-24
```
$ snap list

Command 'snap' not found, but can be installed with:

sudo apt install snapd
```
 
That's on an 18.04.3 test server.  We remove snapd on purpose.  We prefer to have control over any constraints for network daemons under our control.

Might be possible to purge all snaps and the snapd program to avoid any *stealth* snap installations. I understand that some desktop-centric programs will only be available via snap in 19.10 going forward. YMMV.

---

### Post by Dennis N on 2019-10-24
If you want to see the disabled snaps as well, use the** --all** option.

I infer by observation that two versions of any package are retained when it's updated. I made a notation that the original Chromium Snap when installed was Rev 853 (now gone), many upgrades since then and I have not removed any versions myself.

```
dmn@Tyana-vm:~$ snap list --all
Name                  Version                     Rev   Tracking  Publisher   Notes
atari800-jz           3.1.0-0                     1     stable    jz          -
chromium              77.0.3865.120               899   stable    canonical&#10003;  disabled
chromium              78.0.3904.70                909   stable    canonical&#10003;  -
core                  16-2.42                     7917  stable    canonical&#10003;  core
core                  16-2.41                     7713  stable    canonical&#10003;  core,disabled
core18                20191010                    1223  stable    canonical&#10003;  base
core18                20191001                    1192  stable    canonical&#10003;  base,disabled
gnome-3-26-1604       3.26.0.20191024             97    stable/…  canonical&#10003;  -
gnome-3-26-1604       3.26.0.20190830             92    stable/…  canonical&#10003;  disabled
gnome-3-28-1804       3.28.0-14-g9303a49.9303a49  91    stable    canonical&#10003;  -
gnome-3-28-1804       3.28.0-10-gaa70833.aa70833  71    stable    canonical&#10003;  disabled
gnome-calculator      3.34.1+git1.d34dc842        536   stable/…  canonical&#10003;  -
gnome-calculator      3.34.0+git1.822e4b58        501   stable/…  canonical&#10003;  disabled
gnome-characters      v3.32.1+git2.3367201        359   stable/…  canonical&#10003;  -
gnome-characters      v3.32.1+git2.3367201        317   stable/…  canonical&#10003;  disabled
gnome-logs            3.34.0                      81    stable/…  canonical&#10003;  -
gnome-logs            3.34.0                      73    stable/…  canonical&#10003;  disabled
gnome-system-monitor  3.32.1-3-g0ea89b4922        107   stable/…  canonical&#10003;  -
gnome-system-monitor  3.32.1-3-g0ea89b4922        100   stable/…  canonical&#10003;  disabled
gtk-common-themes     0.1-25-gcc83164             1353  stable/…  canonical&#10003;  -
gtk-common-themes     0.1-22-gab0a26b             1313  stable/…  canonical&#10003;  disabled
quadrapassel          3.32.0+git3.1c047df         105   stable    canonical&#10003;  disabled
quadrapassel          3.32.0+git3.1c047df         154   stable    canonical&#10003;  -
snap-store            20191021.a9948d5            201   stable    canonical&#10003;  -
snap-store            20190829.daf5512            188   stable    canonical&#10003;  disabled

```

---

### Post by s9032g@comcast.net on 2019-10-25
I did the apt install snapd and I got this

steven@steven-Studio-1747:~$ snap list
No snaps are installed yet. Try 'snap install hello-world'.

Don't understand as I know I have at least one, didn't look beyond that, snap program

---

### Post by PaulW2U on 2019-10-25
Which snap(s) do you think you have installed?
What is the output of the following?
```
snap changes
```

---

### Post by s9032g@comcast.net on 2019-10-25
never mind. I made a mistake.

Thanks

---

