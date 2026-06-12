---
title: "Read-Write Permission Blocked"
date: 2012-11-26
forum: General Help
---

### Post by Seadevil on 2012-11-26
I created a new folder and opened properties, under File Access:
i selected Read and write...clicked on "apply permissions to Enclosed files" ...but it doesn't take!  keeps going back to -.
and i cannot copy a file into the folder.

How do I overcome this blocking mode?

thanks

---

### Post by pkadeel on 2012-11-26
where did you create that folder?

if you are not uneasy with command line then you can change the permissions with terminal
```

chmod -Rv a+rwX,go-w /path/to/your/folder

```

---

### Post by dannyboy79 on 2012-11-26
> **Seadevil said:**
> I created a new folder and opened properties, under File Access:
i selected Read and write...clicked on "apply permissions to Enclosed files" ...but it doesn't take!  keeps going back to -.
and i cannot copy a file into the folder.

How do I overcome this blocking mode?

thanks
when you click on a folder, it opens your file manager with your users permissions. So you'll only be able to manipulate and manage file/folder properties within your home directory. ANy files or folders outside of /home/username/ wont be able to be changed unless you envoke your file manager with gksudo, then enter your users password. THis will open the file manager with ROOT privalages so just be very careful and once you're done doing what your original goal was, close the file manager.  Good luck.

one way I do it is to hit ctrl-alt-f2, then type in
gksudo nautilus

---

### Post by Seadevil on 2012-11-26
hi, thanks for the response.

OK, I created the folder "rainlendar" in the /Downloads folder.

when I input: chmod -Rv a+rwX,go-w /path/to/your/folder    as:

chmod -Rv a+rwX,go-w /rainlendar   from the Downloads folder....

I get this message:  invalid mode: 'a+rwX,'  

is there a space between , and go ?  or leave out the comma?









d

---

### Post by Seadevil on 2012-11-26
let me amend that:   reinput chmod -Rv a+rwX,go-w rainlendar,  it changed and now i got:

mode of 'rainlendar retained as 0755 (rwxr-xr-x)

however, nothing was changed as I still cannot copy another folder "skins" into /rainlendar.
???

---

### Post by rnerwein on 2012-11-26
> **Seadevil said:**
> let me amend that:   reinput chmod -Rv a+rwX,go-w rainlendar,  it changed and now i got:

mode of 'rainlendar retained as 0755 (rwxr-xr-x)

however, nothing was changed as I still cannot copy another folder "skins" into /rainlendar.
???
hello
you try to copy /rainlendar --> / is the root directory and write access is only for super user ( root )
allowed (drwxr-xr-x 43 root root 4096 Nov 22 11:03 /)

---

### Post by pkadeel on 2012-11-26
> **Seadevil said:**
> let me amend that:   reinput chmod -Rv a+rwX,go-w rainlendar,  it changed and now i got:

mode of 'rainlendar retained as 0755 (rwxr-xr-x)

however, nothing was changed as I still cannot copy another folder "skins" into /rainlendar.
???
This is most probably the ownership issue.
inside your Downloads folder do
```

ls -l

```
it will output the all entries in downloads folder. check who is the owner of the "rainlendar" entry.

---

### Post by Shuudoushi on 2012-11-26
Okay first make sure the file is made in the Downloads folder. If its path is truly /home/<you>/Downloads and you do not have write permissions then use this command in the term and make sure you use the cd command to get to your downloads folder:```
 chown <file name> <current owner> <you> 
``` that should fix the problem. Please note that if you mess up that command it will just spit out and error; if it does just flip the current owner and you around.

---

### Post by Seadevil on 2012-11-26
pkadeel,  I did that.  I have two folders in Downloads...1. rainlendar 2. skins.  How do i check for ownership?

I tried Shuudoushi's formula:  chown rainlendar dave dave  and get 
chown: invalid user: 'rainlendar'

then tried:   chown rainlendar root dave and get same error msg.

GEEZ...HIT ME WITH A BANANA !!!!   I WAS TRYING TO "DRAG" THE SKINS FOLDER INTO RAINLENDAR.  NOW I 

DID A "RIGHT CLICK & COPY"  AND IT PUT SKINS INTO THE RAINLENDAR FOLDER. LOL.

I BEEN EATING SOUP WITH A FORK ! GEEZ

THANK YOU FOR YOUR HELP.  GREATLY APPRECIATED AND I LEARNED MUCH.

---

### Post by Seadevil on 2012-11-26
hello Rnerwein,  you misunderstand.  in Downloads folder, there are two folders

1. rainlendar  2.  skins

I tried to put 'skins'  into   rainlendar.   or #2  into #1.

Error message says:   Error moving file:  PERMISSION DENIED.

THANK YOU FOR HELPING. I FIXED IT.

---

### Post by Shuudoushi on 2012-11-26
Maybe i should get sleep before trying to tell people commands for now on. >.> The command is: ```
chown <owner> <you> <filename>
``` That one should be right as is. And cg on getting it fixed! XD

---

