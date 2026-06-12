---
title: "Install texlive-full failed"
date: 2015-02-05
forum: General Help
---

### Post by lidengdeng on 2015-02-05
Hi all,

My installation of texlive-full meets an error like:

--------------------------------------------------------------------------------------------------
$ sudo apt-get -f install texlive-full 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 texlive-full : Depends: tex4ht (>= 20051214) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
---------------------------------------------------------------------------------------------------

According to the clue, i tried to install tex4ht with command sudo apt-get install tex4ht, which returns similar error:
--------------------------------------------------------------------------------------
The following packages have unmet dependencies:
 tex4ht : Depends: tex4ht-common (= 20090611-1.1) but 20090611-1.1build1 is to be installed
E: Unable to correct problems, you have held broken packages.
--------------------------------------------------------------------------------------

Then again, I tried to install tex4ht by running sudo apt-get install tex4ht-common, which goes without any error.

Even so, the above errors repeat to run "sudo apt-get install tex4ht" and "sudo apt-get install texlive-full".

Any help,

Thanks,

---

### Post by lidengdeng on 2015-02-06
Solved. 

This is done by using this install package [http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz](http://mirror.ctan.org/systems/texlive/tlnet/install-tl-unx.tar.gz) , following the instructions from [https://www.tug.org/texlive/acquire-netinstall.html](https://www.tug.org/texlive/acquire-netinstall.html)

---

