---
title: "change 'rm' command to send files to the Trash instead of instant deletion"
date: 2008-05-03
forum: General Help
---

### Post by garfieldpbj on 2008-05-03
Hi..

Can anybody tell my how I should do to make a script which works as rm command - but sends files to the Trash instead of instant deletion - I want it to work with the command "del file" (del=delete)..

I've searched the net, but only got confused..

Can anybody please help me?

/Peter

---

### Post by rogblake on 2008-05-03
> **garfieldpbj said:**
> Hi..

Can anybody tell my how I should do to make a script which works as rm command - but sends files to the Trash instead of instant deletion - I want it to work with the command "del file" (del=delete)..

I've searched the net, but only got confused..

Can anybody please help me?
/Peter

This is a quick and dirty script that should do the trick. Save it as /usr/local/bin/del and make it executable (chmod +x /usr/local/bin/del):

----------------- Begin del --------------------------

#!/bin/sh

# Check for args
if [ "$1" = "" ]; then
  echo 'usage: del file'
  exit 1
fi

# Set environment variables
TARGET=~/.TRASH
DAY=`/bin/date '+%d'`
MONTH=`/bin/date '+%B' | /usr/bin/cut -b 1-3 | /usr/bin/tr [:lower:] [:upper:]`
YEAR=`/bin/date '+%Y'`
DATE=$YEAR-$MONTH-$DAY

# Check for target, create if needed
if [ ! -d $TARGET/$DATE ]
then
mkdir -p $TARGET/$DATE
fi

mv $1 $2 $3 $4 $5 $TARGET/$DATE

----------------- End del --------------------------

This places the deleted file(s) in ~/.TRASH in a subdirectory corresponding to the current date. (I just tried it on my system real quick and it seems to work. NO WARRANTY EXPRESSED OR IMPLIED IF THIS SCRIPT SCREWS SOMETHING UP ON YOUR COMPUTER!! I also see via preview that my indenting is taken out here, but that should not be a problem.)

---

### Post by garfieldpbj on 2008-05-03
> **rogblake said:**
> This is a quick and dirty script that should do the trick. Save it as /usr/local/bin/del and make it executable (chmod +x /usr/local/bin/del):

----------------- Begin del --------------------------

#!/bin/sh

# Check for args
if [ "$1" = "" ]; then
  echo 'usage: del file'
  exit 1
fi

# Set environment variables
TARGET=~/.TRASH
DAY=`/bin/date '+%d'`
MONTH=`/bin/date '+%B' | /usr/bin/cut -b 1-3 | /usr/bin/tr [:lower:] [:upper:]`
YEAR=`/bin/date '+%Y'`
DATE=$YEAR-$MONTH-$DAY

# Check for target, create if needed
if [ ! -d $TARGET/$DATE ]
then
mkdir -p $TARGET/$DATE
fi

mv $1 $2 $3 $4 $5 $TARGET/$DATE

----------------- End del --------------------------

This places the deleted file(s) in ~/.TRASH in a subdirectory corresponding to the current date. (I just tried it on my system real quick and it seems to work. NO WARRANTY EXPRESSED OR IMPLIED IF THIS SCRIPT SCREWS SOMETHING UP ON YOUR COMPUTER!! I also see via preview that my indenting is taken out here, but that should not be a problem.)

Thank you for the answer...

Do anybody have some comments to this? Would it work, would it be safe - and is there a better way to do it? 

/Peter

---

### Post by chrisccoulson on 2008-05-03
I haven't looked specifically at the script mentioned, but if you implemented it, you could actually alias rm to del to prevent you accidentally deleting files with rm (see [http://www.hypexr.org/bash_tutorial.php#alias]("http://www.hypexr.org/bash_tutorial.php#alias")

---

### Post by garfieldpbj on 2008-05-03
> **chrisccoulson said:**
> I haven't looked specifically at the script mentioned, but if you implemented it, you could actually alias rm to del to prevent you accidentally deleting files with rm (see [http://www.hypexr.org/bash_tutorial.php#alias]("http://www.hypexr.org/bash_tutorial.php#alias")

Wouldn't that create problems for other programs that use the rm? (haven't read the link yet... but will do it soon..)

/peter

---

### Post by ibuclaw on 2008-05-03
Here is a cleaner script that I propose:
```

#!/bin/bash
remove()
{
    while [ ! -z "$1" ]
    do
        mv $1 $Files
        echo "[Trash Info]" > "$Info/$1.trashinfo"
        echo "Path=$Path" >> "$Info/$1.trashinfo"
        echo "DeletionDate=$DelDate" >> "$Info/$1.trashinfo"
        echo "Moved $1 to Trash..."
        shift
    done
}

while [ $# -gt "0" ]
do
    if [ `whoami` == "root" ]
    then
        export Files="/`whoami`/.local/share/Trash/files"
        export Info="/`whoami`/.local/share/Trash/info"
    else
        export Files="/home/`whoami`/.local/share/Trash/files"
        export Info="/home/`whoami`/.local/share/Trash/info"
    fi
    export DelDate=`date +%FT%T`
    export Path=`pwd`/"$1"
    remove "$1"
    shift
done

```

Save it as something like **mrm** or **trash** and save it in you **/usr/local/bin** directory.
You need to be root to do this, so press "**Alt+F2**" and type:
```
gksu gedit /usr/local/bin/**trash**
```
The last word in the line can be called whatever you want.

Anyways...Paste the text, and save.

open a terminal and type in:
```
export PATH=$PATH
```
and you are all set!
ie: Example Use.
```
trash foo.txt
```

The script should handle multiple files in the manner of "foo foo2 foo3".
Not sure if wildcards (ie: *.txt) will work (You'll have to try that out yourself).

The only thing that is missing is an interactive mode (ie: Are You Sure[Y/N]) But I can put that in in a while, after I get some sleep.

And I say this is cleaner, because it puts the files in the *RIGHT* folder and it creates a "trashinfo" file for the item too.

NOTE: It follows the standards of Gnome as Ubuntu Hardy works. (Of which is now the ~/.local/share/Trash directory, not the ~/.Trash as it once was before).
This script won't work (or at least I don't think it will work) on KDE or other Window Managers.

Regards
Iain

---

### Post by garfieldpbj on 2008-05-03
> **tinivole said:**
> Here is a cleaner script that I propose:
```

#!/bin/bash
remove()
{
    while [ ! -z "$1" ]
    do
        mv $1 $Files
        echo "[Trash Info]" > "$Info/$1.trashinfo"
        echo "Path=$Path" >> "$Info/$1.trashinfo"
        echo "DeletionDate=$DelDate" >> "$Info/$1.trashinfo"
        echo "Moved $1 to Trash..."
        shift
    done
}

while [ $# -gt "0" ]
do
    if [ `whoami` == "root" ]
    then
        export Files="/`whoami`/.local/share/Trash/files"
        export Info="/`whoami`/.local/share/Trash/info"
    else
        export Files="/home/`whoami`/.local/share/Trash/files"
        export Info="/home/`whoami`/.local/share/Trash/info"
    fi
    export DelDate=`date +%FT%T`
    export Path=`pwd`/"$1"
    remove "$1"
    shift
done

```

Save it as something like **mrm** or **trash** and save it in you **/usr/local/bin** directory.
You need to be root to do this, so press "**Alt+F2**" and type:
```
gksu gedit /usr/local/bin/**trash**
```
The last word in the line can be called whatever you want.

Anyways...Paste the text, and save.

open a terminal and type in:
```
export PATH=$PATH
```
and you are all set!
ie: Example Use.
```
trash foo.txt
```

The script should handle multiple files in order of "foo foo2 foo3", not sure if "*.txt" wildcards will would (You'll have to try that out yourself).

The only thing that is missing is an interactive mode (ie: Are You Sure[Y/N]) But I can put that in in a while, after I get some sleep.

And I say this is cleaner, because it puts the files in the *RIGHT* folder and it creates a "trashinfo" file for the item too.

NOTE: It follows the standards of Gnome as Ubuntu Hardy works. (Of which is now the ~/.local/share/Trash directory, not the ~/.Trash as it once was before).
This script won't work (or at least I don't think it will work) on KDE or other Window Managers.

Regards
Iain

Thank you - I'll have a look at it..

---

### Post by ibuclaw on 2008-05-03
> **garfieldpbj said:**
> Thank you - I'll have a look at it..
Your Welcome.

If you find it useful.
I could add some extra functionality for it.

As I said, I think an interactive mode would be brilliant for it (a choice for interactive mode, not default).

Also, I could add a "**Restore**" feature, where if you accidentally Move an item to Trash, you can with a simple command restore it back to it's original position (Something that I think Gnome still can't do ;))

PS: It works perfect for me :D
[PHP]$ trash md5tar text.save test.save testdisk.log
Moved md5tar to Trash...
Moved text.save to Trash...
Moved test.save to Trash...
Moved testdisk.log to Trash...
[/PHP]
Looked in my Trash folder, and they are all there. Looked in the ~/.local/share/Trash/info directory and all files are correctly labelled.

Also, WILDCARDS **DO** WORK.
Proof:
[PHP]
$ touch one.foo
$ touch two.foo
$ touch three.foo

$ trash *.foo
Moved one.foo to Trash...
Moved three.foo to Trash...
Moved two.foo to Trash...
[/PHP]

Regards
Iain

---

### Post by Th3Professor on 2008-05-03
That's pretty slick... I wonder why such a command isn't already a default part of *nix systems.

---

### Post by ibuclaw on 2008-05-03
> **Th3Professor said:**
> That's pretty slick... I wonder why such a command isn't already a default part of *nix systems.

It's **Gnome Specific**. Though, that's not to say that it can become it's own trash collector.

Updated the code a bit:
Support for Interactive Trashing Added:
```

#!/bin/bash
remove()
{
    while [ ! -z "$1" ]
    do
        mv $1 $Files
        echo "[Trash Info]" > "$Info/$1.trashinfo"
        echo "Path=$Path" >> "$Info/$1.trashinfo"
        echo "DeletionDate=$DelDate" >> "$Info/$1.trashinfo"
        echo "Moved $1 to Trash..."
        shift
    done
}

if [ "$1" == "-i" ]
then
    export interact="1"
    shift
else 
    export interact="0"
fi

while [ $# -gt "0" ]
do
    if [ `whoami` == "root" ]
    then
        export Files="/`whoami`/.local/share/Trash/files"
        export Info="/`whoami`/.local/share/Trash/info"
    else 
        export Files="/home/`whoami`/.local/share/Trash/files"
        export Info="/home/`whoami`/.local/share/Trash/info"
    fi
    export DelDate=`date +%FT%T`
    export Path=`pwd`/"$1"
    
    if [ $interact = "0" ]
    then 
        remove "$1"
    else
        echo -n "Trash Item $1?[Y/N]: "
        read -n 1 input
        echo
        case $input in
	    y|Y)
		remove $1
		;;
        esac
    fi
    shift
done

```
And the code in action (Interactive Mode is invoked with **trash -i**)
[PHP]
$ trash -i *.foo
Trash Item one.foo?[Y/N]: n
Trash Item three.foo?[Y/N]: y
Moved three.foo to Trash...
Trash Item two.foo?[Y/N]: y
Moved two.foo to Trash...
[/PHP]
Any issues, just PM me.

I'm off to sleep.

Regards
Iain

---

### Post by Th3Professor on 2008-05-04
I'll take a guess that would work across multiple *nix systems, except the export directories might need changing (linux vs bsd unix vs sysv unix).

---

### Post by ibuclaw on 2008-05-04
> **Th3Professor said:**
> I'll take a guess that would work across multiple *nix systems, except the export directories might need changing (linux vs bsd unix vs sysv unix).

It would work regardless.
It's just the GUI interface that will vary.

With Gnome, you look at you Trash folder, and the item is there.
With KDE, the item would have been moved to the **~/.local/share/Trash/files** directory, but when you look in the KDE trash folder via konqueror or dolphin, it is nowhere to be seen.

As I said, if I wanted to, I could make it it's own trash collector with commands including:
[LIST]
[*]**trash** - mv files to trash.
[*]**trash -r** - mv files from trash back to original location.
Could make a separate script called **restore** for it.
[*]**trash -l** - list files in the trash folder.
[*]**trash -e** - rm files from trash folder (permanently delete).
Also, could make a separate script called **empty** for that one too.
[/LIST]

Regards
Iain

---

### Post by Th3Professor on 2008-05-04
Trash doesn't exist on all *nix systems.

Some Unix set-ups don't have Trash.

Any Linux (or Unix) set-up could likely not have it if one doesn't use the GNOME or KDE desktop environments and they just use a simple window manager, or better yet they don't use X at all.

Though, one could easily fix that by simply creating it, in which case it doesn't have to be in ~/.local/share/Trash or any locations default to GNOME or KDE.

Regardless... kudos to that script, it's good, pretty slick.

---

### Post by ibuclaw on 2008-05-04
> **Th3Professor said:**
> Trash doesn't exist on all *nix systems.

Some Unix set-ups don't have Trash.

Any Linux (or Unix) set-up could likely not have it if one doesn't use the GNOME or KDE desktop environments and they just use a simple window manager, or better yet they don't use X at all.

Though, one could easily fix that by simply creating it, in which case it doesn't have to be in ~/.local/share/Trash or any locations default to GNOME or KDE.

Regardless... kudos to that script, it's good, pretty slick.

Here's what I mean (sorry for the mix up, but you'll see what I mean).

I've completely done it up.
The App can now be setup to be it's own isolated command-line Trash Utility, but as it stands in it's default settings, it's more of an integrated Command-Line/Gnome App.

I think I've put enough information in the readme and trash.man files for you to understand what I mean and how it works.

I've given it as much functionality as what I'd expect any trash app to do. That is moving to trash, restoring from trash (also restores items moved to trash in nautilus), listing all items in trash and emptying (permanently deleting) trash.

If you can think of something it will be better with, just let me know.

I've put it in the tarball attached.

Regards
Iain

---

### Post by drcooljoe on 2011-05-30
I just came across this thread and made a couple tweaks to the scripts from ibulaw to work for files not in the current directory:

```

#!/bin/bash
remove()
{
    while [ ! -z "$1" ] && [ -e $1 ] 
    do
        fb=`basename $1`
        mv $1 $Files
        echo "[Trash Info]" > "$Info/$fb.trashinfo"
        echo "Path=$Path" >> "$Info/$fb.trashinfo"
        echo "DeletionDate=$DelDate" >> "$Info/$fb.trashinfo"
        echo "Moved $1 to Trash..."
        shift
    done
}

if [ "$1" == "-i" ]
then
    export interact="1"
    shift
else 
    export interact="0"
fi

while [ $# -gt "0" ]
do
    if [ `whoami` == "root" ]
    then
        export Files="/`whoami`/.local/share/Trash/files"
        export Info="/`whoami`/.local/share/Trash/info"
    else 
        export Files="/home/`whoami`/.local/share/Trash/files"
        export Info="/home/`whoami`/.local/share/Trash/info"
    fi
    export DelDate=`date +%FT%T`
    export Path=`pwd`/"$1"
    
    if [ $interact = "0" ]
    then 
        remove "$1"
    else
        echo -n "Trash Item $1?[Y/N]: "
        read -n 1 input
        echo
        case $input in
            y|Y)
                remove $1
                ;;
        esac
    fi
    shift
done


```

---

