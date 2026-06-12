---
title: "Need a Way"
date: 2007-07-26
forum: General Help
---

### Post by MasterXandrex on 2007-07-26
All, 

Here's my situation and limitations:

My work workstation is a Windows XP PC to which I do have administratve rights. My server at home is a standard Ubuntu Linux (:guitar:) server. I need a way to share a directory (possibly a network directory) to my home from my work PC. 

Firstly, needless to say, I probably shouldn't be doing this do I need as low a profile as possible. Currently, I have a server setup and am able to SSH from work into the server. I cannot go the other direction in any way (nor do I really want to create an SSH server on my workstation). Does anyone know a way for me to do this? 

Thanks,

Xan

---

### Post by dando80 on 2007-07-28
Is an ftp server an option here? Or scp using winscp?

---

### Post by tomcheng76 on 2007-07-28
you need port forwarding in your Office Network
which port will forward to your workstation (which means outside will allow to connect to your workstation using  COMPANYIP:PORT)

---

