---
title: "Applying Imagemagick convert command to lots of files in lots of sub-directories..."
date: 2006-10-29
forum: General Help
---

### Post by Greguti on 2006-10-29
Hi all

I need to create 50x50 pixels cover.bmp files in the sub-folders of my music collection.

For now, I have cover.jpg files that I want to keep. The structure is: */media/iaudio/music/artist/album/cover.jpg*

I can apply the following command, subfolder after subfolder:

```

convert -resize 50x50 cover.jpg cover.bmp

```

But of course it's very annoying to do it for each one (more than 250 cover.jpg files to do!). 

I can create a file with the paths to all the cover.jpg:

```

find . -name cover.jpg > covers.txt 

```

But I don't know how to automate the task, so that it will process the conversion for ALL the cover.jpg files found in the structure.

I guess I must create a script that does the following things:

1 - browse the /media/iaudio/music subfolders in order to find cover.jpg files
2 - apply the "convert" command for each cover.jpg file found
3 - Job done!

Any suggestions to help me? I'm not used to scripts, and I'm quite new in Linux.

Thanks for your help

Greg

---

### Post by yabbadabbadont on 2006-10-29
This assumes that covers.txt is in the current directory and that it was created using the same find command that you posted.

First, run it like this as a test:
```
while read current
do
    echo convert -resize 50x50 "$current" "$(dirname $current)/cover.bmp"
done < covers.txt

```

If the filenames look correct in the output, then remove the word, echo, and run it again.

---

