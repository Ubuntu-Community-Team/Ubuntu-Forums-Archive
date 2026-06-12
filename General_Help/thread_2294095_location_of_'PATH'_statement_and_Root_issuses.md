---
title: "location of 'PATH' statement and Root issuses"
date: 2015-09-09
forum: General Help
---

### Post by Tony_P_Shaw on 2015-09-09
Hello to one and all,
I have a couple of questions to ask :

1) where do I find the 'PATH' statement as I have tried to set up libgdx and it says that my JAVA-HOME needs changing (I did have Java 7 installed but upgraded it to version 8) and how do I change/edit that bit as a non-Root user

2) Is it possible to log-in as a Root user in Kubuntu 14.04 as I would like not to have to keep typing in my root password when installing/un-installing/upgrading software. Yes I know that logging-in as a Root user can (I repeated Can) be dangerous, but as I am the only one who uses and sets up my computer then if anything does go wrong with the box of tricks then it is only me who has to put it right again.

Thank you for any help you can offer.

Tony P Shaw

---

### Post by TheFu on 2015-09-09
2) root is against forum rules (see the sticky post in the security forum), plus running as root is a security risk. Running a GUI as root is a good way to be hacked.  Why not just set the sudo timeout to be longer or use ```
sudo -i
``` to get a terminal with interactive root for those times when you need it longer?  The sudoers manpage is fairly complete.  Also - if you are installing lots of software, I'd create a script - so it is faster next time.  And if you are doing this on more than 3 machines, I'd use ansible.

Lots of options, when you know they exist.

1) any environment variable is set per-userid. There are many different places, but most of the time, the ~/.bashrc is where you want.  ```
export PATH=$PATH:$HOME/bin
```

---

