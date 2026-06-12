---
title: "Scripts/files in home directory do not run/execute regardless of permissions"
date: 2006-10-13
forum: General Help
---

### Post by usr16 on 2006-10-13
This problem has me baffled and unfortunately I don't have yet much experience with Linux. I suppose the solution to this must be simple, for those that know it.

At one point scripts in my home directory have ceased working regardless of permissions, either directly from the console or with Konqueror for example.

IOW, The same script in the /bin directory works but not if it is my home directory. I also found the same applies to any executable.

The error message is always the same:

bash: <name of file> command not found

Strange...

---

### Post by JonahRowley on 2006-10-13
Is **~/bin** in your **$PATH** variable?  Also, is home on its own partition and is it mounted with the noexec option?  Check for that in **/etc/fstab**.

---

### Post by PriceChild on 2006-10-13
Unless the location of the script is in your path, you will need to give ubuntu the location.

e.g. if located in current dir:
./command

or

/path/to/command

---

### Post by usr16 on 2006-10-13
> **PriceChild said:**
> Unless the location of the script is in your path, you will need to give ubuntu the location.

e.g. if located in current dir:
./command

or

/path/to/command

Thanks for the replies, 

No, the home directory is not in the $PATH but yes if I specify the path (or ./) then I can run it from the console, was surprised since I didn't have to do it this way before (still too used to Windows I suppose). It also previously worked by simply clicking it in konqueror. 

So I assume I will solve this problem by simply adding the home dir (~/) in the $PATH variable? Which perhaps it got removed for some reason...

Thanks again.

---

### Post by JonahRowley on 2006-10-14
I wouldn't add ~ to your path.  **~/bin** is the convention, which means you can keep ~ as messy as you like.  There is an option commented out in either **~/.bashrc** or **~/.bash_profile** to add **~/bin** to your path.  Uncomment that, then start a new console (or run that file, like **. ~/.bashrc**) and you should be up and running.

---

