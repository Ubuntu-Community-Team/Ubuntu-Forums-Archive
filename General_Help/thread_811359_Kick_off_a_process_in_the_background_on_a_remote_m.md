---
title: "Kick off a process in the background on a remote machine"
date: 2008-05-29
forum: General Help
---

### Post by Anonymouslemming on 2008-05-29
Hi all,

I need to run a script and background it on a load of our servers at work. I've got SSH keys setup between the boxes, so I can automatically login.

If I do something like 
for i in `cat boxes`; do ssh $i 'ls ; exit'`; done
that works fine - it connects to each box, does the ls and exits. 

The problem is when I try and run my script - it doesn't exit from the machine, so it never goes to run the script on the next machine. I just need to background each of these and leave them running for a few days.

At the moment, I've got the following:

for i in `cat boxes`; do 
     ssh $i 'echo "Starting script"; $HOME/script.sh ; echo "Exiting"; exit'; 
done 

What I see on the remote machine is 
Starting script
Exiting
...and there it sits...
It never exits the first machine, so it never moves onto the second.

If I do this manually, the exit works:
ssh <machine>
$HOME/script.sh
exit

That puts me back on my main server.

Any ideas how I could kick this off remotely would be much appreciated.

---

