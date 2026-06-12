---
title: "Installed packages have unmet dependancies Ubuntu 12.10"
date: 2013-01-16
forum: General Help
---

### Post by ccfcexile on 2013-01-16
I turn on my computer and I get a warning symbol at the top right of the screen (red round symbol with a horizontal white line in the middle) I click on this and the message I get is:

An error occurred, please run package manager from the right click menu or apt-get in terminal to see what's wrong.  The error message was: 'Error: BrokenCount>0'. This usually means that your installed packages have unmet dependancies.

Well, I can't use update manager.  It says to disable 3rd party repositories, but I don't know how.  I clicked on details and it said the following:

The following packages have unmet dependencies:
ca-certificates-java: Depends: java6-runtime-headless but it is a virtual package
openjdk-7-jre-lib: Depends: openjdk-7-jre-headless (>= 7~b130~pre0) but it is not installed

what do I do because I can't open software centre or update my OS.
Any help appreciated

---

### Post by ibjsb4 on 2013-01-16
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post using code tags.

[ATTACH]230147[/ATTACH]

Thank you

---

### Post by tgalati4 on 2013-01-16
Close down any update windows.  Open a terminal and post the following:

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mad2-814 on 2013-01-16
If the earlier responses don't help,try
 ```
sudo apt-get -f install
```

or 
```
sudo dpkg --configure -a
```

---

### Post by ccfcexile on 2013-01-16
Thanks to you all, I've been looking at ubuntu for awhile as an alternative to windows and now 3 out of 4 Comps in our house use ubuntu. Thankyou again for the very quick replies

---

