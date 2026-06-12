---
title: "Update manager fails to download repository information"
date: 2013-01-04
forum: General Help
---

### Post by m1001879 on 2013-01-04
Hi gang,

I'm using 12.04 and my update manager has developed a bug. It won't download the repository information.

Details:

W:Failed to fetch [http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Ideas? Many thanks

---

### Post by Bashing-om on 2013-01-04
m1001879; Hi !

Did you upgrade to 12.04 ?
These links explain the cause:
[https://answers.launchpad.net/ubuntu/+source/indicator-cpufreq/+question/197732](https://answers.launchpad.net/ubuntu/+source/indicator-cpufreq/+question/197732)
[http://askubuntu.com/questions/161878/when-will-the-artfwo-ppa-be-updated-for-12-04-precise](http://askubuntu.com/questions/161878/when-will-the-artfwo-ppa-be-updated-for-12-04-precise)

Solution is to remove those offending ppas from your sources list.

Either edit /etc/apt/sources.list or files in the /etc/apt/sources.list.d directory
or remove them in the ubuntu software center.
[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by stinkeye on 2013-01-04
Too add to **Bashing-om's** post if you go to 
[**_[COLOR="DarkRed"]http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/[/COLOR]_**]("http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/")
you will see there is no packages from that ppa for Precise.

---

### Post by charliewarlie on 2013-04-29
Hi there, I'm having this same problem but am a complete newbie to ubuntu - could someone talk me through how to do this please?

---

### Post by Bashing-om on 2013-04-29
charliewarlie; Hi ! Welcome to the forum.

IF indeed you have the exact same problem, the easiest method is to:
open Software Sources (12.04: launcher ->ubuntu Software Center -> Software sources (from the task bar menu)-> Other Software;
untick the offending ppa (Personal Package Archive) check box.

To be sure, re-boot and try again to update/install updated packages.[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by charliewarlie on 2013-04-30
Brilliant, thank you! :p

---

