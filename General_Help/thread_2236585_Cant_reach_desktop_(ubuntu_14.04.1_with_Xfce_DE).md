---
title: "Cant reach desktop (ubuntu 14.04.1 with Xfce DE)"
date: 2014-07-27
forum: General Help
---

### Post by pretty_whistle on 2014-07-27
Everything was fine till now.  I shutdown the computer and now I can't reach the desktop.  It's just sitting there stuck.  The screensaver wont even come up.  I can reach the login screen ok but after I hit "enter"at the password prompt the login screen leaves but then it hangs, frozen.  Help!

I have ubuntu 14.04.1 LTS with Xfce DE.

---

### Post by pretty_whistle on 2014-07-27
I'm thinking an update caused this because nothing was changed on my computer except my running updates and then "suddenly" this happens.  What else could it be...........  :-k

---

### Post by Bashing-om on 2014-07-27
pretty_whistle; Hi !

 Do not know yet, but I am willing to help explore this situation.

Let's boot to the text terminal, and see what results when attempting to start the GUI manually.

Boot to the grub menu, 'e' key for edit mode with the latest nonrecovery kernel highlighted -> boot options screen ; arrow down and across to the terms "quiet splash" and replace them with the term "text". Key combo ctl+x to continue the boot process to TTY1.

Login and username in this terminal to login to the system.

I am aware of 2 differing commands to startup xfce4. Let's look and see how it is currently supposed to start.
post back:
```

cat ~/.xinitrc

``` and we will attempt to explicitly start xfce4.

[INDENT][INDENT]gotta start somewhere
[INDENT][INDENT][INDENT]looks like a good start to me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-27
I am in tty.  It says "no such file or directory".

:(

---

### Post by pretty_whistle on 2014-07-27
Wait.... I typed it in wrong......

it just repeats it back to me.

---

### Post by Bashing-om on 2014-07-27
pretty_whistle; Well,

Not the result I had expected ( no .xinitrc file ) .

But now I do know the terminal command that "should" work.

What results at that terminal:
```

startxfce

``` nothing fancy just that little bitty command .

[INDENT][INDENT]getting set to go
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-27
> **Bashing-om said:**
> pretty_whistle; Well,

Not the result I had expected ( no .xinitrc file ) .

But now I do know the terminal command that "should" work.

What results at that terminal:
```

startxfce

``` nothing fancy just that little bitty command .
[INDENT][INDENT]getting set to go
[/INDENT]
[/INDENT]


I'm in tty2 not tty1.  Does that matter?

In tty2 it said "command not found".

---

### Post by Bashing-om on 2014-07-27
pretty_whistle; Yikes,

Again, not what I had expected . Does not matter which terminal you are in ... hummmm...
How bout 
```

startx

```

I do not expect it to start, as there is no .xinitrc file, but maybe will give some hints as to why not .

[INDENT][INDENT]still poke'n
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-27
> **Bashing-om said:**
> pretty_whistle; Yikes,

Again, not what I had expected . Does not matter which terminal you are in ... hummmm...
How bout 
```

startx

```

I do not expect it to start, as there is no .xinitrc file, but maybe will give some hints as to why not .
[INDENT][INDENT]still poke'n
[/INDENT]
[/INDENT]


What the....  that's weird.  It gave me half of my desktop.  Plus I have a window about flashplugin installer saying it failed to download extra data files.  The desktop theme reminds me of gnome.  Weird.  The panels are missing........

---

### Post by Bashing-om on 2014-07-27
pretty_whistle; Welp ..

I am also try'n to wrap my mind around this.
Doing a bit of research as to why we would not want to revert the desk top back to defaults .. And what is missing in the startup routine.

[INDENT][INDENT]safety is no accident
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Well,

As a thought, look at what the script file "/usr/bin/startx" is executing.

In particular compare this:
```

userclientrc=[color=blue]$HOME/.xinitrc[/color]
sysclientrc=/etc/X11/xinit/xinitrc


userserverrc=$HOME/.xserverrc
sysserverrc=/etc/X11/xinit/xserverrc
defaultclient=/usr/bin/xterm
defaultserver=/usr/bin/X
defaultclientargs=""
defaultserverargs=""
defaultdisplay=":0"

```
with your output of terminal command:
```

cat /usr/bin/startx

``` 
See in mine, the file .xinitrc is required; I expect that to be also true with your file // and we know that the file does not exist in your system.

Will also be worth while to md5sum "/usr/bin/startx" - as a check for corruption - ; soon as I can verify how to know what that hash value should be .

Maybe also next investigate the script file "/etc/X11/xinit/xinitrc', see what it is executing.

Then once the startup routines are verified/corrected; and if problems still exist, we start looking for problems in the desk top config files (??).

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Hey;

I am done for this session. I will pick this back up on my morrow's eve.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; Well,

As a thought, look at what the script file "/usr/bin/startx" is executing.

In particular compare this:
```

userclientrc=[COLOR=blue]$HOME/.xinitrc[/COLOR]
sysclientrc=/etc/X11/xinit/xinitrc


userserverrc=$HOME/.xserverrc
sysserverrc=/etc/X11/xinit/xserverrc
defaultclient=/usr/bin/xterm
defaultserver=/usr/bin/X
defaultclientargs=""
defaultserverargs=""
defaultdisplay=":0"

```
with your output of terminal command:
```

cat /usr/bin/startx

``` 
See in mine, the file .xinitrc is required; I expect that to be also true with your file // and we know that the file does not exist in your system.

Will also be worth while to md5sum "/usr/bin/startx" - as a check for corruption - ; soon as I can verify how to know what that hash value should be .

Maybe also next investigate the script file "/etc/X11/xinit/xinitrc', see what it is executing.

Then once the startup routines are verified/corrected; and if problems still exist, we start looking for problems in the desk top config files (??).
[INDENT][INDENT]just what I think
[/INDENT]
[/INDENT]


I typed this into the terminal "/usr/bin/startx" and the screen blacked for a moment and gave me the partial desktop again.

I typed in "cat /usr/bin/startx" into the terminal and got this:

```
     fl
fl







exit $retval

```

I typed "/etc/X11/xinit/xinitrc" into the terminal and it said "no such file or directory".

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Yuk,

That can not be good !

Let's back up here and regroup.
Background info; What is the original install ?, What has led you to install xfce4 for the Desktop Environment, IS xfce4 your preferred DE ?

Current: The basics;
What is there to work with ?
Post back the outputs - between code tags, to maintain readability - of terminal commands:
```

ls -la /usr/bin/startx
ls -la /etc/X11/xinit/xinitrc

``` as I want to see the file sizes and the permissions.


Maybe 'I' am going about this from a the wrong perspective ... But, xfce4 is the DE that I am the more familiar with.

[INDENT][INDENT]'tis indeed a puzzl'n thing
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; Yuk,

That can not be good !

Let's back up here and regroup.
Background info; What is the original install ?, What has led you to install xfce4 for the Desktop Environment, IS xfce4 your preferred DE ?

Current: The basics;
What is there to work with ?
Post back the outputs - between code tags, to maintain readability - of terminal commands:
```

ls -la /usr/bin/startx
ls -la /etc/X11/xinit/xinitrc

``` as I want to see the file sizes and the permissions.


Maybe 'I' am going about this from a the wrong perspective ... But, xfce4 is the DE that I am the more familiar with.
[INDENT][INDENT]'tis indeed a puzzl'n thing
[/INDENT]
[/INDENT]


Background info:
What was original install?  I'm not sure I understand the question.  It's Ubuntu 14.04.  I had upgraded from 13.10.
What led me to install xfce4?  I liked how it functioned.
Is Xfce4 my preferred DE?  Yes it is.  I dont use anything else.

Output of ls -la /usr/bin/startx:
```
-rwxr-xr-x 1 root root 4834 Jun 17  2012 /usr/bin/startx
``` 

Output of ls -la /etc/X11/xinit/xinitrc:
```
-rw-r--r-- 1 root root 164 Nov  3  2010 /etc/X11/xinit/xinitrc
```

---

### Post by steeldriver on 2014-07-28
The **apparently **truncated /usr/bin/startx is likely just because the contents of the file are scrolling off the end of the screen, no? I really don't see anything there to be alarmed about

Likewise the absence of a $HOME/.xinitrc is normal - the script *looks *for one there, but uses a system file in its absence

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; OK !

Our focus then is getting xfce4 back up and functional !

The outputs of the 'ls' commands are same same as my 'original' files - so must contain more - , so what you related last for cating 'startx' must be an error somewhere.

Let's doublecheck and verify.
what results:
```

cat /usr/bin/startx

``` again with a file size "4834", gotta be more in that file !

Clarification: as to "original install" a standard install with unity as the desk top ? Such that now we have a conflict of interest in the DE's ?

It is in the process ->
[INDENT][INDENT][INDENT]we be look'n
[/INDENT][/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; OK !

Our focus then is getting xfce4 back up and functional !

The outputs of the 'ls' commands are same same as my 'original' files - so must contain more - , so what you related last for cating 'startx' must be an error somewhere.

Let's doublecheck and verify.
what results:
```

cat /usr/bin/startx

``` again with a file size "4834", gotta be more in that file !

Clarification: as to "original install" a standard install with unity as the desk top ? Such that now we have a conflict of interest in the DE's ?

It is in the process ->[INDENT][INDENT][INDENT]we be look'n
[/INDENT]
[/INDENT]
[/INDENT]

Yes, it was a standard install with unity.

You want me to do this again? cat /usr/bin/startx?  Ok, here it is:
```
         fi
fi







exit $retval
```

....but I dont think you wanted me to run that again, lol.  Oh well..... :)

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Yeah.

I did, I did want that command run again .. I just do not comprehend what is going on here, with that as an output !
OK, My think'n - for what it is worth -
You do the terminal command 'startx', right; that command calls the file ' /usr/bin/startx ' and begins executing it .. 
HUH ??? in this case there is nothing to execute, so the point of confusion, as you do get a messed up desk top with the command 'startx' - what in the world is executing and from where ?

Let's say there is a "display manager" at play here.
What returns:
```

ls -la /etc/X11/default-display-manager

```
Now, IF that file exist, what does it contain ?
```

cat /etc/X11/default-display-manager

```

Depending, maybe I best boot into an install that has unity, and from a stable install, see if I can determine the boot process of unity and how to force loading up xfce4 instead ??/ may come to that ! But, honestly, since I set up xfce4, I have not looked back at unity. It may take us a bit to finger out that activation process, just to figure out on your system how xfce is started .

[INDENT][INDENT]the Chase is On
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; Yeah.

I did, I did want that command run again .. I just do not comprehend what is going on here, with that as an output !
OK, My think'n - for what it is worth -
You do the terminal command 'startx', right; that command calls the file ' /usr/bin/startx ' and begins executing it .. 
HUH ??? in this case there is nothing to execute, so the point of confusion, as you do get a messed up desk top with the command 'startx' - what in the world is executing and from where ?

Let's say there is a "display manager" at play here.
What returns:
```

ls -la /etc/X11/default-display-manager

```
Now, IF that file exist, what does it contain ?
```

cat /etc/X11/default-display-manager

```

Depending, maybe I best boot into an install that has unity, and from a stable install, see if I can determine the boot process of unity and how to force loading up xfce4 instead ??/ may come to that ! But, honestly, since I set up xfce4, I have not looked back at unity. It may take us a bit to finger out that activation process, just to figure out on your system how xfce is started .
[INDENT][INDENT]the Chase is On
[/INDENT]
[/INDENT]


Output of ls -la /etc/X11/default-display-manager
```
-rw-r--r-- 1 root root 18 May 13  2012 /etc/X11/default-display-manager
```

Output of cat /etc/X11/default-display-manager
```
/usr/sbin/lightdm
```

---

### Post by pretty_whistle on 2014-07-28
I have to say you're doing a lot of work on this.  I thank you. :)  That's nice of you to do it.  :)

Just thought I'd say that..............

---

### Post by JKyleOKC on 2014-07-28
Going back to post #3 in this thread, try using the command "less /usr/bin/startx" to view the startx script and compare with the start of the script posted by bashing-om. The startx script is MUCH longer than can be displayed on any terminal screen, so you are only seeing the very last lines of the script, which don't tell anyone much.

In general, I prefer using "less" to "cat" for viewing files, and for posting here I use "cat filename >tempfile", then copy the content of the "tempfile" this creates, and paste it into the message for posting. The plain "cat filename" approach fails when the file being viewed has more lines than the screen can hold.

---

### Post by Bashing-om on 2014-07-28
OH JKyleOKC; My friend indeed !

You come to the rescue once more ! Thanks heaps .. Will file that info in the fore front of the gray matter, as will have many references in the future !.

@ pretty_whistle. with JKyleOKC's advisory, what is the contents of the "/usr/bin/startx" file ?

[INDENT][INDENT]reason, cause, and effect ->
put gray matter in motion to 'reason'
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
When I used the word "less" in front it sure produces longer output but it wont let me copy and paste it. :(

Edit:
It'll only copy what's on the visible part of the window........

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Hey,

As a suggestion, as JKyleOKC advised; redirect that output from the command to a text file :
```

cat /usr/bin/startx > output.txt

```
(the control character '>' performs that redirect function.)
Then with the 'less' command you can page through it.
```

less output.txt

```
It keeps slipping my mind that you do not have the GUI and as such the conveniences of the GUI for copy/paste. All that is important at this time is that your file contain the entries as depicted from my output in post #11.

Will check others in due time, but I bet the 'startx' script is calling ~/.xinitrc, and ,xinitrc is non-existent .. so no desk top is startable !

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; Hey,

As a suggestion, as JKyleOKC advised; redirect that output from the command to a text file :
```

cat /usr/bin/startx > output.txt

```
(the control character '>' performs that redirect function.)
Then with the 'less' command you can page through it.
```

less output.txt

```
It keeps slipping my mind that you do not have the GUI and as such the conveniences of the GUI for copy/paste. All that is important at this time is that your file contain the entries as depicted from my output in post #11.

Will check others in due time, but I bet the 'startx' script is calling ~/.xinitrc, and ,xinitrc is non-existent .. so no desk top is startable !
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]


Hmm... weird.  I typed it in but it produced nothing-no txt on the desktop.  Did it put it somewhere else?  Like in documents?  Because if it did I cant access that at all.  My Home folder is missing.........

---

### Post by pretty_whistle on 2014-07-28
Duh....I can access documents after all by opening any folder...lol.  Well....it's not in there.  Where is it?

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; HUmm .....

This is getting stranger and stranger ..

The command should have made that text file in your home directory ( as that I expect is your Present Working Directory ) else we can give it the explicit path to put that file in your /home directory ...- don't you just love learning new things ? -

1. Let's 'find' that file:
```

sudo find / -name output.txt

```Will take a bit of time to search all files on your system looking for this particular file, give it some time to complete.

2. Is your /home directory gone gone ?
From where you are when you login to the system, what results:
```

ls -la /home

```
in that output there is a directory as your username;
```

ls -la /home/<username>

```
are all your files visible ?? ( fingers crossed)

[INDENT][INDENT][INDENT]are we getting ready to punt ?
[/INDENT][/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; HUmm .....

This is getting stranger and stranger ..

The command should have made that text file in your home directory ( as that I expect is your Present Working Directory ) else we can give it the explicit path to put that file in your /home directory ...- don't you just love learning new things ? -

1. Let's 'find' that file:
```

sudo find / -name output.txt

```Will take a bit of time to search all files on your system looking for this particular file, give it some time to complete.

2. Is your /home directory gone gone ?
From where you are when you login to the system, what results:
```

ls -la /home

```
in that output there is a directory as your username;
```

ls -la /home/<username>

```
are all your files visible ?? ( fingers crossed)
[INDENT][INDENT][INDENT]are we getting ready to punt ?
[/INDENT]
[/INDENT]
[/INDENT]


Here's output-txt
```
#!/bin/sh

#
# This is just a sample implementation of a slightly less primitive
# interface than xinit.  It looks for user .xinitrc and .xserverrc
# files, then system xinitrc and xserverrc files, else lets xinit choose
# its default.  The system xinitrc should probably do things like check
# for .Xresources files and merge them in, start up a window manager,
# and pop a clock and several xterms.
#
# Site administrators are STRONGLY urged to write nicer versions.
#


unset DBUS_SESSION_BUS_ADDRESS
unset SESSION_MANAGER




userclientrc=$HOME/.xinitrc
sysclientrc=/etc/X11/xinit/xinitrc




userserverrc=$HOME/.xserverrc
sysserverrc=/etc/X11/xinit/xserverrc
defaultclient=/usr/bin/xterm
defaultserver=/usr/bin/X
defaultclientargs=""
defaultserverargs=""
defaultdisplay=":0"
clientargs=""
serverargs=""


enable_xauth=1




# Automatically determine an unused $DISPLAY
d=0
while true ; do
    [ -e /tmp/.X$d-lock ] || break
    d=$(($d + 1))
done
defaultdisplay=":$d"
unset d




whoseargs="client"
while [ x"$1" != x ]; do
    case "$1" in
    # '' required to prevent cpp from treating "/*" as a C comment.
    /''*|\./''*)
	if [ "$whoseargs" = "client" ]; then
	    if [ x"$client" = x ] && [ x"$clientargs" = x ]; then
		client="$1"
	    else
		clientargs="$clientargs $1"
	    fi
	else
	    if [ x"$server" = x ] && [ x"$serverargs" = x ]; then
		server="$1"
	    else
		serverargs="$serverargs $1"
	    fi
	fi
	;;
    --)
	whoseargs="server"
	;;
    *)
	if [ "$whoseargs" = "client" ]; then
	    clientargs="$clientargs $1"
	else
	    # display must be the FIRST server argument
	    if [ x"$serverargs" = x ] && \
		 expr "$1" : ':[0-9][0-9]*$' > /dev/null 2>&1; then
		display="$1"
	    else
		serverargs="$serverargs $1"
	    fi
	fi
	;;
    esac
    shift
done


# process client arguments
if [ x"$client" = x ]; then
    client=$defaultclient


    # For compatibility reasons, only use startxrc if there were no client command line arguments
    if [ x"$clientargs" = x ]; then
        if [ -f "$userclientrc" ]; then
            client=$userclientrc
        elif [ -f "$sysclientrc" ]; then
            client=$sysclientrc












        fi
    fi
fi


# if no client arguments, use defaults
if [ x"$clientargs" = x ]; then
    clientargs=$defaultclientargs
fi


# process server arguments
if [ x"$server" = x ]; then
    server=$defaultserver


    # For compatibility reasons, only use xserverrc if there were no server command line arguments
    if [ x"$serverargs" = x -a x"$display" = x ]; then
	if [ -f "$userserverrc" ]; then
	    server=$userserverrc
	elif [ -f "$sysserverrc" ]; then
	    server=$sysserverrc
	fi
    fi
fi


# if no server arguments, use defaults
if [ x"$serverargs" = x ]; then
    serverargs=$defaultserverargs
fi


# if no display, use default
if [ x"$display" = x ]; then
    display=$defaultdisplay
fi


if [ x"$enable_xauth" = x1 ] ; then
    if [ x"$XAUTHORITY" = x ]; then
        XAUTHORITY=$HOME/.Xauthority
        export XAUTHORITY
    fi


    removelist=


    # set up default Xauth info for this machine


    # check for GNU hostname
    if hostname --version > /dev/null 2>&1; then
        if [ -z "`hostname --version 2>&1 | grep GNU`" ]; then
            hostname=`hostname -f`
        fi
    fi


    if [ -z "$hostname" ]; then
        hostname=`hostname`
    fi


    authdisplay=${display:-:0}


    mcookie=`/usr/bin/mcookie`














    if test x"$mcookie" = x; then
        echo "Couldn't create cookie"
        exit 1
    fi
    dummy=0


    # create a file with auth information for the server. ':0' is a dummy.
    xserverauthfile=`mktemp --tmpdir serverauth.XXXXXXXXXX`
    trap "rm -f '$xserverauthfile'" HUP INT QUIT ILL TRAP KILL BUS TERM
    xauth -q -f "$xserverauthfile" << EOF
add :$dummy . $mcookie
EOF








    serverargs=${serverargs}" -auth "${xserverauthfile}




    # now add the same credentials to the client authority file
    # if '$displayname' already exists do not overwrite it as another
    # server man need it. Add them to the '$xserverauthfile' instead.
    for displayname in $authdisplay $hostname$authdisplay; do
        authcookie=`xauth list "$displayname" \
        | sed -n "s/.*$displayname[[:space:]*].*[[:space:]*]//p"` 2>/dev/null;
        if [ "z${authcookie}" = "z" ] ; then
            xauth -q << EOF 
add $displayname . $mcookie
EOF
        removelist="$displayname $removelist"
        else
            dummy=$(($dummy+1));
            xauth -q -f "$xserverauthfile" << EOF
add :$dummy . $authcookie
EOF
        fi
    done
fi
























xinit "$client" $clientargs -- "$server" $display $serverargs






retval=$?


if [ x"$enable_xauth" = x1 ] ; then
    if [ x"$removelist" != x ]; then
        xauth remove $removelist
    fi
    if [ x"$xserverauthfile" != x ]; then
        rm -f "$xserverauthfile"
    fi
fi






































exit $retval



```

Home directory does exist and I can access it just by opening a folder-it's in the left navigation area.  I just didnt realize it at first.

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Hey ! We do have access to a GUI ... 

Well done !

OK as in the file :
> 
It looks for user .xinitrc and .xserverrc
# files, then system xinitrc and xserverrc files, else lets xinit choose
# its default.

The 'startx' file is good !
so once more let's follow the path, see where it is failing .
```

ls -la ~/.xinitrc
ls -la /etc/X11/xinit/xserverrc
ls -la /etc/X11/xinit/xinitrc

```

[INDENT][INDENT]good things those bread crumbs[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; Hey ! We do have access to a GUI ... 

Well done !

OK as in the file :

The 'startx' file is good !
so once more let's follow the path, see where it is failing .
```

ls -la ~/.xinitrc
ls -la /etc/X11/xinit/xserverrc
ls -la /etc/X11/xinit/xinitrc

```
[INDENT][INDENT]good things those bread crumbs[/INDENT]
[/INDENT]


Output of ls -la ~/.xinitrc
```
ls: cannot access /home/nutin/.xinitrc: No such file or directory


```

Output of ls -la /etc/X11/xinit/xserverrc
```
-rwxr-xr-x 1 root root 46 Nov  3  2010 /etc/X11/xinit/xserverrc


```

Output of ls -la /etc/X11/xinit/xinitrc
```
-rw-r--r-- 1 root root 164 Nov  3  2010 /etc/X11/xinit/xinitrc


```

---

### Post by monkeybrain20122 on 2014-07-28
Not that I can help. Just to add that it happened to me as well after an update for xubuntu 14.04 a few days ago. Since I was installing it for someone and haven't done much with it, I just reinstalled (with same 14.04.0 ISO) instead of tearing my hair out trying to fix it. After reinstalling I did an update and it is fine. I have no idea what happened.

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Welp,

Been considering .. what is your thoughts to put that "~/.xinitrc" file in place ?
I have my original file I could upload here and you could then copy that file into place ?

But I think there is a cleaner way .. to copy a default file from the system into place ..Looking into that now.

For now, what is the system using for a "session manager" ?

Post back the output of terminal command:
```

ps -e|grep xfce4-session

``` and let's see if it is "xfce4" .
EDIT: Humm:
This:
> 
Your login script, .xinitrc, works with startx, but graphical login managers like GDM do not look for .xinitrc. Instead, they look for a file named .xsession in your home directory. To make GDM run your .xinitrc script, you have to link it to .xsession with the following command:

Cause for a pause.
see:
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)


[INDENT][INDENT]meanwhile, back at the ranch
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
> **monkeybrain20122 said:**
> Not that I can help. Just to add that it happened to me as well after an update for xubuntu 14.04 a few days ago. Since I was installing it for someone and haven't done much with it, I just reinstalled (with same 14.04.0 ISO) instead of tearing my hair out trying to fix it. After reinstalling I did an update and it is fine. I have no idea what happened.
Interesting.  I wonder if the update was fixed since then.  It could be.

That's helpful to know, thanks, because I was wondering about trying to update it again.  I was thinking I may have to stay away from updating for a while but maybe not if it's fixed.  :)

I'm trying to get it fixed but I bet I end up having to restore it with my backup.  Call me skeptical........

---

### Post by pretty_whistle on 2014-07-28
> **Bashing-om said:**
> pretty_whistle; Welp,

Been considering .. what is your thoughts to put that "~/.xinitrc" file in place ?
I have my original file I could upload here and you could then copy that file into place ?

But I think there is a cleaner way .. to copy a default file from the system into place ..Looking into that now.

For now, what is the system using for a "session manager" ?

Post back the output of terminal command:
```

ps -e|grep xfce4-session

``` and let's see if it is "xfce4" .
EDIT: Humm:
This:

Cause for a pause.
see:
[https://wiki.ubuntu.com/CustomXSession](https://wiki.ubuntu.com/CustomXSession)

[INDENT][INDENT]meanwhile, back at the ranch
[/INDENT]
[/INDENT]


> **Bashing-om said:**
> pretty_whistle; Welp,

Been considering .. what is your thoughts to put that "~/.xinitrc" file in place ?
I have my original file I could upload here and you could then copy that file into place ?

But I think there is a cleaner way .. to copy a default file from the system into place ..Looking into that now.

For now, what is the system using for a "session manager" ?

Post back the output of terminal command:
```

ps -e|grep xfce4-session

``` and let's see if it is "xfce4" .
[INDENT][INDENT]meanwhile, back at the ranch
[/INDENT]
[/INDENT]


Nothing came up.

I'm going to try something...............  I'm going to restore my backup and that should solve it.  Of course, it's possible the backup will fail to restore for some reason.  So, just in case it fails and I have this same problem I'll keep this thread alive.  If it restores ok I'll post it and end the thread.

---

### Post by pretty_whistle on 2014-07-28
Ok, done.  Restoring my backup was successful. :)

The end of this thread has come.................

---

### Post by Bashing-om on 2014-07-28
pretty_whistle; Great !

All's well that ends well;
Please mark this thread solved; aides others seeking the solution, helps keep the forum clean and precludes others miss-directing efforts to aid.

[INDENT][INDENT]do something different, next time
[/INDENT][/INDENT]

---

### Post by pretty_whistle on 2014-07-28
A final note:

I believe it was an update that broke it.  After restoring my backup I ran updates again and it's been fixed!  I restarted several times just to be sure I can reach the desktop ok, I did.  :)  So whichever update was the culprit it has been fixed.  Now no one else has to worry about it.

(posted 7-28-2014, 8:48pm MST)

---

