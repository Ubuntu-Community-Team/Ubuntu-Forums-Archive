---
title: "problem with folder permision..."
date: 2008-03-21
forum: General Help
---

### Post by Mia_tech on 2008-03-21
I just moved a folder from another ubuntu machine to my pc, and I can open files inside the folder without problem but when it comes to saving the modified file, I get a permision error, I issued:
```
sudo chmod ugo+rwx /folder/myfolder
```

but after that, I'm still unable to save files, I can create new ones though, but no modify the existing ones...any help appreciated

thanks

---

### Post by danwood76 on 2008-03-22
this is because youve only changed the permissions of the folder and not the files within it.

If you were to do:
```

sudo chwon -R username:username /folder/myfolder

```
you would become the owner of all the files and be able to write them without completely opening up the permissions.

Note that the -R makes the function recursive and so it works through all subfolders and files.

---

### Post by Mia_tech on 2008-03-22
> **danwood76 said:**
> this is because youve only changed the permissions of the folder and not the files within it.

If you were to do:
```

sudo chwon -R username:username /folder/myfolder

```
you would become the owner of all the files and be able to write them without completely opening up the permissions.

Note that the -R makes the function recursive and so it works through all subfolders and files.

thanks for the help ... I also could've use the same with chmod

```
sudo chmod -R ugo+rwx /folder/file
```

that would chane the permision on the file and subdirectories

thanks

---

### Post by danwood76 on 2008-03-23
> **Mia_tech said:**
> thanks for the help ... I also could've use the same with chmod

```
sudo chmod -R ugo+rwx /folder/file
```

that would chane the permision on the file and subdirectories

thanks

Yeah but you open the folders up to reading and writing rights to everyone.
One of the beauties of a UNIX operating system is the permissions, if you own the file or folder you naturally can read and write. but if you do the chmod and open the permissions right up anyone can view and change it.

The more files on your system with complete read and write permissions the more insecure you make your system.

---

### Post by Mia_tech on 2008-03-23
> **danwood76 said:**
> Yeah but you open the folders up to reading and writing rights to everyone.
One of the beauties of a UNIX operating system is the permissions, if you own the file or folder you naturally can read and write. but if you do the chmod and open the permissions right up anyone can view and change it.

The more files on your system with complete read and write permissions the more insecure you make your system.

that's true...how would I give full rights to a specific user with chmod?

thanks

---

