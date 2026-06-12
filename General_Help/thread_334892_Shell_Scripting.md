---
title: "Shell Scripting"
date: 2007-01-09
forum: General Help
---

### Post by studiesrule on 2007-01-09
I want to make a script that will update all my svn directories regularly, and build them if required. What I thought of doing was writing a simple shell script and then using cron to run the script every so often.

However, I do not know how to check if the svn has actually updated anything, and how to use the if statements with that. As of now, I am just making every thing always. Since make is change-based, I don't actually make anything. But it does waste time and processor time to go on in its recursive process. As of now it is:

```

#! /bin/sh
# This file will update via svn several folders, and make the updated files

# Geany
svn checkouot https://svn.sourceforge.net/svnroot/geany/trunk ~/usr/geany
make -C ~/usr/geany/

# CodeBlocks
svn checkout svn://svn.berlios.de/codeblocks/trunk ~/usr/cb-svn
make -C ~/usr/cb-svn/

```

Thanks in advance...

---

### Post by koenn on 2007-01-09
have a look at rsync. it can synchronise files/directories between your pc and a remote system and only transfers the differences. 

If you run it verbose it will also give you a list of the files that have changed so you could use that to decide if you have to "make" anything. 

I don't know how svn works, but on I remember reading on the rsync website about syncing with a CVS so maybe you wanna have a look: 
[http://samba.anu.edu.au/ftp/rsync/rsync.html](http://samba.anu.edu.au/ftp/rsync/rsync.html)

---

### Post by schilcha on 2007-01-09
here's, what I do with CVS (don't know about svn, but you can do the same thing pretty similar):
```

if [ `cvs -n update 2>/dev/null | wc -l` -gt 0 ]; then
  echo "qaqa" # or do something more intelligent...
fi
```

the -n flag means "dry-run", i.e. pretend to be updating your working copy, but don't really do it.

2> /dev/null redirects stderr to the sink, since cvs produces quite a bit of messages to stderr

finally count the lines of to-be updated files with wc -l and check if that count (evaluated enclosed in ` ... `) is greater than zero (-gt 0)

I don't know, if this syntax is sh-compatible. It for sure is bash-syntax.

Good luck,
   schicha

---

### Post by studiesrule on 2007-01-10
thanks a lot, especially to schilcha. I got it working using this script:
```

# This file will update via svn several folders, and make the updated files
addr=
no=0
addr[0]=~/usr/geany; no=`expr $no + 1` #Geany
addr[1]=~/usr/cb-svn; no=`expr $no + 1` #CodeBlocks
for ((i=0;i<$no;i++)); do
	if [ `svn diff -r HEAD ${addr[i]}|wc -l` -gt 0 ]; then
		svn update ${addr[i]}
		make -C ${addr[i]}
		echo "${addr[i]} updated to latest revision"
	else
		echo "${addr[i]} already latest revision"
	fi
done

exit 0;

```

---

