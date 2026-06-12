---
title: "Deleting Directory with millions of files or directory"
date: 2015-08-22
forum: General Help
---

### Post by ramsforums on 2015-08-22
Greetings everyone

My Laptop was reporting limited storage space. So I installed Bleachbit and executed with root privileges. I have enabled all options including WIPE. It ran overnight for 12 hours and application became unresponsive. So I have pressed the power button for 10 seconds it power down the laptop.


Upon booting I saw a directory T6o1L9lGg- which  contains huge number of files. I am unable to list using ls command

tried to delete using sudo rm -r T6o1L9lGg-
Not working. it runs for ever.


Tried the following command
mkdir empty
sudo rsync -a --delete ./empty/  ./T6o1L9IGg-/

This also not working ran over two hours and continue to run.

So I came across the following thread

[http://www.stevekamerman.com/2008/03/deleting-tons-of-files-in-linux-argument-list-too-long/comment-page-1/#comment-16588](http://www.stevekamerman.com/2008/03/deleting-tons-of-files-in-linux-argument-list-too-long/comment-page-1/#comment-16588)


Here a David Villegas posting

```


[COLOR=#EEEEEE][FONT=Lucida Grande][David Villegas]("http://www.supporttec.com/")[/FONT][/COLOR]
[COLOR=#BBBBBB][FONT=Lucida Grande][September 1st, 2013 at 1:03 am]("http://www.stevekamerman.com/2008/03/deleting-tons-of-files-in-linux-argument-list-too-long/comment-page-1/#comment-84613")[/FONT][/COLOR][COLOR=#000000]
[FONT=Lucida Grande]After a nightmare on a server with free space but out of inodes, because of spam attack on a misconfigured postfix&#8230; i found this blog post!, in my case was 8 million files on /var/spool/postfix/maildrop folder.[/FONT]
[FONT=Lucida Grande]The only useful formula that works on my case was the Mikhus script on php.
find, rsync, rm fail with that ammount of files [IMG]http://www.stevekamerman.com/wp-includes/images/smilies/icon_sad.gif[/IMG][/FONT]
[FONT=Lucida Grande]but i wrote a similar c++ script, to speed up the delete.[/FONT]
[FONT=Lucida Grande]HOW:
just copy and paste this code to /var/spool/postfix/mydel.c
and compile with g++ -o mydelexec mydel.c[/FONT]
[FONT=Lucida Grande]CODE:
//COMPILE WITH: g++ -o mydelexe mydel.c
#include
#include
int main() {
struct dirent *d;
DIR *dir;
char buf[256];
int i;[/FONT]
[FONT=Lucida Grande]printf(&#8220;***mydelexe***\n&#8221;);
dir = opendir(&#8220;maildrop&#8221;);[/FONT]
[FONT=Lucida Grande]while( d = readdir(dir) ) {
i++;
if(i%100==0) {
printf(&#8220;%s %i deleted!\n&#8221;,d->d_name,i);
}
sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
remove(buf);
}
return 0;
}[/FONT]
[FONT=Lucida Grande]This c do the same of the php, but a bit faster&#8230; for my 8 million files gone after few hours[/FONT][/COLOR]

```


After compiling I got the following



```

rama@develop ~ $ g++ -o mydelexec mydel.c
mydel.c:2:9: error: #include expects "FILENAME" or <FILENAME>
 #include
         ^
mydel.c:3:9: error: #include expects "FILENAME" or <FILENAME>
 #include
         ^
mydel.c:13:2: error: stray &#8216;\342&#8217; in program
  printf(&#8220;***mydelexe***\n&#8221;);
  ^
mydel.c:13:2: error: stray &#8216;\200&#8217; in program
mydel.c:13:2: error: stray &#8216;\234&#8217; in program
mydel.c:13:2: error: stray &#8216;\&#8217; in program
mydel.c:13:2: error: stray &#8216;\342&#8217; in program
mydel.c:13:2: error: stray &#8216;\200&#8217; in program
mydel.c:13:2: error: stray &#8216;\235&#8217; in program
mydel.c:14:2: error: stray &#8216;\342&#8217; in program
  dir = opendir(&#8220;maildrop&#8221;);
  ^
mydel.c:14:2: error: stray &#8216;\200&#8217; in program
mydel.c:14:2: error: stray &#8216;\234&#8217; in program
mydel.c:14:2: error: stray &#8216;\342&#8217; in program
mydel.c:14:2: error: stray &#8216;\200&#8217; in program
mydel.c:14:2: error: stray &#8216;\235&#8217; in program
mydel.c:19:4: error: stray &#8216;\342&#8217; in program
    printf(&#8220;%s %i deleted!\n&#8221;,d->d_name,i);
    ^
mydel.c:19:4: error: stray &#8216;\200&#8217; in program
mydel.c:19:4: error: stray &#8216;\234&#8217; in program
mydel.c:19:4: error: stray &#8216;\&#8217; in program
mydel.c:19:4: error: stray &#8216;\342&#8217; in program
mydel.c:19:4: error: stray &#8216;\200&#8217; in program
mydel.c:19:4: error: stray &#8216;\235&#8217; in program
mydel.c:21:2: error: stray &#8216;\342&#8217; in program
  sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
  ^
mydel.c:21:2: error: stray &#8216;\200&#8217; in program
mydel.c:21:2: error: stray &#8216;\234&#8217; in program
mydel.c:21:2: error: stray &#8216;\342&#8217; in program
mydel.c:21:2: error: stray &#8216;\200&#8217; in program
mydel.c:21:2: error: stray &#8216;\235&#8217; in program
mydel.c:21:2: error: stray &#8216;\342&#8217; in program
mydel.c:21:2: error: stray &#8216;\200&#8217; in program
mydel.c:21:2: error: stray &#8216;\234&#8217; in program
mydel.c:21:2: error: stray &#8216;\342&#8217; in program
mydel.c:21:2: error: stray &#8216;\200&#8217; in program
mydel.c:21:2: error: stray &#8216;\235&#8217; in program
mydel.c: In function &#8216;int main()&#8217;:
mydel.c:9:1: error: &#8216;DIR&#8217; was not declared in this scope
 DIR *dir;
 ^
mydel.c:9:6: error: &#8216;dir&#8217; was not declared in this scope
 DIR *dir;
      ^
mydel.c:13:15: error: &#8216;mydelexe&#8217; was not declared in this scope
  printf(&#8220;***mydelexe***\n&#8221;);
               ^
mydel.c:13:27: error: &#8216;n&#8217; was not declared in this scope
  printf(&#8220;***mydelexe***\n&#8221;);
                           ^
mydel.c:13:31: error: &#8216;printf&#8217; was not declared in this scope
  printf(&#8220;***mydelexe***\n&#8221;);
                               ^
mydel.c:14:19: error: &#8216;maildrop&#8217; was not declared in this scope
  dir = opendir(&#8220;maildrop&#8221;);
                   ^
mydel.c:14:30: error: &#8216;opendir&#8217; was not declared in this scope
  dir = opendir(&#8220;maildrop&#8221;);
                              ^
mydel.c:16:24: error: &#8216;readdir&#8217; was not declared in this scope
  while( d = readdir(dir) ) {
                        ^
mydel.c:19:14: error: expected primary-expression before &#8216;%&#8217; token
    printf(&#8220;%s %i deleted!\n&#8221;,d->d_name,i);
              ^
mydel.c:19:15: error: &#8216;s&#8217; was not declared in this scope
    printf(&#8220;%s %i deleted!\n&#8221;,d->d_name,i);
               ^
mydel.c:19:35: error: invalid use of incomplete type &#8216;struct main()::dirent&#8217;
    printf(&#8220;%s %i deleted!\n&#8221;,d->d_name,i);
                                   ^
mydel.c:8:8: error: forward declaration of &#8216;struct main()::dirent&#8217;
 struct dirent *d;
        ^
mydel.c:21:18: error: expected primary-expression before &#8216;%&#8217; token
  sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
                  ^
mydel.c:21:19: error: &#8216;s&#8217; was not declared in this scope
  sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
                   ^
mydel.c:21:21: error: expected primary-expression before &#8216;%&#8217; token
  sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
                     ^
mydel.c:21:45: error: invalid use of incomplete type &#8216;struct main()::dirent&#8217;
  sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
                                             ^
mydel.c:8:8: error: forward declaration of &#8216;struct main()::dirent&#8217;
 struct dirent *d;
        ^
mydel.c:21:53: error: &#8216;sprintf&#8217; was not declared in this scope
  sprintf(buf, &#8220;%s/%s&#8221;, &#8220;maildrop&#8221;, d->d_name);
                                                     ^
mydel.c:22:12: error: &#8216;remove&#8217; was not declared in this scope
  remove(buf);
            ^



```

I have changed #include to #include <studio.h> etc. still not working

1) How do I delete the directory?
2) How do I make the code work?

Thanks

---

### Post by TheFu on 2015-08-22
Can't help with the code - looks like C to me, not C++. Not needed simply to remove files.

You can chunk the files into groups - try all the a*, then b*, then c* ...  directories with more than 1000 files get really slow and start to cause issues like this.  Plus 1 tiny error to the directory on disk and all of them can be lost.

So - a few tools that are known to handle this stuff - 
* xargs - [https://unix.stackexchange.com/questions/96935/faster-way-to-delete-large-number-of-files](https://unix.stackexchange.com/questions/96935/faster-way-to-delete-large-number-of-files) explains
* find -exec rm {} # this will be slower because it works on 1 file at a time OR
* use GUI file manager and the delete key on the top directory. Don't go inside the direct with all the files. It will be bad.

Best to not let directories have so many files in the future.

---

### Post by ramsforums on 2015-08-22
> **TheFu said:**
> Can't help with the code - looks like C to me, not C++. Not needed simply to remove files.

You can chunk the files into groups - try all the a*, then b*, then c* ...  directories with more than 1000 files get really slow and start to cause issues like this.  Plus 1 tiny error to the directory on disk and all of them can be lost.

So - a few tools that are known to handle this stuff - 
* xargs - [https://unix.stackexchange.com/questions/96935/faster-way-to-delete-large-number-of-files](https://unix.stackexchange.com/questions/96935/faster-way-to-delete-large-number-of-files) explains
* find -exec rm {} # this will be slower because it works on 1 file at a time OR
* use GUI file manager and the delete key on the top directory. Don't go inside the direct with all the files. It will be bad.

Best to not let directories have so many files in the future.


Thank you TheFu. I do not know what is the content of directory. when I issue a command, the command starts executing no console output. command runs for ever.  for example I tried as follows

find <FOLDERNAME>  -name  "a*"   -type f -print -delete

I have tried this also

cd <FOLDERNAME>
sudo find . -type f -print  -delete

---

### Post by www.pantz.org on 2015-08-23
If you want to delete the dir  and it is taking forever, then it just might take a long time to delete that many files. You will likely have to let it just sit and delete the files. If you want to make sure it is doing something and has not locked up run  rm  with -v    I would suggest  *rm -vfR <directory> *

---

### Post by Doug S on 2015-08-23
> **ramsforums said:**
> It ran overnight for 12 hours and application became unresponsive. So I have pressed the power button for 10 seconds it power down the laptop.I wonder if something got corrupted on your file system when you hit the reset button.

The directory file size is huge (from your other thread), and yes typically means millions of files. It is somewhat indeterminate from just the directory file size, because it's size is a function of the number of characters in file name.

---

### Post by tgalati4 on 2015-08-23
It's possible that you have a failing disk drive.  What are the SMART parameters of this drive?

---

### Post by Habitual on 2015-08-24
It's a typical bleachbit + user goof.
You will have to rm or other that directory manually.

Don't use bleachbit as root and don't enable all options.

---

### Post by ramsforums on 2015-08-25
Looks like the damage is done. I am unable to delete the Directory. It contains  billions of directories. 

See the below Screen for the directory structure. The owner of directory is root

[IMG]http://i.imgur.com/tGS7ajj.png[/IMG]

I have tried as follows


> 
sudo  rm -vfR   T6o1L9lGg-/


It  was searching for an hour+ then started deleting folders from T6o1L9lGg-/  It ran over 10 hours. The laptop ScreenSaver activated and password protection was on. The hard disk was t but laptop was not responding. So I have to force shutdown by pressing the power button more than 10 seconds. upon booting, the directory and size remains same. no changes.

2) I have tried 

> 
sudo mkdir empty
sudo rsync -av --delete ./empty/ ./T6o1L9IGg-/


The command executed and got a prompt 

> 
sending incremental file list


After about 3  hours the folders starts displaying. It ran for about 6 hours then due to some power trip the laptop shutdown.

When I reboot the folder remains same size. 
When I execute the g++  as mentioned in the first thread, nothing happens. Looks like the code is not working.

Any other suggestion? If no other option, I may need to format my laptop.

Thank you

---

### Post by Doug S on 2015-08-25
> **ramsforums said:**
> It  was searching for an hour+ then started deleting folders from T6o1L9lGg-/  It ran over 10 hours. The laptop ScreenSaver activated and password protection was on. The hard disk was t but laptop was not responding. So I have to force shutdown by pressing the power button more than 10 seconds. upon booting, the directory and size remains same. no changes
Disable screensavers and such, so that your laptop just stays on and the screen remains visible. Then let the command finish, no matter how long it takes.
Also, do not confuse the size of the directory file with the aggregate size of its contents, the two are not the same. The size of the directory file will not reduce, even as the contents become much much much less.

Example:
This directory contains 1 million files:```
drwxrwxr-x 2 doug doug 45608960 Aug 25 08:55 doug_test
```and now here is that same directory after all the files have been deleted:```
drwxrwxr-x 2 doug doug 45608960 Aug 25 09:37 doug_test
```

---

### Post by chopra on 2015-08-25
This is just a crazy thougth, but is it possible to copy everything on this directory's partition to a new partition, change the mount point of your root directory if need be, and then force the unwanted directory to be destroyed by wiping out its partition? I don't know what effect this would have, maybe someone with more knowledge than I would, but it's just an idea.

Chopra

---

