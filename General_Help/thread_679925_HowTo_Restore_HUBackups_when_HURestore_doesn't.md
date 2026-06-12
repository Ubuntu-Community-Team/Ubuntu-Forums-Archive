---
title: "HowTo: Restore HUBackups when HURestore doesn't"
date: 2008-01-27
forum: General Help
---

### Post by Bruce M. on 2008-01-27
**[COLOR="Red"]WARNING:[/COLOR]** HURestore may **NOT** work on your computer!

This HowTo will explain how to recover those backups safely.

HUBackup uses by default; **~/.hubackup-data/**

[LIST]
[*] ~ **[COLOR="Red"]=[/COLOR]** /home
[*] /.hubackup-data **[COLOR="Red"]=[/COLOR]** hidden folder ( the . hides the folder)
[/LIST]

**[COLOR="Red"]NOTE:[/COLOR]** *If you loose the **/home** folder, you loose the backups, **I suggest you move them now***.

Put your backup someplace else (another partition or HD). Generally a good practice for any backups.

So you know what I am talking about as we get further into this HowTo this is my setup:
[LIST]
[*] Root ( / ) is: /dev/sda5/
[*] Home ( /home/bruloo ) is /dev/sda7/ **Remember**, your /home is really /home/user_name
[/LIST]
And my backups are here:
[LIST]
[*] /media/sdb1/backups/24Jan2008/bruloo-master-archive.1.dar
[*] /media/sdb1/backups/24Jan2008/bruloo-master-catalog.1.dar
[/LIST]

On 25 Jan 2008 **I** deleted my new /home by mistake and had to re-install Ubuntu. Hence the need to have my backups restored in a real time situation.

I downloaded HUBackup & HURestore, because that is what I used only to find; HURestore did **[COLOR="Red"]NOT[/COLOR]** work!

I found [this]("http://sivang.blogspot.com/2008/01/restoring-file-using-hubackup.html") (quoted below) while searching for help.

> 
Monday, January 07, 2008
Restoring File Using HUBackup

After receiving quite some emails about folks bewildered by the crashing hurestore I think it's only fair to create a post about how to restore files from archives created using hubackup using the underlying archiver , DAR.

Usually after a typical run of hubackup you will have two resulting files:

.hubackup-data/paepp-master-archive.1.dar
.hubackup-data/paepp-master-catalog.1.dar

(Thanks goes to Peter Päppinghaus for sending me an email about this)

To restore , which actually usually means extract in DAR's language you need to do something like:

dar -x .hubackup-data/paepp-master-archive -R TARGET_DIR

If there is more then one slice DAR knows how to switch between them properly.

That should be enough for most of operations, for more detailed explanation of what dar can do in restoration (or backup for that matter) DAR's manual pages are quite good.

Posted by Sivan Greenberg at 9:31 PM


As stated above you will need the **DAR** archiver/unarchiver program.

If you do not have it, you can download it from
> >System >Administration >Synaptic Package Manager

**[COLOR="Red"]NOTE:[/COLOR]** DAR is used in Terminal
>  > Applications > Accessories > Terminal

Now if we use the commands the way Sivan Greenberg suggested you will have problems; using my example:
```
dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home/bruloo
```
**[COLOR="Red"]Problems:[/COLOR]**
[LIST=1]
[*] You will be informed that file permissions will ***NOT*** be restored, **but you need them in /home**.
[*] For every file you have in your */home* folder you will need to press [Return] (I had 38,000+ files).
[*] You will not see any progress, other than your HD light flashing.
[/LIST]

So from The DAR Help page (To keep things short, only the commands I used are shown):
```

usage: dar [ -c | -x | -d | -t | -l | -C | -+ ] [<path>/]<basename> [options...]

Commands are:
   -x  extracts files from the archive
   -l  lists the contents of the archive

Common options:
   -R <path>       filesystem root directory (current dir by default)
   -v              verbose output
   -wa             don't warn before overwriting and removing files

```

First lets list the files in the archive to make sure something is there (do NOT use the **.1.dar** filename extensions).

It is fairly fast so try it with the **-l** command: 

```
bruloo@bruloo:~$ dar -l /media/sdb1/backup/24Jan08/bruloo-master-archive
```
Many pages will scroll by ending with something like this:
```
[Saved]       [  69%]   -rw-r--r--   bruloo     bruloo  5452    Thu Jan 24 19:58:06 2008        .conkyscripts/conkymain
[Saved]       [  66%]   -rw-r--r--   bruloo     bruloo  4937    Wed Jan 23 19:31:30 2008        .conkyscripts/conkytest
[Saved]       [  62%]   -rw-r--r--   bruloo     bruloo  3152    Wed Jan 23 20:20:45 2008        .conkyscripts/conky_top_left
bruloo@bruloo:~$
```
Good the files are there, now to get them.

**[COLOR="Green"]Problem fixes:[/COLOR]**
[LIST=1]
[*] To get permissions restored, use: **sudo**,
[*] So as not to hit [Return] 38,000 times: **-wa**
[*] To see what is happening: **-v**
[/LIST]

The code that works:
```
sudo dar -x /media/sdb1/backup/24Jan08/bruloo-master-archive -R /home/bruloo -wa -v
```

You will need to replace:
[LIST=1]
[*] **/media/sdb1/** - if you don't have the backups on this second HD.
[*] **/backup/24Jan08/** <<-- change this to the folder where your "your_name-archive" file is.
[*] **/home/bruloo** to /home/your_name
[/LIST]

If you have any questions I'll be here.
Bruce Milmine

---

### Post by K.Mandla on 2008-01-30
Moved to General Help.

---

### Post by ReverendJ1 on 2008-02-05
When restoring like this, will it erase newly created files? i.e. I did a backup, but have since created a new folder/files. Will the restore remove these folders/files?

---

### Post by Bruce M. on 2008-02-15
> **ReverendJ1 said:**
> When restoring like this, will it erase newly created files? i.e. I did a backup, but have since created a new folder/files. Will the restore remove these folders/files?

Did you use HUBackup to create your backup?

I'm not sure if it will delete your new files, I see no reason for it to do that though.

Personally I'd create a new backup with your new folders.

Sorry for the delay, haven't been on the computer much in the past two weeks.
Bruce

---

### Post by Bruce M. on 2008-03-04
As an after thought, and discovered after this.  Check out QuickStart in my signature.

---

### Post by trooperchix on 2008-05-03
:confused: Ok, I am trying to work through your thread and...  I haven't gotten very far at all.  I have my dar file on my dvd drive.  

eddie@kilimanjaro:~$ sudo dar -l /media/cdrom0/eddie-master-archive
[sudo] password for eddie: 
/media/cdrom0/eddie-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
Continuing...
/media/cdrom0/eddie-master-archive.1.dar is required for further operation, please provide the file. [return = OK | Esc = cancel]
Continuing...

And I can hit Enter all day and it says the same message over and over.  Please advise..  I'm bummed, because it looks like there should be two dar files in order to restore these files.  I used HUbackup to burn to DVD and I did get a write error that didn't make any sense, but I skipped it and it finished writing (as far as I could tell).  Now that I have wiped my HD clean, I find I have only 1 dar file...  Please tell me I can still restore my old info, if not in the same order it was before...

Thanks guys,
Trooperchix

---

