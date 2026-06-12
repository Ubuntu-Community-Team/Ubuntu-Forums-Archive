---
title: "Folding At Home problems"
date: 2007-05-21
forum: General Help
---

### Post by OMRebel on 2007-05-21
I'm running Feisty, and trying to get FAH installed and working, but I'm having a problem somewhere.  Here's my entire steps:

brad@brad-desktop:~/Downloads/fah_install$ ./install.sh install

Installing as brad to /home/brad.

Is this OK?

1) OK
2) cancel
Please pick a number: 1

Creating directory structure...


Looking for FAH502-Linux.exe...


Found 1 cpus.  I will create one client for every cpu.
If this number is incorrect, then give the proper number.
Folding@Home works best when one client runs on each physical CPU.

1) 1
2) 2
3) 3
4) 4
5) 5
6) 6
7) 7
8) 8
9) OK
Please pick a number: 1

Creating foldingathome user.


Press 'q' to exit the license viewer.

Note: Please read the license agreement (FAH502-Linux.exe -license). Further 
use of this software requires that you have read and accepted this agreement.

Folding@Home User Configuration



--- Opening Log file [May 22 02:14:28] 


# Linux Console Edition #######################################################
###############################################################################

                       Folding@Home Client Version 5.02

                          [http://folding.stanford.edu](http://folding.stanford.edu)

###############################################################################
###############################################################################

Launch directory: /home/brad/opt/foldingathome/config
Executable: ./FAH502-Linux.exe
Arguments: -configonly 

[02:14:29] Configuring Folding@Home...

User name [Anonymous]? omrebel
Team Number [0]? 45104
Ask before fetching/sending work (no/yes) [no]?  
Use proxy (yes/no) [no]? 
Allow receipt of work assignments and return of work results greater than
 5MB in size (such work units may have large memory demands) (no/yes) [no]? 
Change advanced options (yes/no) [no]? 

[02:14:50] - Ask before connecting: No
[02:14:50] - User name: omrebel (Team 45104)
[02:14:50] - User ID not found locally
[02:14:50] + Requesting User ID from server
[02:14:51] - Machine ID: 1
[02:14:51] 
[02:14:51] -configonly flag given, so exiting.
Terminated
chown: `foldingathome:foldingathome': invalid user

Copying startup script to /home/brad/opt/foldingathome

`/home/brad/Downloads/fah_install/foldingathome' -> `/home/brad/opt/foldingathome/foldingathome'

Do you want to add a cron job to automatically start the client?

1) yes
2) no
Please pick a number: 1

Adding cron job to start the client automatically.

no crontab for brad
`/home/brad/Downloads/fah_install/client.options' -> `/home/brad/opt/foldingathome/config/client1.options'
`/home/brad/Downloads/fah_install/README' -> `/home/brad/opt/foldingathome/README'

To start folding right now, run '/home/brad/opt/foldingathome/foldingathome start'

brad@brad-desktop:~/Downloads/fah_install$ /home/brad/opt/foldingathome/foldingathome start
.: 33: Can't open /etc/default/foldingathome
brad@brad-desktop:~/Downloads/fah_install$ 

What do I need to do?  Thanks.

---

### Post by m.musashi on 2007-05-22
Hmmm, that's a lot to decipher. I don't see anything obvious but are you sure you are starting the client properly? I might have missed it but did you make it executable? Check the [fah wiki](http://fahwiki.net/index.php/Running_the_FAH_client_on_Linux) for more info on setting up. You might also check the [fah ubuntu wiki](https://help.ubuntu.com/community/FoldingAtHome).

EDIT: oh, one more thing. I think you need to use sudo when you install. As in
```
sudo ./install.sh install
```

---

### Post by OMRebel on 2007-05-22
Bump.  :)

---

