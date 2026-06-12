---
title: "rsync bash script issue"
date: 2014-09-22
forum: General Help
---

### Post by ric_Poirier on 2014-09-22
Hi everyone,

For some time now, I have been trying to write a bash script (using *rsync*) that would allow me to:
[LIST=1]
[*]backup my home folder on a removable hard drive;
[*]sync all files from my home folder to the hard drive, except **~/Videos/Films**, **~/Videos/Séries télé** and **~/Music**, which I want to collect. For these three directories, I would like *rsync* not to delete on the hard drive the files I delete on my computer.
[/LIST]
I have tried to make a script using a couple variables, to practice, but also to make the script a bit more general.

Here is the script:

```

        coldir1='Videos/Films/'
        coldir2="Videos/Séries télé/"
        coldir3='Music/'

        collection1="$HOME/$coldir1"
        collection2="$HOME/"$coldir2""
        collection3="$HOME/$coldir3"

        disk="sauvegarde"
        pathdisk="/media/$USER/$disk/"
        pathlogs="$HOME/.logs/$disk"
        outputlog="$pathlogs/sortie.log"
        errorlog="$pathlogs/erreurs.log"

rsync -arv --ignore-errors --delete --progress --stats --exclude=$coldir1 --exclude="$coldir2" --exclude=$coldir3 $HOME/ $pathdisk >> $outputlog 2> $errorlog

rsync -arv --ignore-errors --delete --progress --stats $collection1 $pathdisk$coldir1 >> $outputlog 2> $errorlog

rsync -arv --ignore-errors --delete --progress --stats "$collection2" $pathdisk"$coldir2" >> $outputlog 2> $errorlog

rsync -arv --ignore-errors --delete --progress --stats $collection3 $pathdisk$coldir3 >> $outputlog 2> $errorlog

```

Now, when I run a debug on this script, I get:

```

+ coldir1=Videos/Films/
+ coldir2='Videos/Séries télé/'
+ coldir3=Music/
+ collection1=/home/eric/Videos/Films/
+ collection2='/home/eric/Videos/Séries télé/'
+ collection3=/home/eric/Music/
+ disk=sauvegarde
+ pathdisk=/media/eric/sauvegarde/
+ pathlogs=/home/eric/.logs/sauvegarde
+ outputlog=/home/eric/.logs/sauvegarde/sortie.log
+ errorlog=/home/eric/.logs/sauvegarde/erreurs.log
+ rsync -arv --ignore-errors --delete --progress --stats --exclude=Videos/Films/ '--exclude=Videos/Séries télé/' --exclude=Music/ /home/eric/ /media/eric/sauvegarde/
+ rsync -arv --ignore-errors --delete --progress --stats /home/eric/Videos/Films/ /media/eric/sauvegarde/Videos/Films/
+ rsync -arv --ignore-errors --delete --progress --stats '/home/eric/Videos/Séries télé/' '/media/eric/sauvegarde/Videos/Séries télé/'
+ rsync -arv --ignore-errors --delete --progress --stats /home/eric/Music/ /media/eric/sauvegarde/Music/

```

Now, notice the ' in the following debug line:

```

+ rsync -arv --ignore-errors --delete --progress --stats  '/home/eric/Videos/Séries télé/' '/media/eric/sauvegarde/Videos/Séries  télé/'

```

When I look at the rsync output for this line, I see this:

```

sending incremental file list
Entourage/
Entourage/Entourage - Season 1/
Entourage/Entourage - Season 2/
Entourage/Entourage - Season 3/
Entourage/Entourage - Season 4/
Entourage/Entourage - Season 5/
Entourage/Entourage - Season 6/
Entourage/Entourage - Season 7/
Entourage/Entourage - Season 8/

Number of files: 220 (reg: 203, dir: 17)
Number of created files: 0
Number of deleted files: 0
Number of regular files transferred: 0
Total file size: 40,071,507,161 bytes
Total transferred file size: 0 bytes
Literal data: 0 bytes
Matched data: 0 bytes
File list size: 0
File list generation time: 0.001 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 9,189
Total bytes received: 386

sent 9,189 bytes  received 386 bytes  19,150.00 bytes/sec
total size is 40,071,507,161  speedup is 4,185,013.80

```

One last note: I have run several times this script, so *rsync* has nothing more to transfer.

The problem is I have other directories that do not show in there (for example, some Walking Dead seasons, with subdirectories). My questions are:
[LIST=1]
[*]Why do they not show?
[*]Is there a syntax problem with my variables?
[*]What exactly is the **sending incremental file list** line? Is it a list of the directories/subdirectories that *rsync* reads before transferring?
[/LIST]

Thanks a lot, and sorry for all the code. Just wanted to be clear, hope this is helpful...

---

### Post by TheFu on 2014-09-23
I don't know, but


        collection2="$HOME/"$coldir2"" 

is not valid.  You cannot nest quotes like that in bash.  

Also, the first line is missing #!/bin/bash - this is needed.

I would only use normal 7-bit ASCII characters in directory names until getting this to work, I'd avoid spaces or any accented characters.  Get it working, then put in the names I prefer after everything else is working. It shouldn't be an issue, but sometimes these programs are created by people who don't handle those characters daily. I'm probably wrong, but .. 

So - I can recommend the ABSG - advanced bash scripting guide - as a good resource for reference.
I'm concerned about the --ignore-errors. Why?  rsync is an amazing tool - especially for mirroring things. I use it all the time.  For backups, where versioning is mandatory (and it is always), there are better tools like rdiff-backup.

---

### Post by Jonor on 2014-09-23
If writing the script becomes too involved and you are willing to try a graphical tool then luckybackup should cover it, 
including the exceptions and executing other things. Check out the advanced options for a task.
It is also based on rsync i understand. My external (usb flashdrive) media has to be "primed" with an ordinary copy / paste though. 
I suspect it suffers time out problems if the changes to the backup are too large.
Internal drives don't need priming.

---

### Post by oldfred on 2014-09-23
I am planning on converting to TheFu suggestion of rdiff-backup, but currently use rsync. My versioning is periodical copies of most important data to DVDs.

I started with this simple script.

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first 

But since I create new installs regularly and may not have created the mount point I added that to the script and the mount. Once needed once per install, so better in my new install script, not here.

```

#!/bin/bash
# backup script - mybackup.sh
# a - archive, retain file settings equals -rlptgoD (no -H,-A,-X)
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# -l, --links copy symlinks as symlinks
# -i, --itemize-changes
# -t, --times preserve modification times
# --exclude option to prevent copying things

# ! not 
if [ ! -d /mnt/backup ]; then
     mkdir /mnt/backup
fi
 
mount -t ext3 /dev/sda2 /mnt/backup

rsync -aurvlP --exclude-from=mybackup_excludes.lst /home /mnt/backup
echo "done"
exit 0

```

Then I have another file in same location that is mybackup_excludes.lst
```
# mybackup_excludes.lst
# Note: Trailing SLASHES MATTER, copy form exactly!!!
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found
/home/*/.wine
/home/*/.macromedia

```
There are a lot of temporary files & folders in /home which you do not need to copy.

 Some files to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)


 [http://askubuntu.com/questions/320458/how-to-exclude-multiple-directories-with-rsync](http://askubuntu.com/questions/320458/how-to-exclude-multiple-directories-with-rsync)

---

### Post by TheFu on 2014-09-23
Oldfred - do you verify that /mnt/backup is actually mounted?
I didn't a few years ago and fill up / - it was bad.
Then I got the mount working and all the files under /mnt/backup -pre-mount were still there eating storage. It was bad.  So now I verify that mounted storage is actually mounted as expected in all backup scripts.  Filling up / is always bad, as you know.

And just to be clear - rdiff-backup is good for where we need versioned backups, not so much for large, unchanged, media files.  I still use rsync for those .... and for remote editing with vim, of course.  Hard to believe, but rsync + vim + ssh allow smart remote editing of files!

---

### Post by oldfred on 2014-09-23
@TheFu
I guess I do not verify that it mounted, but have not had issues. But I still do it manually and not via cron.
 I did have an issue before I added the mount command in my script and it did copy into / and as you say that could cause major issues. I also learned the hard way. :)  I have a larger / of 25GB and only use 11GB so had space and did notice a large jump in use in /.

---

### Post by ric_Poirier on 2014-09-23
> **TheFu said:**
> I don't know, but


        collection2="$HOME/"$coldir2"" 

is not valid.  You cannot nest quotes like that in bash.  

Also, the first line is missing #!/bin/bash - this is needed.

I would only use normal 7-bit ASCII characters in directory names until getting this to work, I'd avoid spaces or any accented characters.  Get it working, then put in the names I prefer after everything else is working.

So - I can recommend the ABSG - advanced bash scripting guide - as a good resource for reference.
I'm concerned about the --ignore-errors. Why?  rsync is an amazing tool - especially for mirroring things. I use it all the time.  For backups, where versioning is mandatory (and it is always), there are better tools like rdiff-backup.

Thank you for your answer **TheFu,** here's a follow up.

[LIST=1]
[*]Sorry for not including the Sha Bang in my previous post, but I had it at the beginning of my bash script. 
[*]I changed "Séries télé" to "Tv shows", and then to "Shows" and I get the same output. I think that may not be the cause... 
[*]For the *--ignore-errors* option, I added it because otherwise, my *--delete* option is not working, especially on the first *rsync* command. See this post here: [http://ubuntuforums.org/showthread.php?t=1745350](http://ubuntuforums.org/showthread.php?t=1745350). If I remove it, files just accumulate at the backup destination. 
[*]I got rid of the double quotes. Here is my code now: ```
#!/bin/bash # ;-)

        coldir1='Videos/Films/'
        coldir2='Videos/Shows/'
        coldir3='Music/'

        collection1="$HOME/$coldir1"
        collection2="$HOME/$coldir2"
        collection3="$HOME/$coldir3"

        disk="sauvegarde"
        pathdisk="/media/$USER/$disk/"
        pathlogs="$HOME/.logs/$disk"
        outputlog="$pathlogs/sortie.log"
        errorlog="$pathlogs/erreurs.log"

        rsync -arv --ignore-errors --delete --progress --stats --exclude=$coldir1 --exclude=$coldir2 --exclude=$coldir3 $HOME/ $pathdisk >> $outputlog 2> $errorlog

        rsync -arv --delete --progress --stats $collection1 $pathdisk$coldir1 >> $outputlog 2> $errorlog

        rsync -arv --delete --progress --stats $collection2 $pathdisk$coldir2 >> $outputlog 2> $errorlog

        rsync -arv --delete --progress --stats $collection3 $pathdisk$coldir3 >> $outputlog 2> $errorlog
``` 
[/LIST]


What is weird is that I seem to still get an incomplete incremental file list for the "Shows" directories (Entourage subdirectories only are printed, but not those of Walking Dead). However, I tried formatting the backup hard drive before running the script, and I see the files are syncing (The Walking Dead subdirectories).

But if I run the script a second time (without formatting, I get the following output:

```
sending incremental file list
Entourage/
Entourage/Entourage - Season 1/
Entourage/Entourage - Season 2/
Entourage/Entourage - Season 3/
Entourage/Entourage - Season 4/
Entourage/Entourage - Season 5/
Entourage/Entourage - Season 6/
Entourage/Entourage - Season 7/
Entourage/Entourage - Season 8/


```

and that's it. Where is the directory "Walking Dead" and its subdirectories? In fact, the ./ directory does not appear as well...

I really don't get it. Is this normal behaviour?

Finally, what exactly is the incremental file list? Maybe I just misunderstand what it is...

P.S. Thanks for the guide, it is very clear and very nice. I have started reading it.

To everyone: thanks for your suggestions of alternatives, but I would really like to make this script work, because I use this as an exercise to learn scripts. Also, I want to make this a **crontab** job.

---

