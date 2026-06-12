---
title: "Problem with Personal Repositories"
date: 2006-11-15
forum: General Help
---

### Post by zetetic on 2006-11-15
In order to avoid entering the so called "dpkg hell", I have created a personal repository, following the instructions contained here: [https://help.ubuntu.com/community/PersonalRepositories](https://help.ubuntu.com/community/PersonalRepositories)

This is a simple yet very efective way of resolving dependencies (both on install and when removing) of the debian packages downloaded from the web (I mean .debs not in the repositories).

After creating the personal repository I can install and remove .deb packages donwloaded from the web using "aptitude install" and "aptitude remove" (or "aptitude purge", and thus, correct me if I'm wrong, resolving dependencies both on installation and on removing packages.

It seems the method is working quite well, but there is a problem:

Whenever I put a new deb in the "mydebs" directory (/usr/local/mydebs), I should run the commmand <sudo update-mydebs>, in order to execute the script (named update-mydebs) created in the following directory: "/home/myname/bin".

But when I enter that command I get the following error: "sudo: update-mydebs: command not found"

But if I, instead, enter the command <sudo -s update-mydebs>, I get another king of error: "/bin/bash: update-mydebs: No such file or directory".

So, I only can execute the script if I introduce the path to it, entering the following command: <sudo ~/bin/update-mydebs>

So it seems there's something worng with the PATH.

How can I execute the command without needing to introduce the PATH to the script, as showed on the above mencioned link?

PS:
Yes, my "~/.bash_profile" has this line: <PATH=~/bin:"${PATH}">
But I think that by using <sudo update-mydebs> I'm running that command as root, and therefore I think the PATH contained in ~/.bash_profile" can't solve the problem.

---

