---
title: "I don't have permission to access other drives"
date: 2013-11-03
forum: General Help
---

### Post by mcjohnalds45 on 2013-11-03
After messing with the user accounts & names, I found I can't access my external drives without using sudo.

When I access one normally:
```

> cd "/media/john/FreeAgent Drive"
bash: cd: /media/john/FreeAgent Drive: Permission denied
```

  However, using sudo I can cd into it and view the permissions:
```

> sudo cd /media/john
> sudo ls -l
drwx------   1 john john 20480 Sep 24 10:45 FreeAgent Drive/
```
  
The strange thing is I *am* john, because id returns:
```
uid=1003(john) gid=1003(john) groups=1003(john), ...
```

[HR][/HR]
So I'm interpreting this is as "You cannot access this drive. Only john can access this drive. You are john."

I've also tried the following with no result.
 ```

> sudo chown john:john "FreeAgent Drive"
> sudo chmod o+rw "john/FreeAgent Drive"
```

---

### Post by ajgreeny on 2013-11-03
I am a bit suspicious of this output ```
uid=1003(john) gid=1003(john) groups=1003(john), ...
``` which shows your uid as 1003, whilst I think probably the system is expecting your uid to be 1000.

If this is a multiuser system it may be that I am completely wrong about this, but I can not see any other clues as to the refusal to let you, john, access that drive which, as you say, is owned by john.

---

### Post by Morbius1 on 2013-11-03
> **mcjohnalds45 said:**
> After messing with the user accounts & names, I found I can't access my external drives without using sudo.
"messing" with user accounts is probably the cause of all this and I'm probably not the one to get you out of this but the permissions of /media/john/FreeAgent Drive is almost irrelevant if /media/john isn't correct. To extend what          ajgreeny just posted run the following command:
```
getfacl -tn /media/john
```
Do you get this among the output:
> user   1003      r-x
Or this:
> user   1000      r-x

---

### Post by mcjohnalds45 on 2013-11-03
I solved it, YAY!!!! Thanks for the tip, I didn't know about ACLs till now.

If anyone's wondering, "/media/john/"'s owner and group was root, and it's ACL didn't give john rwx permissions.

```

> getfacl -t /media/john
# file: media/john
USER   root      rwx     
user   old       r-x     
GROUP  root      ---     
mask             r-x     
other            ---
```

Typing the following gave john (and only john) rwx permissions, letting me access the external hard drives inside.

```

sudo setfacl -m u:john:rwx /media/john
```

Thanks Morbius1 and ajgreeny :D

---

### Post by Morbius1 on 2013-11-04
/media/john doesn't need to have rwx permissions. All it needs is r-x permissions: The ability to read and list the contents of the directory.

Everyone's /media/$USER directory has ACL's set to r-x as that directory is created and it's permissions set by the system not the user. If it had to be forced to rwx no one by default would be able to access an external storage device.

I suspect that this resolved the issue for you not because you set it to rwx but becase you restated the user "john" with it's new uid instead of the one you had when you first installed your system. This might be a bug since the system should have changed "john's" uid everywhere it was referenced. I guess it depends on how much messin' you did when you where "messing with the user accounts & names".

---

