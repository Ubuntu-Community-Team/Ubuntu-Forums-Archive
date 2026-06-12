---
title: "Deleting a mixture of hidden and normal directories and files"
date: 2016-02-24
forum: General Help
---

### Post by Crabro on 2016-02-24
I am having trouble deleting backup directories of my evolution files in my daily backups script. I wish to delete the old backup so that I get a clean copy of the files. Some directories within the path are hidden, and some not.
for example I can have a path like 
'/media/backups/daily_backups/evolution_Wed/local/share/evolution/mail/local/.eBay Archives.2014.2014 10 23 SSD/cur/1234567890123.gandalf:2,RS'
I have tried the obvious rm -rf and several variations on the find including things like find /path/to/dest/ -iname ".*" -type d
I have even tried a mv to a tmp directory.
However they all fail, I think because of the mixture of hidden and not hidden directories.
If I use caja then it works as expected, so I know it can be done, I just don't know how!
TIA

---

### Post by papibe on 2016-02-24
Hi Crabro.

Hidden files and directories shouldn't be a problem for 'rm' is you run it one level above.

For instance, this may leave some files around:
```
rm -rf  /media/backups/daily_backups/evolution_Wed/*
```
However, this should delete all the Wednesday backup (please review before running):
```
rm -rf  /media/backups/daily_backups/evolution_Wed/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Crabro on 2016-02-24
Thanks papibe.
I have tried that and end up with many errors, typically:
rm: cannot remove &#8216;/media/backups/daily_bkps/evolution_Wed/Local/share/evolution/mail/local/.Miscellaneous.Exec.Exec 2009/cur&#8217;: Directory not empty
Thanks,
Crabro

---

### Post by papibe on 2016-02-24
Are you using a script to remove the files?

Is there a find command in there?

If you want to remove the whole backup, you need just one command. However, if you are committed to your script, make sure your find command has de '-depth' option so it tries to delete the 'leafs' before a branch.

Regards.

---

### Post by Crabro on 2016-02-24
I run a script daily to copy the two evolution data directories. Within evolution I store files in logical (to me!) folders. Eg my ebay folder contains a folder for each purchase or sale. Once the purchase or sale is complete I move the folder to an archive folder. I am concerned that by just overwriting each backup I will end up with two copies of folders, hence the need to delete each daily backup.
I have tried the find command but without the 'depth' option, but with the -delete option, which according to 'man' implies -depth?
I (think) I have tried all of:
'find /path/to/dir/ -type d -iname ".*" -delete'
'find /path/to/dir/ -type f -iname ".*" -delete'
'find /path/to/dir/ -type d -iname "*" -delete'
'find /path/to/dir/ -type f -iname "*" -delete'
I just ran the second version and received:
find: cannot delete &#8216;/media/backups/daily_bkps/evolution_Wed/Local/share/evolution/mail/local/.ebay.Archive.2012.2012 07 19 DS:TCG.cmeta&#8217;: No such file or directory
Do I have to run these in some kind of a loop?
Regards,
Crabro

---

### Post by papibe on 2016-02-24
Thanks, that's correct. The delete option implies -depth :D

Not sure which one the first version or the second one, but if you separate the deletes, you should delete files before delete directories.
```
find /path/to/dir/ -type f -delete
find /path/to/dir/ -type d -delete
```
'find' should have no problem finding hidden files and directories.

Nevertheless, this, as simple as it looks, should work too:
```
find /path/to/dir/ -delete
```
Note that this would also remove the bottom directory 'dir'

An example:
```
$ ls

$ mkdir -p tmp2/tmp3 tmp2/tmp4 tmp2/.tmp5 tmp2/.tmp6; touch tmp2/tmp3/dummy1 tmp2/.tmp5/dummy2

$ ls
tmp2/

$ tree -a tmp2/
tmp2/
&#9500;&#9472;&#9472; tmp3
&#9474;** &#9492;&#9472;&#9472; dummy1
&#9500;&#9472;&#9472; tmp4
&#9500;&#9472;&#9472; .tmp5
&#9474;** &#9492;&#9472;&#9472; dummy2
&#9492;&#9472;&#9472; .tmp6

4 directories, 2 files
                                              
                                        
$ find tmp2/  -delete

$ ls

$
```
Let us know how it goes.
Regards.

---

### Post by Crabro on 2016-02-25
Thanks for the idea.
Well, I ran your code creating tmp2 etc in my home directory and it worked exactly as you predicted.
I then cd to my backup and full of enthusiasm tried it there. Problem!
Find reported many errors, typically:
find: cannot delete &#8216;/media/backups/daily_bkps/evolution_Thu/config/evolution/mail/folders/et-expanded-folder:__local_eBay_20Buying_2012_2012_2002_20Nail_20Punch&#8217;: No such file or directory
It then went on to report that it could not delete non-empty directories.

I have just had a look at rsync, and that supports --delete which may do what I want; --help says it deletes extraneous files from the receiver. Does this mean that it will end up reflecting the source? Would this not be quicker, too?
I could pm you and send you a sample of the files?
I am clutching at straws here!
Thanks,
Crabro

---

### Post by SeijiSensei on 2016-02-25
A reliable method to delete dot files is to use
```
rm \.?*
```
The "?" matches an alphameric character and the asterisk represents the rest of the filename.

---

### Post by Crabro on 2016-02-25
As a further note to the above, I think there is clearly a problem with the server containing the backups (a Netgear NAS).
As I am unhappy with the state of the script I closed evolution and copied evolution's files into evolution_Thu. I then deleted evolution_Wed and copied evolution_Thu into evolution_Wed
When I r-click, Properties on these folders I get 1900 files, 62MB, but both copies reported 26,000+ files and 1.5GB - which I believe!
Crabro

---

### Post by Crabro on 2016-02-25
> **SeijiSensei said:**
> A reliable method to delete dot files is to use
```
rm \.?*
```
The "?" matches an alphameric character and the asterisk represents the rest of the filename.
I tried this and received
rm: cannot remove ‘..’: Is a directory

---

### Post by SeijiSensei on 2016-02-25
Well, you don't want to delete "..", that points to the directory above the one you are in.  (Try entering "cd .." and see where you end up.)

It will delete the dot files in the directory, though.

---

### Post by papibe on 2016-02-25
> **SeijiSensei said:**
> A reliable method to delete dot files is to use
```
rm \.?*
```
The "?" matches an alphameric character and the asterisk represents the rest of the filename.
Are you sure?
```
$ echo \.?*
[COLOR="#FF0000"]**..**[/COLOR] .bash_history .bash_logout .bashrc .cache .config .lesshst .local .profile .selected_editor .ssh .viminfo .vimrc
```
I'd use this expression instead:
```
$ echo .[^.]*
.bash_history .bash_logout .bashrc .cache .config .lesshst .local .profile .selected_editor .ssh .viminfo .vimrc
```
Or this one:
```
$ echo !(.|..)
```
Regards.

---

### Post by SeijiSensei on 2016-02-25
Are we talking about ".."? If you use rm without -r then it won't touch directories.  And if you don't use -f you'll be prompted for each delete on most systems.  I'm not sure I understand the point you're making.  All the other entries in your first list besides ".." are files.  What am I missing?

---

### Post by Crabro on 2016-02-26
Thanks all, for all your help.
I went on to develop a script which used rsync --delete, which worked fine using hidden and not hidden files in hidden and not hidden directories.
However once I tried it with the evolution files, similar errors occurred as before.
Whilst doing some more research I remembered there is a backup option within evolution, which I wondered if I could trigger. I ran it and it created a compressed archive .tar.gz
So that is what I have done, I am creating a compressed archive within my script, using tar -zcvf. Uses less space, too!
I appreciate your efforts though.

---

