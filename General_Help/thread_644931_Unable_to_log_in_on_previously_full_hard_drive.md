---
title: "Unable to log in on previously full hard drive"
date: 2007-12-19
forum: General Help
---

### Post by Naye on 2007-12-19
I managed to get my hard drive filled up to 100%, at which point I could no longer log in. Now I've read through previous threads here on the subject, and using the Terminal I've gotten the 100% down to 89%. I've cleared out .Trash, I've used sudo apt-get clean, I've uninstalled Wine, and df tells me I've got 11% free disk space. 

For some reason, though, all of this just isn't enough - I can access the system using the Terminal window, and I can mount the disk to a (brand new, Gutsy) LiveCD, but I simply cannot get it to log me in properly. Not even using GNOME in safe mode works. It will log me in far enough that I can see my custom background colors, but no further.

Does anyone have any idea on what I should do next? I'm running Gutsy on a Toshiba Satellite M40X-161 laptop. I've been using Ubuntu for eight months or so, but I'm still very inexperienced when it comes to both operating the Terminal, and figuring out how things work. Any help would be greatly appreciated!

---

### Post by bodhi.zazen on 2007-12-19
Your config (ie . files in $HOME) are probably corrupt.

You can test this by making a new user. It the new user can log in, either use the new user or delter the .gnome files in $HOME.

You will lose your desktop settings, but it should work.

---

### Post by Naye on 2007-12-19
Fantastic! Thank you so much for that quick reply - turned out to be exactly that! My new user can access the system just fine.

If it's not too much trouble, could you tell me if there's anything in particular I need to think about when deleting those .gnome files? Will I find them if I look through /home/[username] with the Terminal, or is there some other way I should go about it? 

Alternatively, how do I set things up so that my new user can both read & write the files under my old user account?

Again, many thanks for your fast (and correct) response!

---

### Post by bodhi.zazen on 2007-12-19
Best be cautious and use natuilus

Open a terminal, enter ```
gksu nautilus
```

*Note you will need to add you new user to the admin group first

view -> show hidden files

navigate to you old home.

The config files start with a .

Hard to know which one is corrupt, so delete one at a time and re-try the old user.

---

### Post by Naye on 2007-12-19
Thanks for the help, yet again. 

I've spent a couple of hours deleting files and trying to log back in with the old user, but I haven't had any success at all... Maybe I'm just not getting the right files, but unless I should go after entire folders, I know I've tried deleting them all. Any ideas? (Though this might be the time to start a new thread, since the nature of my current problem is different from the subject...)

---

### Post by bodhi.zazen on 2007-12-20
You should try :

With the old user, delete the entire directory(s) (folder) .gnome , .gnome2 , and .gnome2_private

+++++++++++++

If that fails, add the new use to the admin group and copy any data you need to your new user.

I do this on the command line

sudo cp fiile1 file2 .... fileX /home/new_user
sudo chown -R new_user.new_use /home/new_user

HTH, sorry it has taken you so long :(

---

### Post by ~LoKe on 2007-12-20
You could always make a new user, chown all the .config files in the home directory to your old user, and copy them over (thereby overwriting the old configs).

Now sure how that would work out...but it shouldn't do any damage assuming it's a **new** user and you chown all the files properly.

---

### Post by Naye on 2007-12-20
I really appreciate the tips! Unfortunately the first solution didn't work for me, and now I've discovered that my new (created yesterday) user is having the same issues that my old user did! Creating yet another new user works, for now, but I'm not willing to put a lot of work into copying things into another account when I'm not sure that account will still be there on re-boot. Definitely time to start a new thread, I'd say!

---

### Post by Naye on 2007-12-20
> **~LoKe said:**
> You could always make a new user, chown all the .config files in the home directory to your old user, and copy them over (thereby overwriting the old configs).

Now sure how that would work out...but it shouldn't do any damage assuming it's a **new** user and you chown all the files properly.

I'm experiencing other problems that make me hesitant to rely too much on the new user's .config files - I did try to copy them over, but apparently cp doesn't work on the .gnome files? I'm a beginner user of the terminal window, and I was hesitant to chown .config files belonging to the account I was currently logged in on, so I still haven't explored that option fully. Thanks for the suggestion, though!

---

