---
title: "Ubuntu Anti Virus"
date: 2007-02-27
forum: General Help
---

### Post by zunacai on 2007-02-27
We are going to migrate from Windows XP Proffessional to Ubuntu 6.10, about 1500 workstations. 

We need to find out wether an anti-virus is needed, if so, what does Ubuntu recommend?

I know Ubuntu partnered up with Panda Software and back in they day DesktopSecure was in the Ubuntu repos (no longer I guess) 

Tips are truly appreciated.

Thanks

---

### Post by floke on 2007-02-27
(1) Nope (not really - especially if you only use the official repos)
(2) Clamav - from the repos (Klamav offers a GUI for it)

---

### Post by Arup on 2007-02-27
If you deal with windows executables and lots of attachments, anti virus is a good idea for not spreading virus, your Ubuntu can't get infected but the attachments can infect other windows users. Avast makes very good and free Linux AV as well.

---

### Post by arkangel on 2007-02-27
this topic was discussed  many times before , in short:
-the anti virus in Linux are to catch some viruses that travel from one WIntendo user to another , (email and other services for example).
- The number of virus for linux is really small ,(can be counted with your hand and all of them are academic relics ). I never read or heard  of a linux user infected with any virus. here we have a lab  with 200 suse or sun workstations , our users  have acces to 2 altix supercomputers and a linux cluster ,  I have installed ubuntu on my laptop and we use fedora in our desktops , and we dont know what a virus is (the email serves uses it for  the reason explained before , - i wouldnt  install an antivirus on  my comp because it might slow down the  system )


So that is one of the advantages of using  Linux :)

---

### Post by az on 2007-02-27
> **zunacai said:**
> We are going to migrate from Windows XP Proffessional to Ubuntu 6.10, about 1500 workstations. 

Excellent.  That's an impressive number.  There are many support options available to you,  you know.  

> **zunacai said:**
> 
We need to find out wether an anti-virus is needed, if so, what does Ubuntu recommend?

There is no one person or company that can tell you what "Ubuntu' recommends.  It depends on your needs.

Your workstations will not be vulnerable to windows viruses.  They will be susceptible to other vulnerabilities, though, for which the best practice is to keep up to date with the software updates and not install and run software from third-parties unless you know what they do and have a security infrastructure in place (they can get audited and updated when needed)

If you are running a mail server and will be serving documents to windows machines, it is advisable to install a windows-virus scanner, such as clamav or any other application of your choice on that server.

As you would pay for support and security for 1500 windows workstations (on top of the licencing fees), you should have people that tend to those areas for your Ubuntu workstations.

> **zunacai said:**
> 
I know Ubuntu partnered up with Panda Software and back in they day DesktopSecure was in the Ubuntu repos (no longer I guess) 


I think DEsktopSecure is still in the Dapper-commercial repository.  That version is only a 30-day trial anyway.

Which makes me remember to tell you to run Dapper, the LTS version of Ubuntu, and not Edgy.  Dapper is much better suited for a workstation since it is more stable and is a Long Term Support release.

---

### Post by aysiu on 2007-02-27
Read this:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

