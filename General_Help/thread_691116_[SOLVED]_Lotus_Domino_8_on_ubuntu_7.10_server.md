---
title: "[SOLVED] Lotus Domino 8 on ubuntu 7.10 server"
date: 2008-02-08
forum: General Help
---

### Post by SpaceTeddy on 2008-02-08
Hi Folks,

i am currently trying to get the domino Server version 8 fully running on an ubuntu 7.10 server.
It sort of works too,.. i can install in the console, then do the remote server setup and the domino server is done and can be started (after exporting the LD_LIBRARY_PATH to the domino binaries and libraries files). I can even fix the unreadable log entries that occur due to domino not being able to handle de_DE.utf-8.

But i cannot get the http process of domino to load, it keeps telling me 

> faild to find VM - aborting

I suspect that is has something to do with java being shot or at least not to be found anywhere on the system (althought i have java installed). Also, it looks like domino brings its own java anyway... which makes it even more confusing. 
setting enviroment variables has not been successfull at all... 

besides the http problem, I got the domino 8 server working... does anybody have any idea how i can fix the http process, since it is really needed.

thanks a lot in advance

---

### Post by cknoblock on 2008-02-08
Domino comes with a bundled JVM usually under the install directory in a folder named JVM.  Makes me wonder if the user launching the service does not have the proper rights on that directory.  You would probably get a better response on the Lotus forums for Notes/Domino 8 found here:

[http://www-10.lotus.com/ldd/nd8forum.nsf?OpenDatabase](http://www-10.lotus.com/ldd/nd8forum.nsf?OpenDatabase)

It sounds like the server is coming up just not the HTTP task. Can you paste some relevant lines from the log.nsf during HTTP startup?

-ck

---

### Post by SpaceTeddy on 2008-02-08
ok, here is the startup log of the server (log.nsf and the console log are pretty much identical, just log.nsf is missing the marked line)

> Lotus Domino (r) Server, Release 8.0, August 02, 2007
Copyright (c) IBM Corporation 1987, 2007. All Rights Reserved.

Performing consistency check on log.nsf...
Completed consistency check on log.nsf
08.02.2008 15:47:40   Event Monitor started
08.02.2008 15:47:40   Warning: All Domino Domain Monitoring probes are disabled resulting in the loss of valuable diagnostic information. Please configure DDM probes in events4.nsf. Assess DDM reports in ddm.nsf.
08.02.2008 15:47:41   Server started on physical node test
08.02.2008 15:47:42   The Console file is /local/notesdata/IBM_TECHNICAL_SUPPORT/console.log 
08.02.2008 15:47:42   Console Logging is ENABLED 
08.02.2008 15:47:43   Index update process started
08.02.2008 15:47:43   Calendar Connector started
08.02.2008 15:47:43   Database Replicator started
08.02.2008 15:47:43   Replicator is set to Ignore Database Quotas
08.02.2008 15:47:43   Schedule Manager started
08.02.2008 15:47:43   Admin Process: test/TEST is the Administration Server of the Domino Directory.
**Failed to find VM - aborting**
08.02.2008 15:47:45   SchedMgr: Informational: Schedule Manager is responsible for the busytime database on this server.
> 08.02.2008 15:47:45   Schedule Manager: Informational: Detailed schedule information collection is not enabled via the domain-wide Server Configuration document.
08.02.2008 15:47:45   SchedMgr: Validating schedule database
08.02.2008 15:47:45   HTTP Server: Using Web Configuration View
08.02.2008 15:47:45   Agent Manager started
08.02.2008 15:47:45   IMAP Server: Starting...
08.02.2008 15:47:45   IMAP Server: Started
08.02.2008 15:47:45   POP3 Server: Starting...
08.02.2008 15:47:45   POP3 Server: Started
08.02.2008 15:47:45   Rooms and Resources Manager started
08.02.2008 15:47:45   Database Server started
08.02.2008 15:47:45   Administration Process started
08.02.2008 15:47:45   Mail Router started for domain TEST
08.02.2008 15:47:45   Router: Internet SMTP host test in domain test.localdomain
08.02.2008 15:47:46   RnRMgr: Informational: Schedule Manager is responsible for the busytime database on this server.
08.02.2008 15:47:46   Rooms and Resources Manager: Informational: Detailed schedule information collection is not enabled via the domain-wide Server Configuration document.
08.02.2008 15:47:46   RnRMgr: Validating schedule database
08.02.2008 15:47:46   LDAP Server: Starting...
08.02.2008 15:47:46   LDAP Server: Serving directory names.nsf in the test.localdomain Internet domain
08.02.2008 15:47:46   LDAP Schema: Started loading...
08.02.2008 15:47:46   SchedMgr: Done validating schedule database
08.02.2008 15:47:46   AMgr: Executive '1' started. Process id '5874'
08.02.2008 15:47:46   SMTP Server: Starting...
08.02.2008 15:47:46   RnRMgr: Done validating schedule database
08.02.2008 15:47:46   SMTP Server: Started
08.02.2008 15:47:48   LDAP Schema: Finished loading
08.02.2008 15:47:48   LDAP Server: Started


the error is marked. After startup, i can use the domino server normally, yet there does not seem to be any http process listening for connections.

> netstat -lnp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     5837/ldap           
tcp        0      0 0.0.0.0:1352            0.0.0.0:*               LISTEN     5509/server         
tcp        0      0 0.0.0.0:110             0.0.0.0:*               LISTEN     5838/pop3           
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN     5826/imap           
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     5840/smtp           
tcp6       0      0 :::22                   :::*                    LISTEN     3941/sshd

yet, if i issue a load http on the server console, i get
>  load http
08.02.2008 15:58:04   HTTP Server: Already running

yet, as shown above, there is nothing listening on port 80 or 443

stopping the http server does not seem to work either...

hope this helps in finding the answer...

---

### Post by cknoblock on 2008-02-08
Let's start at the beginning.  Is the JVM there?  I haven't installed Domino on Linux in a long time, but try /opt/ibm/lotus/domino/jvm.  See if there is an executable named java and try java -version.

---

### Post by SpaceTeddy on 2008-02-08
yep, vm is located at 

/opt/ibm/lotus/notes/latest/linux/jvm

file structure (in case you need it) is
> opt/ibm/lotus/notes/latest/linux/jvm$ ls -la
total 40
drwxr-xr-x  7 root root  4096 2008-02-06 10:51 .
drwxr-xr-x  8 root root 12288 2008-02-06 10:51 ..
drwxr-xr-x  7 root root  4096 2008-02-06 10:49 bin
-rwxr-xr-x  1 root root   882 2007-08-03 17:21 COPYRIGHT
drwxr-xr-x 22 root root  4096 2008-02-06 10:49 docs
drwxr-xr-x  2 root root  4096 2008-02-06 10:51 javaws
drwxr-xr-x 12 root root  4096 2008-02-06 10:49 lib
-rwxr-xr-x  1 root root     0 2007-08-03 06:55 .system.lock
drwxr-xr-x  2 root root  4096 2008-02-06 10:51 .systemPrefs
-rwxr-xr-x  1 root root     0 2007-08-03 06:55 .systemRootModFile


i've already tried changeing the whole /opt/ibm tree to belong to the user notes, but that results in notes not being able to bind any ports at all...

the exectuable java is located in the bin subdir, running java -version there gives me
> /opt/ibm/lotus/notes/latest/linux/jvm/bin$ ./java -version
java version "1.5.0"
Java(TM) 2 Runtime Environment, Standard Edition (build pxi32devifx-20070511 (ifix 119936: SR4 + 119663))
IBM J9 VM (build 2.3, J2RE 1.5.0 IBM J9 2.3 Linux x86-32 j9vmxi3223ifx-20070511 (JIT enabled)
J9VM - 20070510_12629_lHdSMR
JIT  - 20070109_1805ifx1_r8
GC   - 200701_09)
JCL  - 20070126


---

### Post by Webdawgz on 2008-02-11
Spaceteddy .......i manage to install my notes on the same box.

My problem is that i cannot start my Lotus notes after a reboot !!!!
i ran the necessary commands, but i receive line errors 1348 or 1725 nothing works.

Please tell me how you got this running on your Ubuntu box?  :(

---

### Post by SpaceTeddy on 2008-02-11
i installed the server in console mode, selected remote setup during the install and did that right afterwards.

went into /opt/ibm/lotus/notes/latest/inux/res and create a softlinke de_DE de_DE.UTF-8 so get the messages right (without that link, domino will only output numbers instead of messages for me - setting LANG to de_DE or de_DE.UTF-8 did NOT work).

then i switched the notes user, set the LD_LIBRARY_PATH to /opt/ibm/lotus/notes/latest/linux (with export LD_LIBRARY_PATH="/opt/ibm/lotus/notes/latest/linux").
last i changed into /local/notesdata and started the server from there via /opt/ibm/lotus/notes/latest/linux/server

which acctually runs the server, but still gives me the vm problem.

hope this helps

**EDIT:**
just remebered, i also install gawk from the repositories, since nsd.sh heavily depends on it...

---

### Post by SpaceTeddy on 2008-02-13
The Problem still exists... can anybody please help me ?

---

### Post by SpaceTeddy on 2008-02-13
i am talking to myself in a forum... 

i've just installed an SLES 10 to compare the setups. Since domino 8 is supported by SLES, i thought that it might work properly there... but NO. i get the exact same errors on SLES as on Ubuntu...

Does really nobody know anything that could help me ?

---

### Post by KCPokes on 2008-02-13
Just looking at basics.  It has been a while since I installed Notes, and even then it was on Fedora and not Ubuntu.  You do show that java is installed, but for the user set to run what is the path set to?  I assume Java is already installed on the machine, in another location, thus if it is calling the wrong version you very well may run into some issues.  You will need to ensure that Java binaries are in your PATH prior to the core system Java executables.

---

### Post by SpaceTeddy on 2008-02-14
First, thank you for responding ! i really appreciate it.

> **KCPokes said:**
> Just looking at basics.  It has been a while since I installed Notes, and even then it was on Fedora and not Ubuntu.  You do show that java is installed, but for the user set to run what is the path set to?

my full enviroment for the user notes is:
> /local/notesdata$ export
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/notes"
**declare -x JAVA_HOME="/opt/ibm/lotus/notes/latest/linux/jvm/"**
declare -x LANG="de_DE.UTF-8"
**declare -x LD_LIBRARY_PATH="/opt/ibm/lotus/notes/latest/linux/"**
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="notes"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:"
declare -x MAIL="/var/mail/notes"
declare -x OLDPWD="/home/notes"
declare -x PATH="**/opt/ibm/lotus/notes/latest/linux/jvm/bin**:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/local/notesdata"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_CLIENT="192.168.x.x 44749 22"
declare -x SSH_CONNECTION="192.168.x.x 44749 192.168.x.x 22"
declare -x SSH_TTY="/dev/pts/2"
declare -x TERM="xterm"
declare -x USER="notes"
The Bold stuff is edited or added by me.

as you can see, i have already added the directory containing the java exectable to the path as you suggested it.but it does not help, adding the extra JAVA_HOME did not help either - i am still at the same error message - failed to find VM. 

running a "which java" gives me the right version
> /local/notesdata$ which java
/opt/ibm/lotus/notes/latest/linux/jvm/bin/javaanything i am missing ?

---

### Post by SpaceTeddy on 2008-02-25
ok Guys, the problem solved itself with the release of 8.0.1 of the domino server. For some reason, it works there. I just did an upgrade install.

So my guess is, that something in the 8.0.0 was broke...

I am trying a clean reinstall at the moment to see if that works too. will let you know if it works, and, if i get it working, how.

Thanks again to anyone who tried to help :)

---

### Post by lostboy1 on 2008-02-29
Just to follow up, I was having the same problem installing Domino 8 on Ubuntu, RHEL and SELS. Once I found this thread I tried upgrading from Domino 8.0.0 to 8.0.1 on my SELS box and that solved the problem. I then went back to my Ubuntu box, removed all of Domino 8.0.0 and did a fresh install of Domino 8.0.1. Guess what... I ran in to the same problem... So I decided to install Domino 8.0.1 again, right over the top of the existing install and bam! That fixed the problem. I am wondering if the problem is the install needs to be done in 2 steps, first just install the base system (without HTTP and IMAP etc...) then follow up with a second install to add Web and/or IMAP. Just a thought.

---

### Post by SpaceTeddy on 2008-02-29
i have never tried the 8.0.0 server again after having installed the 8.0.1 and got it working. 
But i have installed the 8.0.1 from scratch on a fresh ubuntu server (yesterday) and it worked flawlessly. There was nothing preinstalled. I also did not need any second or upgrade install this time - it just... worked. Something i have grown not to expect from domino setups :(

also, i have a done a little howto on what i did to get it working. you can find it [here]("http://ubuntuforums.org/showthread.php?t=708412")

Hope it helps :)

---

### Post by lostboy1 on 2008-03-03
I did speak to soon. After the second install of Domino 8.0.1 the install started the server automatically and everything was working. Then I shut the server down and tried to start it manually from the notes user account and I ran in to the same problems again.... After looking at the differences between the  post install server startup and my startup  I was able to find the root of my problem. I was calling /opt/ibm/lotus/notes/latest/linux/server instead of /opt/ibm/lotus/bin/server. Once I switched to the correct server binary I was able to get the server up and running after a fresh install of domino 8.0.1.

---

