---
title: "Help sorting files."
date: 2015-01-17
forum: General Help
---

### Post by Arunomi on 2015-01-17
Hi I have 456 tusen files and l wounder if I can use find and move command to sort all file by there extentions in folders. Example the command should find out what kind of extentions is in the folders and make dir like "jpg" and then move all jag in to that folder and then move to the next extention.  I hope it's possible and that some one can help me.

---

### Post by Holger_Gehrke on 2015-01-17
You could try this:
```
for i in $(ls -1 -p|sed '/\/$/d;s/.*\.\(.*\)/\1/'|sort|uniq) ; do mkdir $i; mv *.$i $i; done
```
but if there's really 456000 files it might **fail horrible** because the shell expands wildcards before executing the commands and then the commands might become longer than the buffer the shell has for them. I'd say it's safe if no more than about 1000 files have the same extension. You should remove the 'mkdir' command and replace the 'mv' with 'echo' to test this in a way that can't do anything catastrophic.

That  little snippet takes the list of files in the current working  directory, removes the subdirectories from it, shortens the file names  to their extension, sorts the list of extensions and removes all  multiples from that list before going through this list and making one  directory named for the extension per extension and moving files with  that extension into that directory. Fails in interesting ways for files  with no extension (makes a directory with the filename and moves the  file into it).

---

### Post by Arunomi on 2015-01-18
How do I use this command? should it bee mande to a shell script and the executed?

---

### Post by Holger_Gehrke on 2015-01-18
It's just a normal command. Execute it in the bash in a terminal. Just open a terminal window, change to the directory with all the files and cut-and-paste the line (paste in the terminal is Ctrl-Shift-V, because Ctrl-V is already in use for something else in the shell).

And I've checked the limit for the command length after all expansions of wild cards are done, on my system it's about 2 MB so my estimate of about a thousand files with the same extension can be changed upwards - by an order of magnitude at least :-)  ... You can check that limit on your system by executing ''getconf ARG_MAX' in a terminal-window.

---

### Post by Arunomi on 2015-01-18
It works wounders i tried it on 4000 files and it dose exakly what i want it to do. There is just one problem, it only works in the dir im in and not on the sub dir's.
It would bee nice if it could go down in sub dir's and fetch files and then delete the sub dir's.

---

### Post by Arunomi on 2015-01-18
I put it in a file and executed it as a shell script.

---

### Post by Arunomi on 2015-01-18
On my system it sorted 2900 files of the same sort in one go.

---

### Post by Arunomi on 2015-01-18
So if i try to sort all 456000 files in a go whats the worst that can happen. All files get lost/deleted and the system crashes?

---

### Post by Arunomi on 2015-01-18
arunomi@desktop-P5K:/media/arunomi/Backup/Test$ getconf ARG_MAX
2097152

---

### Post by Lars Noodén on 2015-01-18
It would be a good idea to make a backup using [tar](http://manpages.ubuntu.com/manpages/trusty/en/man1/tar.1.html) or something.  

```

cd /home/arunomi/tusen/
tar zcf /home/arunomi/tusen.tar.gz ./*

```

Then if something goes wildly wrong, you can restore from the back up.  Then when you are sure the move went ok you can delete the backup copy.

---

### Post by Arunomi on 2015-01-18
dose Tar compress files? The sizes im working with is 1.8TB.

---

### Post by Lars Noodén on 2015-01-18
Tar will compress, look at the z and j options in the manual page.  But 1.8 TB is a lot, so a lot of space will be needed.  Also, if the files are already compress, such as JPEG files, they won't change size.  

How are you doing your backup currently?

---

### Post by Arunomi on 2015-01-18
I tried to use testdisk but I could not get the partition back so i used photorec and it found 456000 files and they are now save on a seperate 3 tb hdd. So i have 6 tb of space but i dont want to save any thing on the first 3 tb hdd.

---

### Post by Holger_Gehrke on 2015-01-18
A simple way to check how many files of a given extension there are:
```

ls -1 *."ReplaceWithExtension"| wc -l

```
or for an overview:
```

for i in $(ls -1 -p|sed '/\/$/d;s/.*\.\(.*\)/\1/'|sort|uniq) ; do echo $i : $(ls *$i|wc -l); done

```
You can see that this is the same loop-construction as the 'separate files into directories' command line in post 2 just with  different commands in the body of the loop.

You could also do
```

ls -1a|wc -c

```
this would tell you what the length of the command line would be if all files where of the same extension. If that's smaller than the allowed 2MB, nothing bad should happen.

After you've separated the files by extension - and presumably by type of content - you'll want to check the integrity of the files. For image files 'identify' from the image magick suite can be used for this. For .zip Archives - including OpenOffice odf-files - unzip with the option -t can do this check. Of course this can be done (semi-) automatically by doing something like this:
```

mkdir badfiles; for i in * ; do unzip -t "$i"||mv "$i" badfiles;done

```
This would test all files in the current directory with unzip and move all files that are either damaged zip files or not zip files at all into the directory badfiles. 

Similar tests can be found for a lot of file formats.

---

