---
title: "Can't launch Synaptic or Dropbox"
date: 2018-11-21
forum: General Help
---

### Post by George_Weischadle on 2018-11-21
Running 16.04 LTS on a new computer that I just switched over to.  I'm not able to launch Dropbox or Synaptic.  No error messages, the launch icons simply flash, then time out after a few seconds.  Any help will be appreciated.

George

---

### Post by oldos2er on 2018-11-21
Can you copy and paste any text output when running ```
pkexec synaptic
``` in a terminal?

---

### Post by George_Weischadle on 2018-11-23
Sorry for this late response due to the Holiday.  Entering that command via terminal window produced no text output but _did_ launch synaptic.

---

### Post by Frogs Hair on 2018-11-23
Let's see the output of the following commands.

```
lsb_release -a 
``` ```
echo $XDG_CURRENT_DESKTOP
```

---

### Post by George_Weischadle on 2018-11-23
Trying ... so far am unable to copy/paste the Terminal output string to my email app.

---

### Post by Frogs Hair on 2018-11-23
Just paste into the reply window , no need for email.

---

### Post by George_Weischadle on 2018-11-23
Here you go:

```
$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:printing-9.20160110ubuntu0.2-amd64:printing-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

[INDENT]echo $XDG_CURRENT_DESKTOP
[/INDENT]

UNITY
```

---

### Post by Frogs Hair on 2018-11-23
Is your system fully up to date since installing ?

---

### Post by George_Weischadle on 2018-11-23
YESSS!!  That was it!  I had unchecked some of the repo update boxes thinking those might let in unnecessary stuff that could interfere with operation.  But I checked them again, and all is good - even after a power recycle.  I'm a happy camper.  Thanks very much!

---

