---
title: "Cant install Envy"
date: 2007-04-08
forum: General Help
---

### Post by Petester on 2007-04-08
I just downloaded Envy 0.9.1 for Edgy but then it says 
Error: Dependency is not satisfiable: module-assistant

I dont know what happened. Cna someone help me fix it? THanks

---

### Post by Maestro23 on 2007-04-08
> **Petester said:**
> I just downloaded Envy 0.9.1 for Edgy but then it says 
Error: Dependency is not satisfiable: module-assistant

I dont know what happened. Cna someone help me fix it? THanks

You need to install "module-assistant" first

> sudo aptitude install module-assistant

*Anytime you are installing something and it tells you it has a dependency error, you need to install that package first.

*EDIT: As kodoku stated, make sure all your repo's are enabled it you don't find it on the first search.

Some links that will help you down the road:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

Community Docs: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)


Welcome and Good luck.

---

### Post by kodoku on 2007-04-08
Its actually a source problem.

You have to enable all of your repos (I think module-assistant is in the multiverse repo)

Applications -> System -> Administration -> Software Sources (and check everything)

When you do that, you should be given the option to reload all software sources, and do it.

Then try running the Envy deb again, it should be able to satisfy the dependencies afterwards

---

### Post by Petester on 2007-04-09
So all i need is to check all "repo"'s? THanks a lot

Would you mind me asking something - what are repos?

---

### Post by lukew on 2007-04-09
> **Petester said:**
> So all i need is to check all "repo"'s? THanks a lot

Would you mind me asking something - what are repos?

Thats servers with software on them. Because everything is free(opensource) all software can be grouped together on a few servers for our convenience. 

/etc/apt/sources.list has a list of URL type sources or repositories. 

You can install any software contained with anyone of these repos from one command.

```
sudo apt-get install software-module-name

```


Any Bill tells us that linux is harder than windows ;)

Luke

---

### Post by Petester on 2007-04-09
Thanks a lot, I got Envy installed now.

---

