---
title: "Nvidia Proprietary Drivers on 12.04"
date: 2013-06-09
forum: General Help
---

### Post by nreynolds2121 on 2013-06-09
So I have a Geforce 7900 GS card and everything boots fine with the open source driver including full Unity. However, I wish to take full advantage of the card for gaming, which means i need to use the proprietary drivers which has presented quite the problem. Everytime I try to install any of the drivers listed in jockey I get dumped into the shell at boot. From reading through google I have noticed many people saying the solution is to revert back to an older version of X, which I would like to avoid so that when any new updates occur, im in the loop. i've also read that enabling the nvidia repos will remove Noveau which I want to avoid as it is the only thing working. Does anyone have any advice on this matter, otherwise its back to windows for my gaming, and I have been windows free for at least 7 years.

---

### Post by deadflowr on 2013-06-09
Your card is fully supported by the drivers provided in the repos.
You can look over this
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

You can also try downloading the drivers from nividia
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

This might help solve your problems
[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)


As far as downgrading the Xserver, I've not read that for nvidia, but have for AMD legacy cards.
And adding the nvidia repos shouldn't, by default, remove nouveau. It should only blacklist the open-source drivers, which might be what's going wrong.

---

### Post by nreynolds2121 on 2013-06-09
I tried installing from repos at first, which is when it just dumped me into shell on boot. So after reading in the terminal i ran sudo apt-get purge 'nvidia-*' , which uninstalled all nvidia and allowed ubuntu to boot up again. Now however when I go to additional drivers instead of a list of driver options such as nvidia-current, nvidia-173 and so on its the same amount of options except they all say Nvidia Binary Xorg Driver, Kernel Module and VDAPU Library. When I go select one of them in the description field you can see that its the 173 or the current. I've tried every single one except for the experimental and all of them dump me to shell right when lightdm is about to load. Then I have to do the sudo apt-get purge 'nvidia-*' to go back to open source drivers. P.S. Thank you for your quick reply and help.

---

### Post by sum1nil on 2013-06-10
I installed the newest Nvidia driver they offered from [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)


It will offer to 'blacklist' the Noveau modules in order to work. I just do not think Nvidea and Noveau play well together. 

13.04 does not even offer restricted Nvidea drivers.

---

### Post by nreynolds2121 on 2013-06-10
Hmmm, Didn't really want to try manually installing but if its the only alternative. I just tried blacklisting noveau then reinstalling drivers from the repos in terminal with lightdm stopped, and it still doesn't work.

---

### Post by sum1nil on 2013-06-10
I wonder what 'lsmod' would have said at that point?
Maybe the Noveau module and Nvidea module was there at the same time?

 During the installation of Nvidea's driver, I got the impression it was going to 'aggressively' make sure Noveau would not be loaded.

 I can't remember all it stated, but make sure to record the file changes on paper in case you have to go back to Noveau.


Might be a tad to much competition between those groups.

---

### Post by nreynolds2121 on 2013-06-12
I am going to reinstall the nvidia drivers from the repos and do lsmod to see if their both fighting each other. Just out of curiosity, which the most stable of the nvidia choices, ive heard either 173 or current.

---

### Post by nreynolds2121 on 2013-06-12
Ok, reinstalled Nvida 173, rebooted, as usually Lightdm a no go, did lsmod in shell, Noveau is not loaded, Nvidia is, im stumped.

here is my xorg.log

[http://pastebin.com/ECUxKPVv](http://pastebin.com/ECUxKPVv)

---

