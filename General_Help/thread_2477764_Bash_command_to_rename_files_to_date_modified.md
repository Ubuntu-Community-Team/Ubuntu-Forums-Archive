---
title: "Bash command to rename files to date modified"
date: 2022-08-06
forum: General Help
---

### Post by rufuz2 on 2022-08-06
Hi ubuntuforums. 

[B][SIZE=3]EDIT: Don't use this code. For some reason it deletes some files. I don't understand why it would do that. Do you? 

EDIT2: I think it's because Snapchat messes up the time created/modified somehow, so that a lot of files have the same date modified. Use at your own risk and remember to make backups before executing. [/SIZE][/B]

I'm not sure where posts about shell/bash scripting should go, so I thought I'd just share this here. For the last few hours I've been trying to figure out how to mass rename my Snapchat videos to the last time they were modified, because Snapchat assigns just a random number to them. [s]I finally figured it out after a lot of searching and experimenting, so I wanted to share it.[/s] 

```
find -type f -name "Snapchat*" -printf '%f\n' | while read a; do n=$(date +%y%m%d-%H%M%S -r $a); mv "$a" "$n.mp4"; done
```

This renames all files starting with "Snapchat" to the date and time they were modifed and adds ".mp4" at the end. Please note that this renames all files into .mp4 files. It can be extended to read the file extension, but I don't need it to and I've spent enough time on this already. 

):P

---

### Post by &amp;KyT$0P# on 2022-08-06
> **rufuz2 said:**
> EDIT2: I think it's because Snapchat messes up the time created/modified somehow, so that a lot of files have the same date modified. 

You could add the [FONT=Courier New]-i[/FONT] option in the [FONT=Courier New]mv[/FONT] command so that it will prompt before overwriting.  Refer to [FONT=Courier New]man mv[/FONT] for more info

---

### Post by ajgreeny on 2022-08-06
> **halogen2 said:**
> You could add the [FONT=Courier New]-i[/FONT] option in the [FONT=Courier New]mv[/FONT] command so that it will prompt before overwriting.  Refer to [FONT=Courier New]man mv[/FONT] for more info
This is good advice.

I have the options **-iv** for commands **cp**, **mv** and **rm**, giving me an extra chance to think before the action is taken, just in case it will do something I haven't thought about.

---

### Post by TheFu on 2022-08-06
I'd probably use the stat command to get the ctime for the name of the file.  I'd be worried that the script above would have filename collisions, possibly overwriting files because the date command could easily return the same second.  Or just add a check before renaming for an existing target file and appending a .1, .2, .3, .4 .... as needed.

---

