---
title: "ps2pdf watched directory?  (like distiller)"
date: 2008-03-09
forum: General Help
---

### Post by phillywize on 2008-03-09
Anyone have an idea how I might set up a watched directory that will spit out pdf's of postscript files that get dropped into it, a la the acrobat distiller feature?  I'm aware of cups-pdf, but am looking to take the watched-directory approach.

Thanks in advance for any tips!

Bob

---

### Post by phillywize on 2008-03-20
Bump

---

### Post by syadnom on 2008-03-21
2 options here

1)crontab
have crontab run once per minute, looking in a directory for .ps files and converting them to .pdf
[SIZE="1"]> * * * * * for x in `ls /path/to/ps/directory/*.ps`;do ps2pdf $x & mv $x /path/to/ps/dirtectory/processed; done[/SIZE]
pros: simple, straight forward, only converts ps files that exist, then move them out of the way. alternatively delete them. 

cons: must wait up to 1 minute for script to work.

you will get pdf output in the /root folder unless you change 
> do ps2pdf $x 
to
> do ps2pdf $x /destination/path/$x.pdf

then your file will be file.ps.pdf, or you can use some more scripting top do the work.

I think the solution below is better.  fits the system better, can be stoped and restarted easily.

2)looping bash daemon with init scripts
build a looping bash script plus an init launcher to make a daemon.  using a lock file for daemon, daemon lives when lock file exist, dies when it does not.   init script creates lock file and launches daemon, init can then destroy lock file and daemon kills itself at next cycle.

this is much more complicated but i will build the scripts for you and you can cut and paste.
i decided to create this in /usr/share/ps2pdfd
> sudo mkdir -p /usr/share/ps2pdfd
paste the following code into the file /usr/share/ps2pdfd/ps2pdfd
> 
gedit /usr/share/ps2pdfd/ps2pdfd
[QUOTE]
#ps2pdfd daemonizing script by Daniel Denson
#license GPLv2
#this allows you to have a config file, which is good
. /etc/ps2pdfd.conf
#make the directories.  the -p will not give directory exists errors so it is good
mkdir -p $ps
mkdir -p $oldps		
mkdir -p $pdfdest
chmod -R 755 $ps
chmod -R 755 $oldps
chmod -R755 $pdfdest
#here is the loop
while true; do
	if [ -f /var/lock/subsys/ps2pdfd.lock ]
		then
					cd $pdfdest
					for x in `find $ps -maxdepth 1 -type f`;
					do ps2pdf $x && mv $x $oldps;
					done
		else
			echo "stopping ps2pdfd"
			exit
	fi
sleep $pswait
done
[/QUOTE]
mark it executable
> chmod 755 /usr/share/ps2pdfd/ps2pdfd
same deal here
> 
gedit /usr/share/ps2pdfd/ps2pdfd.conf
[QUOTE]
#ps dropbox directory - ps=/path/
ps=/psdropbox/

#old ps file storage directory - oldps=/path/old/
oldps=/psdropbox/old/

#where to put the pdf files - pdfdest=/path/pdfdest/
pdfdest=/psdropbox/pdfdest/

#wait period in seconds
pswait=2[/QUOTE]
and then link that to /etc
> ln -s /usr/share/ps2pdfd/ps2pdfd.conf /etc/ps2pdfd.conf

now edit the conf file
> gedit /etc/ps2pdfd.conf[QUOTE]
#!/bin/bash
#ps2pdfd daemon startup script by Daniel Denson
#license GPLv2
#
# description: ps2pdfd daemon
#

# Start the service ps2pdfd
start() {
        echo "Starting ps2pdfd: "
        ### Create the lock file ###
        touch /var/lock/subsys/ps2pdfd.lock
        /usr/share/ps2pdfd/ps2pdfd &
        echo
}

# Stop the service ps2pdfd
stop() {
        echo  "Stopping ps2pdfd: "
        ### Now, delete the lock file ###
        rm -f /var/lock/subsys/ps2pdfd.lock
        echo
}

### main logic ###
case "$1" in
  start)
        start
        ;;
  stop)
        stop
	;;
  status)
	if [ -f /var/lock/subsys/ps2pdfd.lock ]
		then
			echo "ps2pdf appears to be running"
		else
			echo "ps2pdf does not seem to be running"
	fi 
       ;;
  restart|reload|condrestart)
        stop
        start
        ;;
  *)
        echo $"Usage: $0 {start|stop|restart|reload|status}"
        exit 1
esac

exit 0[/QUOTE]

now mark it execultable
> chmod 755 /usr/share/ps2pdfd/ps2pdfd.init
now you need to put this init script in the appropriate directories.
ubuntu has a default runlevel of 2, which means you want to create a link into the rc2.d and also the init.d directories.

> 
ln -s /usr/share/ps2pdfd.init /etc/init.d/ps2pdfd
ln -s /etc/init.d/ps2pdfd /etc/rc2.d/S99ps2pdfd


i like to use sysv-rc-conf to edit my runlevels, you can check it out.  this daemon will only be running in runlevel2 but you can put it in 3 4 and 5 like most ubuntu scripts either by linking into rc3.d etc or by using sysv-rc-conf.

good luck, hope you like this setup.  I have never packaged up a deb before or I would build it up.

please consider this script as GPL

---

### Post by phillywize on 2008-03-21
Syadnom,

Many thanks! I look forward to setting up that script asap, and I'll keep you posted on how it goes.

Bob

---

### Post by phillywize on 2008-03-22
Works like a charm -- thank you so very, very much.

A few things I noticed along the way:  first, in your scripting directions above, the second ps2pdfd.conf file seems like it should actually be ps2pdfd.init.  Things weren't coming together until I made that change.  Also, I've generally had to create and run all this stuff as root, which seems pretty standard.  I think one of the side effects, however, is that the resulting pdf's are owned by root.  Any thoughts on how I could get this script to generate pdf's owned by user?

Even so, this is great as is.  Thanks again.

Bob

---

### Post by ibuclaw on 2008-03-22
> if [ -f /var/lock/subsys/ps2pdfd.lock ]
then
cd $pdfdest
for x in `find $ps -maxdepth 1 -type f`;
do ps2pdf $x && mv $x $oldps;
done
else
echo "stopping ps2pdfd"
exit
fi

Between the line "**done**" and "**else**" put "**chown username:username *.pdf -R**"

Where "**username**" is your username (ie: fred).

Or if you have more than one user on your system. Make a variable before the if statement.
```

**username=`whoami`**
if [ -f /var/lock/subsys/ps2pdfd.lock ]
then
cd $pdfdest
for x in `find $ps -maxdepth 1 -type f`;
do ps2pdf $x && mv $x $oldps;
done
**chown $username:$username *.pdf -R**
else
echo "stopping ps2pdfd"
exit
fi

```

That should fix it
:KS

Regards
Iain

[EDIT]
or you could put it in your .conf file: 
> 
gedit /usr/share/ps2pdfd/ps2pdfd.conf
Quote:
#ps dropbox directory - ps=/path/
ps=/psdropbox/

#old ps file storage directory - oldps=/path/old/
oldps=/psdropbox/old/

#where to put the pdf files - pdfdest=/path/pdfdest/
pdfdest=/psdropbox/pdfdest/

#wait period in seconds
pswait=2

[B]#the username the program will change the ownership of the created pdf file to
username=`whoami`[/B]


And remove the exact same line from the other file, and the same results will be acheived. Only difference is that the code will look cleaner (more professional) 8)

---

### Post by phillywize on 2008-03-22
Bingo.  Thanks.

Another issue I spotted is this:  it doesn't seem to like filenames with spaces.  If I save a .ps file to /psdropbox named:

Holt v. Navarro.ps

What happens is the following:

1.  The daemon produces, in /pdfdest, 3 files (all consisting, it appears, of a single blank page): (a) Holt.pdf; (b) v.pdf; and (c) Navarro.pdf.
2.  Holt v. Navarro.ps is not moved to /old, and hence...
3.  The script gets stuck, looping back and converting the ps into those three pdf's over and over until I delete the .ps from psdropbox.

---

### Post by ibuclaw on 2008-03-22
Change
```
 for x in `find $ps -maxdepth 1 -type f`; 
```

to
```
 **for x in "$ps"*.ps; **
```

Another up is that now it won't try to convert non-postscript files!
Also, unlike "find", you don't need to specify the maxdepth, because it will only ever search the drive which it is currently in! (or pointed to)

But, if for some bizarre reason you have a postscript file that doesn't have the extension ".ps" then it won't convert it at all.
 
That is it. I hope that is now bug free!

Regards
Iain

[EDIT]
:KS :KS :KS
This is my 100th Post!
:KS :KS :KS

---

### Post by phillywize on 2008-03-22
> **tinivole said:**
> Change
```
 for x in `find $ps -maxdepth 1 -type f`; 
```

to
```
 **for x in "$ps"*.ps; **
```


Tried that -- looks like progress, but it gives this error (every 2 seconds, until I kill it, since I presume it just keeps looping through); perhaps it's having problems because it looks for a .ps file and doesn't find one:

```
Error: /undefinedfilename in (/home/bob/pdf/psdropbox/*.ps)
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push
Dictionary stack:
   --dict:1152/1684(ro)(G)--   --dict:0/20(G)--   --dict:92/200(L)--
Current allocation mode is local
Last OS error: 2
GPL Ghostscript SVN PRE-RELEASE 8.61: Unrecoverable error, exit code 1
```

Had I any coding knowledge whatsoever (beyond, um, the BASIC I learned in 2d grade), I'm sure I could fix this myself.  But alas, I'm a new-generation linux user, and am useless when it comes to coding anything.  Thanks for your help! (and congratulations on reaching the century mark; many good posts, I'm sure.)

Edit:
The error looks like  it comes from inside ghostscript.

Edit edit:
I started it, and let it run anyway, then dropped a .ps in psdropbox, and still has the same problem as before with handling spaces.  :(

---

### Post by ibuclaw on 2008-03-22
> **phillywize said:**
> 
[CODE]Error: /undefinedfilename in (/home/bob/pdf/psdropbox/*.ps) 

Oops, sorry my bad. I'll try running the program (as I haven't yet, I've just been making prototypes and testing the different parts of it) and see if I get it round to a working level.

Hmm...
If it were running as a batch program, it would work.
But since it's in loop, the string { "$ps"*.ps } will return "/path/to/psdir/*.ps" and ps2pdf will constantly try to turn the non-existant file "*.ps" into "*.pdf".

SO!
Once again, at the drawing boards.
I think that adding a nested "if" statement to separate the existing files from the non-existing ones may do the trick.

Be Right Back in 2 Minutes!

Regards
Iain

---

### Post by ibuclaw on 2008-03-22
```

for x in $ps*.ps;
   do if [ -f $x ]
   then
      ps2pdf $x && mv $x $oldps;
   else
      break
   fi
done

```

Hope that does it. (Again)

Also, I'm not that much of a BASH programmer either, but I've learnt other stuff such as C, C++, C#, BASIC (at college) and Logo (at Primary School 8) ) But tbh the basic syntax never changes and I find that I can read out a program and know what it does!

Plus the fact that I love to problem solve, so I go out reading the man pages for fixes for faulty code!

Regards
Iain

---

### Post by phillywize on 2008-03-22
> **tinivole said:**
> ```

for x in $ps*.ps;
   do if [ -f $x ]
   then
      ps2pdf $x && mv $x $oldps;
   else
      break
   fi
done

```



Closer yet...but for some reason, 
```

   do if [ -f $x ]
```

gives me this:

> 
/usr/share/ps2pdfd/ps2pdfd: line 20: [: too many arguments


I took a look at the bash man page and tried to figure out what's missing (a ; somewhere?), but no luck.  Any thoughts?


> **tinivole said:**
> 
Also, I'm not that much of a BASH programmer either, but I've learnt other stuff such as C, C++, C#, BASIC (at college) and Logo (at Primary School 8) ) But tbh the basic syntax never changes and I find that I can read out a program and know what it does!

Plus the fact that I love to problem solve, so I go out reading the man pages for fixes for faulty code!


I'm taking notes; I'd love to learn something from all this.  Thanks again.

Bob

---

### Post by ibuclaw on 2008-03-23
Okay, I've Finished it.

I've had a nights sleep and had another attempt at it.

I've finally managed to install it on my PC (at long last). I was rather tired and got confused by the errors in the second post on what to do, so at the time I could only guess what could fix it.

But now I've debugged it, I've seen the errors you saw, I've made a (this time 99.99% effective) fix, and a installer to copy the files into their right place for you.

You can now run the program in your own user (fixed it by chmodding /var/lock/subsys to 777)
And you can run it just by typing the command "ps2pdfd start" in the terminal (I created a script file in /usr/local/bin to solve this)
I've left a full-ish amount of details in the README file included in the tarball.

The tarball can be [Download it Here.]("http://ubuntuforums.org/attachment.php?attachmentid=63603&d=1206330254") or on the post after this one.
Don't get the 8.3KB one, I've since made a major update of it.

Oh and by the way, the fix for the "too many arguments" error was because the **$variables** weren't **"$quoted"** so the if statement treated the string piece by piece and not as a whole.
I Think I might go out and buy a BASH Shell Script "Learn How-to" book later this week. As I'm just having too much fun writing scripts!

Other than that, I hope you enjoy this, learn from it and continue to use it in the future.

I'm glad I have helped you.

Regards
Iain

---

### Post by ibuclaw on 2008-03-23
Okay, it wasn't quite as finished and dusted as I originally liked it would be:

This is a serious face lift, most of the original code is either rewritten or gone.
With quite a bit added in.
To quote my README file...
#Known Bugs
 o None!

#Fixed Since First Writing This
 o Multiple Files dumped in the DropBox is now supported
 o Spaces in file are now supported.
 o Program failed to work after restarting the Computer.
   Lock file is now created in the /home/user directory.
 o Deleting a folder crashed the program with "Error Folder does not exist"
   Folders are now respawned in the loop while the daemon is running.
 o The Program is Now More Verbose. echo "Which is Nice to Know!"
 o Root running this program is disabled by default.
 o Percentages in the filename caused an error.
   They are now replaced with a space using sed.
 o Improved the installer. But it's still no Makefile...
 o Added commandline argument "cleanold" which deletes all ".ps" files in the oldps folder.
 o All known error messages are now kicked!
   Byebye for Now!

#TODO
 o Make a Makefile for installing this script.

I think I'm done with this for the month or so.
If you find any errors phillywize, I hope I have documented it enough for you to fix it yourself.
Despite I've only been working on this for a day, it feels like too long.

 :lolflag:

Regards
Iain

---

### Post by phillywize on 2008-03-24
> **tinivole said:**
> 
I think I'm done with this for the month or so.
If you find any errors phillywize, I hope I have documented it enough for you to fix it yourself.
Despite I've only been working on this for a day, it feels like too long.


Well, I am looking forward to setting it up (away from my machine at the moment, and no ssh tunnel, so I will install this asap).  But let me thank you and syadnom for going out of your way to create  such a useful tool.  There's no emoticon for a beer, but I owe you at least that!

I'll keep you posted on how it goes, and thanks again for your help.

Bob

P.s., if indeed there are any errors, it'll be my own special occasion to learn a bit of scripting and share the FOSS wealth.  But seriously, thank you again.  Can't tell you how grateful I am for the time, effort, and expertise.

P.P.S. - From the README file:

> 
#THANK-YOU:
I'd like to thank phillywize of the UbuntuForums.org for pointing out all the errors I made in reworking this script.
This one is for you!


Thank YOU! I am a useless bum when it comes to coding, as my inability to do anything but helplessly report back error messages demonstrates.

---

### Post by ibuclaw on 2008-03-25
Don't forget that this app can run without a terminal open too! (Thanks to the "while true" statement written by synadom, you can close the terminal you started the app on and it will continue to run while the lockfile is still there.)
You can include "ps2pdfd start" in your login startup scripts, and have "ps2pdfd stop" in your logout scripts.

EDIT:
One last fix (as always, typical young programmer always making mistakes :lolflag:)
I've just upgraded to Hardy beta on a clean install and got an error that /etc/ps2pdfd.conf didn't exist.

It shouldn't affect you since you already have it installed correctly.

But add this to the install function in the setup script
```
     ln -fs /usr/share/ps2pdfd/ps2pdfd.conf /etc/ps2pdfd.conf 
```
and this one in the uninistall function
```
    rm -f /etc/ps2pdfd.conf 
```

It may come in handy when if upgrade to hardy.

---

### Post by phillywize on 2008-03-25
Welp, I set it up as you packaged it (very nice) and let it run, and it works like a charm.  Thanks again!  It's huge (in the moral sense; not the resources sense).  Hopefully others will find this and can make use of it.

Bob

---

