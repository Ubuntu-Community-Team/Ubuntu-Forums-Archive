---
title: "Thunderbird email antivirus setup"
date: 2007-05-19
forum: General Help
---

### Post by gobbles414 on 2007-05-19
I am using Ubuntu 7.04 for my operating system and the latest Ubuntu build of Thunderbird for my email: version 1.5.0.10 (20070403). So that I can send and receive emails with my colleagues who are running Microsoft Windows, I would like to install an antivirus on my computer. It would be best for me if the antivirus scanner works with Thunderbird; but I am willing to switch to Evolution if it is absolutely necessary. A set of step-by-step instructions would help me a lot. Thanks in advance for your assistance.

---

### Post by the.phantom on 2007-05-19
ok i am a new and a lightweight on ubuntu !!!

there are a few a/v's that you can use, i use "avast" and it is easy to install, but most are "on demand" scanners.

and there is not much floating around that can harm linux ! and if you wil do a few searches on this forum most think a a/v is not really needed, a good firewall is though!

have you gone to "grc.com" and ran a "shields up " (firewall checker for open ports)

and look through your t-bird settings, there are some great security features and the spam filter works great !

mitch

i myself use a "ad on" for t-bird called "allow html temp"
so when i open a mail i view it in text only and if i trust the sender i can click and view it in html ... pretty hard to get anything in text, you would have to open  a bad attachment to get anything.

mitch

---

### Post by gobbles414 on 2007-05-19
Thanks Phantom! I passed all of the Shields Up scans with full stealth (thanks to Firestarter). I've installed Avast and it seems to be working. I'll test it a little more and report back. By the way, is there an Avast GUI that you can recommend?

---

### Post by the.phantom on 2007-05-19
> **gobbles414 said:**
> Thanks Phantom! I passed all of the Shields Up scans with full stealth (thanks to Firestarter). I've installed Avast and it seems to be working. I'll test it a little more and report back. By the way, is there an Avast GUI that you can recommend?

[http://ubuntuforums.org/showthread.php?t=229128&highlight=avast](http://ubuntuforums.org/showthread.php?t=229128&highlight=avast)

should do it for you
or you can start it with 

gksudo avastgui

in the terminal ;-D

---

### Post by gobbles414 on 2007-05-27
Sorry for taking so long to get back to this thread. Work has been keeping me very busy. Anyway, I have been experimenting with Avast for about a week now and I am very pleased! I only have two questions left for you:

(1) At least in gksudo avastgui, a THOROUGH/TEST ARCHIVES scan of my ENTIRE SYSTEM results in scanning errors. I am given a list of items that could not be scanned. The reasons given in the report are either "no such device" or "permission denied". Do you have any ideas about this?

(2) How do I setup and/or confirm email scanning between Avast and Thunderbird. My email provider does not allow for the sending of so called false positive virus test files.

Thanks again for all of your help.

---

