---
title: "Script Problem"
date: 2007-01-05
forum: General Help
---

### Post by zempher on 2007-01-05
I have a script that used to work until recently.  No upgrades, changes, etc..., just stopped working.

Script:

#! /bin/bash

#This script will take the newest file from the sourceFolder and copy it into 
#the newFile in DestinationFolder. If newFile.jpg doesn't exist, it will
#create it. Otherwise, it will overwrite the existing file.
cp `ls -dt /home/ftp/*/* | head -1` /var/www/recCenterPic.jpg

Whenever I run the script from the CL, I receive the following error:

directorychange:  line 6:  /bin/ls:  Argument too long
cp: missing destination file operand after `/var/www/recCenterPic.jpg`
Try `cp --help' for more information.

What does this mean and why am I having this problem.

Oh..., and I am very new to ubuntu!

Thanks.

---

### Post by meng on 2007-01-05
It means, I think, that the output of
ls -dt /home/ftp/*/* | head -1
is not recognized as a single filename

I can't wrap my brain around that command right now ... why don't you check the output by typing it in correctly at the command line, and see if it's what you intended?

---

### Post by indytim on 2007-01-05
Hey MIng,

Nice signature... it is a real "hoot" :D 

IndyTim

---

### Post by moma on 2007-01-05
Meng is probably right.

Maybe the filename contains spaces.

Enclose the resulting filename in double quotes. Like this
cp "`ls -dt /home/ftp/*/* | head -1`"  /var/www/recCenterPic.jpg

---

### Post by meng on 2007-01-05
IndyTim: Thanks, though I'm not sure I can claim it as my own idea; I have this vague feeling I saw it somewhere else first.

---

### Post by zempher on 2007-01-05
The file name both original and the replaced files do not contain any spaces and I did try running the script from the CL, but still encounter the same error.

---

### Post by moma on 2007-01-05
Split the command and debug the parts.
What does this say:
$  [COLOR="SeaGreen"]ls -dt /home/ftp/*/* | head -1[/COLOR]

---

### Post by zempher on 2007-01-05
When run from the CL, I get:

bash: /bin/ls: Argument list too long

---

### Post by koenn on 2007-01-06
the `  ` in your script is an old trick - it's better to replace it with something like
```
cp "$(ls -dt /home/ftp/*/* | head -1)" /var/www/recCenterPic.jpg
```

I don't think this will solve the problem, but do it anyway :)

what is the name of the newest file in /home/ftp ?


you want to copy the newest file from a directory - is there a reason for the /*/* - why isn't 
ls -dt /home/ftp/* sufficient ?

---

### Post by moma on 2007-01-06
The normal advice is to use [COLOR="Red"]find[/COLOR] and [COLOR="Red"]xargs[/COLOR] commands to avoid "Argument list too long" errors.  But it's difficult in this case because you will find the most recent file in /home/ftp directory structure.  In your case the "Argument list too long" error occurs because the directory structure contains (too) many files. Find and | xargs can handle any number of files.
$ man find
$ man xargs
----------------------------------------------------

Anyway,
The following webpage has a tiny Perl-script that may solve your problem.
[http://www.webreference.com/programming/perl/minimal_perl2/5.html](http://www.webreference.com/programming/perl/minimal_perl2/5.html)

> #!/usr/bin/perl -wnl 
# From pathname inputs, emits name of one most recently modified 
# Gives correct answer where pipelines of this form may not: 
#   find . -print | xargs ls &#8211;lrdt | tail -1 
# NOTE: Use find or locate to provide input, or ls -d dir/*, 
# but *not* simply "ls dir" (dir won't be present in pathname) 
# Sample invocations: 
#      locate '*.c' | most_recent_file 
#      ls -d /etc/* | most_recent_file 
#      find /local -name 'somescript' | most_recent_file 
#      most_recent_file < filelist 
BEGIN { 
 $newest=0;  # initialize modification-time reference point 
} 

# Get file's numeric modification time; 10th value from stat 
  $mtime=(stat $_)[9];     # indexing into output of stat 

  if ($mtime && $mtime > $newest) {  # if True, current file is newest yet seen 
    # Remember mod-time for comparison to others, 
    #   and remember filename for final report 
    $newest=$mtime; 
    $name=$_; 
   } 

END { 
  print $name; 
}

Save the code into "most_recent_file" file.
Make the script executable
$ [COLOR="SeaGreen"]chmod +x most_recent_file[/COLOR]

Run it like this 
$ [COLOR="SeaGreen"]find /home/ftp/ -type f -print |  /path_til/most_recent_file[/COLOR]

Another example
$ [COLOR="SeaGreen"]echo $(readlink -f $(find /home/ftp/ -type f -print | /path_til/most_recent_file ) )[/COLOR]

Note: Use -name argument to find command to match specific file type or extension.
$ find /home/ftp -type f -name "*jpeg" | ....

[COLOR="Red"]file[/COLOR] command can reveal the content (type) of file.

Find image files (png, jpg,...) only
$ file  * | grep "image data"

---

