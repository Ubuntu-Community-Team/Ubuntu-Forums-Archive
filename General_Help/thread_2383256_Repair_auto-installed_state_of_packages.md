---
title: "Repair auto-installed state of packages"
date: 2018-01-22
forum: General Help
---

### Post by taatt4 on 2018-01-22
I need to fix package dependencies of a system of which I became administrator.
The former sysadmin has broken many of the auto-installed relationships between packages for apparently no reason.


I want to automate (with a script) the repair process as much as possible.
The idea is to build a list of the installed packages which are dependency (because recommended or dependent/pre-dependent) of another package.
Subsequently, calling [FONT=lucida console]aptitude markauto[/FONT] on every package of the list should bring back the system to a saner configuration.


A command to retrieve the dependent packages is:
```
aptitude search '~i !~M !~E (~Rpredepends:~i | ~Rdepends:~i | ~Rrecommends:~i)'

```

Unfortunately, this doesn't take in account recursive dependencies (e.g. apport Depends python3-apport, but python3-apport recommends apport).
How can I intercept this loop and exclude those packages from the list?




Thanks,
Raffaele.

---

### Post by cruzer001 on 2018-01-22
Hello

What version of Ubuntu are you running?

```
inxi -S
```

The command to fix broken packages:

```
sudo apt -f install
```

I don't know about a script, I usually work things out with apt.

---

