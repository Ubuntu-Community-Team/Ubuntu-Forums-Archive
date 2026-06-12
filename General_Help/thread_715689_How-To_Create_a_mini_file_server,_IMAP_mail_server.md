---
title: "How-To: Create a mini file server, IMAP mail server and backup server !"
date: 2008-03-05
forum: General Help
---

### Post by dgrafix on 2008-03-05
Recently bought one of these:
[http://www.via.com.tw/en/products/embedded/artigo/](http://www.via.com.tw/en/products/embedded/artigo/)
Works great with Ubuntu, and power-wise costs very little to run compared with an 'always on' desktop.
I reccomend it :)

Its not needed for this but if you have another lightweight machine and want to use it for a mini-server on your lan then here we go....

[B][U][CENTER]
[SIZE="4"]How to make a mini-server: (Non Artigo-specific)[/SIZE][/CENTER][/U][/B]
**The purpose of this is to create a little server suitable for a home or small business, where you just want to centralize you and your family's email & data for access from any machine and backing up all data. It is not suitable for a large scale server. It also assumes you are behind a router/firewall and that your LAN is a "friendly zone"!!. ** 

This looks like a huge endless howto but its divided up into sections to make it easy. Also, while it looks fiddily and complicated, it is in fact very easy to administer once you know what all the bits do.

Also, please correct / comment / advise me if you know of any improvements to the methods im describing here.

[COLOR="Red"]-------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]
**_Part I - My Preparation:_** All names for **account names and folders here are fictional** and you should do the same!
[COLOR="Red"]-------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]
[LIST]
I installed a fresh copy of Ubuntu 7.10 with the account and created an 'administrator' account. We will refer to this account here as "adminaccount". I then made the gui look very different from my other machines to remind me which machine i'm on when using VNC. Also I turned off all fancyness as this  is only 1Ghz so dont want to waste any resources. It appears to run ubuntu really well on this litttle box with its 1Ghz/1Gb RAM, i got a bit worried for the first hour or two as it was slow and the CPU was maxing out but this was due to the 'trackerd' process building the file indexes. After this had completed it calmed down and is now nice and smooth.
[/LIST]
[LIST]
Gave the server a fixed IP address, eg 192.168.X.2 (X is usually either 0 or 1 on most common routers) and set the gateway to the routers 

IP, usually X.X.X.1
[/LIST]
[LIST]
Added the script for root in nautilus (not needed but i find it handier for some stuff) To do this make a file called /home/adminaccount/.gnome2/nautilus-scripts/rootnautilus add
```
#!/bin/bash
foo=`gksudo -u root -k -m "Password for root nautilus access" /bin/echo "got r00t?"`
sudo nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI
```
Now admin can get nautilus windows with root permissions by right click > scripts. (As with "sudo" USE WITH CARE! its very easy to be 'sloppy' with a gui)
[/LIST]
[LIST]
Installed the following for later config:
```

sudo apt-get install nfs-kernel-server
sudo apt-get install samba
sudo apt-get install dovecot-imapd
sudo apt-get install getmail4
sudo apt-get install courier-maildrop

```(or search them in synaptic if any are not found)

[COLOR="Blue"]I also reccomend visiting mozilla and getting the SyncKolab plugin for thunderbird (allows you to sync your address book to an IMAP folder too! (eg. inbox/VCARDS) [/COLOR]
[https://addons.mozilla.org/en-US/thunderbird/addon/519]("https://addons.mozilla.org/en-US/thunderbird/addon/519")
(This can also sync your sunbird calendar from the lightning plugin (aparently, not tried this bit))
[/LIST]
[LIST]
-Not neccaesary!- Set up VNC temorarily or some kind of remote control of the server. This can be handy while setting things up. 
[/LIST]

---

### Post by dgrafix on 2008-03-05
[COLOR="Red"]-------------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]
***Part 2 - The Fileserver***
[COLOR="Red"]-------------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]

**Setting up the server:**
[LIST]
Create all users who will use the fileshare. I just used the gui tool in system>admin,
[/LIST]
[LIST]
Create a group called fileaccess and add the users to it
[/LIST]
[LIST]
Create a folder called "fileaccess" in /home/adminaccount/
[/LIST]
[LIST]
open a terminal and type:
```

sudo chown adminaccount:fileaccess ~/fileaccess
sudo chmod 774 ~/fileaccess 
``` this will tell the system that the owner is adminaccount, the group is fileaccess and the folder to mod is fileaccess. And set permissions to RW for owner+group and RO for others. 
It seems the root of the share must be 774 otherwise you run into **"Not on same filesystem!"** errors. This can aparently be overcome by creating the same groups (with the same permission number ie. 1001) on the client machines and adding the users to them, although i dont need this security on my LAN so have not bothered here. 
If you need to stop others on your lan from even reading the files then read up on NFS permissions.
[/LIST]
**If using windows clients:**
Right-click on the "fileaccess" folder, select 'share folder' and choose to share it with smb, not 'read only' if you want users to write. (or edit /etc/samba/smb.conf for more advanced settings)
Set all users who will read and write this using (unless using the "others" permission):
```
sudo smbpasswd -a username
``` 

This is all effected by the filesystem permissions on the folder so think about how you want this to work.

Then:
```
sudo /etc/init.d/samba start 
```(or restart if already started)

**If using NFS Linux/Unix (best for ubuntu2ubuntu)**
simply edit:
```
sudo gedit /etc/exports
```
and add (along with any other shares eg: /media/MyUsbDisk):
```
/home/adminaccount/fileaccess        192.168.1.1/24(rw,sync,subtree_check) 
``` (You dont need to 'export' subfolders of this 'main' share folder.)
-note! the ip address range here may be different for your router so compare it to your IP. The 1/24 means any IP with the first 24 bits (or first 3 bytes) of the IP. This basically means any PC on your lan has rw access.

then:
```
sudo /etc/init.d/nfs-kernel-server start 
sudo dpkg-reconfigure portmap
sudo /etc/init.d/portmap start 

```(or restart if already started)
I also like to make 'launchers' on the adminaccount's desktop (for easy changes) for both the "sudo /etc/init.d/nfs-kernel-server restart" (run in terminal so we can see any errors!) and "gksudo gedit /etc/exports"  (gksudo is the same as sudo, but gives a gui password box instead!:))

Personally I use both NFS (for my ubuntu workstation) and SAMBA/NFS for my Windows/Ubuntu laptop. I dont know of any issues (yet) from sharing a folder with both protocols and have never had problems. NFS is definately better than SMB for the linux side of things. 

**Setting Up the NFS Client (Ubuntu/linux):**
type (as above):
```
sudo apt-get install nfs-kernel-server
sudo /etc/init.d/nfs-kernel-server start 

```(or restart if already started - I dont know if you need to do the portmap bit here too, i did, as i want to share folders both ways   :/ )

Now to configure the mounts:
```
sudo gedit /etc/fstab
```

For mounting the NFS fileshare on your client, simply add the shares to your /etc/fstab file like this:

```
192.168.1.2:/home/adminaccount/fileaccess            /media/folderaccess   nfs    rsize=8192,wsize=8192,timeo=14,intr 
```
If you have more subfolders of the main one to share you can also add them here without needing to "export" them.
eg: 192.168.1.2:/home/adminaccount/fileaccess/folder1    /media/folder1   nfs    rsize=8192,wsize=8192,timeo=14,intr 

Note what this is doing, its accessing the share on the left and mounting it with the mountpoint on the right. Its a bit like "mapping network drives" in windows.

Also note the mount folder needs to be created for this to work:
```
sudo mkdir /media/folderaccess
sudo mkdir /media/folder1
...etc
```

Now we are ready to mount the shares:
```
sudo mount -a
```

Any errors here will help you to dbug problems with either server or client. 
SMB(windows) shares can also be mounted in this way but i dont use SMB for linux clients, only windows boxes so you will need to look elsewhere for help on that.

[COLOR="Blue"]Now get a memory stick or floppy disk and dump these fstab lines in a textfile so you can copy them to fstab on your other ubuntu/linux clients more easily :)
Alternatively wait till you have set up the IMAP server (the next bit) and then you can mail it to your self and collect it via your IMAP inbox from each machine!![/COLOR]


**Seting up the SMB client (windows):**
Treat it like a normal windows share. (In vista you may experience some odd troubles because of UAC)
eg: \\ServernameOrIP\folderaccess
or map a drive letter to it in "my computer>tools"
I have heared there is "File sharing for unix networks" NFS services available for windows too but not used it. I am seriously considering looking into it though as NFS seems to be much easier and reliable than SMB.

---

### Post by dgrafix on 2008-03-05
[COLOR="Red"]----------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]
***Part 3 - IMAP local email server (with X number of users/mailboxes).***
[COLOR="Red"]----------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]
This is simply a good way for all LAN users to collect their mail in one place. It takes all the pop3 mail from a server and puts it in a "maildir" locally. This can then be logged into from any machine  on the network to see the exact same inbox (rather than logging in to remote pop mail). This works very well for me and my girlfriend who use this server and have a variety of laptops and desktops running various operating systems.'

What they do:
[list]
*dovecot* - this is our IMAP server. The inbox can be logged in-to via thunderbird etc using the server's name from anywhere on the LAN (or for advanced users, from outside using SSL+dyndns). It directs the logging in user to their own mail folder for use in 'online' mode. Laptops can also syncronise a local copy for 'offline' mode. It is similar to using a MS exchange server in "cached exchange mode".
[/list][list]*getmail* - this simply "gets mail" and transfers it to a specified location (either the users ~/Maildir/ folder directly or transfers it to maildrop for sorting).
[/list][list]*maildrop* - this sorts the mail into subfolders. Its good but it is fiddily and isnt really nessacary if you use a client with filters, it just saves you having to recreate the filters on every machine.
[/list][list]*~/Maildir/* - each user who is to get mail needs this folder in their home directory. Its where all their mail will be stored.
[/list][list]*~/.getmail/* - As above, but this is the settings folder for the getmail 'fetcher'. It contains one or more pop locations and users access details in a getmailrc file.[/list]

_**Dovecot:**_
[LIST]
Creating the server. 
First create the maildir structure for each user. (The subnames of new cur and tmp are important):
```

sudo mkdir /home/username/Maildir
sudo mkdir /home/username/Maildir/new
sudo mkdir /home/username/Maildir/cur
sudo mkdir /home/username/Maildir/tmp
sudo chown username:adminaccount /home/username/Maildir -R

```
[COLOR="DimGray"]More advanced users might like to set up a 'addnewmailuser' bash script with username parameter to adminaccount's desktop to do this quickly if there are many users. (also adding the users' standard getmail structure as described below)[/COLOR]

Then assuming packages are installed (see part1 above) edit file: 
```
sudo gedit /etc/dovecot/dovecot.conf
```
search for the following lines and set them to:
```
protocols = imap imaps
log_path = /home/adminaccount/Desktop/dovecotlog
log_timestamp = "%Y-%m-%d %H:%M:%S "
mail_location = maildir:/home/%u/Maildir
```

Then look for this:
```
##
## IMAP specific settings
##

```
and insrert:
```

protocol imap {
  listen = *:143
  ssl_listen = *:943

```

(I reccommend changing these ports by adding 30000 or something to the numbers, but remmember the port numbers when trying to connect!)

Then !!!read carefully!!! through the rest of conf file and decide wether you need the SSH part or not. Visit [www.dovecot.org](www.dovecot.org) for more info.

If not then simply change these (only do this if behind a router with your IMAP ports closed unless you know what you are doing!):
```
ssl_disable = yes
disable_plaintext_auth = no

```

Now start the server:
```
sudo /etc/init.d/dovecot start
```(or restart if started)

Test logging into this from your thunderbird client at localhost(or IP from another machine). If using a port offset you need to go back into account settings and manually change the port. In evolution just use localhost:143 or 149 if ssh (+port offset if used ie: 30143). You will not see any new email but if you receive no errors then assume it works so far.

The server is not configured to send mail, so for the sending bit just use your normal SMTP settings as usual.
[/LIST]


_**Getmail:**_
Getmail is very simple, it simply sucks the POP3 mail from your remote mailbox and sends it somewhere.
Create the following. Either do this as root and chown them to user permissions or log in as user to do this (no need for sudos and chowns),
```

sudo mkdir /home/username/.getmail
sudo chown username:adminaccount /home/username/.getmail

sudo gedit /home/username/.getmail/getmailrc

```

This creates the getmail dir + setup. 
In the file thats created we can have one or more pop3 sources, Eg:
```

[options]
#set verbose 1 for debugging
verbose = 0
message_log = ~/.getmail/log

#Set to false to only pick up mail marked as new!
read_all = true
#Set to false to leave a copy on the remote server (may want to also set the above to false if this is the case!)
delete = true


#--------------------------section for each server----------------------
[retriever]
type = SimplePOP3Retriever

#Pop 3 details here 
server = mail.somewhere.com
username = user@somedomain.com
password = somepassword

#if you  want it to go straight into maildir, uncomment this
[destination]
type = Maildir
path = ~/Maildir/

#if you  want it to go straight into maildrop for sorting, uncomment this
#[destination]
#type = MDA_external
#path = /usr/bin/maildrop
#unixfrom = True

#if you  want it to go straight into procmail for sorting, uncomment this
#[destination]
#type = MDA_external
#path = /usr/bin/procmail
#unixform = True
#--------------------------/section for each server----------------------

```
Now set it so noone can read it  but the user/admin as it contains passwords. (u+rwx,g+rwx,o-rwx)
```

sudo chmod 770 /home/username/.getmail

```
Now by typing **getmail ** (by a logged in user) the mail should be delivered to the mailbox of whichever user is logged in and running it. 
However, this is a server and we are logged in as adminaccount so this will not work (unless of course "adminaccount" has a mailbox). 
So we need to do this automatically! However, first I reccomend using switch user and try typing "**getmail --verbose**" in a users terminal to test if mail is recieved,

If all seems well then;

```
sudo gedit /etc/crontab
```
Then for each user add a cron job to getmail using their account.. say every 3, 5 or 10 minutes or something.
We need to add something like:
```

*/5 *   * * *   bob    getmail 
*/5 *   * * *   mary    getmail 
*/5 *   * * *   john    getmail 

```
the */5 means 5 minutes in the cron system,

Thats it, 

You should now have a working mail server that collects remote mail every X minutes. To log in to this simply use a Tbird or whatever client in IMAP mode on the servers IP/port.
If you are planning to just use the thunderbird filters to sort mail then simply make your filters as you need them and then find 

the mailfilters file (or whatever its called, its pretty obvious). 
It can be found in the: ~/.mozilla-thunderbird/....../Imap mail/  structure somewhere (its quite obvious which one it is) 
Copy this to a memory stick so you can copy it to your other clients.
However, I use maildrop for this instead, as it is more centralised and you dont need to install the filters on every machine.

_**Maildrop: (Not *Needed*!):**_ - but has its uses!

Maildrop (or you can use 'procmail' which is less strict and has a different filter syntax that is more complicated IMO) is a bit of a fiddle but can be very useful (and powerful by all accounts) it basically sorts mail into subfolders of maildir (at least thats what we will be using it for here).
[COLOR="Red"]Important -  Creating subfolders in Maildir is not a case of simply making folders with xterm/nautilus as they use a special naming format to create the structure. The best way to make/administer mail folders is to use thunderbird or a mail client to make the subfolders in your inbox. This way they will be created in the special "maildir" format.[/COLOR]

Assuming you have installed the maildrop program (part 1) the next step is to edit/create a file called: 
```
sudo gedit /etc/maildroprc
```
and make the following lines at the top (comment out all stuff already in there if it isnt already):
```

MAILDIR  = "$HOME/Maildir"

```
Now. If you want to add global (forced) sorting on all your users so they all see the same structure (eg. a common junk filter rule) you can put your rules in the above file. However, if you want them to be able to have unique mailfilters at a user level, then create an extension of the above file called ~/.mailfilters that the users can edit themselves (dont forget to chown it). You can also make spam assasin active on this too (see maildrop help)

The most basic syntax examples for these two files is as follows:
```

on its way...when i get home :)

```
More info on these highly powerful filters can be found here:
[http://www.courier-mta.org/maildrop/documentation.html](http://www.courier-mta.org/maildrop/documentation.html)

Now we need to set the getmail delivery location in our "/home/username/.getmail/getmailrc" file(s) for the user(s) who wishes to use this system to maildrop rather than ~/Maildir/. This is self explainatory in the rc file we created above.

Now we can test the setup by logging in as a user and typing "getmail --verbose". The good thing about maildrop opposed to procmail is **the mail will stay on the remote pop3 server if there is any syntax errors **in the filters :)

---

### Post by dgrafix on 2008-03-05
[COLOR="Red"]----------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]
***Part 4 - The Backup solution***
[COLOR="Red"]----------------------------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]

The timed backup:
This uses the sync command to syncronise a backup of your full/part system with a second storage device. The great thing is is that it only deals in what has changed rather than copying everything time and again. It also deletes from the backup anything that has been removed from the original. It is a 'full sync' so dont worry about progressive file pollution of your backup area!

We need a second harddisk for this (you could use a partition but that would half defeat the object) 
I myself am using a usb disk called "USB-bigstore" This needs to be formatted to EXT3.
Now name it using the command (you should "umount -a" before and "mount-a" after):
```
sudo e2label /dev/devicename USB-bigstore
```
**It is really important that the area for the backup is at least the same size or little larger than the data/disk you are backing up!**. For example, my harddisk is 80gig, The backup USB drive is also 80gig to ensure total impossibility of running out of room (because i am not backing up everything on the disk. If i were then i may want a larger backup are as i dont honestly know if any temporary space is needed for caching or something...).

To start with i go to my disk which should now always mount as:
/media/USB-bigstore
because we have named it so.

Make a folder called "fsbackup" or whatever on the usb drive, 
```
mkdir /media/USB-bigstore/fsbackup
```
Then create a file (no sudo!) called "backuplist" and include the folders:
```

/home
/etc
/var

```
This above is an example, you may want to change this to suit you.

Now create a file (no sudo!) called "excludelist" and add;
```

*/.trash
*/.beagle
*/.thumbnails
*/.beagle
*/temp

```
One again for example. This basically is an ignore list and will not backup anything that matches entries in this file. These settings work well for me personally.
[COLOR="Red"]NOTE: If you are attempting to backup the entire filesystem (/) in 'backuplist' for some reason, make sure you add the virtual folders like /dev and /media to the exclude list otherwise you may get big problems.[/COLOR]

Now we need the actual script to back up everything. 
Create a file (no sudo!) called "backup-now" and insert:
```
#!/bin/bash
sudo rsync -a -r --verbose --delete --exclude-from=/media/USB-bigstore/fsbackup/excludelist --files-from=/media/USB-bigstore/fsbackup/backuplist / /media/USB-bigstore/fsbackup
```
If you have changed any names then you need to change accordingly.

Dont forget to give it execution permissions for server adminaccount 
```
sudo chmod 770 /media/USB-bigstore/backup-now
```

Now set up a launcher on the adminaccount's desktop and set it to "app in terminal" and insert the command; "sudo /media/USB-bigstore/backup-now'

Clicking this file should give you a teminal, enter password and backup should begin. 

Confirm backup has worked by looking in fsbackup folder that you have all you should have.

:KS Thats it! You should now have a simple backup system.

You can also turn this into a scheduled weekly/daily backup by using the /etc/crontab system (as described in the mail howto above) but use root as the user. 
[COLOR="RoyalBlue"]Fear not, because as the script and the lists are on the usb drive, nothing untoward can happen if the device is not plugged in (although unlikely to anyway :)[/COLOR]

There are many more cool things that can be done with sync like a second usb hdd for a grandfather>father>son system or simply a daily and weekly system. Also worth a mention is when combined with RAR (or is it TAR?) you can also create DVD size chunks for a monthly backup, although i am not bothering with that this time.

---

