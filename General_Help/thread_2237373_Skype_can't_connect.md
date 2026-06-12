---
title: "Skype can't connect"
date: 2014-08-01
forum: General Help
---

### Post by Canaryguy on 2014-08-01
Hello,
I'm trying to log in into Skype but I get the message "Skype can't connect" in Ubuntu 14.04 x32. I have logged in using Windows and Android and everything is fine. Skype was also working fine this morning. Anyone having the same problem?

---

### Post by Todor_Bobev on 2014-08-01
I had the same problem, but downloaded skype from their site again (seems to be updated a little) and it now works fine. I am on 12.04 lts if that has any difference.

---

### Post by Canaryguy on 2014-08-01
Thank you Todor_Bobev. I had forgotten that option. I had installed Skype through the Terminal: sudo apt-get install skype

But I downloaded the .deb file from the Skype website and I installed it. Now I can log in.

---

### Post by Todor_Bobev on 2014-08-01
You are welcome, enjoy!

---

### Post by sergius248 on 2014-08-01
Thanks, I had he same problem.
I am using Trusty Thur 10.04 (64 bit)  with Mate 1.8.0 environment.
I have tried to erase the /.Skype folder as advised somewhere else but did not work. Eventually uninstalled skype using Synaptic Package Manager (although it probably wasn't necessary) and killed the process.
Downloaded the "Debian.7 (multiarch)" distribution .deb package and installed it.
It seems to be working fine now. Still I haven't any clue of why the old package stopped working.

---

### Post by pierreu1 on 2014-08-01
> **Todor_Bobev said:**
> I had the same problem, but downloaded skype from their site again (seems to be updated a little) and it now works fine. I am on 12.04 lts if that has any difference.

Hi,

It worked! But,... 

I had the same problem after years of using Skype with no real issues. I went on the Skype download website to download the 12.04 multiarch version if you are running that U. version, of course. An upgrade did not work; you must uninstall skype using synaptic (just the main Skype package only). Then, proceeded with the download/save and clicking on the .deb package. Automatically Soft. Center will one. Click install, and even the desktop link worked. Fantastic! Thanks!

---

### Post by uzoexcel on 2014-08-01
same here..i just resolved mine now while following the instructions on this link
[http://askubuntu.com/questions/488053/how-to-install-skype-4-3](http://askubuntu.com/questions/488053/how-to-install-skype-4-3)
> **Canaryguy said:**
> Hello,
I'm trying to log in into Skype but I get the message "Skype can't connect" in Ubuntu 14.04 x32. I have logged in using Windows and Android and everything is fine. Skype was also working fine this morning. Anyone having the same problem?

---

### Post by martinr on 2014-08-23
See this thread for: [how to keep using your old Skype version]("http://ubuntuforums.org/showthread.php?t=2240954&p=13105799#post13105799").

---

