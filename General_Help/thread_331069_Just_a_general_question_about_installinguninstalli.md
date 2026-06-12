---
title: "Just a general question about installing/uninstalling."
date: 2007-01-04
forum: General Help
---

### Post by Roasted on 2007-01-04
I haven't really dealt with many programs on linux that weren't obtainable by adding the repository and apt-get'ting then. I downloaded google earth which came in a .bin file. I set it to execute and installed it.

Just out of sheer curiosity, how would I uninstall it? Synaptic showed nothing for google earth when I searched for it, which I kind of expected. Because Synaptic only shows things I've installed via repositories, right?

So then I went to add/remove, but google earth wasn't listed there. Google Earth is however listed under Applications>Internet>GoogleEarth. Soooo, hmm. If I wanted to uninstall it, how would I do that? Apt-get remove --purge googleearth?

---

### Post by aysiu on 2007-01-04
Someone can correct me if I'm wrong, but my understanding is that everything is a file. Presumably you could do something like ```
sudo updatedb
locate earth
``` or ```
locate google
``` to find all the folders it installed to and delete those files...?

---

### Post by Quillz on 2007-01-04
Try ```
sudo apt-get --purge remove google earth
```

---

### Post by bapoumba on 2007-01-04
Hi,
if you installed a .bin, there should be somewhere in one of your specific application files, an uninstall script (not using google earth, so you'll have to browse your files).

---

### Post by Roasted on 2007-01-04
But couldn't I use --purge remove instead of taking the time to locate the file? I did a locate google earth and a lot showed up.

I'm just trying to get a feel for what the general way to uninstall something is. It always seems like there's 90 ways to do something with Linux and everybody has their own method. What's the most typical to simply want to uninstall a program, bam, just like that?

---

### Post by Roasted on 2007-01-06
All right this is very confusing to me. I figured I'd uninstall it via apt-get remove --purge just to see what would happen since I didn't get anymore responses.

Turns out it cannot find the package.

google, google-earth, googleearth, google earth, nothing works. What the hell? How can I get rid of this now?

---

### Post by 23meg on 2007-01-06
> But couldn't I use --purge remove instead of taking the time to locate the file?No, since it's not installed via apt.

I did a forum search for "uninstall google earth" and it seems [this]("http://www.ubuntuforums.org/showpost.php?p=1657750&postcount=6") is the way to uninstall it.

---

### Post by quartzy on 2007-01-06
> **23meg said:**
> No, since it's not installed via apt.

I did a forum search for "uninstall google earth" and it seems [this]("http://www.ubuntuforums.org/showpost.php?p=1657750&postcount=6") is the way to uninstall it.

On a side note to that link, ~ stands for you home folder so that assumes google-earth is installed to /home/user/google-earth.

---

### Post by Roasted on 2007-01-06
Odd.... ](*,) :-?

---

### Post by koenn on 2007-01-06
> **Roasted said:**
> It always seems like there's 90 ways to do something with Linux and everybody has their own method. 
Some people like it that way. 90 ways to do something, so you can choose the one that bests suits you, or best suits the task you're trying to accomplish. 

Anyway, in short :
if you installed something with synaptic (or apt,, or any package manager), that package manager knows where and how you installed it, and you can uninstall it through the package manager as well. So in this case, that's why apt-get --purge remove won't work. 

if you installed something any other way, it probably came with installation instructions, and hopefully also with uninstall instructions. If so, follow the uninstall instructions. If there aren't any; aysiu's suggesting of "find and delete" would be OK - or you'd go looking for specific instructions on the web. 

kinda makes sense, doesn't it ?

---

### Post by Roasted on 2007-01-06
The find and delete method, if I'd be using "locate google" to find everything, would take hours. Looooooooads of files show up. That's why it didn't... ahem... make sense to me.

---

### Post by koenn on 2007-01-07
> **Roasted said:**
> The find and delete method, if I'd be using "locate google" to find everything, would take hours. Looooooooads of files show up. That's why it didn't... ahem... make sense to me.
That's why it's only 3th choice, after package managers and uninstall instructions.
Still, you're kinda underestimating the power of the commandline.

a command like
```
find / -iname  'google*'
```
finds all files or directories that have 'google' in their name ;
```
find / -type d -iname  'google*'
```
finds directories (folders) with 'google' in the name, 
and if you want to find and delete them, you could do something like
```
find / -type d -iname  'google*  -exec rm -rf {} \;
```

Wouldn't take more than a couple of seconds (maybe minutes if you have really large hard disks).

---

### Post by Roasted on 2007-01-07
Man. How do you guys get so aquainted with these commands and know how to type them to people like me? I was at borders the other day and I found this small book with linux commands. It was only 15 bucks and I considered on picking it up... unless someone has a great, straight forward command sheet from a web site they can link me??

---

### Post by Ramses de Norre on 2007-01-07
No better way to learn commands as using the terminal and reading man pages.
Really, you wont need a book except if you want to start learning sed or awk or something.

---

### Post by koenn on 2007-01-07
> No better way to learn commands as using the terminal and reading man pages.
yep, that's always a good start. Plus reading other people's howto's and see what kind of commands and options they use; (the "find and delete" command was already mentioned in an other thread on this forum :)  )

It's hard in the beginning, but you'll learn in time. If i'm looking at a job that's going to take hours in a GUI, i rather spend those hours figuring out some commands to do it in CLI (command line) ... that way, you build up a vocabulary of useful commands just by using them

---

### Post by aysiu on 2007-01-07
I learned commands by copying and pasting them from this page:
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by koenn on 2007-01-07
and you occasionally mistake rm for mv , right ?  :)

---

### Post by aysiu on 2007-01-07
> **koenn said:**
> and you occasionally mistake rm for mv , right ?  :)
My mind works in weird ways. I think phonetically when I type. The way I remember the *mv* and *rm* commands is by expanding what they stand for--*move* and *remove*, respectively. Both have the word *move* in them, so I don't think of the two as being that distinct when I type them.

You may see that sometimes in my posts, too, before I proofread them.

---

### Post by Roasted on 2007-01-07
I know how to use the man feature, it's just... all of these random characters you can include in commands to do different things, I have no idea what's what, so I can't even THINK to look up "Man this" or "Man that" I just have no idea what to think unless I have a command in front of me and I can learn from it. That's why I thought about a book, where I can see, ohhhh, this command does this. Interesting! Blah.

---

### Post by koenn on 2007-01-07
could work too, it 'll help you think in terms of "I know there's a command for this ..." (but then you still need to find it :)

---

### Post by Ramses de Norre on 2007-01-07
No single character is random;) And it are mostly the find and sed stuff which look really complex and cluttered sometimes.
You can get the book, but I personally don't think it'd be very useful. But in the end that's up to you.

---

### Post by olejorgen on 2007-01-07
use apropos to find a command

eg. "apropos find"

---

### Post by Roasted on 2007-01-07
> **olejorgen said:**
> use apropos to find a command

eg. "apropos find"

I like that. Thank you. Got any other goodies to share?

---

### Post by olejorgen on 2007-01-08
Well, I'm not that experienced yet, so not really :) but man, apropos, google and occasionally info are your friends. 

PS: You can search with / in man pages

---

### Post by glabouni on 2007-01-14
> **Roasted said:**
> Man. How do you guys get so aquainted with these commands and know how to type them to people like me? I was at borders the other day and I found this small book with linux commands. It was only 15 bucks and I considered on picking it up... unless someone has a great, straight forward command sheet from a web site they can link me??

actually there is plenty of such command sheets, they're usually called "reference cards", here are some for to browse. If you search around the web I'm sure you'll find more. it is also a good call to look for "cheatsheets".

[Linux Command Line Reference card]("http://www.pixelbeat.org/cmdline.html")
[An A-Z Index of the Linux BASH command line]("http://www.ss64.com/bash/")
[Linux Command Reference Index ( GNU / linux kernel 2.4.18-3, 2.4.18-14 and 2.4.20-6 )]("http://www.perpetualpc.net/srtd_commands_rev.html")
[Quick Reference Cards]("http://www.digilife.be/quickreferences/quickrefs.htm")
[Debian GNU/Linux Reference Card]("http://people.debian.org/~debacle/refcard/")
[http://mygamecompany.com/Linux/Commandline/linuxcommandline.htm]("http://mygamecompany.com/Linux/Commandline/linuxcommandline.htm")

btw, if you wanna learn about sheel and cli (command line interface), you should have a look at [LinuxCommand.org]("http://linuxcommand.org/").

---

### Post by glabouni on 2007-01-14
As I was curious about how to uninstall google-earth, I gave it a try.

> wget -c [http://dl.google.com/earth/GE4/GoogleEarthLinux.bin](http://dl.google.com/earth/GE4/GoogleEarthLinux.bin)
sudo sh GoogleEarthLinux.bin

during installation there is a readme button, I clicked and read the readme which includes an "UNINSTALLING" section which read:
> UNINSTALLING:

 Run the "uninstall" script as the user that installed the program, which
  will be in the directory where you installed previously. Alternately,
  delete the installed copy and also $HOME/.loki/installed/googleearth.xml

 During operation, Google Earth writes files only to $HOME/.googleearth ...
  when uninstalling, you can delete this directory at your discretion, but
  you will lose your preferences, placemarks, and download cache.


once installation procedure finishes, the installer says 

> The product was installed in:
/opt/google-earth/
[[IMG]http://img233.imageshack.us/img233/2953/screenshotgoogleearthseio3.th.png[/IMG]](http://img233.imageshack.us/img233/2953/screenshotgoogleearthseio3.png)

google earth is now fully installed and ready for uninstall, so I went for this solution:

> **23meg said:**
> I did a forum search for "uninstall google earth" and it seems [this]("http://www.ubuntuforums.org/showpost.php?p=1657750&postcount=6") is the way to uninstall it.

and found myself with a no such file or directory error. 
there is a ~/.googleearth directory though, but no uninstall script inside.

so I went for the previously mentioned /opt/google-earth/ where I found an uninstall script

>  ./uninstall 
Could not find a usable uninstall program. Aborting.

quite odd. I read the readme again and noticed it said to run the uninstall script as the user who installed the program. so I tried to sudo it to the same result.

a quick search shows that others are experiencing the same difficulties:
[Désinstaller Google Earth avec uninstall.sh]("http://forum.ubuntu-fr.org/viewtopic.php?id=88007")
[Google Earth para Linux!]("http://www.ubuntu-es.org/index.php?q=node/18913")

the [google earth online FAQ entry for uninstall]("http://earth.google.com/support/bin/answer.py?answer=20738&useful=0&show_useful=1") does not even mention linux
I found a lead on [linuxquestions]("http://www.linuxquestions.org/questions/showthread.php?p=2329903#post2329903") mentioning [loki]("http://liflg.org/").
another search later I found "[Une nouvelle façon de désinstaller Google Earth.]("http://blog.racoon97.net/?2006/08/14/40-comment-desinstaller-google-earth")" also mentioning loki.
you can also get loki uninstall from: [http://www.lokigames.com/development/loki_uninstall.php3](http://www.lokigames.com/development/loki_uninstall.php3)

so I got myself a brand new uninstaller installed to try to uninstall google earth. only problem is loki_uninstall can't uninstall what was installed beforehands. 

I ran the google earth installer again just in case it would provide an uninstall link, and much too my surprised it tried to install itself in another directory: ~/google-earth and failed ending up in a semi installed google-earth though saying install was successful. 
I tried the brand ~/google-earth/uninstall script only to get another error:
```
Could not open product information for -L
```
this new google-earth installation still doesn't show in loki_uninstall. 

So basically I now have a working google earth installed in /opt a broken google earth install in my home directory, both of em I can't remove using the provided uninstall script. 

here's the content of the uninstall script:
cat /opt/google-earth/uninstall 
```
#! /bin/sh
#### UNINSTALL SCRIPT - Generated by SetupDB 1.6 #####
DetectARCH()
{
        status=1
        case `uname -m` in
           amd64 | x86_64)  echo "amd64"
                  status=0;;
           i?86 | i86*)  echo "x86"
                  status=0;;
           90*/*)
            echo "hppa"
            status=0;;
            *)
         case `uname -s` in
             IRIX*)
                echo "mips"
                status=0;;
           AIX*)
           echo "ppc"
           status=0;;
             *)
                arch=`uname -p 2>/dev/null || uname -m`
                       if test "$arch" = powerpc; then
                          echo "ppc"
                       else
                          echo $arch
                       fi
                status=0;;
         esac
        esac
        return $status
}

DetectOS()
{
  os=`uname -s`
  if test "$os" = OpenUNIX; then
     echo SCO_SV
  else
     echo $os
  fi
  return 0
}

FindBinary()
{
  arch=$1
  if which loki-uninstall 2> /dev/null > /dev/null || type -p loki-uninstall 2> /dev/null > /dev/null; then
    if loki-uninstall -v > /dev/null 2> /dev/null; then
        echo `exec 2>&-; which loki-uninstall || type loki-uninstall`
    else
        echo "$HOME/.loki/installed/bin/`DetectOS`/$arch/uninstall"
    fi
  else
    echo "$HOME/.loki/installed/bin/`DetectOS`/$arch/uninstall"
  fi
}

arch=`DetectARCH`
UNINSTALL=`FindBinary $arch`

# Special case: if amd64 and binary is missing, try to run x86 build...
if test ! -x "$UNINSTALL" ; then
  if test "$arch" = amd64 ; then
    UNINSTALL=`FindBinary x86`
  fi
fi

if test ! -x "$UNINSTALL" ; then
    echo Could not find a usable uninstall program. Aborting.
    exit 1
fi

exec "$UNINSTALL" -L google-earth "/opt/google-earth/.manifest/google-earth.xml" "$1"

```

if I get this right, all the informations needed for uninstall are inside that xml file, and I need to find a way to feed loki_uninstall with it.

---

### Post by glabouni on 2007-01-14
the only missing documentation from [http://faqs.lokigames.com/]("http://faqs.lokigames.com/") is the only one that would have been useful.

so I tried to apply the [KISS]("http://catb.org/jargon/html/K/KISS-Principle.html") and went for:
sudo loki_uninstall /opt/google-earth/.manifest/google-earth.xml
```
Warning: This XML file was generated with a later version of setupdb (1.6).
Problems may occur.
Product: Google Earth
Installed in /opt/google-earth
Uninstalling desktop menu entries...
Uninstalling mimetypes...
Running /usr/bin/update-mime-database /home/user/.local/share/mime
***
* Updating MIME database in /home/user/.local/share/mime...
Wrote 0 strings at 20 - 20
Wrote aliases at 20 - 24
Wrote parents at 24 - 28
Wrote literal globs at 28 - 2c
Wrote suffix globs at 2c - 34
Wrote full globs at 34 - 38
Wrote magic at 38 - 44
Wrote namespace list at 44 - 48
***

Note that '/home/user/.local/share' is not in the search path
set by the XDG_DATA_HOME and XDG_DATA_DIRS
environment variables, so applications may not
be able to find it until you set them. The
directories currently searched are:

- /root/.local/share
- /usr/local/share/
- /usr/share/

Could not remove install directory: Directory not empty
Google Earth has been successfully uninstalled.
```

-edit-
"directory not empty" error is coming from me having put the loki_uninstall file in there. this file apart all seems to have worked as intended.
-/edit-
now I have to track any leftovers and remove them by hand. I should have made a partimage backup before trying this.
my advice: do *not* install google earth from official download, better off using synaptic or apt-get and the medibuntu non-free repository which provides google earth.

```
## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

---

