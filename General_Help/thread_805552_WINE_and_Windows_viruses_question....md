---
title: "WINE and Windows viruses question..."
date: 2008-05-24
forum: General Help
---

### Post by kelinu on 2008-05-24
if I had to install WIne on my Ubuntu, would my Ubuntu be vulnerable to viruses for windows? Will my linux get infected? Also, I have my hardrive partitioned for dualboot with Ubuntu and WIndows...so if a windows virus had to be run on linux with wine...would it also infect my windows partition too?

Thanks

---

### Post by werries on 2008-05-24
no it cannot infect linux. 
really the virus couldnt get out of wine even if it knew how to. in linux, editing system and application files requires the password, nothing is just open access.
so you're pretty safe. it wouldnt even know how to handle the linux file structure.
definitely cant infect anything unless you take a virus and put it on your windows partition yourself.

---

### Post by nowshining on 2008-05-24
quite frankly,

yes, but only ur /home and nothing else & the same with spyware/viruses,etcc unless u run as root. As long as u do that then don't worry, if ur so worried u can use a virtual machine to run a copy of windows that way it won't infect ur linux /home.

Try virtualbox for a virtual machine.

Alas altho many would a ton most likely wouldn't run right in WINE and the only thing u'll have to do is remove the .wine folder in ur /home folder and create a new or clean it out.

---

### Post by snkiz on 2008-05-24
Windows viruses can not infect your linux filesystem and they are less efective in wine because of its bottle structure. There are about 900 or so viruses out for linux most of them are harmless or limited by the linux permission system, some even come with an uninstall script. Avg is a good anti-virus its in the repos it can scan your windows partition and wine. what you should be worried about is the new generation of cross-platform infections using macros, and java and things like that. Even those however will be limited by your user permissions. I would post sources but I can't from my phone, all of this info I've found by google linux viruses and wikipedia.

---

