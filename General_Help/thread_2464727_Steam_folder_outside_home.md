---
title: "Steam folder outside /home/"
date: 2021-07-10
forum: General Help
---

### Post by dorpapst on 2021-07-10
Hey friends,
My steam library is within the folder 
/home/user/.steam/.debian-installation
according to the steam settings.

I would like to make the games shared between two users on the computer since we play the same games, but dont want to have 100 instead of 50GB used on the disk.

Does anybody of you know a clever way of making it accessible for two users? The second user does not have sudo rights. Both are logged in into the same Steam account.
I read some articles and my idea is now to move the steam-folder into /opt/steam and then change the path in the settings.

Is that the correct way to do it? Will I got problems of some sort? 
I guess I need to find a correct chmod command for that folder as well.


Is there somebody out there who already did something like that?

Many greetings and thanks!

---

### Post by Tadaen_Sylvermane on 2021-07-10
I can't help but think it would be easiest to have independent .steam folders and a single steamapps (where the games themselves are) and symlink it into each users .steam folder. That would he my first step.  Then make sure all pf the users can read and write to the steamapps locatiin. 

I don't know how steam handles games so it may cause problems.

---

### Post by CatKiller on 2021-07-10
> **Tadaen_Sylvermane said:**
> I can't help but think it would be easiest to have independent .steam folders and a single steamapps (where the games themselves are) and symlink it into each users .steam folder. That would he my first step.  Then make sure all pf the users can read and write to the steamapps locatiin. 

I don't know how steam handles games so it may cause problems.

You don't even need to go that far (although symlinks are fine - I used to do that when I had an HDD and an SSD so that I could put selected games on the faster smaller drive at will). Steam has its own setting for where the games library is; you can just set that to wherever.

The thing that would potentially cause issues is that the Steam client does at least some permissions checks on the files in the library; it's why a library on NTFS is problematic - NTFS can't hold the execute permission, so it needs to be set at mount time. If the Steam client checks for ownership as well as permission (I have no idea if it does) then the OP will struggle to do what they want.

---

### Post by Tadaen_Sylvermane on 2021-07-11
True enough I guess.

I rather find it easier to create a symlink and keep defaults vs custom settings in the app. Just less questions when searching for issues.

---

