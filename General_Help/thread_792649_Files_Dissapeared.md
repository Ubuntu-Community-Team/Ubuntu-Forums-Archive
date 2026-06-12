---
title: "Files Dissapeared"
date: 2008-05-13
forum: General Help
---

### Post by Zatarg on 2008-05-13
I dual boot ubuntu hardy with vista,
I needed to reinstall vista so I copied the files I needed to keep to the ubuntu partition.

I reinstalled vista, (bout 4 days ago) and have been using the files on ubuntu, however I tried to move them back to Vista, and of the 5gb of files, only 78mb went over, and the rest have disappeared. 

I was using cut and paste, and i cant see them as hidden folders, or nor does the search function find them.

Is there any way i can get these files back?

Cheers

---

### Post by prshah on 2008-05-13
> **Zatarg said:**
> however I tried to move them back to Vista, and of the 5gb of files, only 78mb went over, and the rest have disappeared. 


Did something happen to interrupt the moving process?

In any case, either check the trash, or the /lost+found directory.

---

### Post by Zatarg on 2008-05-13
No, it complete successfully, or i am assuming so as the progress bar reached the end and the moving files window disappeared.

Nothing in trash nor lost+found.

EDIT: Acessing lost+found told me i didnt have the permission so i sudo nautilus-ed to get in, however I just noticed i get this error in the console:

```
steven@steven-laptop:~$ sudo nautilus
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:6596): WARNING **: Unable to add monitor: Not supported

--- Hash table keys for warning below:
--> trash:///

(nautilus:6596): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:6596): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
steven@steven-laptop:~$ 

```

Is this maybe why i can't see anything in lost+found? And if so how would i enable user sharing?

Thanks again.

---

