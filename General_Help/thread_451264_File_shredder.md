---
title: "File shredder"
date: 2007-05-22
forum: General Help
---

### Post by FRuMMaGe on 2007-05-22
As most people know, "deleting" using the wastebasket or recycle bin doesn't actually erase files.  It merely unlinks them from the file system.

Does anyone here know of a linux file shredder that can be used to delete files and also delete files already unlinked from the file system?

Prefferably with several passes.

---

### Post by FRuMMaGe on 2007-05-23
bump

---

### Post by az on 2007-05-23
shred
SHRED(1)			 User Commands			      SHRED(1)

NAME
       shred - overwrite a file to hide its contents, and optionally delete it

SYNOPSIS
       shred [OPTIONS] FILE [...]

DESCRIPTION
       Overwrite the specified FILE(s) repeatedly, in order to make it	harder
       for even very expensive hardware probing to recover the data.

       Mandatory  arguments  to  long  options are mandatory for short options
       too.

       -f, --force
	      change permissions to allow writing if necessary

       -n, --iterations=N
	      Overwrite N times instead of the default (25)

       -s, --size=N
	      shred this many bytes (suffixes like K, M, G accepted)

       -u, --remove
	      truncate and remove file after overwriting

       -v, --verbose
	      show progress

       -x, --exact
	      do not round file sizes up to the next full block;

	      this is the default for non-regular files

       -z, --zero
	      add a final overwrite with zeros to hide shredding

       --help display this help and exit

       --version
	      output version information and exit

---

### Post by Rytron on 2008-03-11
Hi,
Is there a GUI shredder available for Ubuntu?
For examples it would be great to install program that if you right clicked on the trash icon it would give you the option to delete all in the recycle with an option to overwrite several times.

Also it would be brilliant if you could right click on the HDD / partitions and have the option to shred empty space.

Any suggestions?

---

### Post by HermanAB on 2008-03-11
GUI tools don't exist because the shredder doesn't really work.

The only way to securely delete a file, is to delete the whole disk drive:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

The other way is to encrypt partitions and forget the key when you want to delete something.

Cheers,

Herman

---

### Post by oneadvent on 2008-03-11
You could do a 7 pass scan on it, but for the life of me I cannot think of the name of that program, I will post it if no one else has when I get home.

However, it is not GUI.

You could make one though!

---

### Post by justifiedandancient on 2008-03-27
Well it may be technically feasible to write a secure file eraser for some FS types but it would be horrendously complex for some of them. There are those that claim to work on 'Doze for NTFS but it is likely to be as effective as the Linux shred command. The CMRR article listed above tells you all really (don't) want to know. If you're just trying to cover your tracks use shred (minus GUI) otherwise the disk has got to go.

---

### Post by pablo180 on 2008-06-16
> **Rytron said:**
> Hi,
Is there a GUI shredder available for Ubuntu?
For examples it would be great to install program that if you right clicked on the trash icon it would give you the option to delete all in the recycle with an option to overwrite several times.

Also it would be brilliant if you could right click on the HDD / partitions and have the option to shred empty space.

Any suggestions?

I just created a launcher on the desktop with the command **shred** and drop the files that I want shredding onto it. Seems to work OK and if you add -u it will remove the file as well. It's not perfect but better than opening a terminal everytime you want to shred something. 

Doesn't shred folders though, only files.

---

### Post by benny bronx on 2008-06-16
You can add the shred command to the context menu with:

[http://www.gnome-look.org/content/show.php/shred_file?content=66603]("http://www.gnome-look.org/content/show.php/shred_file?content=66603")

You can wipe free space with secure-delete from the repo or, as I have, bcwipe for linux. Neither come with a gui.

---

### Post by SSVegito888 on 2008-07-18
I am new to linux.  I really wish there was a GUI for any file shredder program and I suck at programming so I probably won't be able to make one.

I feel kind of weird asking this, but does anyone feel like doing a little project to make a file shredding GUI that supports folders and option to select how many passes it performs.
I and the rest of the world would greatly appreciate it.



Thanks,

SSVegito888

---

