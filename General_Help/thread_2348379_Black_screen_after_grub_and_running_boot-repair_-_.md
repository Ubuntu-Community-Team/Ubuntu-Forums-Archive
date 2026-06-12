---
title: "Black screen after grub and running boot-repair - missing boot loader"
date: 2017-01-03
forum: General Help
---

### Post by ubuntini2 on 2017-01-03
Please help!
First question- if missing boot loader is indeed the issue, how does it suddenly go missing?

 I think my black screen is most likely a result of installing new Intel graphics software on my ubuntu-mate 16.04 lts system.
 I created a live boot-repair disk and ran it twice.

 This is the output
[http://paste.ubuntu.com/23731363/](http://paste.ubuntu.com/23731363/)

 I also get a nearly full partition error message on my sda3 partition.

 Prior to trying boot-repair I also added nomodeset to my grub menu but when I tried
Quote:
[TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                            sudo update-grub                    [/TD]
[/TR]
[/TABLE]

I get an error
Quote:
[TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                            cannot create /boot/grub/grub.cfg.new: Read-only                    [/TD]
[/TR]
[/TABLE]

2nd Question> can I uninstall software on my primary boot drive from a live usb?

---

