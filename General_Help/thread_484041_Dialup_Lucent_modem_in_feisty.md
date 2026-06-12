---
title: "Dialup Lucent modem in feisty"
date: 2007-06-25
forum: General Help
---

### Post by zorkerz on 2007-06-25
This problem has been discussed a bit here [http://ubuntuforums.org/showthread.php?t=479784](http://ubuntuforums.org/showthread.php?t=479784)

I am trying to get my dialup modem working in xubuntu 7.04
I have been using the [wiki]("https://help.ubuntu.com/community/DialupModemHowto") and my scanmodem tool output shows this as my modem.
> Class 0780: 11c1:0452 Communication controller: Agere Systems LT WinModem
My first hang up comes in the [lucent driver section.]("https://help.ubuntu.com/community/DialupModemHowto/Lucent")  I am getting the "FATAL: Module not found" error for both ltserial and ltmodem. The wiki provides advice for hoary users (which does not work for me) but nothing for feisty 7.04 users.

Next section is the alternative martian driver which is specifically for an error that i do not receive but i have been trying it anyways for lack of other options. I get a command not found error when trying to enter the second to last command in this section > sudo martian_helper --daemon
the command "sudo martian_modem --daemon" does work

From this point I have been trying to get the modem to connect to the internet.
I have not gotten gnome-ppp to work it does not detect a modem on the system.

I have setup wvdial. It says it cannot detect or find the information for the serial port but this does not seem to be a show stopper. The modem dials up no problem and will stay online seemingly indefinitely as long as I do not use internet applications. Normally I can get in one set of google  results before it disconnects. I have tried commenting out the two lines as specified in the wiki and also adding a "replacedefaultroute" line but none of these have made any difference.
This is similar to my [problem]("http://ubuntuforums.org/showthread.php?t=190728&page=2") with another modem on this computer however now it only disconnects why trying to use an internet application.

Thanks to anyone who actually reads through this. I realize its long and no fun to read but at least it will serve to remind me what I have tried already.

If anyone can think of anything it would be much appreciated, I am at a dead end here.
thanks

---

### Post by Matchless on 2007-06-25
Just a last comment from my side. See if your lan card is not interfering here, especially if it is plugged into something, disable if possible. Also just check that you phone line is not loaded with fax, modem, multiple phones, burglar alarm etc. These things sometimes cause some weird problems. If not I seriously suggest a new clean install of Ubuntu.

---

### Post by zorkerz on 2007-06-27
Unfortunately there are no other network devices on the computer and it is the only thing plugged into the phone line. Plus dialup still works in windows 98. I think I may give xubuntu one more fresh install but i have little hope that it will work.
thanks as always

---

### Post by RJQ on 2007-06-28
After 10 times of trying with a fresh installation of Feisty k/ubuntu I realize that a least for me it will not work, now I know that it is a Kernel related problem but I am totally new in this to go further, my Dapper works wonders but nothing seams to work for Edgy or Feisty, martian is totally useless for my computer, for some reason simply does not work, the only time it could find the modem and actually make the call without any other result was on a quite ugly duplication of the kernel from Dapper installed then in feisty, from this (may be senseless action) I saw that the kernels do not provide support for the modules and the lucent modem and from there I do not know what else can I do, for now I am holding all my downloads in a backup in case the repositories became unavailable, a least while I use dial up.
:(

---

### Post by wh7qq on 2007-06-29
Been going through a search for support for this one myself...about the only current distro I have tried that actually supports this one out of the box is DSL...Damn Small Linux...based on the 2.4.7 kernel for the sake of older hardware.  Most of the "mainstream distros" based on newer kernels just don't work. This winmodem is getting increasingly difficult to support.  I suggest a US Robotics external serial modem from ebay...around $20 us if you can find one. Avoid all internal or usb modems.  

Paul

[COLOR="Red"]Quote from one of the developers on the Kanotix forum, Nov. '06:
[/COLOR]
[COLOR="DarkOrchid"]"The ltmodem has long been unmaintained, and is based upon a large ugly binary blob that is linux unfriendly. It was not included in recent snapshots because the module would fail to even build with recent linux kernels. It has since been fixed, but may disappear at any given time in the very near future.

Please consider finding an alternative dial-up access method, whether it be by dedicated dial-up router, external modem or whatever, if possible."
[/COLOR]

---

### Post by solar george on 2007-07-22
> "The ltmodem has long been unmaintained, and is based upon a large ugly binary blob that is linux unfriendly. It was not included in recent snapshots because the module would fail to even build with recent linux kernels. It has since been fixed, but may disappear at any given time in the very near future.

Please consider finding an alternative dial-up access method, whether it be by dedicated dial-up router, external modem or whatever, if possible."


It is still included in the 386 restricted drivers - I've updated the wiki
[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

---

### Post by bliffle on 2007-09-14
I only need dialup for emergency use or while traveling with a laptop, so I don't want to drag along my old serial port modem. So what I'm doing is dualbooting to XP for portable internet, put stuff in shared files, then boot back to ubuntu. But this has to end.

---

### Post by kevdog on 2007-09-19
Do you still need help with the martian modem??

---

### Post by bliffle on 2007-10-06
I'm trying to get dialup going again.

[http://ubuntuforums.org/showthread.php?t=553250&highlight=dialup&page=2](http://ubuntuforums.org/showthread.php?t=553250&highlight=dialup&page=2)

I'm stalled at the point where one does the 'make'.

---

