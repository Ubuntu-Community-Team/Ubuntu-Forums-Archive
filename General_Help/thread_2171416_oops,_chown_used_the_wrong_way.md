---
title: "oops, chown used the wrong way"
date: 2013-08-30
forum: General Help
---

### Post by creepwood on 2013-08-30
I accidently used sudo chown <username> -R / instead of just everything from the point down. Now pretty much is messed up. some of the stuff was permission denied, but appearntly I messed up quite a bit anyway. I can't even backup my home directory right now.

I'm getting this message when doing sudo
```
sudo: /etc/sudoers is owned by uid 1000, should be 0
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

``` 

What can I do? Atleast I want to repair it enough so that I can backup my home directory.

---

### Post by Impavidus on 2013-08-30
This way the system is messed up so badly that the fastest way to fix it is reinstalling. Usually you should still have access to your home directory, but if you don't, you can try a live disk. That will definitely give you access to everything and allow you to make the backups you need. The live disk is the same as the installation disk, so you'll need is anyway.

---

### Post by oldfred on 2013-08-30
I might try a couple of things, but you will have to reinstall as the settings are not just root but other system owners and it would take forever to fix them all.

I would use live installer to copy /home first

You might just try changing everything to root and then change /home to you, but a lot of things still will not work as neither root nor you are the correct owner.

These are the settings for /home 0 some duplicate as I copied from different places.
 Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/$USER/.dmrc
sudo chown $USER:$USER /home/username  
 sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.



You can try a "dirty" install or where you just overwrite files (no reformat) and keep data. But I would backup first. Probably still have to reset /home.


 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by ajgreeny on 2013-08-30
I think you will have to backup your home either using a live session from DVD or USB or you may just be lucky enough to be able to boot to recovery mode from the grub menu, though I think that could be impossible as well if file permissions and ownership are incorrect.

---

