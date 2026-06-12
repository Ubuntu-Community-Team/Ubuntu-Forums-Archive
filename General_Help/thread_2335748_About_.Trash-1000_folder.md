---
title: "About .Trash-1000 folder"
date: 2016-08-31
forum: General Help
---

### Post by satimis on 2016-08-31
Hi all,

Ubuntu 14.04

I have 2 HD installed on this PC

1) 1TB SSD for operating system
2) 1.8TB WD HD for storage, as backup

There is a .Trash-1000 (additional to .Trash-0) on the storage disc having 3 folders on it ;
-expunged
-files
-info

Whenever I delete a folder and/or files they will be saved on .Trash-1000/files/ .  But I couldn't delete them.  I have tried deleting them.  They will be recreated a .trashinfo file.

I'm prepared to delete .Trash-1000 by running;```

sudo rm -rf /path/to/folder/.Trash-1000

```

Can I delete it without influencing other folder and/or file and/or the PC?

What will be the function of .Trash-1000 /expunged /files and /info ?

Please help.  Thanks advance.

Regards
satimis

---

### Post by &amp;KyT$0P# on 2016-08-31
Yes you can use [FONT=Courier New]rm -fvR .Trash-1000[/FONT], I've done that before on systems with unconventional mountpoints and nothing went wrong.
.Trash-0 is equivalent but for root user (uid 0) instead of your user account (uid 1000).  I don't know what happened to create that but I've never seen it.

Something else I've done on that system but not really tested though (it's a special-purpose VM not a testbed), can .Trash-1000 be symlinked to [FONT=Courier New]~/.local/share/Trash[/FONT]? :-k

---

### Post by satimis on 2016-08-31
> **halogen2 said:**
> Yes you can use [FONT=Courier New]rm -fvR .Trash-1000[/FONT], I've done that before on systems with unconventional mountpoints and nothing went wrong.
.Trash-0 is equivalent but for root user (uid 0) instead of your user account (uid 1000).  I don't know what happened to create that but I've never seen it.

Hi,

Thanks for your advice.

I'll delete .Trash-1000 later.  After clarifying everything

> 
Something else I've done on that system but not really tested though (it's a special-purpose VM not a testbed), can .Trash-1000 be symlinked to [FONT=Courier New]~/.local/share/Trash[/FONT]? :-k

&#10219; ls -ald /media/satimis/data/.Trash-1000/```

drwx------ 5 satimis satimis 4096 Aug 26 00:24 /media/satimis/data/.Trash-1000/

```

No.

satimis

---

### Post by &amp;KyT$0P# on 2016-09-01
> **satimis said:**
> ls -ald /media/satimis/data/.Trash-1000/```

drwx------ 5 satimis satimis 4096 Aug 26 00:24 /media/satimis/data/.Trash-1000/

```

No.
:confused:
I meant create such a symlink after deleting that.

---

### Post by satimis on 2016-09-01
> **halogen2 said:**
> :confused:
I meant create such a symlink after deleting that.

If I understand your advice correctly.

1)
Delete .Trash-1000 including its folders, /expunged /files and /info 

```

sudo rm -fvR /media/satimis/data/.Trash-1000

```

leaving Trash-0 behind

2)
Then run;

```

sudo ln -s .local/share/Trash /media/satimis/data/.Trash-0

```

Please correct me if wrong

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2016-09-01
Close but not quite (and I'm only saying I've done that on a system where stability is pretty important - it's not necessarily advice).

Second command should be this
```
sudo ln -s ~/.local/share/Trash /media/satimis/data/.Trash-1000
```

---

### Post by satimis on 2016-09-03
> **halogen2 said:**
> Close but not quite (and I'm only saying I've done that on a system where stability is pretty important - it's not necessarily advice).

Second command should be this
```
sudo ln -s ~/.local/share/Trash /media/satimis/data/.Trash-1000
```

Performed following steps;

&#10219; sudo rm -fvR /media/satimis/data/.Trash-1000/
```

.....
removed '/media/satimis/data/.Trash-1000/files/ISO_n_Sofware_20100613_20160131/Espon_3490_Photo_20100902/Epson_UK/epson322276eu.exe'
removed directory '/media/satimis/data/.Trash-1000/files/ISO_n_Sofware_20100613_20160131/Espon_3490_Photo_20100902/Epson_UK'
removed directory '/media/satimis/data/.Trash-1000/files/ISO_n_Sofware_20100613_20160131/Espon_3490_Photo_20100902'
removed directory '/media/satimis/data/.Trash-1000/files/ISO_n_Sofware_20100613_20160131'
removed '/media/satimis/data/.Trash-1000/files/Web_Documents_n_ISP_20130114_20160630.trashinfo'
removed directory '/media/satimis/data/.Trash-1000/files'
removed directory '/media/satimis/data/.Trash-1000/expunged'
removed directory '/media/satimis/data/.Trash-1000/'

```

&#10219; sudo ln -s .local/share/Trash /media/satimis/data/.Trash-1000

&#10219; ls -ald /media/satimis/data/.Trash-1000```

lrwxrwxrwx 1 root root 18 Sep  3 22:41 /media/satimis/data/.Trash-1000 -> .local/share/Trash

```

Create a file "Trash-1000_testing.txt" on SSD drive (Operating System)
Copied the file to 1.8TB WD HD (for storage, as backup)

On deleting it popup an warning;```

Are you sure you want to permanently delete “Trash-1000_testing.txt”?
If you delete an item, it will be permanently lost
[Cancel][Delete]

```

-> Delete

The file deleted but I couldn't find it on .local/share/Trash

&#10219; ls .local/share/Trash/```

expunged  files  info

```

&#10219; ls .local/share/Trash/expunged/ | grep Trash-1000_testing.txt
no output

&#10219; ls .local/share/Trash/files/ | grep Trash-1000_testing.txt
no output

&#10219; ls .local/share/Trash/info/ | grep Trash-1000_testing.txt
no output

Regards
satimis

---

### Post by &amp;KyT$0P# on 2016-09-03
> **satimis said:**
> &#10219; sudo ln -s .local/share/Trash /media/satimis/data/.Trash-1000

&#10219; ls -ald /media/satimis/data/.Trash-1000```

lrwxrwxrwx 1 root root 18 Sep  3 22:41 /media/satimis/data/.Trash-1000 -> .local/share/Trash

```
That's a broken symlink, you missed the ~ I added ;)
```
sudo rm -fv /media/satimis/data/.Trash-1000
sudo ln -s **[COLOR="#FF0000"]~/[/COLOR]**.local/share/Trash /media/satimis/data/.Trash-1000
```

---

### Post by satimis on 2016-09-03
> **halogen2 said:**
> That's a broken symlink, you missed the ~ I added ;)
```
sudo rm -fv /media/satimis/data/.Trash-1000
sudo ln -s **[COLOR="#FF0000"]~/[/COLOR]**.local/share/Trash /media/satimis/data/.Trash-1000
```

Performed following steps;

sudo rm -fv /media/satimis/data/.Trash-1000
[sudo] password for satimis: 

&#10219; sudo ln -s ~/.local/share/Trash /media/satimis/data/.Trash-1000

&#10219; ls -ald /media/satimis/data/.Trash-1000```

lrwxrwxrwx 1 root root 32 Sep  4 06:28 /media/satimis/data/.Trash-1000 -> /home/satimis/.local/share/Trash

```


Copied "Trash-1000_testing_01.txt" on SSD drive (Operating System)
To 1.8TB WD HD (for storage, as backup)

Right-click "Trash-1000_testing_01.txt" and Delete

It popup an warning;```

Are you sure you want to permanently delete &#8220;Trash-1000_testing.txt&#8221;?
If you delete an item, it will be permanently lost
[Cancel][Delete]

```

-> Delete

But I still couldn't find the deleted file on SSD Trash.  Whether I need to change owner (root root) to (satimis satimis)?

satimis

---

### Post by &amp;KyT$0P# on 2016-09-03
You've done it right this time.

I've done some investigating and it looks like only KDE file managers (Dolphin & Konqueror) can handle the symlink. :-k
Sorry about that.

---

