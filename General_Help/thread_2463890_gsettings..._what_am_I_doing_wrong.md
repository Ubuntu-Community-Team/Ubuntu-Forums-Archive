---
title: "gsettings... what am I doing wrong?"
date: 2021-06-20
forum: General Help
---

### Post by GhX6GZMB on 2021-06-20
I'm trying to set up an exclude list for Deja-dup, but Gnome geekyness got me (why is it so hard just to make an ASCII exclude/include file?).
Apparently Deja-dup/Duplicity maintain an internal backup file list that can only be accessed with special Gnome commands. I only know this from proprietary software, but OK.

The recipe for doing this I found here:[https://answers.launchpad.net/deja-dup/+question/280954](https://answers.launchpad.net/deja-dup/+question/280954)

However, I get these outputs from the commands that I'm not able to decipher:

```

macro@macro-pc:~$ sudo gsettings get org.gnome.DejaDup exclude-list
['$TRASH', '$DOWNLOAD']
macro@macro-pc:~$ sudo gsettings set org.gnome.DejaDup exclude-list [$HOME/.*]
expected value:
  [/home/macro/.*]
   ^              
macro@macro-pc:~$ sudo gsettings set org.gnome.DejaDup exclude-list [/home/macro/.*]
expected value:
  [/home/macro/.*]
   ^              
macro@macro-pc:~$ sudo gsettings set org.gnome.DejaDup exclude-list /home/macro/.*
Usage:
  gsettings [--schemadir SCHEMADIR] set SCHEMA[:PATH] KEY VALUE


Set the value of KEY to VALUE


Arguments:
  SCHEMADIR A directory to search for additional schemas
  SCHEMA    The name of the schema
  PATH      The path, for relocatable schemas
  KEY       The key within the schema
  VALUE     The value to set


macro@macro-pc:~$ sudo gsettings set org.gnome.DejaDup exclude-list '/home/macro/.*'
expected value:
  /home/macro/.*
  ^             
macro@macro-pc:~$ sudo gsettings set org.gnome.DejaDup exclude-list "/home/macro/.*"
expected value:
  /home/macro/.*
  ^             
macro@macro-pc:~$ 

```

As you can see, I'm trying to keep the hidden files out of my $HOME backups (they are covered by my system backup already, and I want no interference there).

The first command shows the current exclude settings (I think), but the following make trouble.

Any ideas?

Thanks.

---

### Post by CatKiller on 2021-06-20
Don't use sudo with gsettings. It's just going to break things.

---

### Post by GhX6GZMB on 2021-06-20
OK, just tried it without sudo. Same non-result.

---

### Post by GhX6GZMB on 2021-06-20
OK, it seems I'm out of luck, as this thread describes:
[https://askubuntu.com/questions/690990/can-i-ignore-files-by-pattern-in-deja-dup-backup](https://askubuntu.com/questions/690990/can-i-ignore-files-by-pattern-in-deja-dup-backup)

Comment from the link:
[I]"[COLOR=#242729][FONT=-apple-system]the ms-windows registry was such a good idea that some linux developers felt the need to borrow the idea &#8211; "
[/FONT][/COLOR][/I][COLOR=#242729][FONT=-apple-system]
[SIZE=2][FONT=arial]I'll now manually copy my $HOME files to my external USB-HDD instead. Sensible backup programs for user files seems to be non-existent. Has everyone moved to cloud storage today?

Cheers.[/FONT][/SIZE]

[/FONT][/COLOR]

---

### Post by &amp;KyT$0P# on 2021-06-20
Do you have dconf-editor installed?  Are those settings visible in dconf-editor; if so can you successfully change them using dconf-editor?

---

### Post by CatKiller on 2021-06-20
> **ml9104 said:**
> OK, just tried it without sudo. Same non-result.
Since it didn't work you *probably* didn't break anything, but it's worth checking that you haven't made some of the files in your Home directory owned by root. The gconf/dconf/gsettings stuff is just nested text files as I recall (I don't use Gnome any more). 

If you want more control over your backups, you'd probably find it useful to look at duplicity; Déjà Dup is just an automatic front end for duplicity. Certain behaviors are built in, like never backing up ~/.steam even if you're otherwise backing up hidden directories in your Home directory. For direct control, duplicity would be a better bet, I'd say.

---

### Post by philhughes on 2021-06-21
You are missing the single quotation marks around each value in the list, as shown in the get request you made initially, and require quotation marks around the whole list . eg

```
gsettings set org.gnome.DejaDup exclude-list "['home/macro/*', '/home/somewhere_else']"
```

---

### Post by GhX6GZMB on 2021-06-21
Ah!
That is the one permutation I overlooked. I'll experiment further.

Thanks.

---

### Post by GhX6GZMB on 2021-06-24
OK, update on this:

Issuing:
```
macro@macro-pc:~$ gsettings set org.gnome.DejaDup exclude-list "['$HOME/.*']"
```
Results in:
```
macro@macro-pc:~$ gsettings get org.gnome.DejaDup exclude-list
['/home/macro/.*']

```
Which is fine. In the DejaDup (GUI) exclude list, ~/.* appears.
All seems fine... until you do the backup
DejaDup happily includes all files/folders in the exclude list when backing up.

Useless. This is the last time I've installed/deinstalled this "backup software".

Thanks for Your help.

---

