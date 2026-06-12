---
title: "Changed file permissions, and lost some files!"
date: 2008-06-11
forum: General Help
---

### Post by hotstovejer on 2008-06-11
Get this!

For some messed up reason, when I reinstalled Hardy after adjusting some stuff on my primary hd, I used a different user name than my own. When I added myself to my system, I found that the user that I had used for the initial setup had taken ownership of all of my multimedia. No big deal. Whipped open the terminal, and went something like this.
```
sudo chmod -Rv 766 /media/storage

```

All of a sudden, all of my As I Lay Dying is gone! Not in trash, not in another folder, NOWHERE!

Also, that didn't give me ownership of ALL of the files, just some. 

Also, on a different note, my home dir had most of it owned by root. Don't know how THAT happened.

Any help?

Jeremy

---

### Post by cdtech on 2008-06-11
Use sudo chown -R username ./directory to change ownership of a directory.

---

### Post by hotstovejer on 2008-06-11
But why would files all of a sudden not be there??

That's MY question!

---

### Post by hotstovejer on 2008-06-11
OK, that's messed up. Learning experience accomplished.

The old user that owned the drive was deleted. So the old user still had ownership of the files that were "deleted" chmod didn't do what I wanted. chown -R hotstovejer:hotstovejer /media/storage worked like a charm. Yay unix! 

Now, why would I use chmod over chown? chmod would change it for all future users?

Tutorial time, someone!

---

### Post by molotov00 on 2008-06-11
chown makes you 'own' the files. chmod assigns permissions based on whether you are the owner, within a group, or other. so, you could just give all users full access to all files, then it wouldnt matter who owned it... but that's insane.

you should always chown then give other people limited access.

also, you would have saved time if you'd used 'man chmod' before using the wrong syntax. even 'chmod --help' would have been better. --help is a standard parameter for a commands' syntax help. i dont mean it as a jab... i always use --help or man when I'm not 100% sure, especially when running it as root/su

---

