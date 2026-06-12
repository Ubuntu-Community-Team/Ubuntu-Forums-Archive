---
title: "chmod problem"
date: 2016-10-18
forum: General Help
---

### Post by jgw on 2016-10-18
I was trying to change permissions with chmod.  My plan was to change some folders to 766 (rwxrw-rw-)

My command was: chmod -v -R 0766 Billions
I also tried:              chmod -v -R 766 Billions
                                chmod -v rwxrw-rw-


  What I ended up with was strange and I have no idea what happened.  What happened is:
owner: read and write
group:  list, read and write, no access
other:   list, read and write, no access

If I try chmod -v og-rw it tells me that group and others are changed to rw-  but they are actually 
group:  list, read and write, no access
other:   list, read and write, no access

I am, obviously missing something.

Thank you .........................

---

### Post by Impavidus on 2016-10-18
On directories, read permission means that a user can read which files/directories are present in the directory. Just the filenames, so he can list the files. Write permission means that the user can create and delete files and (empty) directories in that directory. Execute permission means that the user can lookup the inodes of the files/directories in that directory, enabling him to access the metadata on the files in that directory and, if he has sufficient permissions on the files themselves, access the files too. Having read but not execute permissions on a directory is rarely useful.

On files, the meaning of read, write and execute permissions are more straightforward.

---

### Post by jgw on 2016-10-18
thanks for the reply..........

I was trying to change the permissions to write/execute, write, write (create/delete/execute, create/delete, create/delete for folders)  I can do this manually with no problem but I cannot get chmod to do it.  for instance:
chmod 766 on a folder and then do an "ls -ld folder name I am told the permissions are now drwxrw-rw-

What I really have is:
owner: create and delete
group: list, read and write, no access
other: list, read and write, no access

My problem is that I don't get the "no access"

if I do:  chmod -R 766 filename. and check the permissions contained in the folder I find there is another folder and a couple of files.  The folder is exactly like the containing folder:
owner: create and delete
group: list, read and write, no access
other: list, read and write, no access

The files, on the other hand are all read and write.  My problem is, obviously, that the folders are flat out wrong (and make no sense, ie. list, create/delete, no access (which I think means that I can list and create and delete but not access it).  It gets even better in that the no access seems to not actually be true as I can access the folder(s) and see what is in them and then access the contents.  My question, therefore, is what is with the "no access?"

---

### Post by Morbius1 on 2016-10-18
Let's use the "Folder" metaphor a bit.

The execute bit on a file allows you to ... well ... execute the file.

But the execute bit on a Folder allows you to open it to see what's inside. It's the "open it" or traverse part of your chmod that's missing.

chmod 766 doesn't do that. chmod 777 does.

Folders have to have odd octal permission numbers on them if you want users to "open" them since that will include the "execute" bit.

[COLOR=#0000cd]*Note: It's a real bad idea going around doing a recursive octal chmod on a folder and all it's contents because you will set all your files to be executable*[/COLOR].

 So this is something I would not do:
```
chmod -R 766 /XXX
```
This would be worse:
```
chmod -R 777 /XXX
```
This would be what I would do:
```
chmod -R a+rwX /XXX
```
The big "X" in "rwX" will set all your folders as executable but will not make files executable unless they were that way to begin with.

Remember UNIX was invented back in the late 1960's when everyone was on drugs so this all made perfect sense.

---

### Post by Impavidus on 2016-10-18
Some of us are really used to the octal permissions (like 766) or the output from ls (like rwxrw-rw-), which simply stand for read, write and execute. These notations work identically for files and directories. The GUI file manager may change the exact words depending on whether it's a file or a directory. So list=read, read and write=write, no access=NOT execute.

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by jgw on 2016-10-18
I just noticed that I have double posted this - My apologies

thanks for the reply..........

I was trying to change the permissions to write/execute, write, write (create/delete/execute, create/delete, create/delete for folders)  I can do this manually with no problem but I cannot get chmod to do it.  for instance:
chmod 766 on a folder and then do an "ls -ld folder name I am told the permissions are now drwxrw-rw-

What I really have is:
owner: create and delete
group: list, read and write, no access
other: list, read and write, no access

My problem is that I don't get the "no access"

if I do:  chmod -R 766 filename. and check the permissions contained in the folder I find there is another folder and a couple of files.  The folder is exactly like the containing folder:
owner: create and delete
group: list, read and write, no access
other: list, read and write, no access

The files, on the other hand are all read and write.  My problem is, obviously, that the folders are flat out wrong (and make no sense, ie. list, create/delete, no access (which I think means that I can list and create and delete but not access it).  It gets even better in that the no access seems to not actually be true as I can access the folder(s) and see what is in them and then access the contents.  My question, therefore, is what is with the "no access?"

---

### Post by jgw on 2016-10-18
Thanks again for the reponses.

I did the chmod -R a+rwX /XXX and it worked like a charm!  (no more "no access")  

I will mark this one solved.

Thanks again!!!!!!!!!!!!!

---

