---
title: "Can't run Snap-store in Ubuntu 18.10"
date: 2018-10-22
forum: General Help
---

### Post by sebastian1978 on 2018-10-22
Upgraded from Ubuntu 18.04 to 18.10.

When click on icon nothing happens.

In terminal see:
```
snap run snap-store
2018/10/22 09:40:10.172805 main.go:158: argument "abort"'s "<&#1089;&#1084;&#1077;&#1085;&#1072; ID>s" should be wrapped in <>s
2018/10/22 09:40:10.172932 main.go:158: argument "ack"'s "<&#1092;&#1072;&#1081;&#1083; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/22 09:40:10.173092 main.go:158: argument "tasks"'s "<&#1089;&#1084;&#1077;&#1085;&#1072; ID>s" should be wrapped in <>s
2018/10/22 09:40:10.173160 main.go:158: argument "create-key"'s "<&#1080;&#1084;&#1103; &#1082;&#1083;&#1102;&#1095;&#1072;>s" should be wrapped in <>s
2018/10/22 09:40:10.173206 main.go:158: argument "create-user"'s "<&#1086;&#1090;&#1086;&#1089;&#1083;&#1072;&#1090;&#1100;>s" should be wrapped in <>s
2018/10/22 09:40:10.173241 main.go:158: argument "delete-key"'s "<&#1080;&#1084;&#1103; &#1082;&#1083;&#1102;&#1095;&#1072;>s" should be wrapped in <>s
2018/10/22 09:40:10.173318 main.go:158: argument "export-key"'s "<&#1080;&#1084;&#1103; &#1082;&#1083;&#1102;&#1095;&#1072;>s" should be wrapped in <>s
2018/10/22 09:40:10.173377 main.go:158: argument "find"'s "<&#1079;&#1072;&#1087;&#1088;&#1086;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.173422 main.go:158: argument "get"'s "<&#1082;&#1083;&#1102;&#1095;>s" should be wrapped in <>s
2018/10/22 09:40:10.173505 main.go:158: argument "interface"'s "<&#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.173567 main.go:158: argument "known"'s "<&#1090;&#1080;&#1087; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/22 09:40:10.173586 main.go:158: argument "known"'s "<&#1092;&#1080;&#1083;&#1100;&#1090; &#1079;&#1072;&#1075;&#1086;&#1083;&#1086;&#1074;&#1082;&#1086;&#1074;>s" should be wrapped in <>s
2018/10/22 09:40:10.173669 main.go:158: argument "login"'s "<&#1086;&#1090;&#1086;&#1089;&#1083;&#1072;&#1090;&#1100;>s" should be wrapped in <>s
2018/10/22 09:40:10.173744 main.go:158: argument "prepare-image"'s "<&#1084;&#1086;&#1076;&#1077;&#1083;&#1100; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/22 09:40:10.173764 main.go:158: argument "prepare-image"'s "<&#1082;&#1086;&#1088;&#1085;&#1077;&#1074;&#1072;&#1103; &#1076;&#1080;&#1088;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/22 09:40:10.173829 main.go:158: argument "services"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.173865 main.go:158: argument "logs"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.173896 main.go:158: argument "start"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.173933 main.go:158: argument "stop"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.173977 main.go:158: argument "restart"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/22 09:40:10.174020 main.go:158: argument "set"'s "<&#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1086;&#1085;&#1085;&#1086;&#1077; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077;>s" should be wrapped in <>s
2018/10/22 09:40:10.174072 main.go:158: argument "sign-build"'s "<&#1080;&#1084;&#1103; &#1092;&#1072;&#1081;&#1083;&#1072;>s" should be wrapped in <>s
2018/10/22 09:40:10.174443 main.go:158: argument "wait"'s "<&#1082;&#1083;&#1102;&#1095;>s" should be wrapped in <>s
2018/10/22 09:40:10.174486 main.go:158: argument "watch"'s "<&#1089;&#1084;&#1077;&#1085;&#1072; ID>s" should be wrapped in <>s
You need to connect this snap to the gnome platform snap.

You can do this with those commands:
snap install gnome-3-26-1604
snap connect snap-store:gnome-3-26-1604 gnome-3-26-1604

(the '3-26-1604' number defines the platform version and might change)


```

---

### Post by Bu83KQdr on 2018-10-23
.

---

### Post by patttern on 2018-10-23
sudo dpkg -r snapd gnome-software-plugin-snap
sudo apt update
sudo apt full-upgrade

---

### Post by deadflowr on 2018-10-23
Did you run the commands at the end:
> You need to connect this snap to the gnome platform snap.

You can do this with those commands:
```
snap install gnome-3-26-1604
snap connect snap-store:gnome-3-26-1604 gnome-3-26-1604
```

---

### Post by sebastian1978 on 2018-10-24
Thanks. It helped.
But I still don't understand why I should connect Snap-store to old Gnome 3.26. :confused:
I tryed to connect to Gnome 3.28 because I have no idea how to connect to 3.30
Got errors
> snap connect snap-store:gnome-3-28-1804 gnome-3-28-1804
2018/10/24 16:45:41.683404 main.go:158: argument "abort"'s "<&#1089;&#1084;&#1077;&#1085;&#1072; ID>s" should be wrapped in <>s
2018/10/24 16:45:41.683481 main.go:158: argument "ack"'s "<&#1092;&#1072;&#1081;&#1083; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/24 16:45:41.683627 main.go:158: argument "tasks"'s "<&#1089;&#1084;&#1077;&#1085;&#1072; ID>s" should be wrapped in <>s
2018/10/24 16:45:41.683712 main.go:158: argument "create-key"'s "<&#1080;&#1084;&#1103; &#1082;&#1083;&#1102;&#1095;&#1072;>s" should be wrapped in <>s
2018/10/24 16:45:41.683787 main.go:158: argument "create-user"'s "<&#1086;&#1090;&#1086;&#1089;&#1083;&#1072;&#1090;&#1100;>s" should be wrapped in <>s
2018/10/24 16:45:41.683804 main.go:158: argument "delete-key"'s "<&#1080;&#1084;&#1103; &#1082;&#1083;&#1102;&#1095;&#1072;>s" should be wrapped in <>s
2018/10/24 16:45:41.683937 main.go:158: argument "export-key"'s "<&#1080;&#1084;&#1103; &#1082;&#1083;&#1102;&#1095;&#1072;>s" should be wrapped in <>s
2018/10/24 16:45:41.684037 main.go:158: argument "find"'s "<&#1079;&#1072;&#1087;&#1088;&#1086;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.684100 main.go:158: argument "get"'s "<&#1082;&#1083;&#1102;&#1095;>s" should be wrapped in <>s
2018/10/24 16:45:41.684237 main.go:158: argument "interface"'s "<&#1080;&#1085;&#1090;&#1077;&#1088;&#1092;&#1077;&#1081;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.684312 main.go:158: argument "known"'s "<&#1090;&#1080;&#1087; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/24 16:45:41.684324 main.go:158: argument "known"'s "<&#1092;&#1080;&#1083;&#1100;&#1090; &#1079;&#1072;&#1075;&#1086;&#1083;&#1086;&#1074;&#1082;&#1086;&#1074;>s" should be wrapped in <>s
2018/10/24 16:45:41.684421 main.go:158: argument "login"'s "<&#1086;&#1090;&#1086;&#1089;&#1083;&#1072;&#1090;&#1100;>s" should be wrapped in <>s
2018/10/24 16:45:41.684539 main.go:158: argument "prepare-image"'s "<&#1084;&#1086;&#1076;&#1077;&#1083;&#1100; &#1087;&#1086;&#1076;&#1090;&#1074;&#1077;&#1088;&#1078;&#1076;&#1077;&#1085;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/24 16:45:41.684573 main.go:158: argument "prepare-image"'s "<&#1082;&#1086;&#1088;&#1085;&#1077;&#1074;&#1072;&#1103; &#1076;&#1080;&#1088;&#1077;&#1082;&#1090;&#1086;&#1088;&#1080;&#1103;>s" should be wrapped in <>s
2018/10/24 16:45:41.684692 main.go:158: argument "services"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.684760 main.go:158: argument "logs"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.684813 main.go:158: argument "start"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.684891 main.go:158: argument "stop"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.684960 main.go:158: argument "restart"'s "<&#1089;&#1077;&#1088;&#1074;&#1080;&#1089;>s" should be wrapped in <>s
2018/10/24 16:45:41.685029 main.go:158: argument "set"'s "<&#1082;&#1086;&#1085;&#1092;&#1080;&#1075;&#1091;&#1088;&#1072;&#1094;&#1080;&#1086;&#1085;&#1085;&#1086;&#1077; &#1079;&#1085;&#1072;&#1095;&#1077;&#1085;&#1080;&#1077;>s" should be wrapped in <>s
2018/10/24 16:45:41.685124 main.go:158: argument "sign-build"'s "<&#1080;&#1084;&#1103; &#1092;&#1072;&#1081;&#1083;&#1072;>s" should be wrapped in <>s
2018/10/24 16:45:41.685760 main.go:158: argument "wait"'s "<&#1082;&#1083;&#1102;&#1095;>s" should be wrapped in <>s
2018/10/24 16:45:41.685825 main.go:158: argument "watch"'s "<&#1089;&#1084;&#1077;&#1085;&#1072; ID>s" should be wrapped in <>s
&#1086;&#1096;&#1080;&#1073;&#1082;&#1072;: snap "snap-store" has no plug named "gnome-3-28-1804"

---

### Post by ophonos on 2018-10-24
> **deadflowr said:**
> Did you run the commands at the end:

This didn't help me. I removed snap with `sudo dpkg -r snapd gnome-software-plugin-snap` advice above. I don't understand why I need it.

---

### Post by ophonos on 2018-10-24
I read about snap a little bit. I am petty sure I don't need another  package manager, while apt works just fine. Even more so a package  manager with bugs. Yep, removing it is the right decision.

---

### Post by j-c-n on 2018-10-28
> **ophonos said:**
> I read about snap a little bit. I am petty sure I don't need another  package manager, while apt works just fine. Even more so a package  manager with bugs. Yep, removing it is the right decision.

I use Atom editor (I installed it from sw manager and it was snap package).
It started more than 10seconds on my Thinkpad T25. And the occupied space of two versions in snap folder  was more than 2GB. 

I removed Atom snap package and installed Atom from deb package. Atom starts more than 3 times quickier and occupied much less space.

---

### Post by ink_rus on 2019-01-18
Best way to fix this but is to put locale to bash profiale /etc/bash.bashrc:

> export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
export LANGUAGE=en_US.UTF-8

or to /etc/default/locale e.g.:

> sudo update-locale LANG=en_US.UTF-8

check changes with

> cat /etc/default/locale

> LANG=en_US.UTF-8
LC_COLLATE=C
LC_MESSAGES=C
LC_ALL=en_US.UTF-8

---

