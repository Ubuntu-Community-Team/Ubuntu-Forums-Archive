---
title: "System Error"
date: 2013-02-09
forum: General Help
---

### Post by Elborath on 2013-02-09
Hi-I have only been using Ubuntu for a couple of weeks so am still very much a newbie! I am running Ubuntu in a partition on both my PC based laptops. On this machine when I boot up I get the warning that there is a system error. I send a report each time but the error persists. It usually then goes on to give me a dialogue box that says 'Sorry Ubuntu 12.04 has experienced an internal error' again asks me to report--which I do and tells me to enter the following into Terminal in order to generate a text report to send:

sudo hcidump -XYt > $HOME/hci.log

However when I do that I am told that the command can't be found. Ububtu seems to run smoothly (though I can't seem to print even though it bluetooth paired with my printer without trouble). When I click on 'details' from the first error blutoothd is top of the list. Anyone got any ideas? Elborath

---

### Post by tgalati4 on 2013-02-09
We are all newbies.  Some just newer than others.

tgalati4@Mint14-Extensa ~ $ which hcidump
tgalati4@Mint14-Extensa ~ $ locate hcidump
tgalati4@Mint14-Extensa ~ $ apt-cache search hcidump
bluez-hcidump - Analyses Bluetooth HCI packets
tgalati4@Mint14-Extensa ~ $ apt-cache policy bluez-hcidump
bluez-hcidump:
  Installed: (none)
  Candidate: 2.4-1
  Version table:
     2.4-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages

Do you have the hci.log?  Can you post it?

It's not installed by default, so perhaps try installing it:

Open a terminal:

```
sudo apt-get install bluez-hcidump
```

Look for other system errors:

```
dmesg | more
```
Spacebar to page forward, "q" to quit.

---

