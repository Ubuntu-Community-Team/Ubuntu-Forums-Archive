---
title: "LiveDVD or Pendrive with SDK + VM?"
date: 2013-09-16
forum: General Help
---

### Post by Kamil_Jwiak on 2013-09-16
Hello,

I'm looking for a solution how to present my app developped to WebOS based mobile phone.
Unfortunatelly, it's not possible to send my phone via p-mail (maybe it is but I don't want that ;) ) and attach this device to university files.

I have to build some kind of "emulator".

I was thinking about installing Ubuntu (e.g 10.04 LTS) on my HDD, configuring SDK/PDK, code editor, VirtualBox 3.2 (version 4 is not supported) and preparing desktop with appriopirate shortcuts and folders.
Then, make LiveCD (DVD) of my installed version.

Is it possible to achive my goal in this way?
What do you think about my idea?

Thanks in advance for any suggestions.

Regards,
Kamil

---

### Post by Kirboosy on 2013-09-16
Welcome to the forums! :D

Yes, your idea sounds very well thought out and easy to achieve. I would recommend installing 12.04 LTS and maybe a lighter version, (Like Lubuntu or Xubuntu). Since its a VM it would be faster to use a lower resource environment.

You could use one of the following tools to create the LiveCD
[UCK]("http://sourceforge.net/projects/uck/")
[Live Magic]("https://chris-lamb.co.uk/projects/live-magic")[URL="http://www.remastersys.com/"]
Remastersys[/URL]

If I may ask, why isn't Virtualbox 4 supported?


Hope that helps!
~Caboose

---

### Post by Kamil_Jwiak on 2013-09-16
Thanks for you support. 
I'll take a look at this links.

I don't know why latest VirtualBox releases doesn't work.
Official [Developers Website]("https://developer.palm.com/index.php?option=com_content&view=article&layout=page&id=1661") (point 3) says that VirtualBox 4.0 is not supported.
Some time ago I have updated VirtualBox to current version and virtualized webOS wont start.

I decided to use Ubuntu 10.04 (which use less resources then newest releases with Unity) because I'm not sure about SDK compatibility with Linux kernel 3.X.

---

