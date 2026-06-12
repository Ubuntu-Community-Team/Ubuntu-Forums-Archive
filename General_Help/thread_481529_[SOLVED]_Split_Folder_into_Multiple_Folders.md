---
title: "[SOLVED] Split Folder into Multiple Folders"
date: 2007-06-22
forum: General Help
---

### Post by rolodoom on 2007-06-22
Hello there. I have a folder with a lot of files (like 70 Thousand). 

1. Is there any way top split them into multiple folders 'cause it takes a lot of time to open the folder in nautilus.

2. and to create some cd iso files??

Thanks

---

### Post by steve0921 on 2007-06-22
If nautilus is too painful to use for this task, you may want to just do it from a terminal (In applications->accessories). You'll need to use the cd (change directory...for moving around) mkdir (make directory) and mv (move files).

For more info, check out the links  in [this helpful forum post.]("http://ubuntuforums.org/showthread.php?p=990636").

For the iso files, I recommend using gnomebaker (applications->sound&video).

---

### Post by McNils on 2007-06-22
> **rolodoom said:**
> Hello there. I have a folder with a lot of files (like 70 Thousand). 

1. Is there any way top split them into multiple folders 'cause it takes a lot of time to open the folder in nautilus.

2. and to create some cd iso files??

Thanks

I don't know of a program that does what you are looking for. But it can be done in a terminal.

```

let fileCount=1000
let dirNum=1

for f in *
do
  [ -d $f ] && continue
  [ $fileCount -eq 1000 ] && {
      dir=$(printf "%03d", $dirNum)
      mkdir $dir
      let dirNum=$dirNum+1
      let fileCount=0
  }

  mv $f $dir
  let fileCount=$fileCount+1
done

```
This code creates folders and puts 1000 files in each of them.

And for yor second problem you have mkisofs. But I recomend k3b.

---

