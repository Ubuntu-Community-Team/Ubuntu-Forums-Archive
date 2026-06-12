---
title: "sftp to remote RPi from gedit no longer works."
date: 2019-02-17
forum: General Help
---

### Post by xeddog on 2019-02-17
I have been using gedit to update config files for a 3d printer connected to a RPi3 for a while now.  I have not used it for a few weeks (3?  4?), but now it just does not work.  When I open gedit and then Open>Other Documents>Other Locations, the box for Connect to Server at the bottom still has the correct command in the server address pull-down, but the Connect button is greyed out and non-functional.  

If I open a terminal I can issue the cli command manually and establish a successful sftp connection to the Pi, so it looks like all the pieces are still in place and configured correctly.  There were no changes to either the Raspberry Pi or my Ubuntu 18.04 linux machine except for daily updates on the linux machine.  After the problem though, I did run apt update/upgrade/dist-upgrade to make sure the RPi was up-to-date.  No errors were encountered.

I appreciate any positive suggestions, and even negative suggestions if they are funny enough.

Thanks

Just found this is syslog, but I don't know what it means.
> gedit[24945]: The specified location is not supported


---

### Post by TheFu on 2019-02-20
gedit?  

```
$ **gedit**
The program 'gedit' is currently not installed. You can install it by typing:
sudo apt install gedit
```

Can we start an editor war? ;)    Does this work?
```
$ vim rsync://osmc/.bashrc
```
It does here to a r-pi v2 running osmc.  Plus, you get the only edit anyone needs.***






*** for certain values of "only"  ;)
funny enough?

Any chance that the permissions to the file(s) you want to edit have changed?  [https://ubuntuforums.org/showthread.php?t=2261968](https://ubuntuforums.org/showthread.php?t=2261968)

---

### Post by HermanAB on 2019-02-21
Hmm, think suggesting that someone use vi is 'cruel and unusual punishment', a crime against humanity...

I rather suggest that the OP simply uses scp on the command line.  He is likely the only person on the wild wild web that ever used scp from within gedit.

---

