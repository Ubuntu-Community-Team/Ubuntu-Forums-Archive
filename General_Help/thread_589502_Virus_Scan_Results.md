---
title: "Virus Scan Results"
date: 2007-10-24
forum: General Help
---

### Post by tribal_graf on 2007-10-24
Does anyone know what this is? JS.XorCrypt was Detected in virus scan. New to Linux and still Windows paranoid. Any help would be appreciated.

---

### Post by wieman01 on 2007-10-24
> **tribal_graf said:**
> Does anyone know what this is? JS.XorCrypt was Detected in virus scan. New to Linux and still Windows paranoid. Any help would be appreciated.
Is is probably a JavaScript trojan or virus. Don't worry, there is nothing to be afraid of if you are running Linux. Just delete the file. Read these:

[http://librenix.com/?inode=21]("http://librenix.com/?inode=21")
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses]("http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses")
[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/]("http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/")

---

### Post by PmDematagoda on 2007-10-24
Windows viruses are virtually useless on Linux, so you could even open the virus up for examination and you won't be harmed:).

---

### Post by Nunu on 2007-10-24
Also without the software knowing your root password it cant install or extract itself hens the reason why you need to go sudo when installing software or drivers.

---

### Post by mahousaru on 2007-10-24
Double Post!

---

### Post by mahousaru on 2007-10-24
As Linux users we should scan for viruses for one reason and that is because we feel sorry for people using Windows. We might be safe but they have a chance to not be depending on their situation.

Personally for Linux it isn't viruses or spyware that is the concern, but with a poorly maintained system being hacked.  Just keep you system patched, and if you start using server stuff like a web server or ftp server, make sure you know what it means to expose it to the internet.

Just to make sure the above paragraph isn't misrepresented, a poorly maintained Windows box can be hacked too.


*The below is a load of waffle to give you an idea of the various ways you can run stuff to make you feel more secure*

**If you must run something to make you feel safer** then there are programs that check for rootkits, which are tools that hackers use to hide themselves and do ensure they can still access your system.  Two great examples are **chkrootkit** and **rkhunter**.  

You could also make sure that your files have not been altered with **Tripwire**.  

Of course it is far better to make sure you are not compromised in the first place so check yourself for vulnerabilities with something like **Nessus***.  

Or aggressively firewall if start opening up services with **psad**, which will try to detect attack patterns via your network card and will warn you, and it can even be set to block the attack**.  

Ubuntu 7.10 comes with **AppArmor** built in which can effectively sandbox any process so if an attacker manges to break in via something, they should not be able to do anything...

Oh the most important thing which makes you more secure compared to at least XP is how you run as a non-administrator user.

Lots and lots of things you can do, but really on a desktop ubuntu machine the only extra thing I personally would consider is turning on **Firestarter** (firewall) when I take my laptop out of my home network and that is only so I can see if something strange starts knocking on my door.

*I have been told that leaving Nessus installed on a always on resource like a server is frowned upon, because if an attacker compromises it, they can use it to compromise other boxes.  Personally I think if an attacker has rooted your box, then they can easily install it themselves in no time :p

**Be careful about  aggressive actions with firewalls. The bad people can use it to deny your own box!  And no matter how much you are tempted to, never set a box to automatically retaliate against an attacker, as they most probably are spoofing an address and you would attack someone else!

---

