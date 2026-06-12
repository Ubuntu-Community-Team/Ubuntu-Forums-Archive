---
title: "How to copy certain files to another folder while retaining its hierarchy"
date: 2017-04-21
forum: General Help
---

### Post by orfeu42 on 2017-04-21
Hi!

My problem is that I want to copy from a directory with multiple subdirectories only a certain type of file to another directory but keep the original directory. Specifying the question:
- I've got a folder where there are multiple subfolders where I've got photos and videos arranged in subfolders (year / month / day)
- What I do is just take the videos there and copy them to another folder but this new folder to be sorted into folders as they were when they were mixed with the pictures (day / month / year)

My first choice was to
directory_origin find -name * -type f -exec mv .EXT ./directory_destiny {} \;

but that only copy in a folder without creating new subfolders that interest me.

It is possible to do so? Saving me a lot of work to move many files and sort :-k

Thank you so much!

---

### Post by TheFu on 2017-04-21
Anything is possible with a tiny bit of scripting.

rsync (use include/excludes)
find | cp -r
tar (use include/excludes or feed the exact file list you want)
tar (use tar cvf - | ( cd new place; tar xvf - )
any backup/restore tool, just selectively restore the types of files you want.

Sometimes it is easier to copy everything, then delete the files you don't want.

BTW, I have this need too - take photos and short movies on vacations, but need to transcode the videos to more efficient formats using a much more powerful system than my travel chromebook.  I'll see what I can get working in the next few minutes. It will probably use rsync from system A to B too, since that is my need.

Found a clear example, tested it.  It works.   [https://ubuntuforums.org/showthread.php?t=763833](https://ubuntuforums.org/showthread.php?t=763833)  
My 'test' version is:
```

$ rsync --list-only -avzm --include '*/'   --include='*mov'   --exclude='*'   ./    hadar:~/V/T/     |more
```

The trick is to include */ and the file-pattern you want.  The *--list-only* option prevents any copy from happening. Good for testing it first.  The other options are explained in the rsync manpage.  I've added a few extra spaces in the command, but those aren't needed. 1 or 50 spaces, doesn't matter. Also, notice with and without the '=' doesn't matter.  The exclude/include order DOES matter.  hadar is the remote system hostname.  If I had lots and lots of files and wanted to see the progress as it happened, I'd use the *--progress* option too.  That way we know it is working.

---

