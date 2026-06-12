---
title: "Please help me recover passphrase to mount home folder in liveusb."
date: 2019-03-14
forum: General Help
---

### Post by usernamoi on 2019-03-14
I still have my username and password, but not the passphrase that ubuntu-studio 16.04 created after installing the os (ie in a backup file). 

Im unable to reach login screen or use safe mode, or any alternate kernel, so currently my only option is to try to fix things or at least create a backup from a liveusb.

---

### Post by TheFu on 2019-03-14
<soapbox>

Whenever using encryption, excellent backups are the primary method of recovery. 

Any corruption due to physical or logical issues really doesn't provide any opportunity for correction after-the-fact.  Backups must occur BEFORE they are needed.  Testing of those backups to ensure that recovery is actually possible is at least as important as the backups themselves.  We see people with corrupted backups in these forums all the time. They did the backups, sometimes for years, but never check that they could restore. All that effort, zero results.

Whenever a Unix system makes a point to tell you to save something, it is a really good idea to do it.

Without the passphrase, I have doubts you'll be able to recover anything.  I stopped using encrypted HOME directories for a few different reasons, being able to have fast, efficient, backups was the primary reason.  HOME directory encryption has been removed from 18.04 and later for a number of issues.
</soapbox>

What have you tried already?
* [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Automatically) - use the same version of the OS as installed. There is a "Live CD method" just below where the link goes. All need the passphrase, I think.
* [https://ubuntuforums.org/showthread.php?t=1534704](https://ubuntuforums.org/showthread.php?t=1534704) - sometimes seeing how others worked through it is helpful.
* [http://www.linux-mag.com/id/7568/](http://www.linux-mag.com/id/7568/)
* [https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](https://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/) a pretty article

Better help comes with clear descriptions, commands shown with output shown in a readable (use code tags) way.

---

### Post by usernamoi on 2019-03-15
Thanks. Yes, but it asks me the passphrase, which i dont have. i think i forgot to write it somewhere (i have been able to find a file with instructions to unwrap the passphrase, but i think I forgot to actually do it and is unlikely i wrote it in paper :/ ).

So, my current approach is either this (find another way to find and recover the passphrase from liveusb), or changing something to tell the os to try to boot directly with a different kernel to one that somehow became duplicated and that stops me from reaching the login screen (i tried to reinstall it, but something went wrong and i cant choose other kernels or safe made in grub). This option would be great too, because even if i had to reinstall everything, i could recover my files and settings. 

Another great option would be to be able to start a tty even without desktop environment to be able to use my user login and password, so from there i could try to "unwrap" my login passphrase, and then use it from a liveusb to recover things. i think that should be possible if i could edit and remove instructions to launch with the current kernel and tell the system to boot with a different one, and in safe mode, so maybe chances or reaching login screen, or at least be able to use the command line should be possible.

AFAIK the files aret corrupt, so as log as theres a way to mount the directory i should be able to recover things. So, if you know how i could do any of those things, you would help me a lot.

---

