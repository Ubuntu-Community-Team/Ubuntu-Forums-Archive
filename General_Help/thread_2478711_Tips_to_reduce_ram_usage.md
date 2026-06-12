---
title: "Tips to reduce ram usage"
date: 2022-09-02
forum: General Help
---

### Post by raleigh3 on 2022-09-02
[https://ubuntu-mate.community/t/tips-to-reduce-ram-usage/25804](https://ubuntu-mate.community/t/tips-to-reduce-ram-usage/25804)

A few tips to reduce RAM usage from a fresh install. Numbers are from a fresh install of U- MATE 22.04.1 after complete update using htop. Reduction numbers come from making the change, rebooting, and letting the system settle down

Base RAM usage fresh install - 688 MB

    Use MATE Tweak to change the panel layout to Traditional from Familiar. Traditional uses the least RAM. Reduction - 10 MB.
    Go to Control Center -> Startup Applications and uncheck Blueman Applet. Obviously you wouldn't do this if you need Bluetooth. Reduction - 40 MB.
    Go to Software Boutique and delete Evolution. Again, if you use Evolution you would not want to do this. Reduction - 17 MB
    If you do 3 above you will still have evolution software running. You can purge the rest of Evolution by going to the terminal and typing "sudo apt purge evolution*" . Reduction - 40 MB.

Total reduction 107 MB down to 581 MB. Nothing earth shattering but it's there.

I think the surprises for me were 1 and 4.

Best of Luck

---

### Post by mIk3_08 on 2022-09-03
Thanks for sharing. Regard and cheers

---

