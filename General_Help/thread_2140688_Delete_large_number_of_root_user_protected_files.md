---
title: "Delete large number of root user protected files"
date: 2013-04-30
forum: General Help
---

### Post by amayan on 2013-04-30
After running Photorec in an attempt to recover lost files i've ended up with a large number of files and folders that are owned by root and i cannot delete, but i would like them gone as they are filling up the my picutres folder. 

Now i've found ways to delete single root files easily, but is there anyway to easily delete a huge bunch of them without me risking doing something wrong as a root user. I'm still fairly infantile in my use of ubuntu... 

Thanks in advance.

---

### Post by The Cog on 2013-04-30
I think photorec creates its own folders. If this is the case then deleting the entire folder should be OK to do (check first please).
To delete an entire root folder, use the command
```
sudo rm -rf foldername
```

---

### Post by amayan on 2013-04-30
Thank you, n yes there's six folders within one of my pictures folders that photorec has created, i've tried the above command with the name of one of photorec's folders but nothing's changed. Do i need to type it's full location or something? or do you think photorec creates another folder elsewhere i may have missed?


EDIT- And i've just found another 208 folders in another of my picture folders :/

---

### Post by amayan on 2013-04-30
- When i try 'gksudo nautilus' as suggested in a similar topic i simply can't find my picture or anything to do with photorec

- When i try 'Change the owner of the files, example sudo chown -R username recup_dir.* or sudo chown -R username /home/username/testdisk-6.14/recup_dir.*. (When asked for the password, use the password from your user session to validate the sudo command)' as outlined on CGSecurity [http://www.cgsecurity.org/wiki/PhotoRec_FAQ#I_can.27t_move.2C_delete.2C_rename_the_recovered_files_.21](http://www.cgsecurity.org/wiki/PhotoRec_FAQ#I_can.27t_move.2C_delete.2C_rename_the_recovered_files_.21) i get the following message: No such file or directory - no matter how i put it

---

### Post by amayan on 2013-04-30
a ha! turns out that after all my whining i could use the 'gksudo nautilus' and simply (but obviously) search for the required files, which are now deleted :)

---

### Post by coffeecat on 2013-04-30
> **amayan said:**
> a ha! turns out that after all my whining i could use the 'gksudo nautilus' and simply (but obviously) search for the required files, which are now deleted :)

Actually, they're not - unless you did a hard delete with shift+del. If you simply used the delete key, all you have done is to move them to root's trash. They may not be cluttering up your Pictures folder any more, but they are still cluttering up your hard drive. If you want to delete them properly, post back.

By the way, The Cog's advice should have worked, and would have deleted the files properly. If it didn't for you it may be because you typed something wrong in the terminal. If you had posted more details we could have helped more.

---

