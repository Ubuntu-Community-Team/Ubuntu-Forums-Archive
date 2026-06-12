---
title: "Creat folders and copy file inside them"
date: 2019-08-14
forum: General Help
---

### Post by OOzypal on 2019-08-14
Hello

I have many photos inside many folders for example:

2008-Home
--1.jpg
--2.jpg
2008-Work
--2.jpg
--2.jpg
--2.jpg
2011-Party
--1.jpg
--2.jpg
--3.jpg

etc.

Each folder has jpg photos. I want to batch these folder and go inisde them then create a folder called jpg then copy all photos inside the jpg folder to be like
2008-Home
--jpg
----1.jpg
----2.jpg
2008-Work
--jpg
----1.jpg
----2.jpg
----3.jpg
2011-Party
--jpg
----1.jpg
----2.jpg
----3.jpg

How can I do that?

---

### Post by coffeecat on 2019-08-14
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by TheFu on 2019-08-14
filenames and directory names beginning with dashes (-) will cause issues with some programs.  Best to avoid that.

---

### Post by OOzypal on 2019-08-14
Sure. But these not (-s). These to show the folder structure.

---

### Post by &amp;wP*!) on 2019-08-14
You can do that with a small Perl script very easily. Following Perl code does what you want, but only for 1 hierarchy:
```


#!/bin/env perl

use Getopt::Long;

$root_dir = ".";

GetOptions (
        "d=s"   => \$root_dir,
);

print "$root_dir\n";

foreach $dir (glob "$root_dir/*") {
        print "Processing $dir\n";
        if (glob "$dir/*.jpg" == "") { print "The directory $dir has no JPEG files. Skipping...\n"; }
        mkdir "jpg";
        system ("mv ".glob ("$dir/*.jpg")." $dir/jpg");
}


```
Save it as something like **mv_jpeg.pl** and make it executable by **chmod 755 mv_jpeg.pl**.
Now you can call it in any root directory you want:
```
./mv_jpeg.pl -d some_dir
```
This creates in each subdirectory under "some_dir" a sub-sub-directory called "jpg" and move all files in the subdir with the extension "*.jpg" into this folder.

You can modify the script in the way you want.
With little effort it can be recursive.

---

### Post by Holger_Gehrke on 2019-08-14
The simplest solution would be something like this
```

for i in list-of-folder-names ; do mkdir "$i"/jpg && mv -- "$i/*[jJ][pP][gG]" "$i"/jpg; done

```
executed in a terminal. Replace "list-of-folder-names" with a space-separated list of directories (if any of the folder-names contains space(s) put the name in quotes). This will create a directory named "jpg" inside each of the named folders and move the files whose names end in 'jpg' (in any variation of capital and minor letters) from the original directory into the new directory. If the attempt to make the directory fails, moving isn't tried (that's what the '&&' means). The '--' in the 'mv' command tells 'mv' that there are no further options, so filenames starting with on or more dashes don't lead to problems.

---

### Post by OOzypal on 2019-08-14
hab@asus:~/Dropbox/Personal/Multimedia/Photo$ ./my_jpeg.pl -d some_dir

       /bin/env: ‘perl\r’: No such file or directory

---

### Post by &amp;wP*!) on 2019-08-14
> **OOzypal said:**
> hab@asus:~/Dropbox/Personal/Multimedia/Photo$ ./my_jpeg.pl -d some_dir

       /bin/env: &#8216;perl\r&#8217;: No such file or directory
There must be no other character after the text **perl**. I do see "\r" in your text. Don't use weird whitespace characters. Just type enter after the 1st line (it should go to the next line in the editor).
If it is still the same problem, change:
```
#!/bin/env perl

```with```

#!/usr/bin/perl
```
... and run the script again. If this does not work either, try this (no matter how 1st line looks like) - change "some_dir" with the top directory name !! -:
```
perl mv_jpeg.pl -d some_dir
```
If this doesn't work, check whether you have Perl:
```
which perl

```If this doesn't return anything, it means to me that you don't have Perl installed on your computer. Install it with the following command: 
```
sudo apt-get install perl
```
afterwards even /bin/env solution should work.

---

### Post by OOzypal on 2019-08-15
I did remove the extra character and I am getting nothing except the some_dir is re-printed in the terminal.

---

### Post by OOzypal on 2019-08-15
> **Holger_Gehrke said:**
> The simplest solution would be something like this
```

for i in list-of-folder-names ; do mkdir "$i"/jpg && mv -- "$i/*[jJ][pP][gG]" "$i"/jpg; done

```
executed in a terminal. Replace "list-of-folder-names" with a space-separated list of directories (if any of the folder-names contains space(s) put the name in quotes). This will create a directory named "jpg" inside each of the named folders and move the files whose names end in 'jpg' (in any variation of capital and minor letters) from the original directory into the new directory. If the attempt to make the directory fails, moving isn't tried (that's what the '&&' means). The '--' in the 'mv' command tells 'mv' that there are no further options, so filenames starting with on or more dashes don't lead to problems.

True it is simple but it is not practical. I can't list so many directories in one line. In addition, it didn't work. It created a jpg folder in each directoy but nothing else with an error-see attached. 

[ATTACH=CONFIG]283806[/ATTACH]

---

### Post by Holger_Gehrke on 2019-08-15
Sorry, got the quoting wrong. It should be
```
for i in list-of-folder-names ; do mkdir "$i"/jpg && mv -- "$i"/*[jJ][pP][gG] "$i"/jpg; done
```
And of course you can easily list hundreds of directories there. ARG_MAX (length of a command including arguments) should be on the order of 2 Megabytes. With command-line completion (tab key) it's not as much of a chore as you think and you can use wildcards (as long as they only expand to the names of directories).
You could also play around with 'find <starting directory name> -type d -exec ...', but that can get really complicated really fast (see the manual page (man find) if you want to see what I mean).

Holger

---

### Post by freedombacon on 2019-08-16
If all the folders are in the same directory, you can replace list-of-folder-names with `ls /path/to/folders`. Using find is probably a better way to do this, but if that line is already working, don't bother with it this time.

---

### Post by sulton on 2019-08-24
hi, if php installed on your system then you can create **index.php** file with code above, insert your path to photo directory and execute with command php **index.php **

```

<?php
$dirs = glob('path/to/photo/dir/*', GLOB_ONLYDIR); // paste your path here


foreach ($dirs as $dir) {
    if (!is_dir($dir . '/jpg')) mkdir($dir . '/jpg', 0755, true);
    $pics = glob($dir . '/*.jpg');
    foreach ($pics as $pic) {
        rename($pic, dirname($pic) . '/jpg/' . basename($pic));
    }
}

```

---

