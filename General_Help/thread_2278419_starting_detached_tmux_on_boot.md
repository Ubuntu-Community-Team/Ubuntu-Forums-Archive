---
title: "starting detached tmux on boot"
date: 2015-05-16
forum: General Help
---

### Post by strange on 2015-05-16
anyone have any ideas on how i could start a detached tmux session on boot as user "strange" my tmux config already opens the applications i want to run in it im just struggling to find how i can start it on boot.

any help would be greatly appreciated

ubuntu mate 14.04 

/strange

---

### Post by Lars Noodén on 2015-05-16
You could launch it from rc.local and use su to run it as a particular user.  Below starts a new session with the name of 'foobar', detached from the current terminal, running the script 'net-dhcp' and setting the remain-on-exit flag.  

```

/usr/bin/tmux new-session -s foobar -d  /usr/local/sbin/net-dhcp \; set -t foobar remain-on-exit on'

```

I use that one to run the 'net-dhcp' script in the background automatically on boot yet save the output for me to review.  If you drop the command, then it would just run the login shell:

```

/usr/bin/tmux new-session -s foobar -d;

```

Then later you can attach to it.

```

tmux a -t foobar

```

---

### Post by strange on 2015-05-16
how does one add something to rc.local?

---

### Post by Lars Noodén on 2015-05-16
/etc/rc.local is a script that runs about last during booting the system.

You can edit it with your favorite editor or with nano, if nano is your favorite:

```

sudoedit /etc/rc.local

```

or if you do not have $EDITOR already set in your environment:

```

EDITOR=/usr/bin/gedit *sudoedit* /etc/rc.local

```

---

### Post by Lars Noodén on 2015-05-16
Since the script /etc/rc.local is run as root you will need to use [su](http://manpages.ubuntu.com/manpages/trusty/en/man1/su.1.html) to run as another user, if you don't want it as root.  

```

/bin/su -l strange -c "/usr/bin/tmux new-session -s foobar -d"

```

---

### Post by strange on 2015-05-16
strange@universe:~$ cat torrent 
tmux -2u new -n rT-PS -s rtorrent "/home/strange/.rtorrent/start; exec bash"
strange@universe:~$ cat /etc/rc.local 
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

/bin/su -l strange -c "/usr/bin/tmux new-session -s rT-PS -d /home/strange/torrent \; set -t rT-PS remain-on-exit on'
exit 0
strange@universe:~$ 

it doesnt seem to work :(

---

### Post by Lars Noodén on 2015-05-16
Make sure the quotes match with su, if you start with a double quote, end with a double quote.  

If you just want it to run bash, which is your login shell by default, you do not need a script (aside from rc.local) to be involved:

```

/bin/su -l strange -c "/usr/bin/tmux new-session -s rT-PS -d  \; set -t rT-PS remain-on-exit on"

```

If you want the tmux session to go away after bash exits, then you can take away the 'set' part, too.

```

/bin/su -l strange -c "/usr/bin/tmux new-session -s rT-PS -d"

```

---

### Post by strange on 2015-05-16
in the first example how does it know to open the torrent script?

---

### Post by Lars Noodén on 2015-05-16
> **strange said:**
> in the first example how does it know to open the torrent script?

It doesn't, but the output from 'cat' in your post above indicates that the torrent script needs work, but that's after you get the tmux part going.  What do you want tmux to run for you?

---

### Post by strange on 2015-05-16
i want tmux to run the torrent script so it is always just there and i can attach to it when i want to do something but it should be running at all times

---

### Post by Lars Noodén on 2015-05-16
> **strange said:**
> i want tmux to run the torrent script so it is always just there and i can attach to it when i want to do something but it should be running at all times

I think this should do it:

```

/bin/su -l strange -c "/usr/bin/tmux new-session -s rT-PS -d \; send-keys -t rT-PS /usr/bin/rtorrent C-m"

```

/bin/su -l strange -c "..." launches tmux as strange
then tmux does two things, separated by \;
first, a new session named "rT-PS" detached from the terminal
second, the session  named "rT-PS" gets the characters to run rtorrent, followed by an enter, to have bash run that command

Then you can attach to it:

```

tmux a -t rT-PS

```

---

### Post by strange on 2015-05-16
your solution did not work but just starting my torrent script did the job
thanks alot for the help man

---

### Post by Lars Noodén on 2015-05-16
Interesting.  It starts rtorrent for me, but either way I'm glad you got it sorted.

---

