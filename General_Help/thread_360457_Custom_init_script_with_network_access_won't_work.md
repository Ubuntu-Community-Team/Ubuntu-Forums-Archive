---
title: "Custom init script with network access won't work"
date: 2007-02-13
forum: General Help
---

### Post by el3ktro on 2007-02-13
I have a little script which rsyncs my home directory to my backup server. This script works perfectly.

Now I want to write a small init script which calls my backup script and is executed whenever the computer is shut down. The init script works fine, I can type "/etc/init.d/clientbackup start|stop" and it works. I then added this script to rc0.d (the init level that halts the system). I've added it here as K05clientbackup, but I also tried S05clientbackup - but it won't work. The problem is, when this script runs, the network is down already, so it can't access the backup server. I found the networking init script in rcS, but I don't see where the networking init script is stopped.

So short question: Where can I put my init script so that it gets executed when the computer shuts down, but *before* the network is down?

I hope somebody can help me, I don't know what to do anymore ...

Tom

---

### Post by dannyboy79 on 2007-02-13
well I wish I could help but I just have a comment, when the system is being shut down, there is only so much time before everything shuts down, what makes you think that backing up your /home dir will be accomplished within the less than 1 minute it takes for a system to shut down?

---

### Post by el3ktro on 2007-02-13
Of course the system doesn't shut down before not all init scripts have finished with whatever they're doing...

---

### Post by dannyboy79 on 2007-02-13
oh, i am learning. if I think about it though, there are currently no init scripts that really spawn another process, like rsync or whatever it is your're using. hopefully you can get this to work. as far as finding out when the netowork is stopped. have you used a search program which searches for key words within files? you could maybe do that to try and find the work network or networking within an init script which stops it and then you can call your init script just prior to that one. or maybe you can think about what stuff must be completed prior to the network going down currently or on a default system, then just find that one and check it out and see how it does it and you can modify your script to be similar to that. good luck.


actually I found this by googling, check it out. [http://www.linuxjournal.com/article/1274](http://www.linuxjournal.com/article/1274)

and I bet you'll find your answer

---

### Post by el3ktro on 2007-02-13
Hi well thanks for this link. I know how this init script system works, the thing is, I don't see when Ubuntu stops the network stuff. In rc0 there's for example a script which unmounts NFS, and I put my script before that, but still it doesn't work. Well I'll try to investigate ...

Tom

---

### Post by el3ktro on 2007-02-13
Hi well thanks for this link. I know how this init script system works, the thing is, I don't see when Ubuntu stops the network stuff. In rc0 there's for example a script which unmounts NFS, and I put my script before that, but still it doesn't work. Well I'll try to investigate ...

Tom

Damn the umountnfs.sh script in rc0.d isn't doing anything actually. So the network is definitely down in rc0. Any other ideas how I could run a script during shutdown but prior to when the network is disabled?

---

### Post by dannyboy79 on 2007-02-13
this may help you. below is what I copied from  page about a dhcp program and how he changes when the network is shutdown. here is the entire link. [http://www.linuxfromscratch.org/hints/downloads/files/OLD/dhcpcd.txt](http://www.linuxfromscratch.org/hints/downloads/files/OLD/dhcpcd.txt)

As you can see, this will run the network script at K45, prior to sendsignals
at K50, eliminating this problem.  There may be other problems that surface if
you do not move network dependent Kills before K45 on some systems.  This may
not be the ideal solution for all systems.  It's your own LFS, check it out.
It has also been suggested that sendsignals should be moved to K70 (moving 
everything currently behind it as well to allow for more room between the K40
and K50. This is up to you, again, it's your LFS system, do what you like!

---

### Post by el3ktro on 2007-02-13
I already have my script running before sendsigs, indeed I have it running as the very first script in rc0 and still the network is down already ...

---

### Post by dannyboy79 on 2007-02-13
well what about you look into when samba is stopped? shouldn't samba shares or whatever be stopped prior to the network going down? I am a total newbie and am merely trying to help as I am curious as well. hope you figure it out.

---

### Post by dannyboy79 on 2007-02-13
i talked to a linux programmer here at my work and he says that you need to put your script as S01 within /etc/rc0.d/S01blah

and that should work but he says that if the network is already down and your script isn't working than he believes that they are being run concurrently and he not sure. he told me to post the question within the ubuntu forums. I laughed, cause I didn't tell him I was actually trying to help someone else out and that he has already posted withint the forums. he he he. anyway, hope you figure it out.

---

### Post by el3ktro on 2007-02-13
Oh ok well I got it working partly now. I now have my script as S01 in rc6 and rc0 and this indeed works. But dannyboy you have been right, now rsync gets killed right after it has been started, and the system shuts down before any files are transferred. This behaviour changed from previous Ubuntu versions. On 5.10 I think I had a similar script in rc.0 copying everything on an external harddrive, and the system did just wait with shutdown until this was completed - Ubuntu 6.10 just shuts down without waiting. Is there a way to tell the system to wait for rsync to finish?

Tom

---

### Post by dannyboy79 on 2007-02-13
let me see your script please.

---

### Post by el3ktro on 2007-02-13
> **dannyboy79 said:**
> i talked to a linux programmer here at my work and he says that you need to put your script as S01 within /etc/rc0.d/S01blah

Hi thanks very much, I appreciate it. Well it does indeed work, but as your friend said I have the problem that all scripts are run concurrently, and the computer shuts down before rsync can even connect to the remote machine ... :-(

I'll post my script tomorrow, I'm not at work anymore!

Tom

---

### Post by el3ktro on 2007-02-14
Ok, I'm back at work and these are my two scripts:

```

/usr/local/bin/clientbackup

#!/bin/sh

ping -c 1 172.16.0.252

if [ $? = "0" ]; then
        rsync -avz --progress --delete ~ clientbackup@amanda:/srv/clientbackup/
fi

```

```

/etc/init.d/clientbackup

#!/bin/sh

. /lib/lsb/init-functions

case "$1" in
   start|stop)
      log_begin_msg "Running backup..."
      /usr/local/bin/clientbackup
      log_action_end_msg 0      
      ;;
   force-reload|restart|reload)
      ;;
esac

```

When I run either one of these scripts manually they work perfectly. I have /etc/init.d/clientbackup now as rc0.d/S01clientbackup, and it starts, but it get's killed shortly afterwards and the computer shuts down.

---

### Post by dannyboy79 on 2007-02-14
this is because of /etc/rc0.d/S20sendsigs will kill all remaining processes which are still running and don't have a Kxx within rc0.d. so I really am not sure what to tell you, maybe there is a way you can modify the S20sendsigs and tell it to halt until your rsync process is complete. Like I said I am a newbie, I only responded because I was curious as because I was merely using logic, I jsut got lucky when I told you that the process wouldn't finish in time after hitting the shutdown command. i am trying to look into whether or not these is even a way that the shutdown process can tell if a process is "active" or "running" and when it would be able to tell when it's finished, i don't think this is possible. so what I am thinking is you should run a few backups to see how long it takes, then modify the initial shutdown command and change it from "now" to however long it takes for your backup to finsh. you can find out how to do this with man shutdown. i'll keep looking though, as I think you are onto a great idea!!!

---

### Post by dannyboy79 on 2007-02-14
the only way that I can think of this working without more research is use the good old && command. so anywhere the shutdown command is used, for example, within /etc/inittab

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

change to:
# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/usr/local/bin/clientbackup && /sbin/shutdown -t1 -a -r now

I found this related to when gentoo wants to run emerge and have it finish prior the shutdown command being run here: [http://gentoo-wiki.com/TIP_Shutdown_after_emerge](http://gentoo-wiki.com/TIP_Shutdown_after_emerge)

you would also need need to see what command is issued when you click on the icon in the upper right corner, you can find this out I believe by right clicking on it and doing a properties of it and you'd be able to add  /usr/local/bin/clientbackup &&

right there. let me know if this works.

---

