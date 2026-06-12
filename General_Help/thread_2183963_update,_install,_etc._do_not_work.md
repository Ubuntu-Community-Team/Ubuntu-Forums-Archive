---
title: "update, install, etc. do not work"
date: 2013-10-27
forum: General Help
---

### Post by jongm on 2013-10-27
hello. i need help with ubuntu's update and upgrade function. it returns this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_linrunner_tlp_ubuntu_dists_raring_main_i18n_Translation-en%5fPH
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

thanks for the help.

---

### Post by ibjsb4 on 2013-10-27
Open a terminal and enter:

```
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update


```

More here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=The+package+lists+or+status+file+could+not+be+parsed+or+opened.&sa=Search&cof=FORID:9)

---

