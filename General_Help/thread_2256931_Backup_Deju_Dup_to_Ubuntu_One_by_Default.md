---
title: "Backup Deju Dup to Ubuntu One by Default?"
date: 2014-12-15
forum: General Help
---

### Post by ksanger on 2014-12-15
Is anyone else concerned that backups are enabled and Ubuntu One is selected as the location?  

Does anyone know where this backup was actually being sent as Ubuntu One is dead?

I really do not want files being sent out from my pc without my permision.  How can I prevent this?

I always did my own backups and was surprised to find this application turned on.  Even more surprised that it was set to send data through deja-dup to Ubuntu One.  Even if its supposedly encrypted.  

Lastly I never signed up for an ubuntu one account.  Why didn't this application generate an error message?  Is this application legitimate?

Is signing up for the Ubuntu Forum the same as signing up for Ubuntu One?

---

### Post by deadflowr on 2014-12-15
1)I can't remember if backups were actually ever enabled on 12.04.
2)Even If UbuntuOne the file service was shutdown, 12.04 still has an Ubuntu One folder inside the Home Folder, it's possible that the backups would go there.
3)The Backup program has an off switch, that is easy to understand.
4)If for some reason backups were enabled and set to backup to Ubuntu One, I would look in you Ubuntu One folder, since that's were the backups would probably go, The Ubuntu file-sharing servers are completely gone now. Wiped.

And 5) Ubuntu One is no longer a file sharing service and instead is Ubuntu's sign-in service. From UbuntOne's defunct page it reads:
> Ubuntu One is the single account you use to log in to all services and sites related to Ubuntu. For more information please read the [Ubuntu One FAQ]("https://login.ubuntu.com/+faq").

You would use this to log into various pages such as the forums, or wikiubuntu, or what have you. Also if you purchase software through the Ubuntu Software Center, the account you have created can be used for that.

Hope something in here helps.

Also, sidenote, the unfortunate loss of Ubuntu One has left users of Ubuntu 12.04 with the leftover cruft and so you would need to remove any Ubuntu One packages yourself.

---

### Post by ksanger on 2014-12-16
Thank you for an excellent answer:

> **deadflowr said:**
> 1)I can't remember if backups were actually ever enabled on 12.04.
2)Even If UbuntuOne the file service was shutdown, 12.04 still has an Ubuntu One folder inside the Home Folder, it's possible that the backups would go there.
3)The Backup program has an off switch, that is easy to understand.
4)If for some reason backups were enabled and set to backup to Ubuntu One, I would look in you Ubuntu One folder, since that's were the backups would probably go, The Ubuntu file-sharing servers are completely gone now. Wiped.

And 5) Ubuntu One is no longer a file sharing service and instead is Ubuntu's sign-in service. From UbuntOne's defunct page it reads:


You would use this to log into various pages such as the forums, or wikiubuntu, or what have you. Also if you purchase software through the Ubuntu Software Center, the account you have created can be used for that.

Hope something in here helps.

Also, sidenote, the unfortunate loss of Ubuntu One has left users of Ubuntu 12.04 with the leftover cruft and so you would need to remove any Ubuntu One packages yourself.

-  I have an Ubuntu One folder link under my Home directory with no files in it.  There is also a .local/share/ubuntuone folder containing shares which is empty and syncdaemon.  Under syncdaemon there is a tritcask folder with a .data file in it.  Renaming the .local/share/ubuntuone folder resulted in a new folder being created after rebooting.  Why I needed to reboot is another issue.

-  Yesterday when I logged in it stated that my launchpad account name/password should work though it did not.  So I reset my password, which I believe became an Ubuntu One account?  Were launchpad credentials used for Ubuntu One without us knowing?

-  If we have never purchased packages through software center, and did not knowingly sign up nor use Ubuntu One share drives, what other packages might we have to remove?

Hard drives are no longer expensive, and if I ever needed to access something from outside of my home network I would do so through my own website.  So I have no need nor desire nor would I ever willingly use cloud services.

---

### Post by deadflowr on 2014-12-16
Too many questions, so I'll stick with what i know.
You can do a quick package search in the software center for anything related to ubuntuone and remove them, or run
```
dpkg -l | grep ubuntuone
```
note the name of the packages listed, and look at removing them.
It took me a while to find, but this is what I did a long time ago to remove
```
sudo apt-get -s purge python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol ubuntuone-couch  
```
the above will run a simulated command, and not actually remove anything, but it shows you what would be removed. It's good to run when removing packages, so that you can review it and see if it'll remove anything wrongly. Thus avoid breakages.
After you've looked it over and feel confident that nothing needed will be removed by accident, simply re-run the command removing the -s option.

---

### Post by ksanger on 2014-12-16
Thank you; 

I've also found I had rhythmbox-ubuntuone and ubuntuone-installer
removing them also removed unity-scope-musicstores
I assume I will not need that either.

---

### Post by deadflowr on 2014-12-17
> **ksanger said:**
> Thank you; 

I've also found I had rhythmbox-ubuntuone and ubuntuone-installer
removing them also removed unity-scope-musicstores
I assume I will not need that either.

Being that I removed it myself, and have never noticed anything wrong since. I would assume it's fine to remove.:p
FWIW here's the Description for what it is
> Description-en: Store music lens for unity
 This package contains the store scope for the "music" lens
 which can be used into Unity to preview and buy online
 media files.

Might be of importance to some, but not me.

---

