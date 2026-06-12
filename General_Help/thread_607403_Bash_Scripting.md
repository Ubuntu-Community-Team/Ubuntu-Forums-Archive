---
title: "Bash Scripting"
date: 2007-11-08
forum: General Help
---

### Post by PreviousN on 2007-11-08
Hi there fellow Ubunters',

I want to make a bash script for ssh port forwarding using variables. Here's what I want it to do. 

Example: /bin/sshforward

Upon running it will ask:

"Hi, what username are you using?" nobody
"what server/hostname are you connecting to?" nards.domain.com
"what port do you want to forward to?" 1337
"what port do you want to forward from?"5900

And then It'll output on the screen this (which should be the proper ssh port forwarding infos):
ssh -L 1337:192.168.2.141:5900 [email]nobody@nards.domain.com[/email]

"do you want to continue? y/n?"
if you put yes it'll enter the command and ask you for your remote password. 

Problem is, I don't know where to start with Bash scripting. I've only done a little /etc/rc.local modifying. Help please? I want to write this offline. Know of any good offline manuals? Or, if one of you think its easy enough...could you write it? I dont' mind doing it, but I am indeed a newb. Thx.

---

### Post by ptn107 on 2007-11-09
Personally i've found some useful bash tidbits on the web, but nothing beats 'Classic Shell Scripting' and 'Bash Cookbook' by Oriley publishing.

save everything below to a file and make it executable, then type  *bash scriptname* on the command line to execute it.  code is also in [http://pastebin.com/m1867a0eb](http://pastebin.com/m1867a0eb)

*The ip address 192.168.2.141 is used in your example, but will vary from user to user.  You may want to ask the user the ip address in a question [as in below].



#!/bin/bash

_CONTINUE ()
{
#Ask to continue
read -p "Do you want to continue (y/n)?: " CHOICE
if [ "$CHOICE" = "y" ]
     then
          ssh -L $TOPORT:$IP:$FROMPORT $HOSTNAME
elif [ "$CHOICE" = "n" ]
     then
           echo "You have chosen not to continue.  Exiting..."
           exit 1
else
     echo "Invalid selection!  Try again."
     _CONTINUE
fi
}

#Ask questions
read -p "Hi, what username are you using?: " USERNAME
read -p "What server/hostname are you connecting to?: " HOSTNAME
read -p "IP Address?: " IP
read -p "What port do you want to forward to?: " TOPORT
read -p "What port do you want to forward from?: " FROMPORT

#Output command for user to check
echo "ssh -L $TOPORT:$IP:$FROMPORT $HOSTNAME"

#Call "_CONTINUE" function from above.
_CONTINUE

---

### Post by devilears on 2007-11-09
this should get you going:

#!/bin/bash
echo "Hi, what username are you using?"
 read username
echo "what server/hostname are you connecting to?"
 read server
echo "what port do you want to forward to?"
 read port1
echo "what port do you want to forward from?"
 read port2
echo "ssh -L $port1:192.168.2.141:$port2 $server"
echo "do you want to continue? y/n?"
read ans
echo ""
echo ""

if [ "$ans" = "n" ]; then
   echo "Goodbye."
   exit 0
fi

if [ "$ans" = "y" ]; then
   echo "enter password please"
   read password
fi

---

### Post by mdebusk on 2007-11-09
> **PreviousN said:**
> 
"Hi, what username are you using?" nobody
"what server/hostname are you connecting to?" nards.domain.com
"what port do you want to forward to?" 1337
"what port do you want to forward from?"5900


It seems to me you really aren't saving yourself any work. You're still typing the full command line, but you're doing ti a piece at a time instead of all at once.

Would it make more sense to set up some bash aliases, or a simple menu using a case statement?

---

### Post by PreviousN on 2007-11-09
Wow. Thanks for all the helpful responses! :guitar:

The reason I want to do it this way is to make forwarding via ssh user-friendly for people like my girlfriend- who I want to stream music to, but don't want to make any permanent holes in my firewall. 

Also, I guess I'm a noob, but it seems that whenever I am at a party and drunk I want to stream music to my friends house, but I always F*c* up the syntax. With this, its REALLY easy. 

Anyways, I'll likely look at this and see if I can improve on it. Like make it a program for ssh:

"hi, what do you want to do?" Forward port? Remote Administration? Set up a Proxy? Forward X session?

And you choose and it then asks you all the other info. 

Thanks again guys!

---

