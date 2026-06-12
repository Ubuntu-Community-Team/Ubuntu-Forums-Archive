---
title: "dl.google.com_linux_chrome_deb_dists_stable_main_b inary-i386_Packages broken"
date: 2013-06-13
forum: General Help
---

### Post by mayervlsk on 2013-06-13
[FONT=arial][SIZE=4]Hello[/SIZE][/FONT]
[FONT=arial][SIZE=4]
[/SIZE][/FONT]
[FONT=arial][SIZE=4]I'm running Chrome in Ubuntu 12.04 64 bits, I have the following problem:[/SIZE][/FONT]
[FONT=arial][SIZE=4]
[/SIZE][/FONT]
[SIZE=4][FONT=arial]The file [COLOR=#000066]dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages[/COLOR] in[COLOR=#000066]/var/lib/apt/lists[/COLOR] has this **** inside:[/FONT][/SIZE][FONT=arial]
[/FONT]
[FONT=arial]<HTML><HEAD><TITLE>Cisco Systems Inc. Web Authentication Redirect</TITLE><META http-equiv="Cache-control" content="no-cache"><META http-equiv="Pragma" content="no-cache"><META http-equiv="Expires" content="-1"><META http-equiv="refresh" content="1; URL=[https://1.1.1.1/login.html?redirect=dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz](https://1.1.1.1/login.html?redirect=dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages.gz)"></HEAD></HTML>[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial][SIZE=4]I guess it's from my university's wifi firewall, I got the right code ([/SIZE][https://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages](https://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages)) but I can't replace it because I have not permission to do that.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Now I can't update, use synaptic or the software center, neither remove or reinstall chrome.[/FONT]

---

### Post by mayervlsk on 2013-06-13
Solved:

$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update

---

