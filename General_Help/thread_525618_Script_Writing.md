---
title: "Script Writing"
date: 2007-08-14
forum: General Help
---

### Post by viajador on 2007-08-14
Hi there!

I've recently started to go beyond the obvious in Linux and went to write my bash scripts for those click-click-click tasks that get you bored. I've encountered the first task that I'm not being able to write down to a script.

Basically,what I want is a script that checks a given file's date and moves it to a given folder. For instance: File01 is from June2007, so the script moves it to a folder named 200707.

Is this possible in batch scripting or is it a task that calls for Python or similar? And where can I learn the skills to write it?

And many obrigados for your help :)

---

### Post by nichipet on 2007-08-14
Let me see if I understand what you want. If the last modified date of a file is, for example, April 2007, you want it moved to an April2007 folder, correct? Do you want it copied or moved? If it is moved, the script either has to know the new locations of files which can get tricky (but still very possible) to be run again when the modification dates change, if it's copied you can run the script on the same location every time which of course is much simpler but will take up more disk space (since every file gets doubled). I am about halfway to finishing a script that will do what you want, if I understand what you are looking for.

---

### Post by AlexThomson_NZ on 2007-08-14
The 'find' command can return files created after a certain date, just do a move based on this output

---

### Post by TimSNL on 2007-08-14
> **viajador said:**
>  And where can I learn the skills to write it?

Google "bash script" and you will find many tutorials to help you learn.

Here are the first two I got mrom my search:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
[http://www.panix.com/~elflord/unix/bash-tute.html]("http://www.panix.com/~elflord/unix/bash-tute.html")

Happy Reading 8-)

---

### Post by pmg on 2007-08-14
> **nichipet said:**
>  Do you want it copied or moved?
There is a third option on Linux.  You could link the file in another directory, with the **ln** command.  That way it exists in both the new directory and the old one, but it's still one flie and only exists on disk once so it's not using twice the disk space.  Updates to the file can use either filename, and the meta-data info other then filename (e.g. inode, owner, modification time) is only on disk once so changing it via either name updates this common info.  If it's erased from one directory it's still in the other, so not erased from disk.

---

### Post by nichipet on 2007-08-14
> **pmg said:**
> There is a third option on Linux.  You could link the file in another directory, with the **ln** command.  That way it exists in both the new directory and the old one, but it's still one flie and only exists on disk once so it's not using twice the disk space.  Updates to the file can use either filename, and the meta-data info other then filename (e.g. inode, owner, modification time) is only on disk once so changing it via either name updates this common info.  If it's erased from one directory it's still in the other, so not erased from disk.

Hm... is that a symbolic link or hard link? Which would be better in this case? That's true, a link may prove better, but it could be the OP wants to move them and skip linking.

---

### Post by pmg on 2007-08-15
What I described is a hard link, in which case each filename is equivalent.  A symbolic link (created with **ln -s**) is a new name that simply points to the old name.  In that case, if the "old" filename is erased the symlink points to something that doesn't exist (i.e. nothing.)

Yes, I agree it might not be what the original poster wants, but when you pointed out the options of copy vs. move, I thought a hard link might be a third interesting alternative, depending on the original goal.

---

### Post by viajador on 2007-08-15
> If the last modified date of a file is, for example, April 2007, you want it moved to an April2007 folder, correct?

Partially :)

What I really want to do is the following:

1) Get all the files from my digital camera with Gphoto2;

2) Move *.JPG to a folder and *.AVI to other folder

3) Create monthly folders and move files according to the file's creation date.

I've already made a script to steps 1) and 2) and have been doing step 3) by hand - which is exactly what I want to automate. The ideal would be to sniff the EXIF details and move the files regarding their "click" date, but since I upload my pictures in a daily basis, I'll be content with the "creation date".

> Google "bash script" and you will find many tutorials to help you learn.

Here are the first two I got mrom my search:
[http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://www.panix.com/~elflord/unix/bash-tute.html](http://www.panix.com/~elflord/unix/bash-tute.html)

Thanks! I'll look around. I've been browsing in linuxcommand.org, but that's kind of a dictionary and It would take forever to read every single command to find something useful.

> The 'find' command can return files created after a certain date, just do a move based on this output

I'll give that one a try! Thanks!

---

### Post by brennydoogles on 2007-08-15
> **viajador said:**
> Partially :)

What I really want to do is the following:

1) Get all the files from my digital camera with Gphoto2;

2) Move *.JPG to a folder and *.AVI to other folder

3) Create monthly folders and move files according to the file's creation date.

I've already made a script to steps 1) and 2) and have been doing step 3) by hand - which is exactly what I want to automate. The ideal would be to sniff the EXIF details and move the files regarding their "click" date, but since I upload my pictures in a daily basis, I'll be content with the "creation date".



Thanks! I'll look around. I've been browsing in linuxcommand.org, but that's kind of a dictionary and It would take forever to read every single command to find something useful.



I'll give that one a try! Thanks!

If you haven't already, you could try F-spot. When it imports photos, it has the option to automatically sort the photos by month, day, and year.

---

### Post by nichipet on 2007-08-15
> **brennydoogles said:**
> If you haven't already, you could try F-spot. When it imports photos, it has the option to automatically sort the photos by month, day, and year.

I was going to suggest looking at something like F-spot. On Mac OS X, I think iPhoto can automatically sort photos the same way and I'm sure someone has added that feature to a Linux program by now.

---

### Post by viajador on 2007-08-15
I don't like to use photo-organizers.

I've tried a few back in windows and I've tried F-Stop in Ubuntu. For some reason, I just get a mess out of those programs. I really rather have an organized folder hierarchy. Anyhow, I've written my script! :D

Here it is:

```

#! /bin/bash

gphoto2 -P          # The -P option gets all your files from your 
                         # camera, both pictures and videos

JPGS="*.JPG"
AVIS="*.AVI"

# Creating folders and moving JPG files

for file in $JPGS
do
mkdir /home/<username>/<folder_where_you_keep_your_pictures>/"`date -r $file +%Y%m`"
mv $file /home/<username>/<folder_where_you_keep_your_pictures>/"`date -r $file +%Y%m`"
done

# Creating folders and moving AVI files

for file in $AVIS
do
mkdir /home/<username>/<folder_where_you_keep_your_videos>/"`date -r $file +%Y%m`"
mv $file /home/<username>/<folder_where_you_keep_your_videos>/"`date -r $file +%Y%m`"
done

echo "Done, Boss!"

```

I've posted a set of instructions to use it. It waits for moderation approval.

---

### Post by pmg on 2007-08-16
How about the following:
```

ls -go --time-style=+%Y%m | awk '{system("echo mv "$5" /path/to/"$4"/"$5)}'

```
The **echo** in there is to just print out the commands rather then execute them, to make sure it's what you really want to do.  Take the echo out to have it really move the files.

---

### Post by Chaotic Thought on 2007-08-16
I saw this post and tried writing the following but now I see you have something already. In any case here's my alternate version for you to try, which uses the find(1) command. The **-iname** predicate of find matches patterns such as '*.jpg' without regard to case. Read the manual page for more information about the syntax.

The date format is supplied by the part in the find command that says **-printf**.

```

#!/bin/bash

# Usage: sort_images PATTERN [ARGS ...]
#
# Sort files matching the shell pattern PATTERN into subdirectories based on
# the ctime value returned by find(1). For example, files with a ctime of
# 2007-08-01 would be placed in the subdirectory "2007-Aug".
#
sort_images()
{
   pattern=${1:-"*.jpg"}
   shift

   find . -iname "$pattern" -printf '%AY-%Ab: %p\n' -maxdepth 1 "$@" |
   (
      while read -r
      do
         date="${REPLY//%:*/}"
         filename="${REPLY//#*: /}"
         dest="$date"
         [ ! -d "$dest" ] && mkdir -v -p "$dest"
         mv -v "$filename" "$dest"
      done
   )
}

gphoto2 -P
sort_images "*.jpg"
sort_images "*.jpeg"
sort_images "*.avi"

```

---

### Post by viajador on 2007-08-18
That one is great! I'll use it instead of mine. I've posted (before I saw your post) mine in tips and tutorials.

See it here: [http://ubuntuforums.org/showthread.php?t=526437](http://ubuntuforums.org/showthread.php?t=526437)

Please reply to my thread with your better version.

Regards and keep up the great work.

---

### Post by vanadium on 2007-08-18
Time now perhaps now to try to sort effectively on exif dat instead of file date. Someone&#347; got a suggestion?

---

