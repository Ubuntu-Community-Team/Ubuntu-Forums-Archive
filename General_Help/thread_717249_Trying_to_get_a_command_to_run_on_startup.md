---
title: "Trying to get a command to run on startup"
date: 2008-03-06
forum: General Help
---

### Post by nemesis256 on 2008-03-06
I'm trying to get a command to run on boot, but it isn't working. I've tried many things, like adding it to the rc.local file, adding it to System > Preferences > Sessions. Just doesn't seem to work. Here's the command I have to use in the terminal to get it started. 

cd /var/jaxer/aptana 
sudo ./jaxermanager & 

So that's what I want to have startup every time I boot. How do I do it? 

Is there a way I can do this with a single line?  I have a feeling that would make it simpler.  for some reason when I try a single line, or if I go to the directory and remove the ./ on the second line, I get an error.  This seems to be the only way to get it started.

---

### Post by Whiffle on 2008-03-06
You shouldn't need the sudo.  

try something like 

/var/jaxer/aptana/jaxermanager &

---

### Post by nemesis256 on 2008-03-06
I've tried that, but like I said it generates an error when it's on one line.  I have no idea why, but it's very strange.  I assume you meant putting this in the sessions right?

---

### Post by Whiffle on 2008-03-06
I was thinking rc.local, which runs with root permissions.

---

### Post by nemesis256 on 2008-03-06
tried it, still won't work.  It still acts as if it gets the error when I put it directly in the terminal on one line.

When putting cd /var/jaxer/aptana in the rc.local file, does it even keep track of that for the command after it?  Or are all lines run as if the others don't exist?

---

### Post by Whiffle on 2008-03-06
It should keep track of it.  What happens when you do 

sudo /etc/rc.local

---

### Post by nemesis256 on 2008-03-06
Well this is annoying.  I booted without the command in the file, added it, ran it like you just mentioned, and it worked.  But then I reboot, and it acts as if it runs into the error when doing it on one line. hmm...

---

### Post by russo.mic on 2008-03-07
I'm pretty sure you don't need to put sudo, or CD or any of that stuff.
just type:

/var/jaxer/aptana/jaxermanager &

Good luck!

---

### Post by nemesis256 on 2008-03-07
I've tried that many times, but it won't work.  It "demands" to be run on two lines.  It's really strange.

---

### Post by nemesis256 on 2008-03-07
so I just found out about the pipeline symbol (|) in the command line.  Apparently it can be used to separate commands.  I tried doing the following but it didn't work:

cd /var/jaxer/aptana | sudo ./jaxermanager

It complains that the jaxermanager could not be found.  So it's obviously not even changing directory.  Why could this be happening?

---

### Post by nemesis256 on 2008-03-10
bump.  Still wondering about separating the command.

---

### Post by Whiffle on 2008-03-10
The pipe command lets you pipe the output of one command to another command-, which isn't what you want here.  You'd want to use either a ;  or && to put the commands together.

---

### Post by julian67 on 2008-03-10
> **nemesis256 said:**
> so I just found out about the pipeline symbol (|) in the command line.  Apparently it can be used to separate commands.  I tried doing the following but it didn't work:

cd /var/jaxer/aptana | sudo ./jaxermanager

It complains that the jaxermanager could not be found.  So it's obviously not even changing directory.  Why could this be happening?

pipe is not to separate commands, it's to pipe the output of one command into the next command so cd /var/jaxer/aptana | sudo ./jaxermanager actually is meaningless.

---

### Post by bodhi.zazen on 2008-03-10
I assume you are running a command that either is not on your path or can not track log or config files (thus you need to cd and internally log files are referanced by something like ./log_file)

At any rate,

Try adding this to rc.local :

```
cd /var/jaxer/aptana; ./jaxermanager &
```

sudo is not needed as rc.local is run as root (as one of the last boot scripts) when you boot.

you use ; to run two commands

command 1 && command 2 = and. Run command 2 if command 1 runs without errors.


command 1 || command 2 = or. Run command 2 if command 1 fails (error).

---

### Post by Oldsoldier2003 on 2008-03-10
> **nemesis256 said:**
> so I just found out about the pipeline symbol (|) in the command line.  Apparently it can be used to separate commands.  I tried doing the following but it didn't work:

cd /var/jaxer/aptana | sudo ./jaxermanager

It complains that the jaxermanager could not be found.  So it's obviously not even changing directory.  Why could this be happening?

cd /var/jaxer/aptana && sudo ./jaxermanager

---

### Post by nemesis256 on 2008-03-11
Well that's kinda strange.  I got the command with the semi-colon to run on startup, and it starts, but I think it hangs.  When I type in ps -aef to get the processes list, the jaxermanager has a time way above 00:00:00.  When I checked it it was 3 minutes and something, which was pretty much the time since the computer booted.  I assume using && instead of the semi-colon wouldn't make a difference.  Why could the process be hanging?

---

### Post by Foxray on 2008-03-11
You might want to try a bash wrapper script like below:

```

#!/bin/bash

cd /var/jaxer/aptana
sudo ./jaxermanager & 

```

then save it to a file like start_jaxermanager.sh

do a chmod +x start_jaxermanager.sh

then run it via rc.local, hope this helps

---

### Post by nemesis256 on 2008-03-12
I made a script like you mentioned, and it works when I run it myself.  But when I get it to run on startup, I get the same problem where the process is hanging.

I may be out of luck.

---

