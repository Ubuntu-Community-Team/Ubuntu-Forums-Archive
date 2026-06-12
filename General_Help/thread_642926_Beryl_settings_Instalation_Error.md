---
title: "Beryl settings Instalation Error"
date: 2007-12-17
forum: General Help
---

### Post by BluePlum on 2007-12-17
Heres the Error In termainal:

andrew@Andrew:~$ sudo apt-get install beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl: Depends: beryl-settings but it is not going to be installed
E: Broken packages
andrew@Andrew:~$ 
andrew@Andrew:~$ sudo apt-get install beryl-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  beryl-settings: Depends: beryl-settings-bindings but it is not going to be installed

Any suggestions?

---

### Post by jken146 on 2007-12-17
Which version of Ubuntu are you using?

---

### Post by BluePlum on 2007-12-17
Gusty Gibbon ( 7.10 ).

---

### Post by oldos2er on 2007-12-17
Gutsy comes with Compiz-fusion enabled, as long as your hardware supports it. You might want to install compizconfig-settings-manager too.

---

### Post by Sef on 2007-12-17
Beryl is no longer being maintained.  Best to go with Compiz-Fusion.

> You might want to install compizconfig-settings-manager too.

Get that from applications > add/remove.  Type CCSM in the search box.

---

### Post by BluePlum on 2007-12-18
I just wanted to try out beryl, cant i have them both at the same time? and i have compiz i just want to see which is better.

---

### Post by Sef on 2007-12-18
> I just wanted to try out beryl, cant i have them both at the same time? and i have compiz i just want to see which is better.

Compiz-Fusion is better because people are working on improving it.  The Beryl team is working on plugins for Compiz-Fusion.

---

### Post by danwood76 on 2007-12-18
compiz fusion is the combination of the two projects, you wont be able to have both at the same time.
Compiz fuzion does everything beryl did and more.

---

### Post by BluePlum on 2007-12-18
o its just that My water effects Dont seem to work in compiz so i was gonna see if they worked in bery. But if you say compiz is better ill take your word for it :Dhttp://www.google.com/ig

---

### Post by danwood76 on 2007-12-18
The water effects are working here!

---

### Post by BluePlum on 2007-12-18
Do you no why my arnt working?

---

