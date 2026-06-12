---
title: "Can't execute scripts on vfat volume"
date: 2006-10-23
forum: General Help
---

### Post by snaga on 2006-10-23
I have a thumb drive thats a vfat volume mounted. The scripts on it all have 777 perms, but they won't execute. I still get an error

```
bash: ./compare_symbols.pl: /usr/bin/perl: bad interpreter: Permission denied
```

If I move the code to the HD, it works fine. I am assuming that there is a mount option I am not using, but I cannot find it.

Any hints would be appreciated.

---

### Post by chavo on 2006-10-23
Should be able to do this by adding exec to the mount options for this partition. Here's my fstab entry for my documents partition ->

```

UUID=CE40-EFBB  /media/docs     vfat    utf8,umask=000,user,exec 0 0

```

I can execute scripts or programs on this partition, including windows programs with wine or cedega.

---

### Post by snaga on 2006-10-23
Huh...could have sworn I'd tried that... 

Thanks!

---

### Post by TiredBird on 2006-10-23
When you mount a thumb-drive using fstab, unless you have a 'uid' option, it will end up being owned by 'root'. You cannot change the permissions on the underlying files with a chmod on the mount point, even if you use sudo. Once a file system is mounted, the ownership established by the mounting cannot be changed. 

VFAT partitions have no ownership or permissions to start with. They have to get it from the mount command or from fstab and if you don't specify the ownership and permissions it will take on the defaults and it can't be changed without remounting it.

Assuming this is your problem, add 'uid=1000' and 'umask=000' as options to your fstab entry. This will make the owner number 1000, (the number that was probably assigned to your login when you installed - might want to check though to be sure) and the permissions will be your default which is probably 755, making it executable by anyone.

To run a script on Ubuntu you will have to give it the full path, eg: ```
/home/username/scriptname
``` in order to execute it. Even if you happen to be in the same directory with the script, the system will follow the environment path and not find it unless you give it the full path to execute. Also make sure that the first line of your script is ```
#! /bin/bash
```I don't mean to sound condescending with any of these suggestions but I'm a newb and these are all mistakes I made personally. It's likely that one of them is causing your problem.

---

### Post by Ocxic on 2006-10-23
vfat partitons do not have any permissions set, the filesystem doesn't have that ability, it's possible that scince the file does not have any permissions associated with it, it doesn't have permission to be an executable and therefore will not run.

i beleive that the .pl mean python or perl try:

"python compare_symbols.pl"
or
"perl compare_symbols.pl"

---

### Post by TiredBird on 2006-10-23
I agree, VFAT files systems don't have permissions or ownership to start with but when you mount them, either with the 'mount' command or through 'fstab' they are assigned ownership and permissions by the Linux system. If you don't specify otherwise, the ownership and permissions will all be defaults which won't let you execute a script. In fact, if you just specify 'defaults' as is commonly done, it will default to 'noexec'.

To be sure that is not the case, 'exec' should be specified as one of the options in addition to the others I mentioned.

---

### Post by TiredBird on 2006-10-23
I'm wrong about 'noexec' being a default. That is only true if you specify 'user', then 'noexec' follows automatically. I still think its a good idea to specify 'exec' as one of the options.

---

### Post by TiredBird on 2006-10-23
Looking at the error message, it does look as if the script was written in perl. However, bash can't seem to find the perl interpreter. The ./ on the front of the script name should take care of the path business, at least as far as the script goes. Snaga says it works from the hard-disk but not the flash-disk. That tells me its a permission problem. I would like to see the  fstab entry. I think something there is screwing it up.

---

