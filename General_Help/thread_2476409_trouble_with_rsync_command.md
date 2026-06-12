---
title: "trouble with rsync command"
date: 2022-06-25
forum: General Help
---

### Post by coley9225 on 2022-06-25
I'm having trouble with an rsync command. I'm replacing one of my back up system from cp -Ru to rsync. The way it is written, it won't transfer files, but the(basically)command with only one directory seems to work.:confused:

Problem script:
```
#! /bin/bash

mount /home/rsync


now=$(date +"%m-%d-%y_%I:%M_%p")


echo -e "### Log file for rsync $now ###" > /home/charles/My_stuff/Atom_project_backup/rsync_logs.txt


rsync -arhhvvn --delete --log-file=/home/charles/My_stuff/Atom_project_backup/rsync_logs.txt --include-from=/home/charles/rsync_include.txt /home/rsync


umount /home/rsync



```

And my include list:
```
## List of files to include in rsync backup.

/home/charles/.config
/home/charles/.gnome2
/home/charles/.local
/home/charles/.Shared_files/.password_info
##/home/charles/.Shared_files/.private
/home/charles/.Shared_files/Documents
##/home/charles/.Shared_files/Downloads
/home/charles/.Shared_files/My_stuff
##/home/charles/.Shared_files/Pictures
##/home/charles/.Shared_files/Python_class
/home/charles/.Shared_files/Recipes
/home/charles/.Shared_files/Scripts
/home/charles/.Shared_files/software_manuals
/home/charles/.Shared_files/sounds
##/home/charles/.Shared_files/stuff_for_tabby
/home/charles/.Shared_files/Tests
##/home/charles/.Shared_files/wallpaper



```

This command seems to work fine:
```
#! /bin/bash

mount /home/rsync


rsync -arhhvvn --delete --noatime --log-file=/home/charles/My_stuff/Atom_project_backup/rsync_logs.txt /home/charles/.config /home/rsync


umount /home/rsync



```

I put off asking for help for a week, because I'm sure it is a simple thing I'm overlooking, but I can't find the issue. 
In the include file, I have also tried;
/home/charles/.config/
/home/charles/.config/*
/home/charles/.config/**
and
/home/charles/.config***
No change to results.

Any help would be appreciated.

---

### Post by TheFu on 2022-06-25
Simplify and test.  Repeat.

I use this command to mirror A --> B when I don't care about retaining owners, group and whatever default permissions are used is fine.

```
$ rsync -avz --delete-after  /path/to/SRC/    /path/to/TGT/  
```

Then I might add an --exclude pattern.  I've never used include/exclude files. Sorry.  If the dest isn't specified, it is assumed (what is assumed, I don't know), but the SRC must always be specified.  Other options don't replace that requirement.  Do you have a source specified?

In this command:
```
rsync -arhhvvn --delete --log-file=/home/charles/My_stuff/Atom_project_backup/rsync_logs.txt \
                                              --include-from=/home/charles/rsync_include.txt \
                                              /home/rsync
```

/home/rsync is the SRC, though I suspect you think it is the DEST.  Look at the rsync manpage Synopsis. There's no example that doesn't include SRC, so it is mandatory.
Ah ... the manpage answers the question for what happens when not DEST is specified: 
```
Usages with just one SRC arg and no DEST arg will list the source files
       instead of copying.
```


I'd send the log file to /tmp/.  Writing logs to an area included in the SRC is bad.

---

### Post by norobro on 2022-06-25
Is the "-n" option the problem?

From the rsync man page:> [FONT=monospace][COLOR=#000000]**--dry-r**[/COLOR][COLOR=#000000]**un**[/COLOR][COLOR=#000000], [/COLOR][COLOR=#ff0000]**-n**[/COLOR]
              This makes rsync perform a trial run that doesn't make any changes  (and  produces  mostly
              the  same  output as a real run). 
[/FONT]

---

### Post by coley9225 on 2022-06-25
norobro, no, I'm using the dry  run option because it's faster than the actual copy process.

TheFu, Thanks. It took a little fighting, but that solved the problem, at least in the dry run. I added /home/charles as thesrc, and it wanted to copy everything in my home dir. The final solution was change 'include-from=FILE' to files-from=FILE, set src as ~/, and remove the /home/charles from all the directories listed in the include file. I mistakenly thought the include from file was the source. 

Thanks so much. Now I can use this in place of my script that uses 'cp -Ru /path /to directory path/to/target' to make my redundant backups( I use timeshift for / and back in time for /home, and those are not included in the rsync list.).

I'll go up to top and mark solved.

---

### Post by TheFu on 2022-06-25
If you are doing backups, why not use a better backup tool that has almost the same options as rsync, but does versioning too?  That tool is rdiff-backup.

---

