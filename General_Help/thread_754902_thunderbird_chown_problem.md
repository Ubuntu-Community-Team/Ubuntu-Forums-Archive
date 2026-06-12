---
title: "thunderbird: chown problem"
date: 2008-04-14
forum: General Help
---

### Post by nahhy on 2008-04-14
Hi everybody,
I have problem with chown persmission. Here is the situation. i have two python scripts, the first allows me to add a new system user. In this stage i used this command line:
```
 os.system('useradd -m -G adm,dialout,cdrom,floppy,audio,dip,video,plugdev,lpadmin,scanner,admin -s /bin/bash '+LOGIN)

```
The problem that it creates a new user without generating all subdirectories in the home such as Documents, music,etc.
My second script customize the thunderbird's profile of the new added user. But when i do 
```

os.system('sudo chown -R '+LOGIN+':'+LOGIN+' '+USER_DIR+'/.mozilla-thunderbird')

```

it doesn't really work. when i log into the system with the new account and do  ```
ls -la
``` i found that user permission is changed like this
```
drwxrwxrwx  3 sthsa sthsa 4096 2008-04-14 11:14 .mozilla-thunderbird
```

 but my thunderbird doesn't work. When i do again a chown, the thunderbird take a consideration . 

What i want is creating a new user with generating all his subdirectories and to give enough permission to the .mozilla-thunderbird so that when the i log with the new account i had my profile thunderbird already configured.any idea.

---

### Post by davidpbrown on 2008-04-14
I haven't done this before but understand there is a template for new user profiles at /etc/skel.
Maybe look to changing that and it might copy all directories there across to new profiles??

---

