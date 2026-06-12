---
title: "Setting up internet connection?"
date: 2005-10-15
forum: General Help
---

### Post by gregnorc on 2005-10-15
How would I do this? I'm using a thinkpad 600e with a Netgear FA511 10/100 Mbps wired ethernet card. I unplugged my network cable from my windows box and plugged it into the laptop, but when I try and go online, use apt-get, etc, it doesn't work.

How would I set this up? I tried google with no luck.

Thanks for the help

-GregNorc

---

### Post by aclaunch on 2005-10-15
Several steps: you need to find out what chipset your Netgear card uses. Try Googling the exact model and see what you get. Linux uses kernel modules to drive peripherals so once you know what chipset you can find out what module needs to be loaded.

To load the module (if it is not done automatically) do "sudo modprobe modulename". Then go to the System->Admin->Networking and set up your card.

You can also use the terminal to check if the card is being identified. Open a terminal and type "dmesg | grep Netgear". This will select any boot messages regarding that card. You can also do "ifconfig" which should show what network interfaces are recognized.

Do some of this and post back.

Good Luck,
Alan

---

### Post by EggMan on 2005-10-25
hello i am having the same problem so i can try to help/get some help with this it would be grand

---

