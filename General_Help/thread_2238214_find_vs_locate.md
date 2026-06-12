---
title: "find vs locate"
date: 2014-08-06
forum: General Help
---

### Post by cmcanulty on 2014-08-06
I am taking the free online Intro to Linux course and am having trouble with find vs locate. Why do I get a large number of results for a search in locate and the same files don't pop up when I try find? I went over the section 3x but am missing something, thank you

---

### Post by Vaphell on 2014-08-06
the main difference is that find deals with true contents of the hdd and locate deals with a daily snapshot of the disk state stored in database which may or may not be current. You can refresh it at will with sudo updatedb.
The way you query these tools may also be a factor, but without further details it's hard to say.

---

### Post by steeldriver on 2014-08-06
I *suspect* what's tripping you up is that locate matches the search string against the whole path, whereas the 'find -name' matches against *only* the actual file name

But since you didn't give us any actual examples, it's hard to say for sure

---

### Post by nerdtron on 2014-08-06
And also may be your find command is limited to a directory or the current directory only. Try find / and you'll search from the root of the filesystem. I never have the use for locate command.

---

### Post by whitesmith on 2014-08-06
All this and more: locate uses a database of files compiled at some usually unknown time. So locate will return results faster, but find gives a picture of files/directories at this specific instant. Many changes may have occurred after locate  last ran. If this is confusing, see```
man locate
```vs```
man find
```

---

### Post by ajgreeny on 2014-08-06
I also agree with all the above, but would just add the comment that I always up-date the file database with sudo updatedb if using locate so that all results will be current and correct for me.
Also note that if you look at the manuals for both find and locate you will see that **man locate** is a great deal simpler to understand with just 164 lines compared with **man find** which has 1272 lines.  Find is, of course, much more powerful, but - - - ?

I have to admit I use locate a lot more than find largely because I can never remember the syntax needed for find (perhaps I should force myself to use it more so I will remember), and to limit the output of locate I pipe it to grep and thereby manage to search a particular folder eg my /home or /etc recursively if needed.

---

### Post by cmcanulty on 2014-08-06
thanks for all the examples here is the return from identical searches
```

cmcanulty@ubuntu1:~$ locate castelnu
/home/cmcanulty/Documents/Guitar/4shared.com/castelnuovo+tedesco.htm
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 1.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 2.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 3.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 4.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 5.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor.zip
cmcanulty@ubuntu1:~$ find castelnu
find: `castelnu': No such file or directory
cmcanulty@ubuntu1:~$ 
```

---

### Post by vasa1 on 2014-08-06
> **cmcanulty said:**
> ...
```

cmcanulty@ubuntu1:~$ locate castelnu
...
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 5.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor.zip
cmcanulty@ubuntu1:~$ find castelnu
find: `castelnu': No such file or directory
cmcanulty@ubuntu1:~$ 
```
Try
```
find -name "castel*"
```
What this does is to search for anything beginning with "castel" in the current directory and its subfolders. So I get:```
[07:21 AM] ~ $ find -name "castel*"
./castelnuovo - naranjos en flor 1.gif
./Desktop/castelnuovo - naranjos en flor 1.gif
./Desktop/castelnuovo - naranjos en flor 2.gif
./Public/castelnuovo - naranjos en flor 3.gif
[07:23 AM] ~ $ 
```
I tihkn it's important to either be in the top **relevant** directory or to specify the relevant directory from within the command. If carelessly used, *find* will work its way down whatever subdirectories exist and take a long, long time (Ctrl+C to the rescue).

*find* is vastly broader in scope than *locate* which does just the one thing.

While *man find* may not be enjoyable reading, here are a couple of articles that show *find*'s utility:
[http://www.oracle.com/technetwork/articles/calish-find-087766.html](http://www.oracle.com/technetwork/articles/calish-find-087766.html)
[http://www.openlogic.com/wazi/bid/188094/](http://www.openlogic.com/wazi/bid/188094/)

Another thing is that *find* uses things like "*" and "." differently than *awk* or *sed* do. Maybe something to do with globbing?

---

### Post by nerdtron on 2014-08-07
> **cmcanulty said:**
> thanks for all the examples here is the return from identical searches
```

cmcanulty@ubuntu1:~$ locate castelnu
/home/cmcanulty/Documents/Guitar/4shared.com/castelnuovo+tedesco.htm
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 1.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 2.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 3.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 4.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor 5.gif
/home/cmcanulty/Documents/Guitar/Pattituras.8m/castelnuovo - naranjos en flor.zip
cmcanulty@ubuntu1:~$ find castelnu
find: `castelnu': No such file or directory
cmcanulty@ubuntu1:~$ 
```

Your comparing two different command entirely on different syntax. You see, the find command requires a little bit more tweaking and it can give more of an elaborate search such as finding files of older than n days or files created by a certain user.
Refer to this guide to see how powerful the find command is and how it is used.
[http://www.tecmint.com/35-practical-examples-of-linux-find-command/](http://www.tecmint.com/35-practical-examples-of-linux-find-command/)

---

### Post by Vaphell on 2014-08-07
in this form you told find to scan dir 'castelnu' without further options. There is no such dir ergo...

also locate search is global, but find scans only dirs+subtrees given as params (default current dir) because disk thrashing is orders of magnitude slower than a simple database lookup and you almost never want to *find /* which would possibly take an hour or so.


if you want to search stuff in your homedir
[FONT=Courier New]find ~ -name '*castelnu*'[/FONT] (shell globs, -iname for case insensitive search)
or
[FONT=Courier New]find ~ -regex '.*castelnu.*'[/FONT] (regex format. -iregex for case insensitive)

---

### Post by vasa1 on 2014-08-09
> **Vaphell said:**
> ...
[FONT=Courier New]find ~ -regex '.*castelnu.*'[/FONT] (regex format. -iregex for case insensitive)
Nice! Never knew about **-regex** or **-iregex**.

---

