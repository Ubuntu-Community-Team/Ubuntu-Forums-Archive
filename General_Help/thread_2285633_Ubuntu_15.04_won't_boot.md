---
title: "Ubuntu 15.04 won't boot ?"
date: 2015-07-07
forum: General Help
---

### Post by alex317 on 2015-07-07
Hello everybody,i have a major problem,hopefully you guys can help me.
So last night i tried changing my account username using usermod -l but i changed it back (that's not the problem).
the problem is that after that,i got into a login loop and while trying to solve that i caused another problem.
So,the problem is that i can't get a GUI all i see is this (see photo) flickering,and that's it.
I don't know what could have possibly caused it but i need help.
[IMG]http://i60.tinypic.com/11kcvfm.jpg[/IMG]

---

### Post by alex317 on 2015-07-07
I can run recovery mode and use the command line from there,but i have no ideea what should i do right now. Any answer is welcomed.

---

### Post by oldfred on 2015-07-07
Please attach screen shots not post in line. Not everyone has high speed INTERNET.
If you use advanced editor you can use paperclip icon to easily add screen shots.

First try regular updates, but probably related to video. 
What video card/chip? 
Did you install proprietary graphics if nVidia or AMD?
Have you tried nomodeset if nVidia or AMD.


 #houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get autoremove
# fix Broken packages -f 
apt-get -f install
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
dpkg --configure -a

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

