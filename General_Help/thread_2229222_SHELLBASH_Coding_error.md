---
title: "SHELL/BASH Coding error"
date: 2014-06-11
forum: General Help
---

### Post by rhss6-2011 on 2014-06-11
A while back I developed a code primarily for people who download a lot of files from torrent sites. The original script worked just fine but I decided to update it and make it a little more user-friendly.
The original script you type the command (in your terminal) "_sh extract.sh /path/to/your/downloads_" and then you follow a menu for what you want it to do.
The NEW script, is supposed to do pretty much the exact same thing, but instead of typing a path you just put it IN the ROOT of your dowloads and it does what it's supposed to do.
Well, it kinda works... **The new script (below)** does what it's supposed to do except one problem... It **extracts all the files INTO the root** directory. **What I WANT it to do, is** find .r00* files, **extract the files inside the folder containing them** - NOT the root of the downloads.

Anyone want to tell me what the error is **INSIDE my code**???

```
#!/bin/bashwhile 
mesg="\n==============================================\n
  01.. Check .sfv files.\n
  02.. Unrar all rar files.\n
  03.. Delete rar and sfv files.\n
  04.. Extract TAR files.\n
  05.. Extract TAR.GZ files.\n
  06.. Extract TAR.BZ2 files.\n
  07.. Gunzip ZIP files.\n
  08.. Move AVI files to your location.\n
  09.. Move MP4 files to your location.\n
  10.. Move MKV files to your location.\n
  X.. Exit
  \n==============================================\n
Select: \c"
do
  echo $mesg
  read selection
  case $selection in
  01)
 #   cd $1
    cfv -r ;;
  02)
**    prevdir=`pwd`**
**    for r in `find `./` -iwholename *.rar`**
**    do**
**      echo "Unpacking in directory: "`dirname $r`**
**      cd `dirname $r`**
**      unrar -rv $r `dirname $r`**
**    done ;;**
  03)
    for g in `find `./` -iwholename *.r01`
    do 
      cd `dirname $g`
      echo "Deleting in directory: "`dirname $g`
      rm *.r?? *.url *.sfv imdb.nfo
      rm -r Sample/
    done ;;
  04)
  # we will need this soon:
    prevdir=`pwd`
    for f in `find `.` -wholename *.tar`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -zxvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
  05)
    # we will need this soon:
    prevdir=`pwd`
    for f in `find `.` -wholename *.tar.gz`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -zxvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
  06)
    # we will need this soon:
    prevdir=`pwd`
    for f in `find `.` -wholename *.tar.bz2`
    do
      echo "Unpacking in directory: "`dirname $f`
      # you were using the wrong arguments for tar; any 
      # arguments after the tar file name in your command
      # tar -xvf $f `dirname $f`
      # are treated as files to extract from within the tar.
      # Instead, cd to the directory first, then extract:
      cd `dirname $f`
      tar -jxvf `basename $f`
      # then go back to the dir we were in to start with.
      cd $prevdir
    done ;;
  07)
    for z in `find `.` -wholename *.zip`
    do
      echo "Unpacking in directory: "`dirname $z`
      gunzip -d -v -r $z `basename $z`
    done ;;
  08)
      for f in `find `.` -wholename *.avi`
    do
      echo "Moving AVI files from: `dirname $f` to $HOME/MOVED_AVI_FILES"
      find ./ -name "*.avi"
      mkdir $HOME/MOVED_AVI_FILES
      mv $f $HOME/MOVED_AVI_FILES
    done ;;
  09)
      for f in `find `.` -wholename *.mp4`
    do
      echo "Moving MP4 files from: `dirname $f` to $HOME/MOVED_MP4_FILES"
      find ./ -name "*.mp4"
      mkdir $HOME/MOVED_MP4_FILES
      mv $f $HOME/MOVED_MP4_FILES
    done ;;
  10)
      for f in `find `.` -wholename *.mkv`
    do
      echo "Moving MKV files from: `dirname $f` to $HOME/MOVED_MKV_FILES"
      find `.` -name "*.mkv"
      mkdir $HOME/MOVED_MKV_FILES
      mv $f $HOME/MOVED_MKV_FILES
    done ;;
  X) 
    exit;;
  esac
done
```

---

### Post by Vaphell on 2014-06-12
```
#!/bin/bashwhile
```
this can't be right


```
 for r in `find `./` -iwholename *.rar`
    do
      echo "Unpacking in directory: "`dirname $r`
      cd `dirname $r`
      unrar -rv $r `dirname $r`
    done
```

1. stop using backticks and use $() instead
2. recognize the difference between ' ' and ` ` - one is quotes, the other is not
3. always quote your variables
4. for loop is not a right tool for that purpose

```
while IFS= read -rd $'\0' r
do
  echo "$r"
  ...
done < <( find ./ ... -print0 )
```

---

### Post by rhss6-2011 on 2014-06-12
I'll try that out... Thanks.
I'm still relatively new to bash & shell coding, so I don't even know what you just responded with really does to be honest... That's what books are for :D

---

### Post by Vaphell on 2014-06-12
you mean the while read loop? Long story short you don't run for loops fed with command outputs (find in this case), you got while read loops for that. For loops should be used with stuff that you can enumerate in advance, eg params, array elems and such.

3 pieces of boiler plate on how to use while read
```
while read -r var; do something_with "$var"; done < <( some_command )
while read -r var; do something_with "$var"; done < file
while read -r var; do something_with "$var"; done <<< "string"
```

Another problem is that linux filesystems allow everything in file names, except null char and /.
Newline is used as delimiter by default in this kind of loop, but the script will be unable to distinguish between completely legit 'file**\n**1.rar' and 'file', '1.rar'.
To fix that problem you need to use \0 (null char) which is unambiguous because it can't collide with filename chars (read -d $'\0' and find -print0).

---

