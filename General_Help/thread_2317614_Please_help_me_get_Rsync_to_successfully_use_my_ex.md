---
title: "Please help me get Rsync to successfully use my exclude list"
date: 2016-03-18
forum: General Help
---

### Post by MibunoOokami on 2016-03-18
Hi all,
 

 I would appreciate it if someone could tell me what I am doing wrong with my Rsync exclusion list?
 

 Recently I discovered through another of my threads Rsync may not have been excluding anything in my exclusion list. Yesterday I cleaned up an old HDD to back up my machine and confirm whether or not Rsync is using the exclusions list. As suspected Rsync didn't exclude anything.
 

 I did plenty of reading of other threads about creating and using exclusion lists with Rsync, then edited my back up script and exclusion list repeatedly to no avail and at this very moment in time Rsync is now saying there's no such file or directory.  Below is a copy of my backup script, my exclusions list and the various alternatives I tried in order to make it work. Please point out and correct my error(s) because clearly I can't work it out for myself and I'm just about at my wits end.
 

 Original back up script = no error messages

 ```
rsync -avrPS --exclude-from=backup_excludes.lst ~/ /media/mno/ADATA/Backup.HP
```
 

 1st edit = as above

 ```
rsync -avrPS --exclude-from='backup_excludes.lst' ~/ /media/mno/ADATA/Backup.HP
```
 

 2[SUP]nd[/SUP] edit = as above

 ```
rsync -avrPS &#8211;exclude-from 'backup_excludes.lst' ~/ /media/mno/ADATA/Backup.HP
```
 

 3[SUP]rd[/SUP] edit = no such file or directory
 ```
rsync -avrPS &#8211;exclude-from=/home/bin/backup_excludes.lst ~/ /media/mno/ADATA/Backup.HP
```
 

 4[SUP]th[/SUP] edit = no such file or directory
 ```
rsync -avrPS &#8211;exclude-from='/home/bin/backup_excludes.lst' ~/ /media/mno/ADATA/Backup.HP
```
 

 Original exclude list.
 ```

 ~/home/*/.cache** 
 ~/home/*/.dbus 
 ~/home/*/.dropbox 
 ~/home/*/.mozilla/firefox/f0siflo0.default/Cache/** 
 ~/home/*/.mozilla/firefox/f0siflo0.default/Cache.Trash 
 ~/home/*/.mozilla/firefox/1ccnqwzj.default/Cache/** 
 ~/home/*/.mozilla/firefox/1ccnqwzj.default/Cache.Trash 
 ~/home/*/.local/share/Trash/** 
 ~/home/*/.cache/thumbnails 
 ~/home/*/.cache/mozilla 
 ~/home/*/.cache/thunderbird 
```
 

 In my second edit I removed the double **. Third edit added them back and removed /home so it was just ~/*/.cache**. Despite all this, all the above directories still get copied complete with their contents. Most of the path names I copied exactly from Rsync when it had run.

EDIT: Solution in post [#6]("http://ubuntuforums.org/showthread.php?t=2317614&p=13457090#post13457090")

---

### Post by mcgess on 2016-03-18
The rsync command assumes that any excluded files must be within the directory you are backing up. If you are backing up /home/your_user_name/ but wish to exclude /home/your_user_name/.cache then the exclude entry is just .cache

---

### Post by MibunoOokami on 2016-03-18
> **mcgess said:**
> The rsync command assumes that any excluded files must be within the directory you are backing up. If you are backing up /home/your_user_name/ but wish to exclude /home/your_user_name/.cache then the exclude entry is just .cache

So the exclude list should be directly in my home (/home) directory rather than in the bin (/home/bin) directory with my backup script?

---

### Post by HermanAB on 2016-03-18
Howdy,

The exclude feature uses pattern matching.  Don't specify the whole path, only the file patterns to exclude.

You'll have better luck with *dropbox*, *thumb* and *rash* than with a full path.

---

### Post by MibunoOokami on 2016-03-18
> **HermanAB said:**
> Howdy,

The exclude feature uses pattern matching.  Don't specify the whole path, only the file patterns to exclude.

You'll have better luck with *dropbox*, *thumb* and *rash* than with a full path.

I was to understand if I were to just put in a word like *thumb* then every directory/file with that in it's name would be excluded. Is that incorrect?

This may be a daft question but are the *s necessary? At this point I'll try anything just want to be sure I get it right.

---

### Post by ajgreeny on 2016-03-18
I am wondering if the leading tilde ~ in your listed entries is one character too many.

~ is the shortcut for your home folder so in the entry you show of ```
~/home/*/.cache**
```
you seem to be listing ```
/home/username/home/*/.cache
``` which, of course, does not exist.

Use just **.cache** in the list and it should work, assuming you are running rsync as user.

---

### Post by mcgess on 2016-03-18
Hi

> So the exclude list should be directly in my home (/home) directory  rather than in the bin (/home/bin) directory with my backup script?

The file specifying files and directories to exclude can be anywhere you want so
```
--exclude-from=/home/bin/backup_excludes.lst
```
is fine as long as the file exists and you have access. Its the contents of backup_exclude.lst which should not have the full directory path name.

> are the *s necessary?
*s just make it easier to catch all possible variations of a name so *dropbox* will match dropbox .dropbox dropbox-cache .some_really_silly_name_containing_dropbox_2

> I was to understand if I were to just put in a word like *thumb* then  every directory/file with that in it's name would be excluded.
True.

There is a way to control the files matched by a pattern as it can be easy to accidentally exclude files that you really want to backup. Suppose for example you have a directory Videos/Spectacular_Car_Crashes/ this would be excluded by the pattern *rash*. To exclude the Trash directory have this line in your backup_exclude.lst 
```
/.local/share/*rash*/
```
Starting the pattern with the / before .local says start from the base of the directory structure you are backing up (your home directory in this case) go into .local then share and then match files against *rash*

When creating new rsync commands I usually use the -n and -v options so that a dry run is performed which lists every file/directory which would be copied across when the command is re-run without the -n.

Martin

---

### Post by montag dp on 2016-03-18
> **ajgreeny said:**
> I am wondering if the leading tilde ~ in your listed entries is one character too many.

~ is the shortcut for your home folder so in the entry you show of ```
~/home/*/.cache**
```
you seem to be listing ```
/home/username/home/*/.cache
``` which, of course, does not exist.

Use just **.cache** in the list and it should work, assuming you are running rsync as user.ajgreeny has it right.  The problem is that you've entered invalid paths in backup_excludes.lst.

---

### Post by MibunoOokami on 2016-03-18
> **ajgreeny said:**
> I am wondering if the leading tilde ~ in your listed entries is one character too many.

~ is the shortcut for your home folder so in the entry you show of ```
~/home/*/.cache**
```
you seem to be listing ```
/home/username/home/*/.cache
``` which, of course, does not exist.

Use just **.cache** in the list and it should work, assuming you are running rsync as user.

Yes, it turns out just using .cache and so on is sufficient enough, I just ran the back up which seemed to take forever but the directories in my exclude list were not backed up.
 I can't believe I was so close when I thought removing the word “home” and one of the forward slashes might make a difference. All I needed to do was remove the tilde and asterix as well.

> **mcgess said:**
> 
*s just make it easier to catch all possible variations of a name so *dropbox* will match dropbox .dropbox dropbox-cache .some_really_silly_name_containing_dropbox_2

There is a way to control the files matched by a pattern as it can be easy to accidentally exclude files that you really want to backup. Suppose for example you have a directory Videos/Spectacular_Car_Crashes/ this would be excluded by the pattern *rash*.
 
 That's what I was worried about

  > **mcgess said:**
> 
 To exclude the Trash directory have this line in your backup_exclude.lst 
```
/.local/share/*rash*/
```
Starting the pattern with the / before .local says start from the base of the directory structure you are backing up (your home directory in this case) go into .local then share and then match files against *rash*


Thanks for the explanation and the solution to avoid not backing up any files that may have a similar name to those I do want excluded.

---

### Post by MibunoOokami on 2016-03-18
I know this thread was about getting Rsync to use my exclude list and to that end this topic is solved, but I have two more questions about other directories to exclude and don't want to start a new thread just for that, so would like to ask them here.

 #1 How important is the .local directory, as in could I exclude that without running into issue somewhere down the track? I think it was some sub-directories within .cache that were using up a fair bit of space.

 #2 I can't help but think that any saved passwords might be there for anyone to use if I were to lose my back up drive. I'd like to exclude whatever directory stores passwords, can you tell me where they are?

 Thank you.

---

### Post by ajgreeny on 2016-03-18
There are some files and folders with configuration details of applications you have installed in the ~/.local folder so you may prefer to backup most of those if that is of value to you.  Trash, of course is unlikely to be necessary.

Have a look through the folders in there, all probably in the share subfolder; only you will know if they're important to you, but they take very little space so I would back them up if it were me.  Your choice.

PS:
If you feel this is really now solved, please mark as such from the Thread Tools menu at the top of the thread.

---

