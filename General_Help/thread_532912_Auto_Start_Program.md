---
title: "Auto Start Program"
date: 2007-08-23
forum: General Help
---

### Post by mattc908 on 2007-08-23
Okay so I run Ubuntu Feisty Fawn Server, I ssh into because I use a different computer to access it. 

I Set up a ventrilo server and was wondering if anyone could help me auto run the following codes, I dont use GNOME or any of the other GUI's just the nice text based service.

After it goes through a restart I start by ssh'in into it. Than I use a dyndns, so I have it update, with the following code:
sudo sh /etc/ppp/ip-up.d/dyndns_update

than sense Im using a remote host, I screen into it by typing (You have to screen in because otherwise when I quit Terminal (OSX) it will shut down the ventril)
screen

Than I access the directory I stored it in (yes I know there are two L's)
cd ventrillo/

than I start the vent server with:
./ventrilo_srv


Now is there anyway with any code I can have it everytime it restarts to auto run that, or make it so I can type just a tiny thing of code and auto run it?

---

### Post by mattc908 on 2007-08-24
Bump?

---

### Post by mattc908 on 2007-08-25
No one on this forum has any clue?!

---

### Post by revford on 2007-08-25
You could try adding the commands to your /etc/rc.local file.

---

### Post by mattc908 on 2007-08-25
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
exit 0


So do I just  add the commands I want in order? (before exit 0)

---

### Post by revford on 2007-08-26
Sorry, I should have been more specific, Yes.

This is all based on Slackware knowledge, but I expect Ubuntu to work the same.  I'm sure an Ubuntu expert can jump in and tell us is we're doing something bad.

Try something like:

```


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Update DynDNS
/bin/sh /etc/ppp/ip-up.d/dyndns_update

exit 0


```

As to the other part, I'd write a simple script called startvent.sh, that changed into the right directory then runs the apps, something like this:

```

#!/bin/sh

# Start the Vent Server
cd /where/the/app/is/ventrillo/
./ventrilo_srv


```

Then add that script to your rc.local, something like this:


```


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Update DynDNS
/bin/sh /etc/ppp/ip-up.d/dyndns_update

# Start the Vent Server
/bin/sh /where/the/app/is/ventrillo/startvent.sh

exit 0


```

I don't know what vent is but I had to do something like this when I used DynDNS a few years ago.

---

### Post by mattc908 on 2007-08-26
Wow thanks for all the help! One concern (im very new to linux) because I ssh into it, as soon as I quit my program (Terminal (mac OSX)) it will stop running ventrilo. But I havnt tried doing what you said yet but will it also quit when I quit terminal thats why I added the program screen to it. So i type screen, and itll act like I was actully using the physical server instead of SSH.

and

cd /where/the/app/is/ventrillo/

what do you mean were the app is, its just in the directory labeled ventrillo, like if I did it all manually I would just type cd ventrillo/ than ./ventrilo_srv

---

### Post by revford on 2007-08-26
When running from the rc.local you don't have to worry about things stopping when you log in or out.

If you want to  keep things running when you log out of your ssh session, you need to use a tool called nohup, like this:

```


cd ventrillo/
nohup ./ventrilo_srv &


```

Where I said /where/the/app/is/ventrillo/ I meant add the full path of the ventrillo directory.

To find this, try using pwd, like this:

```


cd ventrillo/
pwd


```

It should output the full path you'll need for the directions I gave above.  It will be something like:

```


/home/mattc908/ventrillo


```

---

### Post by mattc908 on 2007-08-26
(funny it actully is home/mattc908/ventrillo/)

okay so this is how it looks: 

For startvent.sh
```
 #!/bin/sh

# Start the Vent Server
cd home/mattc908/ventrillo/
./ventrilo_srv#!/bin/sh

```

For rc.local
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Update DynDNS
/bin/sh /etc/ppp/ip-up.d/dyndns_update

# Start the Vent Server
/bin/sh /home/mattc908/ventrillo/startvent.sh
exit 0


```

Yet still wont auto start the server.

---

### Post by revford on 2007-08-26
But the DynDNS worked?

Take the extra hash-bash-slash off the end of startvent.sh, like this:

```

#!/bin/sh

# Start the Vent Server
cd home/mattc908/ventrillo/
./ventrilo_srv

```

If it's still not working there, check the log files to see if it tells you anying during startup.  The files to check are:

/var/log/messages
/var/log/syslog

You can search for things about Ventrillo with something like this:

```


cat /var/log/messages /var/log/syslog | grep ventr


```

---

### Post by mattc908 on 2007-08-26
mattc908@ventserv:~$ /var/log/messages
-bash: /var/log/messages: Permission denied
mattc908@ventserv:~$ /var/log/syslog
-bash: /var/log/syslog: Permission denied

Not exactly sure if DynDns worked because it doesnt need to be updated everytime, but its nice to have it auto update because it will change every so often.

---

### Post by revford on 2007-08-27
You have to use something to read those log files, they are text logs so try something like:

```

cat /var/log/messages

```

And:

```

cat /var/log/syslog

```

The code I gave you before will search those files and give you the results of aything containing the string 'ventr', that should return any error messages about your Ventrillo server.  Just copy it to a terminal and if needs be post back with the results.

---

### Post by mattc908 on 2007-08-27
When physicallly starting up not SSH, I got this error at start:

```

/etc/rc.local:13:ventrilo_srv:notfound

```

---

### Post by revford on 2007-08-27
When you log in to start the server, do you type:

```

cd ventrillo
./ventrilo_srv

```

Or:


```

cd ventrillo
./ventrillo_srv

```

I think it's the second one and that is why it's failed, try adding the second 'l' to the startvent.sh script and see if that works.

---

### Post by mattc908 on 2007-08-27
I type the first with 1 L, the Directory has 2 but the start command has 1 dont ask why =p

---

### Post by revford on 2007-08-27
Fair enough, I thought I'd spotted an easy fix for the problem there.  :)

Okay, there must be a reason it can't see the ventrilo_srv file, can you please try the following?

```
ls -lh /home/mattc908/ventrillo/ventrilo_srv
```

and:

```

cd ventrillo/
pwd

```

I'm sure there is something really simple here we are missing.

---

### Post by mattc908 on 2007-08-28
ls -lh /home/mattc908/ventrillo/ventrilo_srv
```

-rwxr-x--- 1 mattc908 mattc908 310K 2005-09-07 16:58 /home/mattc908/ventrillo/ventrilo_srv

```

cd ventrillo/
pwd
```

/home/mattc908/ventrillo

```

---

### Post by revford on 2007-08-28
Alright, now I'm stumped.  :(

rc.local is telling us ventrilo_srv isn't in the directory /home/mattc908/ventrillo where we know it is.

It's got to be a typo somewhere.

Can you copy/paste the rc.local and startvent.sh scripts here again so we can take another look at exactly what we have there now?

---

### Post by mattc908 on 2007-08-28
rc.local:
 
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Update DynDNS
/bin/sh /etc/ppp/ip-up.d/dyndns_update

# Start the Vent Server
/bin/sh /home/mattc908/ventrillo/startvent.sh

exit 0


```

startvent.sh:

```

#!/bin/sh

# Start the Vent Server
cd home/mattc908/ventrillo
./ventrilo_srv


```

---

### Post by weblordpepe on 2007-08-28
Last time I looked, you had to decide on a runlevel that you wanted, and then use that /etc/init.d/something script to add a .sh file as a service.

And you had to put a funny number infront of it. Here read through this thread (right through) cos it shows how to create a script and have it run at startup [http://ubuntuforums.org/showthread.php?t=507414]("http://ubuntuforums.org/showthread.php?t=507414")

---

### Post by revford on 2007-08-29
I see it now, all sorted!  There is a missing "/" in startvent.sh.

startvent.sh:
```

#!/bin/sh

# Start the Vent Server
cd /home/mattc908/ventrillo
./ventrilo_srv

```

---

### Post by mattc908 on 2007-08-29
Hold on one sec....

=( 
waited 5 mins nothing....... Okay so I have the cavalry comming to our aid, I have a friend that helped google auto start there servers, if anyone would know he would. So Ill let you know what he says! I'll mess around some more and see what happens!
As of now code looks like this:

/etc/rc.local
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# Update DynDNS
/bin/sh /etc/ppp/ip-up.d/dyndns_update

# Start the Vent Server
/bin/sh /home/mattc908/ventrillo/startvent.sh

exit 0                         


```

startvent.sh
```

#!/bin/sh

# Start the Vent Server
cd /home/mattc908/ventrillo
./ventrilo_srv


```

---

### Post by revford on 2007-08-30
That looks right to me now, not sure why it's still failing.  Have you checked the logs again?

**cat /var/log/messages/ /var/log/syslog | grep ventr**

Unless I'm falling down a gap between my knowledge of BSD/Slack and something Ubuntu does differently.

Hopefully your friend can tell us and educate me too.

---

### Post by mattc908 on 2007-08-30
```
 
/bin/sh: Can't open /home/mattc908/ventrillo/startvent.sh       [fail]

```

---

### Post by fvu on 2007-08-31
Does startvent.sh have execute permissions?  Otherwise do:

```
chmod a+x startvent.sh
```

And for ease of code you might consider to let the shell find out what's the script directory instead of cd'ing:

startvent.sh
```
#!/bin/sh

# cd to script dir
cd "$(dirname "$(which "$0")")"

# Start the Vent Server
./ventrilo_srv
```

See also: [http://www.fvue.nl/wiki/Cd_to_script-directory](http://www.fvue.nl/wiki/Cd_to_script-directory)

Freddy Vulto
[http://fvue.nl](http://fvue.nl)

---

### Post by mattc908 on 2007-08-31
```

mattc908@ventserv:~$ chmod a+x startvent.sh
chmod: changing permissions of `startvent.sh': Operation not permitted

```

---

### Post by revford on 2007-09-01
In that case, try:

```
sudo chown mattc908.mattc908 startvent.sh
```

Then do the:

```
chmod a+x startvent.sh
```

It was telling you the permissions were set to not allow you to make changes or run the script.  These new command give ownership of the file to you, then a+x means anyone (a) can (+) execute (x) the script.

---

### Post by mattc908 on 2007-09-01
Still Getting:

```

/bin/sh: Can't open /home/mattc908/ventrillo/startvent.sh       [fail]

``` 

I enter: sudo chown mattc908.mattc908 startvent.sh asks for a password
I enter: chmod a+x startvent.sh  doesnt say anyhting when I enter it...

---

### Post by revford on 2007-09-01
That's right, its saying you don't have permission to run startvent.sh, so you need to change the permissions.

Can you try:

```
ls -lh /home/mattc908/ventrillo/startvent.sh
```

This will tell us who the machine thinks owns the file and what the permissions on it are.

---

### Post by mattc908 on 2007-09-01
Hmmm well I think I may have found a big problem ..... and a possible solution

```

mattc908@ventserv:~$ ls -lh /home/mattc908/ventrillo/startvent.sh
ls: /home/mattc908/ventrillo/startvent.sh: No such file or directory

```

```

mattc908@ventserv:~$ pwd startvent.sh
/home/mattc908

```

should I make startvent.sh in ventrillo directory? or ls -lh /home/mattc908/ventrillo/startvent.sh into:
```

ls -lh /home/mattc908/startvent.sh 

```

For:
ls -lh /home/mattc908/startvent.sh
```

-rwxr-xr-x 1 mattc908 mattc908 78 2007-08-29 12:21 /home/mattc908/startvent.sh

```

---

### Post by revford on 2007-09-02
Okay, we're getting there.

Move the startvent.sh into the ventrillo directory and I think we have it.

```

cd
mv startvent.sh ventrillo/
/
```

Then reboot to give it a try.

---

### Post by mattc908 on 2007-09-02
Hoorah!!! We finally solved it! Thanks man, great work Revford! Thanks for sticking with it.
Funny thing is my friend just got back from LA today to help and we solved it!

---

### Post by revford on 2007-09-02
Magic, I'm just sorry it took so long.

It looks like we had it sorted ages ago, but got lost over where the script was.  :)

---

### Post by mattc908 on 2007-09-02
Haha im wondering to go even a step further, is there away to make the server when it loses internet connection to restart it self?

---

### Post by revford on 2007-09-02
Well, yes, but no simple way.

As I don't even know what Ventrillo is or what it does, I'm not sure where to start on that one.

Basically you'd run a script using cron that tries to connect to the server every hour, if it fails it would kill any existing instances of Ventrillo then run startvent.sh again.

---

### Post by mattc908 on 2007-09-02
Ummm Ventrilo Is a client that is like "Skype" if you know what that is if not it's a big chat room that a bunch of people can enter and just talk, its a room thats up for ever and people join, usually used for online gaming, its easier than typing with friends.

---

### Post by revford on 2007-09-03
Sorry man, that's a bit beyond me now.

But your Google Man, he should be able to sort it for you.

---

