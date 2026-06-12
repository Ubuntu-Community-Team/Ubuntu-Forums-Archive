---
title: "[SOLVED] How the devil?...."
date: 2008-05-20
forum: General Help
---

### Post by anotherdisciple on 2008-05-20
How the devil do I make a script run when each user logs in? I am sharing folders between my wife and myself... and as you may or may not know... sharing folders is kind of a pain on ubuntu. So, I wrote a script that recursively changes the group permissions of the folders that we want to share. Now I just need to make it run when I log in and when she logs in.

Right now I just made a launcher that runs it in the terminal, but I don't want to have to hit that every time I come back to the computer.


I know how to make it run when turn on the computer or reboot, but I need it to run when I log in. Any Ideas?

---

### Post by cdtech on 2008-05-20
You could add it to your sessions menu:

System > Preferences > Sessions, and add it to the desktop startup.

Is that what you want to do, or within the user's home directory startup?

You could add it to the ~/.bashrc file for individual user's

---

### Post by ryanhaigh on 2008-05-20
Add an item to system>preferences>sessions using the script you are using as the command, as you will see when you look through the existing items these are all services/apps that run on login so it should be what you want although I would say there is likely a more elegant solution to your issue, perhaps you could provide more info and avoid having to use this script at all. Permissions should be persistent so I cannot understand why you would need to change them on login.

---

### Post by cb951303 on 2008-05-20
why are you bothering with scripts? just create a directory in your home dir like "/home/me/sharedFolder" than set appropriate permissions and owners for your wife's user. that's it? nothing painful :)

isn't it what you try to achieve?

---

### Post by anotherdisciple on 2008-05-20
well... here's the problem... when you change the permissions... even recursively... it will change all the permissions, but when you create a new file... it defaults as 700 permissions. So, the OWNER of that file can read, write, and execute... however, the GROUP permission is set to 0... so you can't even read it. 

The reason for the script is this. If my wife creates a file (even in a shared folder that has 770 permissions) and I log in under my name... the group permission of that new file is 0, so I can't do anything with it unless if I run that script. So, it would be great to have that script run every time each of us logs in, that way if either of us added anything, we both have permissions.

About running it in Sessions... I tried that... and it didn't work for some reason... is there something you can put before the command to make it run in the terminal? so instead of putting the location as "/home/user/file" you would put "%*@# /home/user/file"... obviously that won't work, but you get the idea.

---

### Post by anotherdisciple on 2008-05-20
> **cb951303 said:**
> why are you bothering with scripts? just create a directory in your home dir like "/home/me/sharedFolder" than set appropriate permissions and owners for your wife's user. that's it? nothing painful :)

isn't it what you try to achieve?

This won't work because the directory has read/write/execute permissions but any new files that are added will have 700 permissions.

---

### Post by mixmaster on 2008-05-20
You need to set the umask so that newly created files have rw permission for both user and group.  Do this in the profile for both yourself and your wife.  Then all newly created files will be available to both of you without the hastle of constantly changing permissions.

You'd even be able to log on at the same time without causing chaos.

---

### Post by anotherdisciple on 2008-05-20
I'm not at a linux computer, so I can't tinker around with it. So, how might I go about changing unmask?

---

### Post by cb951303 on 2008-05-20
Here is what I did 3 min ago. I created a group called "test"
I made myself and my brothers users a member of "test" group
than I created a directory called "sharedFolder" in /home/myAccount/ and set the permissions in nautilus as in picture. I relogged to my account.
I created files, copied files to that directory. I logged out and login from my brothers user. tried to delete the files I created and copied with my user. and it worked perfectly... what else do you need :)

---

### Post by anotherdisciple on 2008-05-20
> **cb951303 said:**
> Here is what I did 3 min ago. I created a group called "test"
I made myself and my brothers users a member of "test" group
than I created a directory called "sharedFolder" in /home/myAccount/ and set the permissions in nautilus as in picture. I relogged to my account.
I created files, copied files to that directory. I logged out and login from my brothers user. tried to delete the files I created and copied with my user. and it worked perfectly... what else do you need :)

I'm not at my home computer, so I can't test this out. But, I changed our share folders to 770 permissions and put us in the same group... so that means we should be able to do anything with those files. And yes... that folder's group is our group. So have you tried EDITING a file? It will let you create and delete... but will it let you edit? I dunno... I'm confused because I did all of those suggestions last night and it didn't seem to work the same way for me!

---

### Post by anotherdisciple on 2008-05-20
Okay kiddos.... I take it that I need to change my umask in /etc/profile ... I'll let you know what happens once I get home... then I'll mark this sucker solved.

---

### Post by mixmaster on 2008-05-20
> **anotherdisciple said:**
> I'm not at a linux computer, so I can't tinker around with it. So, how might I go about changing unmask?
umask 0002 will cause all future files to be created with rw-rw-r-- mask.

Put this in your profile (and your wife's) and make sure you both have the same primary group and you will be able to read and write one anothers files

If you want read-only access by default use
umask 0022

---

### Post by anotherdisciple on 2008-05-20
Why do we need to have the same PRIMARY group? What would happen if my primary was "nick" and her primary was "julie" and the group "admin" contained both both of us?

The reason that I ask is because originally I made both of our primary groups "admin" and I lost access to my files. So, I had to chown nick -R /home/nick/ and chmod 775 -R /home/nick/ . If I change my main group will I have to change ownership to "admin"?

---

### Post by anotherdisciple on 2008-05-20
Why do we need to have the same PRIMARY group? What would happen if my primary was "nick" and her primary was "julie" and the group "admin" contained both both of us?

The reason that I ask is because originally I made both of our primary groups "admin" and I lost access to my files. So, I had to chown nick -R /home/nick/ and chmod 775 -R /home/nick/ . If I change my main group will I have to change ownership recursively to "admin"?

---

### Post by mixmaster on 2008-05-21
> **anotherdisciple said:**
> Why do we need to have the same PRIMARY group? What would happen if my primary was "nick" and her primary was "julie" and the group "admin" contained both both of us?

The reason that I ask is because originally I made both of our primary groups "admin" and I lost access to my files. So, I had to chown nick -R /home/nick/ and chmod 775 -R /home/nick/ . If I change my main group will I have to change ownership recursively to "admin"?
When you create a file it will have the owner:group set to the owner/primary_group of the creator.  If you both have the same primary group then you are guaranteed access.  However, it is not strictly necessary provided each of you is a member of the other's primary group.

Thus if you are fred:husband and your wife is june:wife, then fred must be a member of wife and june a member of husband for full access.  I thought both being in the same primary group would be easier but if it causes grief use this scheme instead.

---

### Post by anotherdisciple on 2008-05-21
Mixmaster... you are a genius! So here is the trick to file sharing on the same ubuntu computer. 

1. Set the same primary group for the users that you want to share files.
2. chmod 770 all of the folders that you want to share.
3. "sudo gedit /etc/profile" and change umask from 022 to 002

Solved... thanks to everyone who helped me out.

---

