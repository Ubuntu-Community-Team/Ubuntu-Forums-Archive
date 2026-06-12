---
title: "All text turned to boxes in Ubuntu 12.10"
date: 2013-09-14
forum: General Help
---

### Post by cluelesswonder on 2013-09-14
Hello!
Yesterday, for no reason I can understand, all of the text on my desktop in 12.10 turned to boxes. Some programs still run and otherwise the desktop looks fine but I can't read anything. Internet browsers and programs like libre office are also not working.
In recovery mode I tried apt-get update the output listed some errors related to security. I don't know what to do. Any suggestions?

---

### Post by grahammechanical on 2013-09-14
This seems to me to be an issue with fonts. Have you installed any kind of "tweak" utility and have you changed the system font? Have you changed the language settings or the keyboard settings.

Regards

---

### Post by cluelesswonder on 2013-09-14
No. I have Japanese installed as well as English but I haven't done anything to change the language or font for any system settings. Changed fonts in libre office but I don't think that would be related. . .?

---

### Post by sbnwl on 2013-09-14
It seems the problem in fonts, or language settings. Could you check by running a guest session/account from the login screen and see if it shows the same problem. If not, then this is the a problem only at your user level, which certainly can be undone safely.

---

### Post by cluelesswonder on 2013-09-14
Thanks for your replies. I'm away from my computer at the moment but the problem starts at the purple Ubuntu screen so I don't think it's just my user level :( I will double check when I get home but any thing else I can do?

---

### Post by cluelesswonder on 2013-09-14
I have been able to check a few things. The boxes seem to be system wide for Ubuntu. Switching users doesn't help. I don't know how to switch language settings in the current state because I can't read anything on the system. The system still recognizes characters but they're unreadable so if anyone has ideas for things i can try within the desktop, I need very detailed locational instructions (ex. check the second line of boxes, select the right most box). . .anyone? :( :(

---

### Post by cluelesswonder on 2013-09-15
I turned on universal access so I could hear the options and made sure the language set to English (Canada) but it didn't solve the problem. When I restarted and got to the purple ubuntu page, the boxes came again. 
I'm really at a loss. I've tried to fix dependencies in recovery mode but it doesn't seem to help. . .
Just before this happened (on Friday) the computer had another problem, when the purple ubuntu page was supposed to come up, it went instead to a black screen, where it seemed to scroll through a series of numbers (something like 1.xxx -26.xxx the x's being numbers) and all were showing something like drdy error. I think from there I restarted and tried to fix dependencies in recovery and ran apt-get update and got the boxes.. . .
But I really can't imagine what triggered everything. As far as I can remember, I haven't updated my computer for at least a week and didn't change anything on the system. Have just been using firefox and libreoffice. . .

---

### Post by cluelesswonder on 2013-09-15
I just ran fact and got the following:

Error reading block 45621284 (attempt to read block from file system resulted in short read) while reading directory block.

/dev/sda7: unexpected inconsistency; run fsck manually. (Without -a or -p options)
Mountall: fsck/[932] terminated with status 4
Mountall: file system has errors: /
Mountall: skipping mounting since Plymouth is not available

?? Could this be related to the problem?

---

### Post by cluelesswonder on 2013-09-16
This problem is ongoing. I've been poking around online trying to find other instances of the same problem. I have found some users with similar problems ([http://ubuntuforums.org/showthread.php?t=1514868](http://ubuntuforums.org/showthread.php?t=1514868), [http://ubuntuforums.org/showthread.php?t=1678246](http://ubuntuforums.org/showthread.php?t=1678246), [http://ubuntuforums.org/showthread.php?t=1551495](http://ubuntuforums.org/showthread.php?t=1551495)) but the solutions are limited to non-existent.
Generally it seems that it is assumed to be a font issue but reinstalling and/or changing font/language settings hasn't solved most people's problems.
I am still open to trying that but can't read anything in my system and am not sure what to try. If I can use BIOS, that would be ideal. I also have access to terminal in the desktop.
In the mean time, I am downloading the 13.04 desktop for re-installation but am hoping I won't have to go that route. . .


It is not hip to be square.

---

### Post by cluelesswonder on 2013-09-16
If I try apt-get upgrade or install in bios I get: 
W: not using locking for read only lock file /var/lib/dog/lock
E:  unable to write to /var/cache/apt ???
Feel like im firing blanks at the sun.

---

### Post by oldos2er on 2013-09-16
Did you run fsck on your partitions? If you're able to run terminal commands, can we see the output of **df -h** ?

---

### Post by cluelesswonder on 2013-09-16
Thanks for the reply. I have run fsck from the BIOS menu a couple of times.
and running df -h in root gives
root@peanut: ~#df -h
df: `/run/user': No such file or directory
Filesystem     Size    Used   Avail   Use%   Mounted on
/dev/sda7     182G   102G   71G    60%     /
udev            1.9G    0        1.9G   0%      /dev
none            741M   776K   740M  1%      /run/shm

---

### Post by oldos2er on 2013-09-17
"df: `/run/user': No such file or directory" seems kind of odd. At this point I'd check the SMART status on the drive, which you'd need to do from a Live DVD or USB if you can't apt-get install anything. See [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by cluelesswonder on 2013-09-18
Thanks again for your suggestions. Apt-get install does work in xterm now and I can still read text there. I've downloaded smart and am running a long test. I'll post the results in a couple hours

---

### Post by cluelesswonder on 2013-09-18
Could there be any connection by way of the fact that when I update system files it returns
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) anything/anything Translation-en_CA  
It seems like an error here could be consistent with the problems I'm having but I'm not sure. If so what can I do?

---

### Post by oldos2er on 2013-09-18
Maybe. Could you copy & paste the entire output from ```
sudo apt-get update
``` here?

---

### Post by cluelesswonder on 2013-09-18
Actually, I managed to fix it!!
I was trying to upgrade to 13.04  in termx and it returned an error and there were dependency issues with libudev1:i386
I restarted my computer and ran apt-get update which repaired the dependency (it installed a number of languages, I noticed) and then tried apt-get upgrade and it's still running the upgrade but the text just magically came back a short way in!
So I guess it's solved?

Thanks so much for your help!

---

### Post by oldos2er on 2013-09-18
You solved it, not me! Glad it's working, and hopefully it'll continue to work.

---

