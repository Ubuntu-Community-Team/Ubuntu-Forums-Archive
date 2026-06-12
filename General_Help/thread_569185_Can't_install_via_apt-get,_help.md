---
title: "Can't install via apt-get, help"
date: 2007-10-06
forum: General Help
---

### Post by clos on 2007-10-06
when i tried to apt-get install xfce4 i get 

```
   1.
      The following packages have unmet dependencies:
   2.
        deluge-torrent: Depends: libboost-date-time1.34.1 but it is not installable
   3.
                        Depends: libboost-filesystem1.34.1 but it is not installable
   4.
                        Depends: libboost-thread1.34.1 but it is not installable
   5.
                        Depends: libc6 (>= 2.6-1) but 2.3.6-0ubuntu20.5 is to be installed
   6.
                        Depends: libgcc1 (>= 1:4.2.1) but 1:4.0.3-1ubuntu5 is to be installed
   7.
                        Depends: libssl0.9.8 (>= 0.9.8e-1) but 0.9.8a-7ubuntu0.4 is to be installed
   8.
                        Depends: libstdc++6 (>= 4.2.1) but 4.0.3-1ubuntu5 is to be installed
   9.
                        Depends: zlib1g (>= 1:1.2.3.3.dfsg-1) but 1:1.2.3-6ubuntu4 is to be installed
  10.
                        Depends: python-support (>= 0.3.4) but it is not going to be installed
  11.
                        Depends: python-glade2 but it is not going to be installed
  12.
                        Depends: python-xdg but it is not going to be installed
  13.
                        Depends: python-notify but it is not installable
  14.
                        Depends: python-dbus but it is not installable
  15.
      E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

help please

---

### Post by taurus on 2007-10-06
What happens when you run these commands from a terminal?

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

