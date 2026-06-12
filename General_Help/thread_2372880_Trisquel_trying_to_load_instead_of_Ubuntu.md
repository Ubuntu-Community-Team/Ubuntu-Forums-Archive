---
title: "Trisquel trying to load instead of Ubuntu"
date: 2017-09-29
forum: General Help
---

### Post by jordans81 on 2017-09-29
Yesterday, I ran some updates for Ubuntu and when I restarted the computer, it tried to boot into Trisquel. A couple of weeks ago, I was trying to add a Disconnect add-on to my Firefox browser and it went to another page which advertised Trisquel which I inadvertently started to download. I realized it was the wrong thing and cancelled the download. I certainly didn't install it, but a couple of weeks later, here it says it has installed Trisquel. I also downloaded IceCat (which I never use) so I'm wondering if that would have done it too.


  I'm on a dual boot with Windows 10, and when the screen comes up to chose my OS, it doesn't show Ubunutu as an option any longer, but shows Trisquel instead. Then I get an error message that says that Trisquel can't load and it boots with Ubuntu. I'd like to get rid of Trisquel on the boot-up and make it go back to the Ubuntu default. Any ideas how to do this?

---

### Post by oldfred on 2017-09-29
You are the second user to say this. 

to see sources lists:
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by vasa1 on 2017-09-29
The other user with the Trisquel/Ubuntu identity crisis posted here: [https://ubuntuforums.org/showthread.php?t=2372144](https://ubuntuforums.org/showthread.php?t=2372144)

---

