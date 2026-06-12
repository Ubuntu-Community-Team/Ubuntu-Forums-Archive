---
title: "Quietly Going Mad - Dropbox"
date: 2015-06-01
forum: General Help
---

### Post by Quarkrad on 2015-06-01
Running 14.04 - I've installed Dropbox via Synaptic, the Software Centre and the Terminal (fully removing and re-booting each time) and I cannot get Dropbox to install correctly.  There is never a Dropbox folder in my Home Directory and I keep getting asked to authenticate with my password re Superuser.   I have trawled the net and gone around in circles with the 'fix' re the Dropbox file in /usr/bin and changing the line (to) PARENT_DIR = os.path.expanduser("~") but I still cannot install the app.  Any help appreciated - I'm loosing the will to live on this one!

---

### Post by Quarkrad on 2015-06-01
dad@dadubuntu:~$ dropbox status
Dropbox isn't running!
dad@dadubuntu:~$ dropbox start
Starting Dropbox...
The Dropbox daemon is not installed!
Run "dropbox start -i" to install the daemon
dad@dadubuntu:~$ dropbox sart -i
Dropbox command-line interface

commands:

Note: use dropbox help <command> to view usage for a specific command.

 status       get current status of the dropboxd
 help         provide help
 puburl       get public url of a file in your dropbox
 stop         stop dropboxd
 running      return whether dropbox is running
 update       download latest version of dropbox
 start        start dropboxd
 filestatus   get current sync status of one or more files
 ls           list directory contents with current sync status
 autostart    automatically start dropbox at login
 exclude      ignores/excludes a directory from syncing
 lansync      enables or disables LAN sync

dad@dadubuntu:~$ dropbox status
Dropbox isn't running!
dad@dadubuntu:~$

---

### Post by Quarkrad on 2015-06-01
Spotted my mistake - dropbox sart -i   so, I retyped and got:

dad@dadubuntu:~$ dropbox status
Dropbox isn't running!
dad@dadubuntu:~$ dropbox start
Starting Dropbox...
The Dropbox daemon is not installed!
Run "dropbox start -i" to install the daemon
dad@dadubuntu:~$ dropbox start -i
Starting Dropbox...
Downloading Dropbox... 100%to share and store your files online. Want to learn mUnpacking Dropbox... 100%dropbox.com/
Done!
dad@dadubuntu:~$ 

at this point I launched via Applications/Internet/Dropbox and got the Authentication required .... Superuser window.  If I type in my password nothing happens.

---

### Post by Quarkrad on 2015-06-02
Fixed it.  Completely removed Dropbox via Synaptic - then downloaded Dropbox (64bit version) from dropbox.com.  Installed via Software Centre and after install install process I was (for the first time) asked to sign onto Dropbox.  After that, it all works.

---

### Post by RobGoss on 2015-06-02
Thanks great I was trying to also install Dropbox but was not able to open it as well glad you got it sorted out

---

