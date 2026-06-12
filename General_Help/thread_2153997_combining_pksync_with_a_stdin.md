---
title: "combining pksync with a stdin"
date: 2013-06-13
forum: General Help
---

### Post by thedawg on 2013-06-13
Hallo everyone, 

I'm having some trouble with the pkgsync.
Pkgsync is started everyday through cron.daily and due to some new libraries, pkgsync is asking for a request if these packages can be trusted. 
Now this is all happening in the background and on ca. 50 Computers, so I can't check every morning if the pkgsync is waiting for an input. 

Now I want to intercept the question with a "grep yes < randomfile" but I'm not sure where and exactly and how to trigger the "grep yes < rndmfile" command.

I'm working with Kubuntu 12.04-64bit LST. 

I hope someone can help me, or has some creative idea :) 

greetings 
the dawg

---

### Post by HiImTye on 2013-06-13
you can add an infinite while loop until either a file exists (faster) or contains data, such as
```
while :; do
 sleep 1
 if [ -f "/path/to/file" ]; then
  ...
  break
 fi
done
```
or, for contents
```
while :; do
 sleep 1
 yes=$(grep yes "/path/to/file")
 if [ -n "$yes" ]; then
  ...
  break
 fi
done
```
unless you're looking for some way to interact with the program, in which case, I'm not sure

edit: if that's the case, it's only the what in the
```
...
```that changes, and you're still part way there
edit 2: some breaks help
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by thedawg on 2013-06-13
no I don't want to interact, it's supposed to happen without me doing a thing 

btw. I'll try it out :)

---

### Post by thedawg on 2013-06-13
So this is my "test-script" (I'm still not very good with coding in linux, or coding at all) 

:" 
#! /bin/sh


export PATH=/usr/local/sbin:/usr/sbin:/usr/bin:/sbin:/bin

while :;

. /usr/sbin/pkgsync
do
 sleep 1
yes=$(grep yes /etc/pkgsync/stdinputpkg)
 if [ -n "$yes" ]; then
< 0 $yes
fi
done "

but and pkgsync is still stopping with these lines:
"
Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  somepackage

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":   "

Don't know, maybe probably done something wrong trying to create the stdin ?

---

### Post by steeldriver on 2013-06-13
I don't know anything about pkgsync and I don't understand what you mean by "grep yes < randomfile", but in general the way to handle this kind of interactive prompting is either

[LIST=1]
[*]find a program setting that tell pgksync to assume the answer "yes" to all such questions - that may be a command line switch to pkgsync itself, or it may be a config setting or environment variable that affects the underlying package management command (for example, apt-get has a -y or --assume-yes flag) 
[*]use the 'expect' program to script the interaction and send a literal "yes" response when it receives the query prompt 
[/LIST]

---

### Post by HiImTye on 2013-06-13
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
yeah, you're going to need to either figure out the interaction method; or how to bypass interaction, and use pkgsync in the ... section

---

### Post by thedawg on 2013-06-14
I'm trying to make the interaction with tcl expect, because it seems to be the easiest solution,... yeah but expect is giving me even more problems, since I've never worked with it -_-
This is so frustrating :D

---

### Post by steeldriver on 2013-06-14
DISCLAIMER: I know just about enough 'expect' to be dangerous - but no more

DISCLAIMER 2: I am in no way endorsing the automatic install of untrusted packages

What have you tried so far? if that's the *only* interaction that you need to intercept, then something like this might work

```

#!/usr/bin/expect -f

set prog /usr/bin/pkgsync
set que "To continue, enter \"Yes\"; to abort, enter \"No\":"
set ans "Yes"

spawn $prog
expect { 
  "$que" 
  { 
    send "$ans\r"
    exp_continue
  }
}

```

---

### Post by thedawg on 2013-06-14
Yeah you are right, the automatic install of untrusted packages is not  the right way, but there is nothing in my pkgsync list, that I haven't  wrote into it.


I just made 1:1 copy of the code, but didn't really work, got this:

"spawn: command not found
couldn't read file "{": no such file or directory
: command not found
The program 'send' can be found in the following packages:
 * mailutils-mh
 * nmh
Try: apt-get install <selected package>
exp_continue: command not found
-su: /etc/cron.daily/pkg-test: line 15: syntax error near unexpected token `}'
-su: /etc/cron.daily/pkg-test: line 15: `}' "

but still thanks for helping :)

---

### Post by steeldriver on 2013-06-14
It looks like you're trying to call expect from inside a shell script, from inside a cron job - BOTH of those additional levels of indirection can cause issues, I suggest you get it working as a simple terminal command first and then worry about how to call it from cron

If you don't want to break out the expect part in its own #!/usr/bin/expect shell, then afaik you have 2 choices - you can either use 'expect -c " ... "' and squeeze your entire expect script in as a command string, or you can use a shell 'here document', however mixing expect and shell syntax is tricky as both the parent shell and the Tcl (expect) shell try to expand things - for example when you're trying to escape double quotes you often need one more \ than you think e.g.

```

#!/bin/sh

export prog=./fakepkgsync
export que="To continue, enter \\\"Yes\\\"; to abort, enter \\\"No\\\":"
export ans="Yes"

/usr/bin/expect <<EOF

spawn $prog
expect {
  "$que"
  {
    send "$ans\r"
    exp_continue
  }
}
EOF

```

I tested that with a 'fakepkgsync' as follows

```

#!/bin/bash

packages=(somepackage otherpackage yetanotherpackage)

for package in ${packages[@]}; do

echo "Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

"$package"

Do you want to ignore this warning and proceed anyway?"

read -p "To continue, enter \"Yes\"; to abort, enter \"No\":  " ans

case "$ans" in
    Yes) echo -e "\n\tfakepkgsync: installing $package\n\n"
    ;;
    No) echo -e "\n\tfakepkgsync: skipping $package\n\n"
    ;;
esac

done

```

```

$ ./test-script
spawn ./fakepkgsync
Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

somepackage

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":  Yes

        fakepkgsync: installing somepackage


Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

otherpackage

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":  Yes

        fakepkgsync: installing otherpackage


Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

yetanotherpackage

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No":  Yes

        fakepkgsync: installing yetanotherpackage


```

---

### Post by HiImTye on 2013-06-14
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
this might be worth reading
[http://xmodulo.com/2012/11/how-to-install-software-packages-in-non-interactive-batch-mode.html](http://xmodulo.com/2012/11/how-to-install-software-packages-in-non-interactive-batch-mode.html)
I've seen pkgsync scripts using the shell variable

---

### Post by steeldriver on 2013-06-14
agreed - if it's using aptitude under the hood then investigating if it's possible to use the  Aptitude::CmdLine::Ignore-Trust-Violations (?) or even Aptitude::CmdLine::Assume-Yes options would almost certainly be less painful

---

### Post by thedawg on 2013-06-18
Yeah gotta say, expect really looks tricky to me, especially because I'm still new to Linux, just know my way around in the shell, but I gotta someday I gotta solve the problem^^ 
[TABLE]
[TR]
[TD="class: text"][/TD]
[/TR]
[/TABLE]

Geniues, didn't see we've reached page 2, so aptitude could solve this also, sounds interesting

---

### Post by thedawg on 2013-06-26
Hahaa, I got it working with aptitude. 
I edited the pkgsync script, so that it would "Assume-Yes" and "Allow-untrusted" 

/usr/sbin/pkgsync:
"        APTITUDE_ARGS="--allow-untrusted -y  -q -o Dpkg::Options::=--force-confdef -o Dpkg::Options::=--force-confold"
        GLOB_STYLE="aptitude"
"

Thanks for the help guys.

---

