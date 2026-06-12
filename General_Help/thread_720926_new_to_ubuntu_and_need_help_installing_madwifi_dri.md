---
title: "new to ubuntu and need help installing madwifi drivers"
date: 2008-03-10
forum: General Help
---

### Post by ontherooftop on 2008-03-10
I just started using ubuntu, I was formerly into windows , and I want to install the madwifi 
drivers. I dont know anything , I just figured out a little how to use package manager and I 
downloaded the madwifi  driver for my atheros card and I have no idea what to do or how 
to install it , can I please get a step by step because I dont even know how to do commands 
or how to even start commands , so any help would be greatly appreciated.

---

### Post by jrusso2 on 2008-03-10
I think the restricted driver manager should be able to handle this.  Is this a usb wifi?

---

### Post by scragar on 2008-03-10
under System > administration > Synaptic Package Manager
do a search for: "madwifi-tools", and mark it for instilation, then click apply to the top right

alternativly, if you want the command line experience(and who doesn't) go to Applications > Accessories > Terminal and enter:```
sudo apt-get install madwifi-tools
``` typing password when prompted.

---

### Post by kevdog on 2008-03-10
madwifi doesnt support usb devices FYI.  For this you need ndiswrapper!

---

### Post by por100pre1 on 2008-03-10
Which chipset does your card use? Madwifi is already included in Ubuntu Gutsy, but madwifi doesn't support the newer Atheros 5008 series chipsets. There's beta driver under development that [can be installed]("http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008"), but **it would likely crash your system so don't use it.** Ndiswrapper doesn't work much either. If your card uses an older chipset it should work out of the box. :(

---

### Post by Gow524 on 2008-03-10
I am new to Ubuntu also, so how do you post any messages in this forum?

---

### Post by por100pre1 on 2008-03-11
> **Gow524 said:**
> I am new to Ubuntu also, so how do you post any messages in this forum?

Go [here]("http://ubuntuforums.org/forumdisplay.php?f=73") and then click **[Make new post]("http://ubuntuforums.org/newthread.php?do=newthread&f=73")**.

---

### Post by hotel86 on 2008-06-22
ok so if madwifi does not support the Atheros AR5008 chipset then what driver does? because that is the addapter that I have.

---

