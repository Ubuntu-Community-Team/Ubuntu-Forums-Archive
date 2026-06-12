---
title: "Scripting and correct directory placement"
date: 2015-10-06
forum: General Help
---

### Post by whereismymindat2 on 2015-10-06
thanks for reading. 

Question, where is the "correct" (most universally appropriate). a bash script should be "placed" (aka what folder/directory). 
Especially one that will be used (more often than not). 

Example. 
I'm trying to diagnose a  problem with Firefox. 

However, I would also like to have a time stamp with each line of output. 

I'm using TEE with append to my log file. (far as I see, TEE does not have a native time stamp). 

Trying this, not working 

```


[NOT ROOT] ~$ firefox 2>&1 |ts '[%Y-%m-%d %H:%M:%S]' tee -a  /home/bender/Desktop/FF_TEE_OUT/FF_Diagnostic.txt
Unknown option: a
usage: ts [-r] [-i] [format]


```



One Example (script)
*********************************************
(of course I don't care about the error> log as running Firefox from a console *IS* showing me the Error log 
THANKS!!

  Where should I place the script file? 

```

************************
How to add timestamp to STDERR redirection
http://stackoverflow.com/questions/1507674/how-to-add-timestamp-to-stderr-redirection
************************

( date 1>&2 ; myscript.sh ) 2>error.log

What you need is a trick to pipe stderr through another program that can add timestamps to each line. You could do this with a C program but there's a far more devious way using just bash.

First, create a script which will add the timestamp to each line (called predate.sh):

#!/bin/bash
while read line ; do
    echo "$(date): ${line}"
done

For example:

( echo a ; sleep 5 ; echo b ; sleep 2 ; echo c ) | ./predate.sh

produces:

Fri Oct  2 12:31:39 WAST 2009: a
Fri Oct  2 12:31:44 WAST 2009: b
Fri Oct  2 12:31:46 WAST 2009: c

Then you need another trick that can swap stdout and stderr, this little monstrosity here:

( myscript.sh 3>&1 1>&2- 2>&3- )

Then it's simple to combine the two tricks by timestamping stdout and redirecting it to your file:

( myscript.sh 3>&1 1>&2- 2>&3- ) | ./predate.sh >error.log

The following transcript shows this in action:

pax> cat predate.sh
    #!/bin/bash
    while read line ; do
        echo "$(date): ${line}"
    done
pax> cat tstdate.sh
    #!/bin/bash
    echo a to stderr then wait five seconds 1>&2
    sleep 5
    echo b to stderr then wait two seconds 1>&2
    sleep 2
    echo c to stderr 1>&2
    echo d to stdout
pax> ( ( ./tstdate.sh ) 3>&1 1>&2- 2>&3- ) | ./predate.sh >error.log
    d to stdout
pax> cat error.log
    Fri Oct  2 12:49:40 WAST 2009: a to stderr then wait five seconds
    Fri Oct  2 12:49:45 WAST 2009: b to stderr then wait two seconds
    Fri Oct  2 12:49:47 WAST 2009: c to stderr

As already mentioned, predate.sh will prefix each line with a timestamp and the tstdate.sh is simply a test program to write to stdout and stderr with specific time gaps.

When you run the command, you actually get "d to stdout" written to stderr (but that's your TTY device or whatever else stdout may have been when you started). The timestamped stderr lines are written to your desired file.



```




```



this one? I assume "Command" (is a place holder for TEE (etc. correct?)/ 
************************
Prepending a timestamp to each line of output from a command
http://unix.stackexchange.com/questions/26728/prepending-a-timestamp-to-each-line-of-output-from-a-command
************************


moreutils includes ts which does this quite nicely:

command | ts '[%Y-%m-%d %H:%M:%S]'

It eliminates the need for a loop too, every line of output will have a timestamp put on it.

$ echo -e "foo\nbar\nbaz" | ts '[%Y-%m-%d %H:%M:%S]'
[2011-12-13 22:07:03] foo
[2011-12-13 22:07:03] bar
[2011-12-13 22:07:03] baz

You want to know when that server came back up you restarted? Just run ping | ts , problem solved :D.



```


Thank you!

---

### Post by yancek on 2015-10-06
If you are running it as a normal user, put it in the user /home directory or anywhere in the user PATH which you can find with the command below when logged in as that user:

```
echo $PATH
```

---

### Post by tgalati4 on 2015-10-06
Years ago, when dinosaurs roamed the earth and Unix was the operating system of choice, a User would put custom binaries in ~/bin.  Fossil remains have been found in the muck of .profile:

> tgalati4@Mint17 ~ $ cat .profile
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

[B]# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"[/B]
fi


Note the fine feathers that this creature had and small braincase.

For me, I put mine in a ~/scripts directory and put a path statement in .bashrc, which also does not exist unless you create it.  Of course as an evolved creature with a large braincase, you could modify *.profile* to use $HOME/scripts instead of $HOME/bin.  And if you are really clever, you can create a symbolic link between ~/bin and ~/script such that the scripts will executed properly when put in ~/scripts.

```
cd
mkdir bin
ln -s bin scripts

```

Logout and then log back in to execute the new .profile.

```
echo $PATH
```

To verify that the ~/scripts directory is in your path.

---

