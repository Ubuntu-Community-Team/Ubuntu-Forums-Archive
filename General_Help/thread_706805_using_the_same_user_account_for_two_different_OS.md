---
title: "using the same user account for two different OS"
date: 2008-02-24
forum: General Help
---

### Post by AbtZ on 2008-02-24
I wonder if it's possible to use the same user account but for two different OS installs (in this case Gutsy and Hardy Tribe 5). I'd like to keep my bookmarks and other settings from my Gutsy install, even when I'm using Hardy.

---

### Post by soldats on 2008-02-24
just save all the info you want then add it to the hardy install and chown it to the user of your choice. you can still use the same name it just wont copy it itself you have to do it.
edit: i meant to save your bookmarks and any settings that are stored in a a file. then chown them to your user. the desktop settings will have to be changed manually but after a logout they should be saved for the next login

---

### Post by AbtZ on 2008-02-24
Uh, perhaps I should try to elaborate.

I have a separate /home partition. I'm looking for a way to add my old user account to the new install. As it is now, I installed Hardy, and I'm not allowed to add a new account with the same name because it says the folder already exists.

Can't I just set it so that it uses the old folder an all of the stored settings in it?

---

### Post by AndyCooll on 2008-02-24
When you install Hardy, at the partitioning stage you should choose the "manual" approach. You can then manually set your /home partition to the one you have already created. 

All in all this will probably be ok. However you should be aware that some applications might not function properly because Gutsy and Hardy will be trying to share the same config files and obviously the Hardy will replace the older ones. This in turn may mean some apps in Gutsy won't function properly.

:cool:

---

### Post by trippinnik on 2008-02-24
if all you want are the settings just copy all the .[folder_name]s over to the other account.  if you want them to share the same folder, the accounts need to have the same User ID number or one of the users won't have permissions.

---

### Post by AbtZ on 2008-02-24
Previously, when installing, I have done that -- installing using the username of my old account. However, I've encountered several problems with that approach, which is why I want to do it differently.

Anyway, I've figured out how to do it. For reference I will list the method I used, below. "test" will be the username.

First fire up the good ol' terminal. Then:

```
sudo su -
adduser test
```
Here it will ask you some questions. Answer (or press enter to skip) and proceed.

```
chmod -R 744 /home/test/
chown -R test:test /home/test/
chmod 644 /home/test/.dmrc
chown test:test /home/test/.dmrc

```

Done! :)

---

