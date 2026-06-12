---
title: "Upgrade OpenOffice.org"
date: 2007-04-26
forum: General Help
---

### Post by liberalist on 2007-04-26
This is probably a very stupid question, but how can I update OpenOffice.org 2.0 to the latest 2.x version available on [http://www.openoffice.org/](http://www.openoffice.org/) ? I understand I have to download the latest 2.x release, unpack the archive. Then I have to delete RPM's (what does that mean?) that are not applicable for my distribution of Linux. Could you please tell me which RPM's to delete? 

After deleting those files I need to type in the Konsole (Terminal) the following line:
```
rpm -Uvih *rpm
```

Is this correct? 

I am using Kubuntu 6.06.1 LTS (Dapper Drake). Thank you very much in advance.

---

### Post by Hagar Delest on 2007-04-26
Not at all.

See this thread : [ HOWTO: Install OpenOffice.org 2.2 on Ubuntu 6.10]("http://ubuntuforums.org/showthread.php?t=398074")
Or this one : [http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370](http://www.oooforum.org/forum/viewtopic.phtml?p=194370#194370).

---

### Post by zvacet on 2007-04-26
Go for Hagar de l'Est advice.In the future if you want to install rpm package you need to install **alien**.It is in synaptic and that package convert rpm to deb.Command is

```
sudo alien package_name.rpm
```

---

### Post by liberalist on 2007-04-27
Thank you all for your kind help. 

> **zvacet said:**
> Go for Hagar de l'Est advice.In the future if you want to install rpm package you need to install **alien**.It is in synaptic and that package convert rpm to deb.Command is

```
sudo alien package_name.rpm
```

Where can I find synaptic in Kubuntu 6.06.1? Thanks for your advice anyway.

---

### Post by Hagar Delest on 2007-04-27
For KDE (Kubuntu), it should be Adept. See your distro documentation.

---

