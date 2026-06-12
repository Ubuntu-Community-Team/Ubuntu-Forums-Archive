---
title: "whoops - messed up my permissions"
date: 2008-06-22
forum: General Help
---

### Post by mactece on 2008-06-22
I'd really appreciate some help with this one.

I have three levels of access on my homecomputer 1 - me, the only one allowed to mess up the computer :) , 2 - my wife allowed to do most things but I want to keep her away from my files and anything which could mess up the system, 3 - the kids (aged 4 and 5 - 'nuff said). So I carefully allocated everyone to groups that gave the appropriate level of access and then used chmod to set the permissions of *all* the files in the HOME folder to 770 :oops: My thinking (!) was that this would pidgeon hole everyone by their user and group access level. Since no-one else uses the PC I thought (!, again) that I could set everyone else to no access. 

The result of this was that I couldn't get acces to my own folders, never mind anyone else's, so I deduce that the system is a user, too, and I've locked it out! I've fixed it for now by changing the permissions to 777. This is of course the opposite of what I was trying to do and also generates an error at login about home access and 664 permissions and so on. I think my computer may be mad at me.

Can you help me to a) fix this and/or b) implement the policy outlined above.

Many thanks

David

---

### Post by drs305 on 2008-06-22
> **mactece said:**
> 
The result of this was that I couldn't get acces to my own folders, never mind anyone else's, so I deduce that the system is a user, too, and I've locked it out! I've fixed it for now by changing the permissions to 777. This is of course the opposite of what I was trying to do and also generates an error at login about home access and 664 permissions and so on. I think my computer may be mad at me.

David

To clear up the 644 .dmrc messages, run:
```
chmod 755 ~/ && chmod 644 ~/.dmrc
```

The 755 gives you RWX, group RX and others RX. You can modify it to your preferences but it will do for now to clear up the errors.

You may need to log out and back in.

As for your other questions, does each of the other users have their own username and home folder?

---

### Post by fahadsadah on 2008-06-22
Home directories should all be set to 664 - ```
chmod 664 /home
```

EDIT: Woops, I was beaten to it. The above command affects your home, mine affecting all homes. The dmrc fix is unnecessary in mine as everything is 664. (+x permissions should not really be set on a whole folder, let alone your home folder, anyway)

---

### Post by chrisccoulson on 2008-06-22
> **fahadsadah said:**
> Home directories should all be set to 664 - ```
chmod 664 /home
```

EDIT: Woops, I was beaten to it. The above command affects your home, mine affecting all homes. The dmrc fix is unnecessary in mine as everything is 664. (+x permissions should not really be set on a whole folder, let alone your home folder, anyway)

That is wrong, and will prevent any user from logging in to the system. /home is set to 755 and owned by root:root. The executable bit must be set on directories else you can't list the files in them. /home should not be writable by anyone other than the root user, hence **755**

Your home folder (~/) should be set to 755 also, but owned by yourself. ~/.dmrc should be **644** (note, **not** 664 as you specified) and owned by yourself also.

---

### Post by sisco311 on 2008-06-22
> **mactece said:**
> I'd really appreciate some help with this one.

I have three levels of access on my homecomputer 1 - me, the only one allowed to mess up the computer :) , 2 - my wife allowed to do most things but I want to keep her away from my files and anything which could mess up the system, 3 - the kids (aged 4 and 5 - 'nuff said). So I carefully allocated everyone to groups that gave the appropriate level of access and then used chmod to set the permissions of *all* the files in the HOME folder to 770 :oops: My thinking (!) was that this would pidgeon hole everyone by their user and group access level. Since no-one else uses the PC I thought (!, again) that I could set everyone else to no access. 

The result of this was that I couldn't get acces to my own folders, never mind anyone else's, so I deduce that the system is a user, too, and I've locked it out! I've fixed it for now by changing the permissions to 777. This is of course the opposite of what I was trying to do and also generates an error at login about home access and 664 permissions and so on. I think my computer may be mad at me.

Can you help me to a) fix this and/or b) implement the policy outlined above.

Many thanks

David

To restore the settings on your home folder:
```
sudo chmod -R 0644 $HOME
sudo chmod -R ug+X $HOME
sudo chown -R $USERNAME. $HOME
chmod 0644 $HOME/.dmrc
```To create a *secure* home(allow your group to read):
```
chmod 0750 $HOME
```To create a *secure* home(don't allow your group to read):
```
chmod 0700 $HOME
```Setup the permissions for kids:

Create a new group (parents):
```
sudo addgroup parents
```Chang the group of the account to parents:
```
sudo chgrp -R parents /home/<home-dir>
```Setup the permissions:
```
sudo chmod -R 0664 /home/<home-dir>
sudo chmod -R ug+X /home/<home-dir>
chmod 0644 /home/<home-dir>/.dmrc
```Set the umask for the kids. Edit the /home/<home-dir>/.bashrc and add this lines:
```
umask 0002
newgrp parents
```Add yourself and your wife to the parents group:
```
sudo addgroup <username> parents
```

---

### Post by mactece on 2008-06-22
Wow! Thanks for all the replies. I haven't been able to try anything yet because I came down with a bad attack of the wife and kids. However, nearly time to climb the wooden hill for the kids and then I can get back on the PC! :p

---

### Post by mactece on 2008-06-23
ok - here's what I did.

While I was waiting for replies I kept looking for help in the forums and found a post (which I lost the connection to - blast) where someone said you need the "other users" to have x in order that files can be listed. This fitted my problem and got me thinking. So I...

- Read all the posts above - again, many thanks.
- Decided that my user structure was robust (i.e. no-one can get to a level I don't want them to) so 771 was the ideal code. This gives access allows the files to be listed but no-one can get to where they shouldn't
- Used chmod to set priority to 771 on all folders in /home (including all subfiles using -R switch)
- Used "gksudo nautilus" to a) change file permissions for the /home and /home/<user> folders (not their contents) to 750 and b) the .dmrc folders to 644

Using gksudo nautilus worked really well because I didn't have to deal with long file lists but could use the different views and right clicking to make fast progress.

Any comments? I'm going to throw the 771 question open with another post.

---

