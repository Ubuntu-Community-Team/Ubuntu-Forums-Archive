---
title: "Shell Script errors"
date: 2008-06-17
forum: General Help
---

### Post by Ryan450 on 2008-06-17
Hey guys,

trying to start a Q2 dedicated server on my linux server. I wrote a shell script to start the server up, but unfortuantely the script spews out a bunch of errors and I just dont understand them. Below is the script followed by the error output.

```

// ********************** START OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
// FILENAME : /home/quake2/start-airrocket-r1q2-server.sh

#!/bin/sh
ip="CHANGEME"
port="27910"
name="r1q2"
q2dir="/home/quake2/quake2/"

echo running server $name on $ip : $port

cd $q2dir
screen -A -m -d -S $name ./r1q2ded-old +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +exec r1q2srv.cfg +map q2dm1 &



// ********************** END OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************

```

```

start-airrocket-r1q2-server.sh: 1: //: Permission denied
start-airrocket-r1q2-server.sh: 2: //: Permission denied
start-airrocket-r1q2-server.sh: 3: 
: not found
start-airrocket-r1q2-server.sh: 9: 
: not found
start-airrocket-r1q2-server.sh: 11: 
: not found
cd: 12: can't cd to /home/quake2/quake2/

start-airrocket-r1q2-server.sh: 13: 
: not found
start-airrocket-r1q2-server.sh: 14: 
: not found
start-airrocket-r1q2-server.sh: 15: 
: not found
start-airrocket-r1q2-server.sh: 16: 
: not found
start-airrocket-r1q2-server.sh: 17: //: Permission denied
start-airrocket-r1q2-server.sh: 18: 
: not found


```

---

### Post by mike2357 on 2008-06-17
I suggest you change the following:

1.  Change the // (comment indicator) to a #  (pound sign) on the very first character of each comment line.
2.  I believe that the #!/bin/sh has to be on the very first line.

If these don't work, re-post with whatever error messages you are getting.

---

### Post by Ryan450 on 2008-06-17
> **mike2357 said:**
> I suggest you change the following:

1.  Change the // (comment indicator) to a #  (pound sign) on the very first character of each comment line.
2.  I believe that the #!/bin/sh has to be on the very first line.

If these don't work, re-post with whatever error messages you are getting.

Alright I made the changes, your absolutely right I completely forgot about that. (too much java coding).

now this is the error that I get. 

```
-bash: ./start-airrocket-r1q2-server.sh: /bin/sh^M: bad interpreter: No such file or directory

```

thing is that I do have that shell installed, and when I type /bin/sh I get the new shell.

---

### Post by mike2357 on 2008-06-17
I suspect something on the very first line of the script is not quite right.  Could you please re-post the contents of the script?

---

### Post by Ryan450 on 2008-06-17
> **mike2357 said:**
> I suspect something on the very first line of the script is not quite right.  Could you please re-post the contents of the script?

```

#!/bin/sh
# ********************** START OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
# FILENAME : /home/quake2/start-airrocket-r1q2-server.sh

ip="CHANGEME"
port="27910"
name="r1q2"
q2dir="/home/quake2/quake2/"

echo running server $name on $ip : $port

cd $q2dir
screen -A -m -d -S $name ./r1q2ded-old +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +exec r1q2srv.cfg +map q2dm1 &



# ********************** END OF SHELLSCRIPT TO START THE R1Q2 SERVER **********************
```

---

### Post by mike2357 on 2008-06-17
I copied your entire script and ran it (I changed the value of q2dir and commented out the call to screen) and it worked fine.

I still think there's a problem on the first line of your script, such as an unprintable character right after the #!/bin/sh.  When I changed #!/bin/sh to #!/bin/junksh I got the same error message you got.  So I suggest deleting the entire line and then typing it back in.  It also could be that the text editor you are using it putting a CTRL-M at the end of the line.

---

### Post by lxevolution on 2008-06-17
Try this:

Make sure that the q2dir entry points to a correct quake2 directory:

```

#!/bin/sh

ip="127.0.0.1"
port="27910"
name="r1q2"
q2dir="**~/quake2/**"

echo running server $name on $ip : $port

cd $q2dir
screen -A -m -d -S $name ./r1q2ded-old +set dedicated 1 +set ip $ip +set port $port +exec q2srv.cfg +exec r1q2srv.cfg +map q2dm1 &

```

Change your file permissions:

```
chmod +x start-airrocket-r1q2-server.sh
```

Run the script

```
./start-airrocket-r1q2-server.sh
```

---

### Post by Ryan450 on 2008-06-17
Alright I rewrote the entire script top to bottom, and while i dont get any more errors from the shell. my script does absolutely nothing.

the screen doesnt get created and the server doesnt launch. no output back except from the echo command I put in. 

any ideas?

---

### Post by mike2357 on 2008-06-17
Well, I guess that's progress of a sort (although a very small sort).

At this point, I'm out of my league.  I don't have any experience with the "screen" command.  Maybe someone else can help.

Good luck.

---

