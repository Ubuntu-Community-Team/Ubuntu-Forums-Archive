---
title: "CD without Typing Full Path Name"
date: 2007-04-01
forum: General Help
---

### Post by baloo56 on 2007-04-01
Hi Everyone,

I am upgrading an old Redhat Linux 5.2 PC at work to a new Ubuntu Dapper PC and I am 99% complete. I am very pleased with Ubuntu and it has been my choice for home use for the past 8 months. The remaining 1% that I need on the new PC is to find a BASH script that will allow me to change to another directory without having to type in the full path to it. On the old PC the script was called vcd. So for example, if I wanted to change to the jigmil directory from home and it was actually at: /home/bart/machines/jigmils, I could just type in vcd jigmils and the script would put me at jigmils. I have searched the old Redhat box for the script for hours but could not find even a hint of it. I have also spent several hours on Google trying to find a script that would work but had no luck. So, I would appreciate it if anyone could help me out here as the script is a very time saving one.  Thank You.

---

### Post by kidders on 2007-04-01
Hi there,

To be honest, typing something like **cd ~/mac[TAB]/j[TAB]** (/home/bart/machines/jigmils) was always good enough for me, but I'm sure we can recreate this script for you, if you describe what you'd like it to do.

**Edit:** I played around for a while, and came up with the following. Something like this might be one (there are a great many) way of doing what you described.

```
#!/bin/bash

# List of search paths, in order
SEARCH_LIST="$HOME:/"

# Directory search depth
SEARCH_DEPTH=1

# Make output look pretty
COLOUR0='\e[0m'
COLOUR1='\e[0;31m'
COLOUR2='\e[1m'

if [ -z "$1" -o -n "$2" ]; then
    echo "Usage: `basename "$0"` [basename]"
    exit 2
fi

DIR_FOUND=""
DIR_OTHERS=""

IFS=$':'
for i in $SEARCH_LIST; do
    
    IFS=$'\n'
    DIR_LIST=`find $i -maxdepth $SEARCH_DEPTH -type d`
    for j in $DIR_LIST; do
        
        if [ "$(basename "$j")" = "$1" ]; then
            if [ -z "$DIR_FOUND" ]; then
                DIR_FOUND="$j"
            else
                DIR_OTHERS="$DIR_OTHERS$j"
            fi
        fi
        
    done
    
done

if [ -n "$DIR_OTHERS" ]; then
    echo -e "${COLOUR2}$1${COLOUR0} is ambiguous:"
    echo -e "${COLOUR1}$DIR_FOUND${COLOUR0}"
    echo $DIR_OTHERS
elif [ -z "$DIR_FOUND" ]; then
    echo -e "${COLOUR1}No candidate for ${COLOUR0}${COLOUR2}$1${COLOUR0}"
    exit 1
else
    echo -e "Directory: ${COLOUR2}$DIR_FOUND${COLOUR0}"
fi

cd "$DIR_FOUND"

```

For demonstration purposes, the script searches your home and '/' for possible destination directories. You would make it work by calling it something like **/usr/local/bin/smart_cd** (being careful to **chown root:root** and **chmod 755** it) and typing...```
alias vcd='. /usr/local/bin/smart_cd'
```(The space after the dot is very important.) After that, **vcd Music** would send you to /home/bart/Music, and (if you set SEARCH_DEPTH to 2) you could get to /home/bart/machines/jigmils with **vcd jigmils**.

How close is that to what you're looking for?

---

### Post by baloo56 on 2007-04-02
Hi Kidders,

That looks like what I am looking for. I will hopefully get a chance to try it out at work in the next couple of days. I will let you know how it works out for me. Many thanks for the time and effort you put into the reply, it is appreciated.

---

### Post by kidders on 2007-04-02
No problem. :-)

---

### Post by baloo56 on 2007-04-10
Hi Kidders,

I had a change to try out the script you kindly sent me, but I came up with the following when I tested it out for the first time:

linux:/home/davew >alias vcd='. /usr/local/bin/smart_vcd'
linux:/home/davew >vcd jigmil
: command not found
: command not found
: command not found
: command not found
'ash: /usr/local/bin/smart_vcd: line 23: syntax error near unexpected token `do
'ash: /usr/local/bin/smart_vcd: line 23: `for i in $SEARCH_LIST; do
linux:/home/davew >

I cut & pasted your original script text so as not to make a typo's. The only change I made was from smart_cd to smart_vcd in the script & file name. Any idea's?
One last Question. Where is the best place to add the alias to so it is permanent in Ubuntu?
Thank You.

---

### Post by kidders on 2007-04-10
> **baloo56 said:**
> I had a chance to try out the script you kindly sent me, but I came up with the following when I tested it out for the first time:

linux:/home/davew >alias vcd='. /usr/local/bin/smart_vcd'
linux:/home/davew >vcd jigmil
: command not found
: command not found
: command not found
: command not found
'ash: /usr/local/bin/smart_vcd: line 23: syntax error near unexpected token `do
'ash: /usr/local/bin/smart_vcd: line 23: `for i in $SEARCH_LIST; do
linux:/home/davew >That's a pity. :-( As I'm sure you noticed, the example I posted makes no effort to handle any errors, or variations in the user environment. Having said that, it probably *should* work properly on most standard Ubuntu systems.

There are a great many things that could cause what I posted to fail. For instance, you may be missing certain utilities, or using versions that object to some of the assumptions I made. Also, your shell (Ash?) may not be syntactically compatible with Bash (which is the shell I had in mind when I wrote the example).

Have you established where the ": command not found" messages are coming from? What kind of system are you running?

---

### Post by baloo56 on 2007-04-11
Hi Kidders,

1) The "command not found" lines are coming from within the smart_vcd script. I tried commenting out various commands within the script but only generated additional "command not found" lines.
2) I noted that the "command not found" lines come before the line 23 error so it was the commands before that line that I commented out.
3) I am running the terminal default, bash shell (echo $SHELL gives me /bin/bash) so I am not sure where the 'ash is coming from.
4) I am running a bulk standard Dell Optiplex GX620 Celeron box with Ubuntu Dapper.
5) Even if I cd to /usr/local/bin and type source smart_vcd to run the script without using vcd I get the errors listed in my previous posting.

I will continue to work my way through it to see if anything obvious presents itself.

---

### Post by kidders on 2007-04-11
How weird. Sorry... I'd assumed you'd customised your system somehow. *[COLOR=Silver]As it turns out, I have a Dapper install I can play with. I'll post back![/COLOR]*

**Edit:** No luck. My little gizmo seems to work as is, on a (relatively) fresh Dapper install. :confused:

---

### Post by baloo56 on 2007-04-11
Hi Kidders,

I ran the smart_vcd script in debug mode and got the following results:

linux:/home/davew >bash -v smart_vcd
#!/bin/bash

: command not foundt_vcd: line 2:
# List of search paths, in order
SEARCH_LIST="$HOME:/"

: command not foundt_vcd: line 5:
# Directory search depth
SEARCH_DEPTH=2

: command not foundt_vcd: line 8:
# Make output look pretty
COLOUR0='\e[0m'
COLOUR1='\e[0;31m'
COLOUR2='\e[1m'

: command not foundt_vcd: line 13:
if [ -z "$1" -o -n "$2" ]; then
    echo "Usage: `basename "$0"` [basename]"
    exit 2
fi

DIR_FOUND=""
DIR_OTHERS=""

IFS=$':'
for i in $SEARCH_LIST; do
/usr/local/bin/smart_vcd: smart_vcd: line 23: syntax error near unexpected token '`do
'usr/local/bin/smart_vcd: smart_vcd: line 23: `for i in $SEARCH_LIST; do
linux:/home/davew >

I thought maybe it is a PATH problem to /bin/bash with all the "command not found" errors but /bin is in my PATH. I will have some more time to play with it tomorrow, but right now...its time to head home. Thank you.

---

### Post by stylishpants on 2007-04-11
The feature you implemented is already built in to the bash shell.

You just set the environment variable CDPATH to a colon-separated list of the dirs you want searched.  Do it in your ~/.bashrc to have it set up automatically every time you log in.


```

fhanson@fhanson:/tmp$ cd Mail
-bash: pushd: Mail: No such file or directory

fhanson@fhanson:/tmp$ export CDPATH="$HOME:/"
fhanson@fhanson:/tmp$ cd Mail
fhanson@fhanson:~/Mail$ 

```

For more information:

man bash | less -p CDPATH

---

### Post by stylishpants on 2007-04-11
BTW if you did not want to have this functionality every time you use the "cd" command, you could define an alias like this:

```

alias vcd="CDPATH='$HOME:/tmp' cd"

```

---

### Post by baloo56 on 2007-04-13
Hi stylishpants,

Thank you for your suggestion to use CDPATH to solve my cd problem. With a little bit of trial & error it proved to be just what I was looking for. Regards.

---

