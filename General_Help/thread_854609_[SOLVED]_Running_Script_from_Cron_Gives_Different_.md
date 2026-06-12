---
title: "[SOLVED] Running Script from Cron Gives Different Results"
date: 2008-07-09
forum: General Help
---

### Post by MasterXandrex on 2008-07-09
OK, I am using a script that should cycle through all files in a directory, determine what is gone and what has been added, it then removes and adds them to SVN and commits. It then updates. All that is fine, the weird thing is when I run it from CRON.

When I run it from CRON, the script does not complete as when I run it from the terminal. 

The command is: 

/home/xandrex/Home_Repo/scripts/svnautocommit /home/xandrex/Home_Repo/ >> /home/xandrex/SVN_log

the crontab entry is: 

0,5,10,15,20,25,30,35,40,45,50,55 * * * * /home/xandrex/Home_Repo/scripts/svnautocommit /home/xandrex/Home_Repo/ >> /home/xandrex/SVN_log

When I look at SVN_log I recieve the following results when ran from terminal:

Wed Jul  9 17:11:34 EDT 2008
At revision 21.

or if I have updated something I get this or similar:

Wed Jul  9 17:12:36 EDT 2008
Sending        scripts/svn/svnautocommit
Transmitting file data .
Committed revision 22.
At revision 22.

but when it is ran from CRON, I only get the date portion

The script is below and any help would be useful.

Thanks,

Xan -- ](*,)


```

#!/bin/bash 
date 

#------------------------------- Subroutines ---------------------------------
usage(){
echo " Usage: $(basename $0) PATH" 
echo ""
echo "Automatically commits the changes of svn working copy located in PATH."
echo "The new files are automatically added and the files that have been removed"
echo "are removed."
echo ""
echo "By Gael Varoquaux"
}

#------------------------------- Process the options -------------------------
if [ $# -eq 1 ]
then
    workingdir="$1"
else
    usage
    exit 1
fi

if ! cd $workingdir
then
    echo $workingdir is not a accessible path.
    usage
    exit 1
fi

#------------------------------- Find out what has changed -------------------

# A warning if this fails :
mkdir -p $HOME/.local
echo "SVN autocommit failed" > $HOME/.local/motd

svnstatus=$(svn status $workingdir)
added=$(printf "$svnstatus" | sed -n 's/^[A?] *\(.*\)/\1/p')
removed=$(printf "$svnstatus" | sed -n 's/^! *\(.*\)/\1/p')

if [ "x$added" != "x" ]
then
    echo adding "$added" to repository
    svn add $added
fi

if [ "x$removed" != "x" ]
then
    echo removing "$removed" to repository
    svn remove $removed
fi

svn commit -m "autocommit" && rm $HOME/.local/motd 
svn update

```

---

### Post by HalPomeranz on 2008-07-10
My guess is that there are some environment variables that are set in your terminal environment that aren't getting set in the environment of the cron job.  Some SVN specific settings perhaps?

If you're not sure, run "env" in your terminal and post the results in this thread.

---

### Post by MasterXandrex on 2008-07-10
I thought about that, in the crontab I've set the environment and path identically, and there are no other variables.

Plus I just realized that from the Cron run I was not getting the errors, this is the output of the cron after I redirected the errors into the log.
```

Thu Jul 10 09:30:01 EDT 2008
svn: Can't convert string from native encoding to 'UTF-8':
svn: Assignment A ?\226?\128?\147 Class 4 ?\226?\128?\147 Mining Department Presentation-ENGR199.doc
svn: Working copy '/home/xandrex/Home_Repo' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
svn: Working copy '.' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)
svn: Can't convert string from native encoding to 'UTF-8':
svn: Assignment A ?\226?\128?\147 Class 4 ?\226?\128?\147 Mining Department Presentation-ENGR199.doc

```
and from the terminal it works perfectly... I don't understand what's going on. They have the same path and shell.


Anyway, from terminal env:
```
TERM=xterm
SHELL=/bin/bash
XDG_SESSION_COOKIE=4f0c2f83914a938118680516483ef5ac-1215709210.963196-1735041177
SSH_CLIENT=157.182.63.67 42314 22
SSH_TTY=/dev/pts/3
USER=xandrex
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
MAIL=/var/mail/xandrex
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/xandrex
LANG=en_US.UTF-8
HISTCONTROL=ignoreboth
SHLVL=1
HOME=/home/xandrex
LOGNAME=xandrex
SSH_CONNECTION=157.182.63.67 42314 192.168.1.100 22
LESSOPEN=| /usr/bin/lesspipe %s
LESSCLOSE=/usr/bin/lesspipe %s %s
_=/usr/bin/env

```

and from the cron env:
```
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
PWD=/home/xandrex
SHLVL=1
HOME=/home/xandrex
LOGNAME=xandrex
_=/usr/bin/env

```


Xan

---

### Post by HalPomeranz on 2008-07-10
Hmmm, yeah that's odd.  I honestly don't know enough about subversion to say why you're getting a locking error when running your script via cron, but it looks to me like it's a subversion issue.  You might try posting to one of the forums/mailing lists at subversion.tigris.org-- I'm guessing that they'll be more likely to be able to help you.  It's probably something really simple.

---

### Post by MasterXandrex on 2008-07-10
Figured it out with some help. I had to set a cron variable

```
 LANG=en_US.UTF-8
```



Thanks for all the help,

Xan

---

