---
title: "Time how long it takes for Firefox to start"
date: 2022-08-20
forum: General Help
---

### Post by raleigh3 on 2022-08-20
I am convinced that Firefox takes longer to start than Seamonkey.

I would like to test how long it takes FF to start.

time firefox does not work.

Is there a way?

Thanks.

---

### Post by VMC on 2022-08-21
```
$ time firefox

real    0m0.099s
user    0m0.048s
sys    0m0.022s
```

---

### Post by grahammechanical on 2022-08-21
The command "time firefox" will work on Ubuntu 20.04 but not on Ubuntu 22.04 because on 22.04 the snap packaged version is default installed.

> graham@UbuntuDev:~$ snap run --trace-exec firefox
[sudo] password for graham: 
Gtk-Message: 12:03:55.005: Failed to load module "canberra-gtk-module"
Gtk-Message: 12:03:55.009: Failed to load module "canberra-gtk-module"
Slowest 10 exec calls during snap run:
  0.025s /usr/lib/snapd/snap-confine
  0.008s /usr/bin/realpath
  0.008s /usr/bin/realpath
  0.008s /usr/bin/realpath
  0.008s /usr/bin/realpath
  0.008s /usr/bin/realpath
  0.166s /snap/firefox/1670/snap/command-chain/desktop-launch
  0.011s /usr/bin/id
  0.016s /usr/bin/cut
  0.020s /snap/firefox/1670/firefox.launcher
Total time: 0.340s 

Is Seamonkey published as a snap? Are we comparing Apples with Pears? I would not be surprised if Seamonkey did load faster the Firefox. They have developed into two different projects. The Seamonkey user interface should be lighter than the user interface that Firefox on Gnome/Ubuntu uses.

Regards

---

### Post by tea for one on 2022-08-21
Try this for firefox snap package
```
time /snap/bin/firefox

```

---

### Post by SeijiSensei on 2022-08-21
Or else dump the snap package and add the Mozilla PPA to your sources list.

[https://launchpad.net/~mozillateam/+archive/ubuntu/ppa](https://launchpad.net/~mozillateam/+archive/ubuntu/ppa)

---

