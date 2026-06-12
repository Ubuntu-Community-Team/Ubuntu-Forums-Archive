---
title: "wine has disappeared from my 14.04 and when i try to install it says..."
date: 2014-12-19
forum: General Help
---

### Post by shantiq on 2014-12-19
```
 sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

but when i use fix broken packages from synaptic it says it cannot

really puzzled here. what is possibly going on?

this what my synaptic looks like [ATTACH=CONFIG]258690[/ATTACH] and i have now also removed all wine from  software-properties-gtk and /var/cache/apt/archives


really puzzled here. what is going on?

---

### Post by shantiq on 2014-12-20
anyone?

---

### Post by carl4926 on 2014-12-20
Reload the sources in synaptic
In synaptic > fix broken packages

---

### Post by shantiq on 2014-12-20
thanx carl but i have done this and this is what happens.   Which packages? What is is talking about?

[IMG]http://s20.postimg.org/hudfv2cgt/wine.png[/IMG]

---

### Post by carl4926 on 2014-12-20
What happens if you run

```
sudo apt-get install -f
```

---

### Post by carl4926 on 2014-12-20
also see
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

### Post by shantiq on 2014-12-20
thanx carl again

> shantiq@shantiq-00000000000000000000000:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.





also picked main server from software center AND disabled PPA     same result


puzzling!

---

### Post by carl4926 on 2014-12-20
It's odd
I'm not experiencing any issues myself so everything seems to be OK

Maybe someone else has some ideas

---

### Post by shantiq on 2014-12-20
yes weird    trying to install from [source]("http://sourceforge.net/projects/wine/files/") now   see if that flies

---

### Post by Yellow Pasque on 2014-12-20
Are you using 32-bit or 64-bit? If you're using 64-bit Ubuntu, then the package you want is probably wine1.6:i386  (unless you really want to run 64-bit Windows programs). Synaptic doesn't show every possible package when it comes to multiarch, so you may need to get creative sometimes...

---

### Post by shantiq on 2014-12-20
thanx guys for input     i think the entire package manager   had had a complete meltdown   for reasons i cannot fathom    so i took the plunge and re-installed 14.04
one of those things       MARKED AS SOLVED    although will forever be a mystery ::]]

---

