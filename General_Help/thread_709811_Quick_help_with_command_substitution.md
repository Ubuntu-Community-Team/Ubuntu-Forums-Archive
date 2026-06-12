---
title: "Quick help with command substitution"
date: 2008-02-27
forum: General Help
---

### Post by lenticular on 2008-02-27
I want to take the output from the locate command and use command substitution to get an ls -l .  If I do:
jross@adam:~$ ls -l `locate /home/jross/wpakey`
-rw-r--r-- 1 jross jross 65 2007-11-12 08:57 /home/jross/wpakey

it works great.

But if I set it down a path where filename or directory names have spaces, it breaks:
Say I have a file " My List"  the command would give me:
ls: /home/jross/WorkDocs/My: No such file or directory
ls: /home/jross/WorkDocs/List: No such file or directory

Essentially, it wants to interpret both parts of the file name as two distinct files.  I don't blame it, but wonder how to get around the problem.  I know that if I could make it parse the filename as quoted "My List" it would work, but I'm not sure how to make that happen.

Thanks,
  John

---

### Post by bodhi.zazen on 2008-02-27
Use " " and -n 1

> ls -l "`locate -n 1 /home/jross/WorkDocs/"My List"`"

You need the -n 1 if the directory is not empty

Use " " for the space (you can escape it with \ in the locate command)

---

### Post by Mr. C. on 2008-02-27
I don't think the -n is what's desired.  This will return only a single result from locate.

Use this instead:

```
locate -0 /home/jross/wpakey | xargs -0 ls -l
```

MrC

---

### Post by bodhi.zazen on 2008-02-27
Hmmm ....

That command did not work at all on my system, let alone on a file with spaces.

---

### Post by Mr. C. on 2008-02-27
Ah, crap.  I see that Ubuntu has an ancient verison of locate (3.0beta), and the system I tested on is using 4.2.31 which includes the -0 argument common with xargs and find.

Anyway, I created a simple locate database to test with:

```
$ ls
a/  b/  c\ d/
$ pwd
/home/mrc/test
$ ls 
$ locate --database=/tmp/locatedb  -0 test | xargs -0 ls -l
/home/mrc/test:
total 12
drwx------ 2 mrc users 4096 Feb 27 18:12 a
drwx------ 2 mrc users 4096 Feb 27 18:12 b
drwx------ 2 mrc users 4096 Feb 27 18:12 c d

/home/mrc/test/a:
total 0

/home/mrc/test/b:
total 0

/home/mrc/test/c d:
total 0
$ 
```

---

### Post by Mr. C. on 2008-02-27
Perhaps this will work better!

```
locate /home/jross/wpakey  | xargs -d '\n' ls -ld
```

MrC

---

### Post by bodhi.zazen on 2008-02-27
Better, but still need " " to handle spaces in file names.

I was wondering what we are trying to do anyways? If we know the file we can list it directly :
> bodhi@VirtualUbuntu:~$ ls -l /home/bodhi/"my test"
-rw-r--r-- 1 bodhi bodhi 0 2008-02-27 20:46 /home/bodhi/my test

Or use grep
> 
bodhi@VirtualUbuntu:~$ ls -l $HOME | grep "my test"
-rw-r--r-- 1 bodhi bodhi         0 2008-02-27 20:46 my test

I think the original question was how to manage spaces in file names / command substitution

---

### Post by Mr. C. on 2008-02-27
The point is that locate is just going to return some list, that the OP wants to do something with, and not have the spaces in filenames be word-split.  The OP doesn't know what locate will return, so needs to protect what comes back from word-splitting.

I'm not sure why you think the command doesn't work, but if you believe it does not, show your commands and output, like this:

```
$ ls -l
total 12
drwx------ 2 mrc users 4096 Feb 27 18:12 a/
drwx------ 2 mrc users 4096 Feb 27 18:12 b/
drwx------ 2 mrc users 4096 Feb 27 18:12 c\ d/

$ locate test
/home/mrc/test
/home/mrc/test/a
/home/mrc/test/b
/home/mrc/test/c d

$ locate test | xargs -d '\n' ls  -ld
drwx------ 5 mrc users 4096 Feb 27 18:12 /home/mrc/test
drwx------ 2 mrc users 4096 Feb 27 18:12 /home/mrc/test/a
drwx------ 2 mrc users 4096 Feb 27 18:12 /home/mrc/test/b
drwx------ 2 mrc users 4096 Feb 27 18:12 /home/mrc/test/c d

$ locate  'c d' | xargs -d '\n' ls  -ld   
drwx------ 2 mrc users 4096 Feb 27 18:12 /home/mrc/test/c d

```

Notice that the file name "c d" is passed to **ls** by **xargs** as a single command line argument (pipes and xargs do not word-split like the shell does in other contexts).

MrC

---

### Post by bodhi.zazen on 2008-02-27
> **lenticular said:**
> But if I set it down a path where filename or directory names have spaces, it breaks:

<cilp>

> **Mr. C. said:**
> I'm not sure why you think the command doesn't work, but if you believe it does not, show your commands and output, like this:

:lolflag: OK :

> bodhi@VirtualUbuntu:~$ ls | grep "my test"
my test

So as you can see, "my test" is in my home ;)

```
 locate /home/bodhi/my test  | xargs -d '\n' ls -ld
```

yields a long output, here is the start 

> -rw-r--r-- 1 root  root  103204 2007-09-28 04:06 /boot/memtest86+.bin
-rwxr-xr-x 1 root  root    1942 2007-05-15 04:01 /etc/cron.weekly/popularity-con
test
-rwxr-xr-x 1 root  root     219 2007-07-30 17:09 /etc/grub.d/20_memtest86+
-rw-r--r-- 1 root  root   15360 2007-06-25 02:47 /etc/libgda-3.0/sales_test.db
-rw-r--r-- 1 root  root     342 2007-08-12 16:36 /etc/popularity-contest.conf
-rw-r--r-- 1 root  root    1807 2007-05-23 04:58 /etc/sane.d/test.conf

<clip>

-rw-r--r-- 1 root  root    7708 2007-08-22 04:34 /lib/modules/2.6.22-10-generic/kernel/drivers/rtc/rtc-test.ko
-rw-r--r-- 1 root  root    7708 2007-10-04 13:53 /lib/modules/2.6.22-13-generic/kernel/drivers/rtc/rtc-test.ko
-rw-r--r-- 1 root  root    7708 2007-10-14 19:40 /lib/modules/2.6.22-14-generic/kernel/drivers/rtc/rtc-test.ko
-rw-r--r-- 1 root  root    7708 2007-08-02 21:13 /lib/modules/2.6.22-9-generic/kernel/drivers/rtc/rtc-test.ko
-rw-r--r-- 1 root  root       0 2007-12-02 18:14 /root/chkroottest
-rwxr-xr-x 1 root  root    8628 2007-10-15 05:14 /usr/bin/cupstestdsc
-rwxr-xr-x 1 root  root   38788 2007-10-15 05:14 /usr/bin/cupstestppd
-rwxr-xr-x 1 root  root     844 2006-01-03 18:20 /usr/bin/dh_testdir
-rwxr-xr-x 1 root  root     569 2006-01-03 18:20 /usr/bin/dh_testroot
-rwxr-xr-x 1 root  root    2119 2006-01-03 18:20 /usr/bin/dh_testversion
-rwxr-xr-x 1 root  root    1939 2007-10-15 04:41 /usr/bin/gdmthemetester
-rwxr-xr-x 1 root  root    7828 2007-09-17 16:33 /usr/bin/gnome-menu-spec-test
lrwxrwxrwx 1 root  root      26 2007-10-16 20:32 /usr/bin/hp-testpage -> ../share/hplip/testpage.py
-rwxr-xr-x 1 root  root    2293 2007-09-28 04:06 /usr/bin/make-memtest86+-boot-floppy
-rwxr-xr-x 1 root  root   11684 2007-10-09 08:12 /usr/bin/panel-test-applets
-rwxr-xr-x 1 root  root   38648 2007-08-06 04:18 /usr/bin/pcretest
-rwxr-xr-x 1 root  root   19384 2007-09-03 20:52 /usr/bin/speaker-test

<clip>

You get the idea, the output is 539 lines long (don't think we need to post the entire output here).

Again, look at the OP question, re spaces (I quoted it above).

---

### Post by Mr. C. on 2008-02-28
> **bodhi.zazen said:**
> 

```
 locate /home/bodhi/my test  | xargs -d '\n' ls -ld
```

yields a long output, here is the start 

The command is flawed from the beginning.  You are calling the locate command with two arguments, which are "/home/bodhi/my" and "test" - this is not what the OP is trying to accomplish.

The OP wants "to take the output from the locate command...".  Your test has already failed this, as it does not provide correct arguments to locate in the first place.  The goal here isn't concerned about how to quote a single pathname argument which is thus passed to locate.  The goal here is to use *the output from the locate command*, or really any command, so that it can thus be used in a subsequent operation, as in arguments to some command such as **ls** ("...and use command substitution to get an ls -l ").

You are misunderstanding the issue.  Again, it is the output from some command, which is interpolated via command substitution that creates the word-split issue.  The original problem clearly shows that the *output from* locate may present some paths which contain whitespace (such as "/home/jross/WorkDocs/My List"), and backslash interpolation will break that single pathname into two distinct words "/home/jross/WorkDocs/My" and "List".

Again, the question is, and I'll rephrase: "How do you take the output from some path listing command, such as **locate**, and interpolate that output into the argument list of another command WITHOUT whitespace word-splitting".  I've provided an answer.

MrC

---

### Post by bodhi.zazen on 2008-02-28
LOL, as is typical there is more then one way of skinning the cat. The first post I make is also a solution.

The command I posted was yours using a file with a space in the name, and as demonstrated, it failed under my interpretation of the question.

I understand why your command failed, and in fact> locate /home/bodhi/"my test"  | xargs -d '\n' ls -ldworks just fine. I agree, it is a matter of syntax re: white space.

I think we need clarification from the OP at this point.

---

### Post by Mr. C. on 2008-02-28
It isn't a general solution and fails completely when there is more than a single value returned from locate.

With double quotes around the interpolated output, ALL output becomes a single string:
$```
 ls -l test
total 12
drwx------ 2 mrc users 4096 Feb 28 09:42 a/
drwx------ 2 mrc users 4096 Feb 28 09:42 b/
drwx------ 2 mrc users 4096 Feb 28 09:42 c\ d/

$ ls -ld `locate test`
ls: /home/mrc/test/c: No such file or directory
ls: d: No such file or directory
drwx------ 8 mrc users 4096 Feb 28 09:42 /home/mrc/test/
drwx------ 2 mrc users 4096 Feb 28 09:42 /home/mrc/test/a/
drwx------ 2 mrc users 4096 Feb 28 09:42 /home/mrc/test/b/

$ ls -ld "`locate -d /tmp/locatedb test`"
ls: /home/mrc/test\n/home/mrc/test/a\n/home/mrc/test/b\n/home/mrc/test/c d: No such file or directory
```

If you can't see the failure here, let's end this nonsense.  You clearly don't get it.
MrC

---

### Post by Joeb454 on 2008-02-28
Bodhi.Zazen's solution worked for me.

I also find that you can escape spaces by using a backslash. e.g something like ```
cd ~/programming/my\ programs
```

---

### Post by Mr. C. on 2008-02-28
> **Joeb454 said:**
> Bodhi.Zazen's solution worked for me.

I also find that you can escape spaces by using a backslash. e.g something like ```
cd ~/programming/my\ programs
```

Reading has become a real problem here!

Once again, the issue isn't how to escape a space - that's trivial.  You're providing an answer to the wrong question.

---

### Post by lenticular on 2008-02-28
Thanks so much for all the great suggestions.  What lead me to ask the question was my need to locate some OpenOffice spreadsheet somewhere in my home directory.  Basically, I wanted locate to return all .odt (or .xls) files, do an ls -l so that I could have a time stamp, then slice and dice with cut to find those that were most recently modified.

It is really gratifying to see the great response on this.

Thanks,
  John

---

### Post by Mr. C. on 2008-02-29
Try using find:

```
find $HOME \( -name "*.ost" -o -name "*.xls" \) -ls
```

This will be more accurate, as the locate database is built only nightly, so any new additions won't be detected.  See also the -newer and  -mtime options to find.

MrC

---

### Post by ghostdog74 on 2008-02-29
then just use find and a bit of sort to get the latest modified. Assuming GNU find,
```

find /path -name "*.odt" -printf "%A@:%f\n" |sort -n   

```
please check the man page of find for more information. You can also use -mmin option.

---

### Post by bodhi.zazen on 2008-02-29
If you are interested, here is a nice overview of find :

[http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

---

