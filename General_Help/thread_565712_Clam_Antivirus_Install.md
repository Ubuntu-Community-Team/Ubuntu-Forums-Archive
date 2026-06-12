---
title: "Clam Antivirus Install"
date: 2007-10-02
forum: General Help
---

### Post by measekite on 2007-10-02
[COLOR=Black]Is this the method to install Clam AV on a [COLOR=Red]**desktop installation of Feisty**[/COLOR]?[/COLOR]


ClamAV AntiVirus Server
        Read #General Notes 
     &#8226;
        Read #How to add extra repositories 
     &#8226;
        Although viruses and spyware are less common in Linux systems, they do exist. Furthermore, 
     &#8226;
        many users share files with Windows users, either on their own computer or on LANs. ClamAV is 
        useful for checking these files. 
        Install ClamAV AntiVirus Server: 
     &#8226;
```
sudo apt-get install clamav
```If you get errors, try running the command again 
 [edit]

How to update virus definitions

        Virus definition updates are provided by the clamav*freshclam module, which is installed as part 
     &#8226;
        of clamav.

---

### Post by santiagoward2000 on 2007-10-02
ClamAV is already in Feisty's Repository. You should do:
sudo apt-get install clamtk
that's ClamAV and a GUI for it.

---

### Post by measekite on 2007-10-02
> **santiagoward2000 said:**
> ClamAV is already in Feisty's Repository. You should do:
sudo apt-get install clamtk
that's ClamAV and a GUI for it.

Thank you,

Do you or anybody else reading this post thing that clamAV is better or at least as good as AVG Antivirus.  They also have a free version.

---

### Post by Dark Hornet on 2007-10-02
Everything that I have heard says that it is better than AVG, and IMO, I think its better. :)

---

### Post by santiagoward2000 on 2007-10-02
I also think ClamAV is better, but I have no numbers to tell you. It is way lighter. Anyway, Virus in Linux are really rare, so they are not of much use (unless you share your files with a Windows PC or partition).

---

### Post by ramjet_1953 on 2007-10-03
Unless you are running Windows programs under Wine, or are forwarding emails with executable attachments to Windows users, you don't really need it.

Even with forwarding emails these days, most email providers scan emails and attachments for viruses, anyway.

With most Linux installs, installing an anti-virus package is just something that takes up HDD space and gives you no real benefit.

Regards,
Roger :cool:

---

