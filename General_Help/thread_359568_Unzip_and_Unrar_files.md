---
title: "Unzip and Unrar files"
date: 2007-02-12
forum: General Help
---

### Post by dmsn on 2007-02-12
Hey all!
How can i unzip all my .zip files?
Also i want to know how to unrar all my .rar files?

Thanks for help.

---

### Post by nereid on 2007-02-12
Use unzip and unrar.

```

unzip foo.zip
unrar e bar.rar

```

Maybe you have to install unrar first.

---

### Post by dmsn on 2007-02-12
Well i already know that ;)
But i want to unzip and unrar many files. Like
unzip *.zip
unrar *.rar
But that doesn't work.

---

### Post by highneko on 2007-02-12
Here's a script I made completely myself. I actually updated it just today. Just install unrar first. :3
sudo apt-get install unrar # to install unrar
```
#!/bin/bash

# Archive files easier

line="~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"
a="Zip all files and folders in current directory"
b="Test all zip archives in current directory"
c="Unzip all archives in current directory"
d="Unrars all archives in current directory"
e="Zip each folder in cd into an archive"
f="Unzip archives directly into the current directory"
g="Uzip using tests to check if directory exists"

function warning {
	printf "$line\nCurrent Directory: $PWD\n$1\n$line\n"
	read -p "Do you want to continue [Y/n]? " continue
	case "$continue" in
		"Y" | "y" )
			echo "$line"
		;;
		"N" | "n" )
			echo "$line"
			exit 0
		;;
	esac
}
clear; printf "$line\
\n[A] $a\
\n[B] $b\
\n[C] $c\
\n[D] $d\
\n[E] $e\
\n[F] $f\
\n[G] $g\
\n$line\n"; read choice
case "$choice" in
	"A" | "a" )
		warning "$a"
		# Zip all files and folders in current directory
		zip -r ${PWD##*/}.zip *
	;;
	"B" | "b" )
		warning "$b"
		# Test all zip archives in current directory
		for x in *.zip; do zip -T "$x"; done
	;;
	"C" | "c" )
		warning "$c"
		# Unzip all archives in current folder
		for x in *.zip; do mkdir "${x%.zip}" && cd "${x%.zip}" && unzip "../$x" && cd ..; done
	;;
	"D" | "d" )
		warning "$d"
		# Unrars all archives in current folder
		for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar x "../$x" && cd ..; done
	;;
	"E" | "e" )
		warning "$e"
		# Zip each folder in cd into an archive
		for x in *; do if [ -d "$x" ]; then cd "$x" && zip -r "../${x}.zip" * && cd ..; fi; done
	;;
	"F" | "f" )
		warning "$f"
		# Unzip archives directly into the current directory
		for x in *.zip; do unzip "$x"; done
	;;
	"G" | "g" )
		warning "$g"
		# Uzip using tests to check if directory exists
		for i in *.zip; do if zipinfo "$i" | grep -q '/'; then unzip "$i"; else mkdir "${i%.zip}" && cd "${i%.zip}" && unzip "../$i" && cd ..; fi; done
	;;
esac

exit 0

```

---

### Post by dmsn on 2007-02-12
Nice script. But i cant install unrar :(

dmsn@laptop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
dmsn@laptop:~$ 

Strange isnt? but unrar-free works.

---

### Post by nereid on 2007-02-12
Do you have the multiverse repositories enabled?

---

### Post by Maestro23 on 2007-02-12
> **dmsn said:**
> Nice script. But i cant install unrar :(

dmsn@laptop:~$ sudo apt-get install unrar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate
dmsn@laptop:~$ 

Strange isnt? but unrar-free works.

Enable extras Repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Sjovan on 2007-08-10
nice script, but shouldn't it be?

```
for x in *.rar; do mkdir "${x%.rar}" && cd "${x%.rar}" && unrar e "../$x" && cd ..; done
```
or something like that...

if you do it with unrar x it would creat a folder into the new folder, and you don't want that.

---

### Post by stchman on 2007-08-10
> **dmsn said:**
> Hey all!
How can i unzip all my .zip files?
Also i want to know how to unrar all my .rar files?

Thanks for help.

Archive Manager can handle .zip file out of the box.  Just double click on .zip files and you will be able to decompress them.

As far as .rar files do the following:

```

sudo apt-get -y install unrar

```

This will allow Archive Manager to unpack .rar files.

You have to make sure that the multiverse repository is enabled.

---

### Post by z-vap on 2007-08-24
I found that if I did ```
unzip "file*.zip" *
``` worked.  I needed to surround the filename with quotes, for it to actually work.

---

### Post by capink on 2007-08-24
The default archiver for gnome ( file-roller ) allows you to graphically select multiple archives and extract them all by right clicking and choosing extract.

---

