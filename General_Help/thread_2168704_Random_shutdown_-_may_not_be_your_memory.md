---
title: "Random shutdown - may not be your memory"
date: 2013-08-18
forum: General Help
---

### Post by pinkmonkeysyndrome on 2013-08-18
Nearly every site you visit is telling you that these random shutdowns you're experiencing are probably caused by faulty memory modules - but that is probably not the answer. Bad or broken video drivers can cause random shutdowns too.

Intel onboard video using i915 drivers caused them in my lappie.

I should have documented this better, some I wrote on the back of a chocolate bar wrapper, but here is the solution I discovered.

First, are you using Intel i915 video drivers?

Open a terminal and input the following:

lsmod

this will list which modules are currently loaded. You are looking for i915

If it is not there, I wish you good luck because what follows will not help you.

If i915 is loaded, in the terminal enter:

sudo apt-get install xserver-xorg-video-intel

Does it say something about unmet dependencies?

You may now do your happy dance because there is a simple solution.

Point your web browser to

[http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html](http://www.webupd8.org/2013/04/how-to-use-intel-linux-graphics-drivers.html)

here is your solution.

(I copied it over)


- for Linux distributions based on Ubuntu 12.10 (like Linux Mint 14):

echo "deb [https://download.01.org/gfx/ubuntu/12.10/main](https://download.01.org/gfx/ubuntu/12.10/main) Ubuntu 12.10 #Intel Graphics drivers" | sudo tee /etc/apt/sources.list.d/intellinuxgraphics.list


- for Linux distributions based on Ubuntu 13.04 (like Linux Mint 15):

echo "deb [https://download.01.org/gfx/ubuntu/13.04/main](https://download.01.org/gfx/ubuntu/13.04/main) Ubuntu 13.04 #Intel Graphics drivers" | sudo tee /etc/apt/sources.list.d/intellinuxgraphics.list


Then, for any of the above, add the repository GPG key and update the software sources using the following commands:

wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | sudo apt-key add -
wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | sudo apt-key add -
sudo apt-get update
sudo apt-get dist-upgrade

And finally, use your distro's update tool to upgrade the packages or alternatively, run "sudo apt-get dist-upgrade" (but make sure this command doesn't try to remove any packages and if for some reason it does, abort and disable the repository).


And so ends three days of pulling my hair out. My lappie hasn't crashed once since I applied this solution. Hope it works for you.

---

