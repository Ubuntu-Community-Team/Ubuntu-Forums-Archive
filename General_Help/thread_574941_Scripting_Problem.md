---
title: "Scripting Problem"
date: 2007-10-13
forum: General Help
---

### Post by Doctor J on 2007-10-13
Since the 'Desktop Drapes' package doesn't work on Dapper [kernel 2.6.15 on x86_64], i've found a shell script that purports to offer the same functionality, and is said to work on Dapper.  However, i'm getting an error when i run it:

```
dave@ubuntu:/bin$ ./wallpaper
cut: option requires an argument -- f
Try `cut --help' for more information.
```

The file looks like this:

```
dave@ubuntu:/bin$ ls -l wallpaper
-rwxr-xr-x 1 root root 1185 2007-09-29 08:48 wallpaper
```

This is mystifying to me, as the cut command does indeed have the -f argument after it.  Perhaps this is a parsing problem?  My knowledge of shell scripts doesn't go beyond this.

1) Is there a bettor forum to address this?

2) Why is this script not completing [the body of the script is attached]?

---

### Post by McNils on 2007-10-13
1. Well, I think Programming talk is better.

2, The variable N is not set. And therefore is there no argument to f.
This line,
BGNAME=`echo $IMGS | cut -d '#' -f $N`
You should add this two lines befere the line above:
N=`echo $NIMGS | wc -w`
((N=RANDOM%N))

The script works best when the image files contain no space in the filename.

---

