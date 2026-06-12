---
title: "How do I correct misspelled username:correct-group in new install w/o problems?"
date: 2020-07-29
forum: General Help
---

### Post by crazybear on 2020-07-29
I just installed Ubuntu 20.04 on a Dell laptop - that part surely doesn't matter. I was having problems being able to move files/folders from the old Ubuntu to the external drive and then from the external drive to the laptop. So, I thought maybe I needed to chown it for the laptop [?]. It was then when I looked at the myaccountname:mygroupname on the terminal that I noticed one letter had been transposed [by me or the system - I know not which] - so that the myaccountname is spelled incorrectly, (but the group name was fine). How can I change this, as there really is but one user [me]? I started to follow some guideline for something similar - not exactly the same - from a website and added 'tempuser', but when I tried to 'be' tempuser and change the misspelling I just endlessly was told I could not. Now, I can't even log in as tempuser...that seems to have disappeared. I can still log on and get into terminal....but don't know how to proceed or even see what is what.

I was in the process of transfering data from my old ubuntu on a desktop to the new ubuntu on the laptop and there seems to be no other easy way other than an external disk. Now in the laptop, I can see all inside the external disk and even open it up in the laptop, _**BUT**_, I can not transfer anything from the external drive to the laptop. That is problem two.

Problem one even if problem two is solvable without changing username, is I want the username to be correct - as it honors someone dear who just died and the letters are scrambled, or I scambled them when typing it in...my vision is not great, and text was very small on the xps with 4K screen [more so when installing - now I have it larger].

Any help on the two, or if the two are related and one, would be appreciated. Thanks in advance.

---

### Post by TheFu on 2020-07-29
This is the hacking, but easy way. 
You can just edit the /etc/group and gshadow files using **sudoedit**.
Be certain you understand what each field means. Don't change the numbers and all will be fine.
the manpage for each of those files spells out what each field means.
```
man -s 5 group
man -s 5 gshadow
```
I've made a few assumptions here, like that you aren't using LDAP for user management and that you won't touch any fields besides the groupname one.

Wouldn't hurt to look at the /etc/passwd and manpage for that file too. These text DBs are easily connected - the passwd uses the gid number to connect a username/uid to the primary group. The group file uses the username to make the connection go back for secondary groups. It is pretty easy.

Be careful and it is probably best to make a backup of these files before you start. If things get screwed up, you may need to boot into a "Try Ubuntu" environment, mount the storage with /etc/ and move the backup copies back as the primaries to try again.  OTOH, these files are really bonehead.

---

### Post by crazybear on 2020-07-29
> **TheFu said:**
> This is the hacking, but easy way. 
You can just edit the /etc/group and gshadow files using **sudoedit**.
Be certain you understand what each field means. Don't change the numbers and all will be fine.
the manpage for each of those files spells out what each field means.
```
man -s 5 group
man -s 5 gshadow
```
I've made a few assumptions here, like that you aren't using LDAP for user management and that you won't touch any fields besides the groupname one.

Wouldn't hurt to look at the /etc/passwd and manpage for that file too. These text DBs are easily connected - the passwd uses the gid number to connect a username/uid to the primary group. The group file uses the username to make the connection go back for secondary groups. It is pretty easy.

Be careful and it is probably best to make a backup of these files before you start. If things get screwed up, you may need to boot into a "Try Ubuntu" environment, mount the storage with /etc/ and move the backup copies back as the primaries to try again.  OTOH, these files are really bonehead.

WOOOWH! I think this is too dangerous and advanced for me. I'm not that advanced I like to try dangerous things.
I was going to try to fix the permisions with 
sudo chown myaccountname:mygroupname /media/disk/myfolder

But, as I said, I don't know if me or the system messed up the 'myaccountname' - one letter was moved to another location.
Wouldn't have the faintest idea what LDAP is, so not likely using it. Also, group name is PERFECT and needs NO CORRECTION...so I think I'll pass on this suggestion
Thanks but no thanks.....especially when what it being done is totally not transparent. It may be the perfect fix, or it might get me in more of a fix.
Also, I don't know where to back up such a large amount of data easily....about 300GB now.

***I just noticed one more thing....I pulled the memory card out of my Nikon and put it in the slot for the Laptop - I could look at the photos, but I could NOT move them into the laptop......and I've never heard of granting permision to a camera memory chip. Really? What is going on? Nothing that connects to the Laptop is allowed to be moved into it - even USB flash drives. Is this some setting or does each need to be chown'd?! Nice security feature, but there has to be a way to turn it off and tell the machine what I just connected is OK!?@***

---

### Post by TheFu on 2020-07-29
**chown** isn't gonna fix the wrong username or groupname on a system, if the desired username is misspelled that is being displayed.

Did you even look at the /etc/passwd and /etc/group files?  They are bonehead.  That fact that you can use an editor means you can probably modify those correctly. They are text files with only 1 type of record in each.  Editing them is easier than editing gnome settings with dconf, IMHO.

As for backups, for these specific files, those files are 4K each, if even that. They are tiny. Just copy them to a new name or to your HOME.  You can copy 3-4 text files that are less than 4K each, right?  That's it.

For 20+ years, this was how Unix user-group administration was done in small, 1-system, setups and it still works the same.  I have confidence that anyone who can use sudoedit (which is just a safe system frontend to the editor you've setup), can modify these files.  There's nothing magical about them.

Or perhaps I've completely missed the issue?  But if any directly listing - **ls -al** shows the wrong username or groupname, then this is, by far, the easiest way to change what gets displayed.  With the wrong username, the changes have to be made in a 4 files - passwd, shadow, group and gshadow, but that's it.

I honestly don't know any other way to accomplish changing a username known to the system that doesn't get 100x uglier fast.

If you didn't go out of your way to setup LDAP, then you aren't using it in a home environment.

---

