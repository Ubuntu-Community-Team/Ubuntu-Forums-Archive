---
title: "Can't Change System Settings"
date: 2013-06-01
forum: General Help
---

### Post by ChochiWpg on 2013-06-01
Hi,

I just performed a fresh install of Ubuntu 12.04.2 LTS without any issues.  I updated the software, I installed the recommended proprietary drivers, installed any additional software that I wanted with no problems.

However, I can't seem to change any system settings, they don't stick.  I can access system settings, I can click on each option, but when I select an option to change it doesn't take.  

For example if I click on Time and Date Settings and place a checkmark beside show weekday and date and month.  It will place a checkmark beside those options but won't actually change in the menu.  When I press the "X" to close out and go back into settings it's back to the default and the options I checked are unchecked.

Also happens with wallpaper, I can see all my wallpaper, but I select another wallpaper other than the default and it won't change.  I turn on auto hide launcher and it doesn't auto hide.  I change my shortcuts on the unity bar and when I restart my computer the settings don't stick they go back to the defaults.

Any idea what I can do to fix this or why it is happening.  Other than that everything is working.

Thanks.

---

### Post by CatKiller on 2013-06-01
Have you got permissions problems on your Home folder?

---

### Post by ChochiWpg on 2013-06-01
I am not at home right now to check, but when I get home I will let you know. Thanks

---

### Post by CatKiller on 2013-06-01
It could be something else, but that's what occurred to me; all those settings are stored in your Home folder and if they can't be written for some reason then the settings won't stick.

---

### Post by ChochiWpg on 2013-06-01
> **CatKiller said:**
> It could be something else, but that's what occurred to me; all those settings are stored in your Home folder and if they can't be written for some reason then the settings won't stick.

If I go to my Home Folder which is on the Unity toolbar just under the dash logo, then click on file and properties.  There is a tab that says permissions.  When I click on permissions it says Owner (and my name) Folder Access (Create and Delete Files) File Access just has a (-) through it.

But if I go to Home Folder, File System, Home and then check properties and permissions in that Home Folder it says you are not the owner so you can't change these permissions.

I am not sure why there are two different Home Folders.

Even weirder, I logout and then log in as guest and I can configure and change all the settings and they do stick without issue.

---

### Post by CatKiller on 2013-06-01
Definitely sounds like a problem somewhere with your Home folder if the guest account works OK. 

To answer your implied question, /home is not the same as /home/username. /home shouldn't be owned by you, but /home/username should. And if you had a second user, /home/username2 should be owned by them, see?

I believe that the line rather than a tick implies that you can access some, but not all, of the files in your Home folder. I don't know if that's usual or not. If you open up your folder and press Ctrl-h (show hidden files) you can check to see if you own everything and what the permissions are. If there's something that doesn't look right you can post the details here and someone can check how they should be.

---

### Post by ChochiWpg on 2013-06-01
> **CatKiller said:**
> Definitely sounds like a problem somewhere with your Home folder if the guest account works OK. 

To answer your implied question, /home is not the same as /home/username. /home shouldn't be owned by you, but /home/username should. And if you had a second user, /home/username2 should be owned by them, see?

I believe that the line rather than a tick implies that you can access some, but not all, of the files in your Home folder. I don't know if that's usual or not. If you open up your folder and press Ctrl-h (show hidden files) you can check to see if you own everything and what the permissions are. If there's something that doesn't look right you can post the details here and someone can check how they should be.

So I performed the task as mentioned and prior to installing Ubuntu I was running Linux Mint 14, then Mint 15.  I didn't wipe my /home folder when I installed Ubuntu, I just mounted it during installation.  A lot of the hidden files pertain to Mint.  Could this be a problem?  I formatted my "/" partition, but only mounted "/home" during install.

The reason I did this was because I wanted a clean install of the system but wanted to keep all my data intact that was in my /home folder so I don't have to re-configure everything again.  Should I have formatted /home as well?

---

### Post by CatKiller on 2013-06-01
Not necessarily. It's possible that you just had  different user number before, or that Mint stores its settings differently.

Either way, I don't think a ```
sudo chown -r user:user /home/user
``` would actually hurt anything. Substitute your username for user above.

If it's not an ownership issue from your previous install we can dig down and look at permissions.

---

### Post by ChochiWpg on 2013-06-01
> **CatKiller said:**
> Not necessarily. It's possible that you just had  different user number before, or that Mint stores its settings differently.

Either way, I don't think a ```
sudo chown -r user:user /home/user
``` would actually hurt anything. Substitute your username for user above.

If it's not an ownership issue from your previous install we can dig down and look at permissions.

This is what it says when I enter the above command.

chochiwpg@ChochiWpg:~$ sudo chown -R chochiwpg:chochiwpg /home/chochiwpg
chown: cannot access `/home/chochiwpg/.gvfs': Permission denied

---

### Post by CatKiller on 2013-06-01
I don't think that strictly matters. It's a mount point for a userland disk mounting system that I don't fully understand. You can unmount it (assuming you aren't currently using any network shares or similar) with ```
fusermount -u ~/.gvfs
``` and then try again. I can't remember if you're likely to need to delete that mountpoint too or not. Either way, it'll be created again automatically should it become necessary.

---

### Post by steeldriver on 2013-06-01
I think you can just ignore the error message - no need to unmount .gvfs

As CatKiller said, .gvfs is a mount point for things that you have mounted as user (probably network shares via nautilus) - it does so with owner user:user and permission mode rwx------ meaning that not even root (via sudo) can mess with them. So the chown will just skip that directory.

---

### Post by ChochiWpg on 2013-06-01
> **CatKiller said:**
> I don't think that strictly matters. It's a mount point for a userland disk mounting system that I don't fully understand. You can unmount it (assuming you aren't currently using any network shares or similar) with ```
fusermount -u ~/.gvfs
``` and then try again. I can't remember if you're likely to need to delete that mountpoint too or not. Either way, it'll be created again automatically should it become necessary.

I performed fusermount -u ~/.gvfs as suggested and then tried sudo chown -R chochiwpg:chochiwpg /home/chochiwpg again and I assume it passed the test it just brought me back to chochiwpg@ChochiWpg:~$

When I try to change wallpaper or any system settings it still doesn't do anything though.

Edit:  I logged out of the user account and logged back in again and now I can change wallpapers and adjust system settings.  

So what exactly did we do, because it seems to be working now.  I will reboot just to see if settings stick.  BRB

---

### Post by CatKiller on 2013-06-01
> **ChochiWpg said:**
> 
When I try to change wallpaper or any system settings it still doesn't do anything though.

That's a bummer. Have a look at permissions, then. ~.gconf and ~.local would be my guess at good places to start. You could just do a recursive chmod, but I'm not sure if that would cause further problems.

---

### Post by ChochiWpg on 2013-06-01
> **CatKiller said:**
> That's a bummer. Have a look at permissions, then. ~.gconf and ~.local would be my guess at good places to start. You could just do a recursive chmod, but I'm not sure if that would cause further problems.

[COLOR=#000000]I logged out of the user account and logged back in again and now I can change wallpapers and adjust system settings. [/COLOR]

[COLOR=#000000]I will reboot just to see if settings stick. BRB

After reboot the settings stuck as well.  You are a genius, thank you so much for your help.  You are the only person who took the time to help, I asked this question in multiple different forums.  I owe you a coffee :)[/COLOR]

---

