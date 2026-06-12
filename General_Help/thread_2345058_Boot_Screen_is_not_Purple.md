---
title: "Boot Screen is not Purple"
date: 2016-11-30
forum: General Help
---

### Post by meetdilip on 2016-11-30
I used to have Gnome and Cinnamon on my laptop. Maybe because of  that, the boot screen has changed to a black one than default Purple  boot screen. I have since then upgraded to 16.04 from 14.04 and  everything was good. 

But recently, I am facing frequent boot failure. The boot screen  flashes, goes transparent and shows some terminal like activities in the  background. In the end, mostly it will say some process failed and I  never get to the GUI.

  
This is happening so frequently that I am not able to use my PC at  all. Will replacing black boot screen with Purple solve this problem ?  If no, kindly suggest a solution for the same. Thanks.

PS: I now use Unity alone with 16.04

---

### Post by meetdilip on 2016-12-02
Can someone help ? I get a lot of between the boot failures.

---

### Post by vasa1 on 2016-12-02
> **meetdilip said:**
> ... Will replacing black boot screen with Purple solve this problem ?  If no, kindly suggest a solution for the same. Thanks.

PS: I now use Unity alone with 16.04
From some of your other posts, I gather you've tried Cinnamon, GNOME, and Unity and upgraded from 14.04 to 16.04. It's possible that some incompatibility has crept in. While it maybe possible to hunt down the cause, I feel it maybe quicker to back up your personal data and do a clean install of whichever flavor you want. Mixing of desktop environments *could* cause problems.

---

### Post by meetdilip on 2016-12-02
Thanks @Vasa1

My main concern are the email IDs in Thunderbird. Their logins and already downloaded email. Is there any reliable guide to take backup Thunderbird and bring all those back after reinstall of 16.04 ?

---

### Post by vasa1 on 2016-12-02
> **meetdilip said:**
> Thanks @Vasa1

My main concern are the email IDs in Thunderbird. Their logins and already downloaded email. Is there any reliable guide to take backup Thunderbird and bring all those back after reinstall of 16.04 ?

I'm sorry, but I have no idea about Thunderbird. I would imagine there's some sort of sync like Firefox has but I'm just guessing.

But if you search for "backing up Thunderbird data", you may find out how. Here's one:
[https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer](https://support.mozilla.org/en-US/kb/moving-thunderbird-data-to-a-new-computer)

---

### Post by oldos2er on 2016-12-02
Thunderbird keeps all its email data in /home/user/.thunderbird/

---

### Post by meetdilip on 2016-12-06
Thanks for the help @vasa1 , @oldos2er

---

### Post by oldfred on 2016-12-06
For both Firefox & Thunderbird, I backup the profiles and restore them to other computers. I have to load each once to create new profile, then edit profile.ini from new one to the one I restore from my backup.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

You may also want to export a list of installed applications to make it easier to reinstall all your apps. And all the settings for those apps are in /home, so backup all of /home, not just Thunderbird & Firefox.

       discussion of alternatives/strategy backups
[URL="https://help.ubuntu.com/community/BackupYourSystem"]https://help.ubuntu.com/community/BackupYourSystem
[/URL]
 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) 

[URL="https://help.ubuntu.com/community/BackupYourSystem"]
[/URL]

---

