---
title: "Questions about apt-... command"
date: 2007-11-05
forum: General Help
---

### Post by VictorR on 2007-11-05
**apt-cache search <model>** searches for the given model in all available sources.
Question 1. Can I search amongst installed only packages? What command does this?

**apt-cache show <package>** shows some info about the package.
Question 2. Assuming I am looking for an application, how can I find the command, which actually launches this application. I mean the shell command again. Sometimes a package might be installed, but the launcher was not put into the menu.

Thanks in advance.

---

### Post by mali2297 on 2007-11-05
> **VictorR said:**
> **apt-cache search <model>** searches for the given model in all available sources.
Question 1. Can I search amongst installed only packages? What command does this?


Try
```

dpkg --list | grep keyword

```
The first part lists all  installed packages. The output is then piped to grep which print lines containing the keyword.

> 
**apt-cache show <package>** shows some info about the package.
Question 2. Assuming I am looking for an application, how can I find the command, which actually launches this application. I mean the shell command again. Sometimes a package might be installed, but the launcher was not put into the menu.


There might be a better alternative, but you can try
```

apropos keyword

```
It will list all commands that have the keyword in their description.

---

### Post by geirha on 2007-11-05
> **VictorR said:**
> 
**apt-cache show <package>** shows some info about the package.
Question 2. Assuming I am looking for an application, how can I find the command, which actually launches this application. I mean the shell command again. Sometimes a package might be installed, but the launcher was not put into the menu.


**dpkg -L package-name** will list all files installed by the package. The runnable files are typically located in /usr/bin/

---

### Post by VictorR on 2007-11-05
That was very helpful.

Thank you.

---

