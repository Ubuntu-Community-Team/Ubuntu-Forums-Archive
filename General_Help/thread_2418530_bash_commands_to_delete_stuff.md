---
title: "bash commands to delete stuff?"
date: 2019-05-07
forum: General Help
---

### Post by jebi on 2019-05-07
hi,

when i need to dump stuff and make folders and paths i use sudo nautilus then make or whatever,

 but when i need to delete them i send them to the recycle bin, but you get an error about ownership or authorization or something

and i have to use this command   sudo chown -R $USER:$USER ~/.local/share/Trash/  

and then delete, could some explain what exactly this means?

i know chown is change owner and ~/.local/share/Trash/ is the path but what is -R $USER:$USER? 

 also there must be a better way with a GUI? 

 and how do i delete say a file or folder from the terminal without this hassle?

 thx

---

### Post by CatKiller on 2019-05-07
**rm** (short for **r**e**m**ove) is the command to delete things.

---

### Post by TheFu on 2019-05-07
Stop using sudo with GUI programs.  It breaks things. What you've described above is just 1 of the problems. There are others.

Shell commands to delete stuff are:
```
rm
rmdir

```
These can be used with and without sudo. You should never need to use sudo to remove things in your HOME.

Did I mention, don't use sudo with GUI programs?  Don't.

All shell commands on your computer have a manual page - manpage.  The manpage describes the command, options, caveats, and warnings.  Every package installed should provide an updated, current, manpage for that tool.  Over the years, commands slightly change, so the local manpage really is the best place to get the most current, accurate, information.

However, if you seek to gain real, directed, knowledge, presented in the correct order, then [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good source.  Unix commands build on each others. Jumping to the middle without the basics makes learning harder and longer.

"Hassle" means different things to different people.  rm ~/path/to/files* will delete all the files in ~/path/to/.

BTW, shell commands don't use the Trash bin. When you delete something, it is gone, gone, gone.

---

### Post by yetimon_64 on 2019-05-08
> **jebi said:**
> hi,

when i need to dump stuff and make folders and paths i use sudo nautilus then make or whatever,

 but when i need to delete them i send them to the recycle bin, but you get an error about ownership or authorization or something...
As TheFu mentions ... > ... don't use sudo with GUI programs? ** Don't**. My emphasis on the last word quoted.
 By using "sudo nautilus" any files created or sent to trash are owned by the root user not you.
There are some circumstances where using sudo with a graphical application can have you left locked out of your user account desktop.

Really *_**don't do it**_*, but if you absolutely insist on such actions use the **-H switch** eg, "**sudo -H <graphical-app-name>**", this will at least keep root to its own home directory and not use yours as has happened here.
 But then the root account file system will be left with cruft files unseen in it instead, using up disk space etc.

Easier to just NOT use sudo and graphical applications as stated above, unless of course you are operating on system owned files and then ensure you include the -H switch for safety.

> **jebi said:**
> ...and i have to use this command   sudo chown -R $USER:$USER ~/.local/share/Trash/ and then delete, could some explain what exactly this means?   
You need to do that because you used nautilus as root by invoking it with "sudo" and the files in trash cannot be deleted by you as they now belong to the root user.

As you go on to mention the "chown" is change ownership; the -R switch means to do so "recursively" (that is any folder involved containing further files will all be changed back over to your ownership as well); the $USER is a system variable which when used will include the issuing users username into the command. For instance **if** you use the name "jebi" as your installation user name, then the command above gets read by the system as ...
 ```
sudo chown -R jebi:jebi ~/.local/share/Trash/
``` In my case I use the name "yetiman" in my install the very same command here would be read as...
```
sudo chown -R yetiman:yetiman ~/.local/share/Trash/
```


 > **jebi said:**
> also there must be a better way with a GUI? 

 and how do i delete say a file or folder from the terminal without this hassle?

 thxThis hassle came about by using sudo and nautilus, DO NOT use sudo when creating or saving files to your home directory.

You only ever need to use sudo for altering system files; something you need to take extreme care when carrying out.

One last reference to TheFu's post ...
> BTW, shell commands don't use the Trash bin. When you delete something, it is gone, gone, gone.         

This is true under normal circumstances, but you can have the rm command send files to the trash bin with the installation of the "trash-cli" package.

If that package is installed the rm command must be escaped to directly delete any file.

For instance here to directly delete "~/path/to/files*" I have to issue the command as ...
```
\rm ~/path/to/files*
```

Issuing ...
```
rm ~/path/to/files*
```
will in my case send the files involved to the trash bin.
This does NOT work with the rmdir command, only with the rm command though.

Regards, yeti.

---

