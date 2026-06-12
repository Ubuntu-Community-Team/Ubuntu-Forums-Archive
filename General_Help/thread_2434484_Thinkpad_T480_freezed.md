---
title: "Thinkpad T480 freezed"
date: 2020-01-06
forum: General Help
---

### Post by jakutenshi on 2020-01-06
Hello,

I have a problem with my Ubuntu 18.04, the beginning of story described there: [https://askubuntu.com/questions/1200615/t480-ubuntu-18-04-freezed-for-hardreset](https://askubuntu.com/questions/1200615/t480-ubuntu-18-04-freezed-for-hardreset) But suddenly without any journalctl errors my laptop freezed, no feedback, only screenlight of the last frame. Hardware works, because when I put the chager in my power button flashed. How can I understand what is going on? It's really dangerous for me: suddenly lost my workfiles for no reason.

Freezed means that the laptop didn't answering on my input, display lights, but no changes, and only hardreset is a solution.

---

### Post by jakutenshi on 2020-01-07
[COLOR=#494949][FONT=&quot]Probably the reason is PCIe driver or the bus itself. Dmesg log is attached. Also there is a bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1426216](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1426216) t480 and ubuntu 18.14 are presented. Does it hardware problem and I should bring the laptop to a service, or it's ubuntu's driver problem and I should wait for patches or change anothe distro?[/FONT][/COLOR]
[COLOR=#494949][FONT=&quot] [/FONT][/COLOR]
[COLOR=#494949][FONT=&quot]Dmesg: [https://gist.github.com/JAkutenshi/5c97938fa4e3af29730c651877760498](https://gist.github.com/JAkutenshi/5c97938fa4e3af29730c651877760498)[/FONT][/COLOR]

---

