---
title: "About &quot;Recursively symlink&quot; thread"
date: 2015-03-30
forum: General Help
---

### Post by veranyon on 2015-03-30
Hi all.
The "http://ubuntuforums.org/showthread.php?t=798899" thread had been closed but in last message had been error (excuse me that my English not very well).
The variables can't work if your folder and files will have spaces.

How to fix that script?

```

#!/bin/bash
if [ "$2" == "" ]; then
  echo "Syntax: $0 source-directory destination-directory"
  echo "Will create directory structure of source-directory in destination-directory"
  echo "and symbolic links with relative paths for all files."
  echo "destination-directory will be created if it does not exist."
  echo
  echo "(c)2012 Ronny Ager-Wick, released under GPL v3"
  echo "inspired by http://ubuntuforums.org/showthread.php?t=798899"
  exit 1
fi
 
src=`readlink -e $1`
dst=`readlink -m $2`
 
if [ ! -d "$src" ] || [ "$src" == "" ]; then
  echo "ERROR: source directory does not exist."
  exit 2;
fi
 
if [ ! -d "$dst" ]; then
  echo "Creating directory $dst..."
  mkdir -p "$dst" # create directory path
  created_dir=1
fi
 
if [ ! -d "$dst" ] || [ "$dst" == "" ]; then
  echo "ERROR: destination directory does not exist, and could not be created."
  exit 3;
fi
 
if [ "$created_dir" == "1" ]; then
  # if dir path was just created, remove the last directory so it will be created below, otherwise the statistics will be wrong
  # Yeah, I know, fiddly, but I'm a perfectionist, so what can you do?
  rmdir "$dst"
fi
 
num_dirs_created=0
num_dirs_skipped=0
num_files_linked=0
num_files_skipped=0
echo "Building new directories in $dst, and linking to files in $src..."
for src_d in $(find $src -xdev -type d); do
  dst_d="$dst${src_d#$src}"
  echo -n "$dst_d"
  if [ ! -d $dst_d ]; then
    mkdir -p "$dst_d"
    echo -n " (Created)"
    ((num_dirs_created+=1))
  else
    echo -n " (Exists)"
    ((num_dirs_skipped+=1))
  fi
 
  # get relative path from destination to source
  rel=$(perl -MFile::Spec -e 'print File::Spec->abs2rel("'"$src_d"'","'"$dst_d"'")')
 
  f_lnkd=0
  f_skpd=0
  for source_file in $(find $src_d -xdev -maxdepth 1 -type f); do
    src_f="$rel${source_file#$src_d}" # source file with relative path
    dst_f="$dst${source_file#$src}" # destination dir & file name
    #echo -n " [ src_f=$src_f / dst_f=$dst_f ] "
    #echo -n " src_f=$src_f, dst=$dst, rel=$rel, src_f#src=$({$src_f#$src}) | "
 
    if [ ! -e $dst_f ]; then
      ln -s $src_f $dst_f  # create link
      ((f_lnkd+=1))
    else
      # file or link exists, don't do anything
      ((f_skpd+=1))
    fi
  done
  ((num_files_linked+=f_lnkd))
  ((num_files_skipped+=f_skpd))
  echo " (linked $f_lnkd of $(($f_lnkd + $f_skpd)) files)"
  ((num_dirs+=1))
done
 
echo -n "Created $num_dirs_created directories"
if [ $num_dirs_skipped != 0 ]; then
  echo -n ", while $num_dirs_skipped directories already existed"
fi
echo "."
 
echo -n "Linked $num_files_linked files"
if [ $num_files_skipped != 0 ]; then
  echo -n ", while $num_files_skipped links or files already existed"
fi
echo "."
```

---

### Post by bardo2 on 2015-04-01
Hi, i am pretty new user in here. thus have no permission to edit above mentioned thread.

After reading through it, i feel goose bumps, i am scared. ...comes to me like... using a jackhammer to nail a sheet of paper.

I do not intend to be disrespectful to your work. Sure, there was a bug in the aforementionned script and you are offering a fix which required precision and effort.
But... I am sure, a one-liner exists, that would be more portable and less error-prone in the first place. I am just saying: maybe a bash script is not the best tool of choice there.

---

### Post by veranyon on 2015-04-01
Yes it's. The script is very cruel))
But to know be the alternatives.
And topic that link I had write in first post, is dead. I do not know why it was closed. Probably all were satisfied with the last answer. Why? - I don't know.

---

### Post by coffeecat on 2015-04-01
Without judging the merits or otherwise of the last post in the referenced thread, I've simply moved it from public view.

A few general points. This is a forum, not a wiki. Our purpose is to have up-to-date conversations where volunteers help other people with their Ubuntu systems. If used as a lookup resource, caution should be exercised. There is plenty of useful information to be found here, but people should be aware that there will inevitably be misleading information as well, particularly in ancient closed threads such as the one referred to.

For staff reference only, the jailed post is now here:

[http://ubuntuforums.org/showthread.php?t=2271742](http://ubuntuforums.org/showthread.php?t=2271742)

Members who are not staff will get a permission denied message if they click on that link.

---

### Post by coffeecat on 2015-04-01
Just to clarify - the jailed post was one from 2012 and was the last post in this thread (before it was removed):

[http://ubuntuforums.org/showthread.php?t=798899](http://ubuntuforums.org/showthread.php?t=798899)

The jailed post is the one that the OP of this thread - veranyon - had a concern about.

---

### Post by veranyon on 2015-04-01
I have nothing against the closure of the theme.
Just explained why start a new topic twice. If you decide to create 10 new similar themes, then those are the rules. Everyone creates their own and the other person does not have to climb with their.

---

