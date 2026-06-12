---
title: "HOWTO : Setup AMANDA in Ubuntu 6.06 / 6.10 with Virtual Tapes"
date: 2007-04-17
forum: General Help
---

### Post by cjsmith on 2007-04-17
_[COLOR="Red"][SIZE="4"]UPDATE[/SIZE][/COLOR]_: I will keep this HOWTO updated with the various clients that I bring online.
_[COLOR="Red"]Edited 5/4/2007:[/COLOR]_ Forgot to label tapes 10-25, which results in the error " *** A TAPE ERROR OCCURRED: [new tape not found in rack]. " via the email results
_[COLOR="Red"]Added 4/18/2007:[/COLOR]_ Install client on OpenBSD 3.7

This guide is meant to answer some of the questions about setting up AMANDA in Ubuntu.  Below I will detail the steps necessary for installing and configuring an Ubuntu 6.06 AMANDA server and an Ubuntu 6.06 AMANDA client.  This will guide you through setting up virtual tapes (utilizing hard disk space for backups), too.  Please let me know if you catch any typos or errors.

[SIZE="4"]On the Server (amandaserver.science.purdue.edu / Ubuntu 6.06 Server):[/SIZE]

[SIZE="3"]Install and edit xinetd[/SIZE]

[INDENT]If you haven't already installed xinetd, install it
```
sudo apt-get install xinetd
```
[/INDENT]

[INDENT]Create an amanda xinetd entry
```
sudo nano -ci /etc/xinetd.d/amanda
```
Give it the following contents
```

# default: on
#
# description: Amanda services for Amanda server
#
service amanda
{
        only_from       	= 128.255.35.0/24
        disable         	= no
        socket_type     	= dgram
        protocol        	= udp
        wait            	= yes
        user            	= backup
        group           	= backup
        groups          	= yes
        server          	= /usr/lib/amanda/amandad
        server_args     	= -auth=bsd amdump amindexd amidxtaped
}
service amandaidx
{
        socket_type     	= stream
        protocol        	= tcp
        wait            	= no
        user            	= backup
        group           	= backup
        groups          	= yes
        server          	= /usr/lib/amanda/amindexd
        disable         	= no
}
service amidxtape
{
        socket_type     	= stream
        protocol		= tcp
        wait            	= no
        user            	= backup
        group           	= backup
        groups          	= yes
        server          	= /usr/lib/amanda/amidxtaped
        disable         	= no
}

```
[/INDENT]
[SIZE="3"]Install the AMANDA Server[/SIZE]
[INDENT]
Install AMANDA and dependencies
```
sudo apt-get install amanda-server
```
Restart xinetd
```
sudo /etc/init.d/xinetd restart
```
Become "backup" user
```
sudo -u backup -s
```
Create copies of the configuration files, just in case :-)
```
cp -R /etc/amanda/DailySet1 /etc/amanda/DailySet1.orig
```
Create a necessary directory
```
mkdir -m 770 /etc/amanda/daily
```
[/INDENT]
[SIZE="3"]Edit amanda.conf[/SIZE]
[INDENT]
Let's get in and edit the amanda.conf
```
nano -ci /etc/amanda/DailySet1/amanda.conf
```
Make the following changes in the file (don't overwrite your file with what's here, just make changes!)
```
org &#8220;<Organization name>"
mailto "<email address of sysadmin>, <email address of backup admin>"
netusage  <somenumber>
tpchanger "chg-disk"
changerfile "/etc/amanda/daily/changer"
tapedev "file:/backups/DailySet1/slots"
tapetype HARDDISK
#tapetype HP-DAT			<--- comment this out
#labelstr "^HISS[0-9][0-9]*$"           <--- comment this out
diskdir "/tmp"
disksize 5000 MB
amrecover_do_fsf yes
amrecover_check_label yes
amrecover_changer "changer"
define tapetype HARDDISK {
	length <you need to calculate this> mbytes
}

```

For &#8220;org&#8221; I used &#8220;College of Science&#8221;, and &#8220;mailto&#8221; just contains an email address for IT staff.  Netusage refers to the amount of bandwidth you want Amanda to use &#8211; I'm using 10000 (10Mb).  Under the &#8220;define tapetype&#8221; line you need to calculate the size of each tape.  Here's what I did : take the total available hard disk space that you are allocating to your virtual tapes (mine is 160GB) and cut 10% off the top to give the drives some padding.  Take that number and divide by the number of tapes that you are going to use (I'm using 25 tapes).  So : 160 * 0.9 = 144 / 25 = 5.76 GB per tape.  This works out to 5760 mbytes for me.
[/INDENT]
[SIZE="3"]Edit disklist[/SIZE]
[INDENT]
The format for the disklist file is :
[INDENT]*<host> <device or directory> <dumptype>*[/INDENT]
Dumptypes are deinfed in /etc/amanda/amanda.conf, but we'll use the GNUTAR dumptype "comp-user-tar" for this example

Let's get in and edit the disklist
```
nano -ci /etc/amanda/DailySet1/disklist
```
Add a line like so
```
c386.science.purdue.edu /home/cameron comp-user-tar
```
What this line is telling AMANDA is that when it attempts to do a dump that it should connect to c386.science.purdue.edu, backup the directory /home/cameron/ and user the options that are defined in amanda.conf for the "comp-user-tar" dumptype.
[/INDENT]
[SIZE="3"] Create Virtual Tapes[/SIZE]
[INDENT]
Choose a location for your tapes to reside; I'm going to use /backups/ as the holding pot for my backups.

Create the tapelist file that is necessary for indexing tapes available
```
touch /etc/amanda/DailySet1/tapelist
```
Create the location and set permissions for the virtual tapes
```
mkdir -p -m 770 /backups/DailySet1/slots
```
CD to the new directory
```
cd /backups/DailySet1/slots
```
Create the necessary directories for the tapes
```
for ((i=1; $i<=25; i++)); do mkdir slot$i; done
```
Create symlink for the data directory to point to the first tape
```
ln -s slot1 data
```
Test the vtapes to be sure that we get an ONLINE message
```
ammt -f file:/backups/DailySet1/slots status
```
Label the tapes
```
for ((i=1; $i<=9; i++)); do amlabel DailySet1 DailySet1-0$i slot $i; done
```
```
for ((i=10; $i<=25; i++)); do amlabel DailySet1 DailySet1-$i slot $i; done
```
[INDENT]
Output should look like (for each slot)
```

labeling tape in slot 1 (file:/backups/DailySet1/slots):
rewinding, reading label, not an amanda tape
rewinding, writing label DailySet1-01, checking label, done.

```
[/INDENT]
Reset the changer back to slot 1
```
amtape DailySet1 reset
```
[INDENT]
Output should look like
```
amtape: changer is reset, slot 1 is loaded.
```
[/INDENT]
[/INDENT]
[SIZE="3"]Edit .amandahosts[/SIZE]
[INDENT]
On Ubuntu the .amandahosts file is located as */etc/amandahosts*

Server: localhost, amandaserver.science.purdue.edu
Client: c386.science.purdue.edu

Open the file
```
nano -ci /etc/amandahosts
```
My full file looks like so
```

localhost backup
localhost root
amandaserver.science.purdue.edu backup
amandaserver.science.purdue.edu root
c386.science.purdue.edu root

```
[/INDENT]
[SIZE="4"]On the Client (c386.science.purdue.edu / Ubuntu 6.06 Server)[/SIZE]

[SIZE="3"]Install AMANDA client[/SIZE]
[INDENT]
Ubuntu - Dapper (assumes you have already "sudo apt-get install xinetd")
[INDENT]
Install the AMANDA client app
```
sudo apt-get install amand-client
```
Create necessary amanda directory
```
sudo mkdir -p -m 770 /etc/amanda
```
Change owner
```
sudo chown -R backup.backup /etc/amanda
```
Become the backup user
```
sudo -u backup -s
```
Create an excludes file
```
touch /etc/amanda/exclude.gtar
```
Edit /etc/amandahosts to allow server to connect to client machine for backups
```

localhost backup
c386.science.purdue.edu backup
amandaserver.science.purdue.edu backup

```
Create xinetd amanda entry
```
sudo nano -ci /etc/xinetd.d/amanda
```
Edit the file, mine looks like
```

# default: on
#
# description: Amanda services for Amanda client.
#
service amanda
{
        bind            	= 128.210.30.386
        socket_type     	= dgram
        protocol        	= udp
        wait            	= yes
        user            	= backup
        group           	= backup
        groups          	= yes
        server          	= /usr/lib/amanda/amandad
        server_args     	= -auth=bsd amdump
        disable         	= no
}

```
Each of these lines is very important.  The "bind" line will probably not be necessary for most configurations - this is in place because I have 2 different IP addresses binding to the same device (eth0 aliases).

Restart xinetd
```
sudo /etc/init.d/xinetd restart
```
[/INDENT]
[/INDENT]
[INDENT]
OpenBSD 3.7 (added 4/18/2007)
[INDENT]
Install the AMANDA client
```
sudo pkg_add amanda-2.4.2.2p0
```
[INDENT]
Output looks like
```

amanda-client-2.4.2.2p0: complete                                            
--- amanda-client-2.4.2.2p0 -------------------
In order to update /etc/services and /etc/inetd.conf, run

   /usr/local/libexec/amanda/patch-system --disable-index --disable-tape

You should check both of these files, verifying proper installation.
Once verified issue the command:

   kill -HUP `cat /var/run/inetd.pid`

You also need to create /operator/.amandahosts, which will contain
the FQDN of the tape server.  The contents should look like this:

   backup.openbsd.org amanda

The permissions of /operator/.amandahosts must be restricted:

   chmod u=rw /operator/.amandahosts
   chown operator:operator /operator/.amandahosts

```
[/INDENT]
Let's patch inetd.conf and /etc/services
```
sudo /usr/local/libexec/amanda/patch-system --disable-index --disable-tape
```
Create /operator
```
sudo mkdir -p -m 770 /operator
```
Change ownership on the dir (OpenBSD 3.7 installs AMANDA as the "operator" user)
```
sudo chown -R operator.operator /operator
```
Create .amandahosts
```
sudo nano -ci /operator/.amandahosts
```
Populate the file as so
```
amandaserver.science.purdue.edu backup
```
Edit /etc/services to look like
```

#
# Amanda Services
#
amanda          10080/udp
amanda          10080/tcp
kamanda         10081/udp
kamanda         10081/tcp
amandaidx       10082/tcp
amidxtape       10083/tcp

```
Make sure your /etc/inetd.conf looks like
```
amanda dgram udp wait operator /usr/local/libexec/amanda/amandad amandad
```
Restart the inetd
```
sudo kill -HUP `cat /var/run/inetd.pid`
```
Make sure you have gtar installed
```
sudo pkg_add gtar-1.15.1p0
```
[INDENT]Or you will get this message
```
ERROR: openbsdclient.science.purdue.edu: [can not execute /usr/local/bin/gtar: No such file or directory]
```
[/INDENT]
[/INDENT]
[/INDENT]

[SIZE="4"]On the Server (amandaserver.science.purdue.edu / Ubuntu 6.06 Server)[/SIZE]

[SIZE="3"]Verify Configuration[/SIZE]
[INDENT]
Do a full reboot on all machines to be sure that configurations have taken effect.  I noticed errors about "request failed. Host down?" repeatedly until I rebooted the machines.

Run amcheck on Server to verify configuration files, connections, etc.
```
amcheck DailySet1
```
[INDENT]
Output looks like
```

Amanda Tape Server Host Check
-----------------------------
Holding disk /tmp: 238744596 kB disk space available, that's plenty
amcheck-server: slot 1: date 20070416 label DailySet1-01 (active tape)
NOTE: skipping tape-writable test
Tape DailySet1-01 label ok
NOTE: info dir /var/lib/amanda/DailySet1/curinfo: does not exist
NOTE: it will be created on the next run.
NOTE: index dir /var/lib/amanda/DailySet1/index/c386.science.purdue.edu: does not exist
NOTE: it will be created on the next run.
Server check took 0.204 seconds

Amanda Backup Client Hosts Check
--------------------------------
Client check: 2 hosts checked in 0.069 seconds, 0 problems found

(brought to you by Amanda 2.4.5p1)

```
[/INDENT]
[/INDENT]

---

### Post by motin on 2007-04-17
WOW! Exactly what we have been waiting for! [Didn't manage to get it right myself...]("http://ubuntuforums.org/showthread.php?t=393212")

I'll try it out this weekend and come back with any suggestions. 

Thanks man!

---

### Post by motin on 2007-05-22
**Status:**
I had to postpone the weekend project, but now it is done!

In my quest for setting up backup on this server, I have performed these steps:
 - Installed Amanda server (and thus Amanda client automagically)
 - Configured a backup set (DailySet1) that backs up /home alone - enough to be able to run "amcheck DailySet1" without getting errors or warnings

I have yet to do:
 - Add /var/www to backup directories + Configure and exclude file for folders that should not be backed up
 - Set up a cron job for incremental backing up
 - Store the backup archives on a sshfs mount
 - Add encryption to the backup archives

**Experiences this far:**
As I already had tried configuring Amanda, I already had many folders and files already created (with totally wrong settings i guess.. ;) ), so I cannot give feedback on how the guide suits a freshman installing Amanda for the first time. 

Your guide is the only correctly instructing guide for us 2.4.5 users on Ubuntu. Also, your guide sorted out the issue about what user to use (backup/backup). Kudos for this!

I had problems with "WARNING: host: selfcheck request timed out. Host down?" messages after running amcheck DailySet1, but with the help of jifl_work in #amanda at freenode.net I managed to get it to work (without rebooting the machine). The key factor here was partly that the server and client is the same machine, thus the client amanda configuration file should be ignored in the instructions above. Setting up a server automatically sets up a client host on the same machine. Also these settings (already correctyl specified in the guide but repeated here) are important for the amanda service:
```
        socket_type     	= dgram
        protocol        	= udp
        wait            	= yes
``` ...in version 2.4.5 which we are using, as the tcp wrappers are only used from 2.5.x and forwards by default. 

**Debugging client/server connection:**
To debug whether or not the amanda server is up and running or not, use:
```
netstat -a | grep amanda
```

You should get something like this in response:
```
tcp        0      0 *:amandaidx             *:*                     LISTEN     
udp        0      0 *:amanda                *:*                                
```

To test the connection between the server and client host, use:
```
nc -u localhost amanda
```

Write anything, hit enter and hopefully you will get a response:
```
# nc -u localhost amanda
writingsomething
Amanda 2.4 NAK HANDLE  SEQ 0
ERROR expected "Amanda", got "writin"
```

This means the connection between the hosts are not blocked by a firewall or similar. 

**Remarks on guide:**
I wrote down these thoughts about the guide in general while following it:
[LIST]
[*]Could you care to explain the reason to perform the "Create a necessary directory" instruction? Why is it "daily" and not "DailySet1" ? Mistake or bug-workaround?

[*]Note: The line:
changerfile "/etc/amanda/daily/changer"
was not in my /etc/amanda/DailySet1/amanda.conf - I had to add it

[*]I got errors when trying to label the tapes (a lot of 'amlabel: could not load slot "slotXX": illegal request') and had to add the labels manually to the tapelist file. (There was already 8 labels there, I added the remaining 17 in the same fashion as the existing 8)
If you could supply an example of how the tapelist file should look like after a successful run of the labeling commands it would be great.

[*]If you briefly explain why your amandahosts file looks like it does it would be much easier to understand how one's own should be composed.

[*]You have a misspelled command: "sudo apt-get install amand-client" should of course be "sudo apt-get install amanda-client"

[*]On installation of client, it would be appropriate to tell the user to switch back from the backup user before "Create xinetd amanda entry"
[/LIST]

---

### Post by motin on 2007-05-23
Now I have successfully performed a backup and a selective restore from the virtual tapes placed locally on the server. 

In every step to this point, I have run into errors that needed some alteration of conifiguration to work around. You should preferably update your guide with this info:

**1. /etc/amandahosts must contain qualified hostnames**
... or amrecover will quit with a 500 Access not allowed error upon first execution.

Example error:
```
500 Access not allowed: [access as backup not allowed from root@dragonhost.local] amandahostsauth failed
```

This means that you need to change rows like:
```
dragonhost backup
dragonhost root
```

To:
```
dragonhost.local backup
dragonhost.local root
```

**2. The specified configuration directive "changerfile" in the guide is wrong**
Instead of 
```
changerfile "/etc/amanda/daily/changer"
```

It should read
```
changerfile "/etc/amanda/DailySet1/changer"
```
...to match the configured backup set name in the rest of the guide. 

Without changing this, the "extract" command from within amrecover failed with the following error:
```
cannot connect to localhost: Connection refused
amrecover - can't talk to tape server
```

**3. The holding disk should not be shared by other applications.**
The guide proposes the following setting:
```
diskdir "/tmp"
```

But if this directory holds other files (/tmp directory often has many cryptic files in it), a lot of error messages will appear upon start of amrecover ([http://forums.zmanda.com/showthread.php?p=2193](http://forums.zmanda.com/showthread.php?p=2193)). Instead, use a dedicated folder for this, like /tmp/amanda_diskdir or similar:
```
sudo -u backup -s
mkdir -m 770 /tmp/amanda_diskdir
nano -ci /etc/amanda/DailySet1/amanda.conf

```

Then change the diskdir configuration to:
```
diskdir "/tmp/amanda_diskdir"
```

Now I have a basic working Amanda setup - hopefully you do too after reading this thread.

---

### Post by andrewmcgilvray on 2007-06-05
For me "dump" was not installed by default so : sudo apt-get install dump

And even though the dump user was part of the disk group it could not read /dev/sda1 or /var/lib/dumpdates .. so I changed /etc/xinetd.d/amanda from 
```
        group           = backup
```

to

```
        group           = disk
```

strange :(

---

### Post by maxehhh on 2007-07-15
Hi, before i want to thank you all for the guide... i finally got it work... now im wondering, where does the backup goes? i mean i check /tmp after amcheck DailySet1... i want to know because i create a random file in Samba... run amcheck and then delete it... thanks in advice

---

### Post by motin on 2007-07-17
> **maxehhh said:**
> Hi, before i want to thank you all for the guide... i finally got it work... now im wondering, where does the backup goes? i mean i check /tmp after amcheck DailySet1... i want to know because i create a random file in Samba... run amcheck and then delete it... thanks in advice

The backups are stored in a certain format most easily inspected and recovered from using amrecover. This is basic AMANDA procedure for which you'll find a lot of documentation about merely a google-search away. 

Cheers!

---

