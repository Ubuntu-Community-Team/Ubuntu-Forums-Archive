---
title: "Virtualbox"
date: 2007-02-14
forum: General Help
---

### Post by kiwidipstick on 2007-02-14
I downloaded virtualbox and tried to install using GDebi Installer. Something went wrong and I have the software update icon displayed with the following comments; An error occurred, please run Package manager from the right click menu or on a terminal to see what is wrong. The error message was; "Unknown Error" 'exceptions. System Error(E: The package virtualbox needs to be reinstalled, but I cannot find archive for it)' I have tried to run package manager but it does not do anything.
Appreciate any assistance to overcome this problem please, in plain language for this dipstick!.

---

### Post by tzulberti on 2007-02-15
Follow the instructions of this howto:
[http://www.ubuntuforums.org/showthread.php?t=340113]("http://www.ubuntuforums.org/showthread.php?t=340113&highlight=virtualbox")

---

### Post by kiwidipstick on 2007-02-15
Thanks tzulberti for this. I have followed it up. Cheers.

---

### Post by kiwidipstick on 2007-02-15
Under the afore mentioned guide, I did what was suggested except for the following.....
I have the problem under your heading "Trouble Shooting". I followed through to remove using synaptic, but when I search in synaptic, I get the result Virtualbox in the left hand pane only. You cannot right click on it. I am stuck, as the icon for updating is still showing with the error message. Any other suggestions please. I sure would appreciate an answer as to how to get this sorted. Cheers.:confused:

---

### Post by kiwidipstick on 2007-02-16
Can anyone please assist me as to how to get rid of update icon showing that there an error with virtualbox. I think that this error icon is stopping me being able to do updates. Thanks.

---

### Post by bob-aptllc on 2007-02-23
After I downloaded the VirtualBox .deb package to my desktop, I tried to install by right-clicking. The first result was a dependency error, but then the same error message you are receiving that VirtualBox needs to be reinstalled but Synaptic was not able to find an archive. (The full saga is at [http://ubuntuforums.org/showthread.php?t=367515](http://ubuntuforums.org/showthread.php?t=367515).) Synaptic was broken and not able to locate any package. I was not able to delete the VirtualBox (0 byte) faulty installation using Aptitude on the terminal.

I concluded that a fresh install of Edgy was the quickest and surest fix. I then followed the instructions for installing VirtualBox from the helpful folks at ubuntugeek.com: [http://www.ubuntugeek.com/create-and...irtualbox.html](http://www.ubuntugeek.com/create-and...irtualbox.html). VirtualBox then installed properly.

-Bob

---

