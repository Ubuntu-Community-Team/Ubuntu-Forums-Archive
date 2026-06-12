---
title: "Auto Text Login -- How?"
date: 2007-04-04
forum: General Help
---

### Post by brentoboy on 2007-04-04
I have a computer that I would like to have automatically login at the text prompt as guest as soon as it is finished booting.

Then, I want it to run a command.

I have seen plenty of installation CDs automatically log in root at the text prompt, how do they do that?

Let me make perfectly clear what I DO NOT need an answer to:   I do not need to have GDM automatically log someone in to a graphical desktop.    I am asking specifically about loging in at the text prompt.

If you get my question, please advise.
If you need more info, here is exactly what I have setup and what I am trying to accomplish:

I have 2 computers (at least 2 that are relevant to the situation).  One is a new high power git-er-done box and the other is an old amd k6-233mhz bucket of bolts.

I recently discovered that if I enable xdmcp in the gdm login settings, and run a remote X session on the dino-box, I can get astonishing performance from my oversized paperweight.  Everything works at blazing speeds (except planet penguin racer), and the Goliath computer has no lag as a result.  It is like having two excellent computers (one just has a really dusty keyboard)

I have whittled the wimp computer down to just ubuntu-minimal and x-window-system-core, and I can start a remote x session by first logging in as guest (password "guest") which is an account local to the "wimp" computer, and has no connection to a user on the power station.

once logged in, I initiate a network X session with the following command:

X -query 192.168.2.234
(names have been changed to protect the innocent)

So, I am not at all concerned about the "security" of the wimpy box.   The guest account cant do much of anything anyway.  

I just want my wife (and the other people who use my computer room as a free for all computer lab) to be able to use the secondary box as a backup plan without having to login as guest all the time and remembering how to issue the command:
X -query 192.168.2.234

So, I want a way to (1) automatically login as guest after booting, and (2) issue a command immediately after login.  so that other users can just "use" and not worry about details.

Is there anyone with a quick fix for my dilemma?

---

### Post by pointone on 2007-04-04
For a general auto-login script, follow the instructions [here]("http://doc.gwos.org/index.php/Automatic_Login_No_Authentication").

In order to run a command on login, edit your $HOME/.bashrc; $HOME/.bash_profile or $HOME/.profile file (whichever it is).

Another possible solution (although untested) would be to tweak the autologin.c script as follows:

```
#include <stdlib.h> 

int main() { 
    system("login -f your_user_here");
    system("X -query 192.168.2.234");
    }
```

This would combine both the login and X initialization commands into one script, so no editing of the .bashrc or .bash_profile files would be necessary. Both methods should work equally well, though.

*Edit* -- On second thought, the second solution I posted would, in fact, run X as root. In theory, you would need to run the command:

```
su --command="X -query 192.168.2.234" your_user_here
```

It's probably safer just to go with the .bashrc / .bash_profile solution, though.

---

### Post by brentoboy on 2007-04-04
That looks like it will help.

but, I must admit I am a little hesitant to jump on their outline for making it all work because if all they wanted to do was auto login to x as a particular user, all they had to do what go into the gnome login settings (System > Administration > Login Window). and set it up to automatically login as a specific user.   I worry this site is probably doing things the hard way.

At first, I was thinking that those directions were just for auto-login to X -- but there is enough info there to auto login at a text prompt, so I'll mess around with the directions they gave.

Thanks for the help.

---

### Post by brentoboy on 2007-04-04
ok,

so I edited .bashrc
and added X -query 192...... to the end of it.

logged out and logged back in and it fired up my remote x session.

That is good, I'm 50% of the way there.

I'll let you know how the rest turns out as soon as I get it working.

---

### Post by pointone on 2007-04-04
No need to worry--the main idea to grasp from the page is how to edit your inittab or ttyX files depending on which version of Ubuntu you're running. The code itself can be adapted to run anything on login.

Another solution you may like would be to edit the autologin.c file as follows:

```
#include <stdlib.h> 

int main() { 
    system("/path/to/some/script");
```

Now, create a script as follows:

```
#! /bin/bash

su --command="X -query 192.168.2.234" your_user_here
... and any other commands you want!
```

This will start X as the specified user without actually logging into the system.

---

### Post by brentoboy on 2007-04-04
Looks good.

Rather than installing a compiler and building my own little login app, I went with the second option on the page.

```

sudo apt-get install mingetty
sudo nano /etc/inittab

```

find the line that says 
```

1:2345:respawn:/sbin/getty 38400 tty1

```
and change it to be 
```

1:2345:respawn:/sbin/getty -n -l "/sbin/mingetty --autologin=guest" 38400 tty1

```

this caused issues, so I changed it to
```

1:2345:respawn:/sbin/getty -n -l /sbin/autologin 38400 tty1

```

and created a shell script named /sbin/autologin that looked like this

```

#!/bin/sh
/sbin/mingetty --autologin=guest

```

it still it didnt work, so I tried to roll my own little autologin as outlined in the rest of the help page
apt-getting gcc wasn't sufficient, I had to get build-essential in order to get it to compile.

once it did, I just put the resulting binary there in /sbin/autologin where I had placed the script using this command:
sudo cp autologin /sbin/autologin

and........
no joy  (yet)

---

### Post by lapsey on 2007-04-04
I tried mingetty and it was painful and silly.

Here is how i set up headless login on my dapper box. Works every time.

No other software was required: this is the first thing I do on a fresh server install. I don't know about build-essential, but as i understand this will only work with gcc-3.4 and above (as available with dapper) 

make, compile and move an autologin script

```

echo "int main() { execlp( \"login\", \"login\", \"-f\", \"USERNAMEGOESHERE\", 0); }
" > autologin.c ; 
sudo apt-get -y install gcc-3.4
sudo gcc-3.4 -o autologin autologin.c
sudo mv autologin /usr/local/sbin
rm autologin.c ; sudo apt-get -y remove gcc-3.4

```

then i edit inittab: ( sudo nano /etc/inittab )

change 
1:2345:respawn:/sbin/getty 38400 tty1
to
1:2345:respawn:/sbin/getty **-n -l /usr/local/sbin/autologin** 38400 tty1


now it will automatically login us USERNAMEGOESHERE :)

for commands to run on login, i add them to the end of .bashrc

```

......
#    export MANPATH
#fi


if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
      vncserver :1 -geometry 800x600 -depth 24
fi

```


that's it!

---

### Post by brentoboy on 2007-04-04
when I change "-f" to \"-f\"
in the code you posted there...

it works!

cool, thanks

---

### Post by lapsey on 2007-04-04
whoops, sorry about that. changed

---

### Post by jrickard on 2007-12-19
I need to do this.  But we don't have inittab anymore.  

I need to automatically login as a user on a headless, minimal PC after bootup.  This would be perfect.  But it's a little dated.  Gutsy doesn't have an inittab

Help??

Jack Rickard

---

