---
title: "Symlinks"
date: 2007-03-15
forum: General Help
---

### Post by Gorbachev on 2007-03-15
So, I decided to move my installation of Enemy Territory to my /home/me/Desktop/Games/WolfET directory, and the symlinks found in /usr/local/bin are obviously broken. I am wondering how to either edit them or delete and create new ones pointing to the correct location.

Can anyone tell me how to do this? Thanks.

---

### Post by girishv on 2007-03-15
Since the links are broken, you can delete them similar to file(s)
rm simlink_to_binary

and then create new simlinks as

ln -s /home/directory/filename .
(The above assumes that you are in the directory where the soft links are to be created)

or 

ln -s /home/directory/executable /usr/local/bin/.

You can also give a new name for the simlink (useful in libraries where a package needs library.so.0 where as another package gives library.so.0.0.1)

Girish

---

### Post by Gorbachev on 2007-03-15
Ok, great :) Now I know how to make symlinks, after rather intense searching.

I still have a delimma thanks to my ineptitude.

I was thinking this would solve my problem, whereas, there is a shortcut named enemy-territory (i guess that's what it'd be called) in my application menu. I click Applications, and have an expandible menu called Other. 

This shortcut links to the old location of enemy territory. How do I edit/delete/move these shortcuts in the application menu? I have tried several directories where these might be stored (I am thinking it is similar to windows, so I could be going about it all wrong) and have had no luck.

I would simply like, for one, to move it to Games in the application menu, then secondly, to direct it towards the proper location of my game installation.

Edit: I have another problem regarding root password.

I go to the terminal, type the following:

sudo passwd
password
then i set and confirm the new password, only to launch synaptic, it asks me for the password, i enter the new password and it says it's invalid. Then i enter the old password and it still works. Regardless of rebooting, or logging out and then back in.. which i thought might help for some reason.

---

### Post by Nythain on 2007-03-15
your root password issue is probably because your link for synaptic is calling it with gsudo, so it still wants your sudoer password... if you set the root password (useless and vulnerable) then try opening terminal, su into root, give the root password there, then run synaptic as root, but i dont know why you would want to do that...

---

### Post by Gorbachev on 2007-03-15
Well, from the sound of it, I don't want to do that.

I simply didn't understand the difference between the sudo password and root password, but now I do. I thought they were the same, so thanks.

---

### Post by Gorbachev on 2007-03-15
I almost forgot, I still don't know how to manage my application menu :confused:

---

