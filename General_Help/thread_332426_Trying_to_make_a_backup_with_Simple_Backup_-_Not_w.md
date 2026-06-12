---
title: "Trying to make a backup with Simple Backup - Not working..."
date: 2007-01-06
forum: General Help
---

### Post by jcroot on 2007-01-06
Hi Guys!

I'm trying to make a backup with SBackup but is not working, I followed this guide:
[http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)

And everytime I hit Backup Now it doesn't do anything, not errors, not messages at all...

I have Ubuntu 6.10 Edgy

---

### Post by orb9220 on 2007-01-06
Did you get the prompt for password when you ran it? If not then the program is not running sudo so that you can save to /var.  You may try changing the Destination to your home folder, If that works then it is a permissions thing.

Sorry couldn't be more help.

---

### Post by jcroot on 2007-01-06
> **orb9220 said:**
> Did you get the prompt for password when you ran it? If not then the program is not running sudo so that you can save to /var.  You may try changing the Destination to your home folder, If that works then it is a permissions thing.

Sorry couldn't be more help.

Yes, it ask me for my password everytime I tried to ran the program... I don't know why is not working, I mean I think I'm the only one with this problem.

---

### Post by Zill on 2007-01-06
IIRC SBackup does not give any messages after the backup routine has started other than a process ID number.  SBackup then runs in the background while the data is gzipped and saved.  Check your SBackup config settings to see where your default directory is set to (typically /var/backup) then take a look at that after a while.  You should see your backup waiting in there!
Then use SBackup restore to select the backup you want to restore from and all your files should be listed.
HTH.

---

### Post by jcroot on 2007-01-06
> **Zill said:**
> IIRC SBackup does not give any messages after the backup routine has started other than a process ID number.  SBackup then runs in the background while the data is gzipped and saved.  Check your SBackup config settings to see where your default directory is set to (typically /var/backup) then take a look at that after a while.  You should see your backup waiting in there!
Then use SBackup restore to select the backup you want to restore from and all your files should be listed.
HTH.

Thanks for your reply, I check my settings and the folder where my backup is suppose to be but there is nothing there, I don't get any error messages, not even the id message thing. Do you know how long I have to wait for the backup to completo? I don't have that many files to backup, really I just want to test this backup tool.

Do you know any other backup tool?

---

### Post by Zill on 2007-01-07
After you have hit the "Backup Now!" button SBackup should immediately show a dialog box advising that "A backup run is initiated in the background" and also a process ID number? If you don't get this then I can only assume that the settings are incorrect.

Have you changed any of the default settings?  It should work "out of the box"!  However, if you want "timed" backups then you will have to change the settings on the "Time" tab, then hit "Save".  With "timed" backups no messages at all are produced, the files are just silently backed up :-)

My full backup is approximately 800MB (gzipped) which takes about 15 minutes to run.  However, this duration is due to my backup destination being an NFS mount on another PC.  If the backup is to a local drive (such as /var/backup) then it should only take a few minutes to run.

I have used SBackup on two PCs for several months now and it seems to be very simple and reliable.  Once set up it just runs in the background automatically every day and so I don't even need to think about it :-)

ps. I am currently using Dapper (6.06) but I assume it will also work with Edgy (6.10).

---

### Post by cpbl on 2007-01-07
{\gripe I've been suffering through and reporting bugs in simple-backup for a year.  I do not understand: what is the recommended backup software for Ubuntu? There should be one amongst the set of the *most basic* required desktop functionality softwares and it should work!  Nevertheless, I've stuck with it, since I love the basic model of simple-backup, the ability to use remote (via SSH) directories, the regexp specification, etc}

I have the same behaviour, except that it started spontaneously -- things used to be working for me.  Try running it from the command line so that you can see the errors:

sudo sbackup

For me, the process ID is reported in the GUI but becomes defunct after about 10 seconds. You can see what is causing the error as above.  Then, you can submit a bug report (launchpad.net) if the error ought to be dealt with properly through the GUI or etc.

c

---

### Post by jcroot on 2007-01-07
> **Zill said:**
> After you have hit the "Backup Now!" button SBackup should immediately show a dialog box advising that "A backup run is initiated in the background" and also a process ID number? If you don't get this then I can only assume that the settings are incorrect.

Have you changed any of the default settings?  It should work "out of the box"!  However, if you want "timed" backups then you will have to change the settings on the "Time" tab, then hit "Save".  With "timed" backups no messages at all are produced, the files are just silently backed up :-)

My full backup is approximately 800MB (gzipped) which takes about 15 minutes to run.  However, this duration is due to my backup destination being an NFS mount on another PC.  If the backup is to a local drive (such as /var/backup) then it should only take a few minutes to run.

I have used SBackup on two PCs for several months now and it seems to be very simple and reliable.  Once set up it just runs in the background automatically every day and so I don't even need to think about it :-)

ps. I am currently using Dapper (6.06) but I assume it will also work with Edgy (6.10).

Thanks for your reply man, well I'm using the recomend settings for the sbackup, I didn't change anything at all and after I hit "Backup now" It doesn't do anything, not messages, no proccess ID, nothing... I let it wait 5 minutes and I still don't see any messages, I also tried using custom settings and save the settings and then click Backup Now but still not luck...

---

### Post by Zill on 2007-01-07
All I can think of is that sbackup must have a problem with Edgy.  I have had no problems with Dapper or Breezy so can't suggest anything else :-(
Has anyone else got it to work with Edgy?
Otherwise you may want to contact the developers via [http://sourceforge.net/support/getsupport.php?group_id=145360](http://sourceforge.net/support/getsupport.php?group_id=145360)

---

### Post by jcroot on 2007-01-07
> **Zill said:**
> All I can think of is that sbackup must have a problem with Edgy.  I have had no problems with Dapper or Breezy so can't suggest anything else :-(
Has anyone else got it to work with Edgy?
Otherwise you may want to contact the developers via [http://sourceforge.net/support/getsupport.php?group_id=145360](http://sourceforge.net/support/getsupport.php?group_id=145360)

Thanks, I will contact them, do you know of any other backup software for Ubuntu 6.10?

---

### Post by Zill on 2007-01-07
Sorry, I don't know of any other simple backup software for Ubuntu.  I used to use Mandriva, which had a good simple backup system built in to the distro.  However, when I moved to Ubuntu the only similar app I found was SBackup.  All the clever folk seem to prefer writing their own scripts :-(
Hope you find something.

---

### Post by nix4me on 2007-01-07
i just installed Sbackup on my edgy machine and tried to do a manual backup of my home folder and it never spit out a file.  Got the message saying is was launched in background, then nothing.

nix4me

---

### Post by nix4me on 2007-01-07
Check that...

i specified my home dir to store the backup and it actually stored the backup somewhere else.  It went to /var/backup for some reason.  Strange since the default is /var/backups and i said put it in /home/username.  It used neither one.  :)

nix4me

---

### Post by jcroot on 2007-01-07
There are some files in my /var/backups directory...

Check out this picture:

[http://img151.imageshack.us/img151/7066/screenshot1ga4.png](http://img151.imageshack.us/img151/7066/screenshot1ga4.png)

Is there my backup file? I didn't specify this directory for the backup so why is saving my backup files there? can I delete all files under /var/backups  ?

---

### Post by nix4me on 2007-01-07
No, those are not your backup files....and don't delete them either.

My files were in /var/backup...not /var/backups.  The dir is owned by root so i had to use root nautilus to view them.

From looking at your screenshot, it looks like you don't have a /var/backup folder.  Sorry, i can't help.

nix4me

---

### Post by Zill on 2007-01-08
nix4me:  I don't think you should try to save the backups to /home/username as this is one of the locations that gets backed up - if SBackup is run more than once it would just keep backing up the backups etc etc etc... :-(

jcroot:  I can confirm that these files are not from SBackup - it looks like it isn't generating the /var/backup directory.

---

### Post by Cariboo1938 on 2007-01-08
> **jcroot said:**
> ....... I mean I think I'm the only one with this problem.No you are not the only one... I have the same problem: I try to use "Simple Backup Suite 0.10", which I found under 
-->System
-->Administration
-->Simple Backup Config
for a system backup.
Under tab "Destination" I chose the desktop as lokal backup directory. 
When I click the button "Backup Now!" I get the message: 
> A backup run is initiated in the background. The process id is: 17483.
My HDD starts working and after a few minutes the HDD indicator light goes out.
I close the "Backup Properties" window. There is no backup file/directory on my desktop. There is no other message either. 
Can somebody give me an idea what I did wrong?

---

### Post by Zill on 2007-01-09
Cariboo1938: As I mentioned above, you may have problems simply because SBackup is in a loop if you set the desktop as the destination directory.  Desktop is a subdirectory of /home/username which is the default source directory.  By setting the desktop also as the destination directory SBackup is trying to backup its own data over and over again, which may be the cause of your problem.
Try using the default destination of /var/backup and see if it runs correctly then.

---

### Post by bobbob1016 on 2007-01-09
I have a similar problem, the backups go to /var/backup/ (I have opened a zip in there as root and the files I wanted backed up are there).  However, I told it to backup to a network SMB drive I mounted on the desktop.  The file is not moved there.  I can move files and things there, I followed the guide to mount the drive on ubuntuguide.org.  The zipped file never gets placed there.

And yes, I did the "Custom Backup Settings" and put the backup destination as the Backup folder (which is mounted as the network drive).  I can see where that might confuse the program, and have it go to the default /var/backup/ but I need to know how I can get around this.

---

### Post by Zill on 2007-01-09
bobbob1016: I would guess that your problem may be with file permissions.  SBackup works as root and expects the destination directory to be owned by root.  An SMB mount on the desktop is probably owned by a user, rather than root.  If you can get an SMB mount owned by root then it may work - but I can't help with this as I don't use Windows or SMB - sorry.

---

### Post by bobbob1016 on 2007-01-09
Ok, that makes sense.  I'm not using Windows either in this transaction, I just thought it'd be easier since I know smb is working, I just didn't want to do a thread hijack.  I'm going to post for help with this then.  Thanks.

---

### Post by Cariboo1938 on 2007-01-09
[SIZE="2"]**Zill:**[/SIZE]  IT WORKS!:-\" 
Thank you for the hint. I figured out what happened: 
Simple Backup [COLOR="Red"]does NOT create the destination directory[/COLOR] which you can define under the Simple Backup Config "Destination Tab". 
[COLOR="Red"]*_One has to create it (as root) before you start Simple Backup._*[/COLOR] It has already to exist before one selects it. 
I didn't have /backup under /var therefore no backup files were created. 
I didn't have a /Desktop directory either.  
To run BACKUP I started -->System -->Administration -->Simple Backup Config. 
Here I was asked for my  password. After that, I just followed the instructions.
For people who are interested, I attached some ScreenShots of the whole procedure.

---

### Post by Zill on 2007-01-10
Cariboo1938: :-)
Thanks for pointing out that the destination directory has to be created by root for SBackup to work - a useful tip.

---

### Post by fadder on 2007-01-10
Do such backup scripts have any advantange over simple use of rsync?
e.g.

for i in Dir1 Dir2 Dir3   # whichever directories are wanted
do
  rsync -av --delete $i /media/usbdisk/Backup
done


Which just copies across (or deletes) any files which have changed since the last time. 
If I wanted a dated copy I use a script to use label=`date +%F` to set the name of the directory. The advantage of rsync is that the backup dir is identical to the one being backup up. Veyr resistant to interupts too.

---

### Post by Zill on 2007-01-10
> Do such backup scripts have any advantange over simple use of rsync?
1)  SBackup creates a gzipped file, taking up less space than the original data.
2)  SBackup automatically sets up a cron job in a nice user-friendly way.
3)  SBackup uses a GUI to make life "easy" for us non-technical folk!

Other than that, if console commands and scripting are your thing then rsync is probably ideal :-)

---

### Post by weigh2tall on 2007-02-03
Hi,
  I've been reading these forums for a few months now as I've dipped my way into ubuntu, but now I've got a problem that I can't seem to find the solution for and I'd like to see if I can get some help.  

Sbackup ran fine when I first installed it and I believe that I set it up to do an auto-backup every so often, well I think it started it the other day and got screwed up somewhere in the process, anywho, now when I try to launch the config program different things happen.  If it's the first time I start it after restarting the computer, I get prompted for my password and then, the taskbar shows that it is starting but when the "starting Sbackup" on the task bar goes away, there's a quick flash of a dialog box that disappears before I can see what it has on it.  The box appears to be blank.  If I start it again, I don't get prompted for the password but the same thing happens, quick pop up and then nothing.  

I've uninstall, reinstalled several times to no avail, through synaptic and apt-get.  Any ideas?   I am a noob so if there's any info you need let me know.

---

### Post by Zill on 2007-02-03
weigh2tall:  It may be that there is an uncompleted sbackup process still running which may prevent a new instance starting properly.  I would open a terminal and try the following command:
```
sudo killall sbackup
```
That should close down any remaining sbackup processes and you should then be able to start it again.

Just my limited knowledge though - if anyone else has a better idea please let us know :-)

---

### Post by weigh2tall on 2007-02-03
I tried and it said "no processes killed"  

how do you run sbackup from terminal?  

when use  'sudo sbackup' or 'sbackup' I get command not found?  
Maybe if I can run it from terminal I'll get some other messages?

---

### Post by Zill on 2007-02-03
weigh2tall:
> I tried and it said "no processes killed"
Try:
```
sudo killall sbackupd
```
> how do you run sbackup from terminal?
```
gksudo simple-backup-config
```

---

### Post by weigh2tall on 2007-02-05
Thanks a million.  

When I ran this:  ~$ gksudo simple-backup-config

I got this:
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 681, in ?
    i = SBConf()
  File "/usr/sbin/simple-backup-config", line 200, in __init__
    self.widgets.get_widget("time_hour").set_value( int(croninfo[1]) )
ValueError: invalid literal for int(): *

I changed the value at line 200 to 0 and the config screen came up and worked like a charm.  

Incidentally, how to you quote code?

Thanks again.

---

### Post by Zill on 2007-02-06
weigh2tall:  Glad to hear you got it working again.  Looks like something got screwed-up somewhere - the internals of sbackup is a mystery to me so I wouldn't have known where to start with your error message.  Well done :KS 

> Incidentally, how to you quote code?
When you reply to a message, the text box has a button at the bottom marked "Go Advanced".  Click on this and additional icons appear at the top of the text box which tags the selected text to insert quotes and code boxes etc.  Alternatively, I suppose you can just type the appropriate tags but I find the icons easier :-)

---

### Post by weigh2tall on 2007-02-06
Thanks, just realized I said 'how to you quote code' should have been do.  Oh well.

---

### Post by Cactus Sediento on 2007-03-01
Hello, 

      I have a similar problem. Sbackup is not working
      
      It worked fine at the begining, with automatics daily backup but around 18 dec 2006 it stopped making backups (a package upgrade probably?)

      When i make a gksudo simple-backup-config, i obtain the following:

> $ gksudo simple-backup-config
GTK Accessibility Module initialized

(simple-backup-config:6738): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


there is no lock at root. The target directory is the standard /var/backup owned by root

somebody knows what is hapening?

---

### Post by weigh2tall on 2007-03-01
This is just an idea and I'll admit I'm a noob, but open your System monitor and see what dbus-dameon and dbus-launch are doing?  If you're adventuresome you could try ending them and see if that fixes the problem.  Again, I'm not sure if that's a viable solution and maybe someone else will say I'm misguided.

---

### Post by Cactus Sediento on 2007-03-02
Thanks a lot,
       I followed your suggestions, but unfortunaly the problem is not fixed. there were two copies of dbus-daemon and one of dbus-launch all three were sleeping.  I finished all of them one after the other. In some cases X restarted,  in others system restarted but without being able to access to HAL. At the end  making a full restart i ended with the two copies of dbus.daemon, and the one of dbus-launch (all sleeping as at the begining), and behaviour of simple backup did not changed, still not working properly. 
        During this months i installed and uninstalled kubuntu....could this be related?

---

### Post by DarkW0lf on 2007-03-03
Can Sbackup be set to split the backup over several CDs or will that have to be done seperately ?

---

### Post by weigh2tall on 2007-03-03
@ Cactus,
  I'm not sure where to go from there, but it seems to me that you might have too many dbus-daemons running.  I could be wrong about that though.  

@ DarkWolf
  I really don't think that's possible, but then again I could be wrong.

---

### Post by Cactus Sediento on 2007-03-04
looks like somegthing related to dbus....but look....dbus stuff i have runing is the following

> $ ps -ax |grep dbus
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 4439 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 7702 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
 7705 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session /usr/bin/gnome-session
 7706 ?        Ss     0:00 /usr/bin/dbus-daemon --fork --print-pid 8 --print-address 6 --session
 8395 pts/1    R+     0:00 grep dbus


when i make a backup now it says that there is another sbackup demon....

> $ gksudo simple-backup-config
GTK Accessibility Module initialized

(simple-backup-config:8240): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
E: Another Simple Backup daemon already running: exiting


but the only sbackup demon i have is the one just anounced in a pop up window by simple-backup-config : 8262....now sadly defunct

> ~$ ps -ax |grep backup
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
 8238 pts/0    S+     0:01 gksudo simple-backup-config
 8240 ?        Ss     0:02 /usr/bin/python /usr/sbin/simple-backup-config
 8262 ?        Z      0:00 [sbackupd] <defunct>
 8339 pts/1    R+     0:00 grep backup

why sbackup complains about another daemon?....where is it?

---

### Post by ryd92 on 2007-06-02
If you are sure no process are running, simply type :
      sudo rm /var/lock/sbackup.lock
--

---

### Post by H.E. Pennypacker on 2007-06-03
It is very upsetting for SBackup to not simply state that the process has begun, and also indicate when it has ended.  Expecting people to open System Monitor to check on the progress is ridiculous.  I have never heard of an application not even bothering with the progress.  The least it could do is provide a progress bar.  That doesn't sound impossible.  

The process ID is worthless...why not just create a progress bar?  Seems like applications have been doing this for, oh maybe, a million years.

---

### Post by Zill on 2007-06-04
As I understand it, SBackup is intended to run quietly in the background until completed, allowing other work to continue without any disturbance.  A "progress bar" is therefore unnecessary and is also, in my opinion, undesirable.

It works for me!

---

### Post by freesitebuilder on 2007-06-06
If it's running in the background, what happens with files that are being created or edited during processing?

I've managed to make it run using the terminal - sudo sbackupd - as suggested in the sbackup forum, but the GUI loads without asking for a p/w, doesn't save config settings, and doesn't run a backup.

---

### Post by Zill on 2007-06-06
> If it's running in the background, what happens with files that are being created or edited during processing?

My _guess_ is that SBackup will save a snapshot of the file "as is" when it gets to that particular file.  Other ideas anyone?

---

### Post by weigh2tall on 2007-06-06
Either that or (this maybe far left field) if it can't get a lock, it passes on to the next file with the intend to catch it next time the incremental runs.   However, I'd have to agree that Zill's answer is probably the most accurate.

---

### Post by dsewell on 2007-07-26
Did anybody find a fix for this?

I have the same problems.  My settings are not saving.  And when I press backup now, nothing happens.

Any ideas / tips?

Thx

---

### Post by Zill on 2007-07-26
dsewell:  I suggest you carefully review this thread from the beginning - it covers a lot of hints and tips about getting SBackup to run correctly.

I run SBackup daily on two PCs with Dapper (6.06) without any problems at all - just make sure you follow the advice in this thread and only change the default settings if you are _sure_ what you are doing ;-)

I am not sure what version of Ubuntu you are using but maybe someone else will confirm that SBackup also works fine on Edgy and Feisty...

If you still have problems then post back with exact details of Ubuntu version, what you have done and what you see.

---

### Post by weigh2tall on 2007-07-26
Zill, I'll confirm that Sbackup will work on Fiesty.  It just ran an incremental last night.  I can still get to the config menu as well.

---

### Post by dsewell on 2007-07-27
Alas, I'm still having problems getting SBackup to run.

I have read the thread start to finish, and tried running from the command line.  I get the following:

> ubuntu@ubuntu:/var/www$ gksudo simple-backup-config

(simple-backup-config:14176): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 490, in on_main_radio_group_changed
    self.widgets.get_widget("vbox12").set_sensitive( False )
AttributeError: 'NoneType' object has no attribute 'set_sensitive'
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 490, in on_main_radio_group_changed
    self.widgets.get_widget("vbox12").set_sensitive( False )
AttributeError: 'NoneType' object has no attribute 'set_sensitive'
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 399, in on_save_clicked
    tail = "\troot\tif [ -x " + self.conf.get("places", "prefix") + "/sbin/sbackupd ]; then " + self.conf.get("places", "prefix") + "/sbin/sbackupd; fi;"
  File "/usr/lib/python2.4/ConfigParser.py", line 511, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'places'
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 399, in on_save_clicked
    tail = "\troot\tif [ -x " + self.conf.get("places", "prefix") + "/sbin/sbackupd ]; then " + self.conf.get("places", "prefix") + "/sbin/sbackupd; fi;"
  File "/usr/lib/python2.4/ConfigParser.py", line 511, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'places'
Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 391, in on_backupnow_clicked
    pid = os.spawnl( os.P_NOWAIT, self.conf.get("places", "prefix") + "/sbin/sbackupd" )
  File "/usr/lib/python2.4/ConfigParser.py", line 511, in get
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'places'


As a newb this does not really help me unfortunately.  Can anybody interpret this and tell me what this means and if there are any clues to enable me to get SBackup running?

Thanks in advance.

Dean

---

### Post by dsewell on 2007-07-27
Sorry, forgot to say I'm running Ubuntu Edgy.

Thx again.

---

### Post by Zill on 2007-07-27
dsewell:  Thanks for the info - very puzzling though :confused:

We know it works on Dapper and Feisty - maybe someone can confirm that it works OK on Edgy as well.

All I can ask are the obvious questions:
Was the Ubuntu installation fresh or an upgrade from an earlier version?
Is the installation standard Edgy or have you "tweaked" it with non-Edgy packages?
Is the SBackup package from the official Edgy repository?
Have you changed any relevant permissions?
Have you changed any SBackup default settings?
Have you checked the dbus-daemon as described by weigh2tall?
Make sure that the default SBackup directory /var/backup (not var/backups!) exists and is owned by root.
Have you tried a reboot? (Yes, I _used_ to be a Windows user :-) )

Otherwise, it looks to me like it may be a DBUS problem - you could file a question at [https://answers.launchpad.net/ubuntu]("https://answers.launchpad.net/ubuntu")

---

### Post by dsewell on 2007-07-28
Thanks.  Answers as follows:

fresh or upgrade -- **Fresh Install**
standard or tweaked Edgy -- **Standard**
SBackup Official -- **Yes**
Changed permissions -- **Not to my knowledge**
Changed settings -- **No**
dbus-deamon -- You have lost me on this one.  Let me do some digging!
default directory -- **Yes,** its /var/backup and is owned by root.
reboot -- **Yes, but still have the problems**

I will get back on the dbus-deamon thingy...

This is the baffling thing.  The set-up is new, and pretty standard so no idea why I'm getting issues.

Cheers again.

---

### Post by tuco penguin on 2007-07-28
I've been struggling with sbackup for a few weeks now and was about to give up and try another backup solution when I got it working.  Thought I would post my key observations in case it helps someone else in the future.  I am running sbackup 0.10 on Ubuntu Feisty:

A)  On first run after installing, sbackup never seems responsive.  After changing my settings and saving them, it does not give the prompt that it has saved my changes, but in fact it seems that it has if I quit and start it again.

B)  As someone else pointed out, root needs to create the backup directory.  Don't know how critical this is, but in my now-working configuration, my backup directory on a networked drive (samba share) was created by root.

C)  Sbackup does not present warning messages if it is not working, so beware and look for the backup archives before assuming that the process it says it created is actually working.

D)  There seems to be a case-insensitivity bug in the "exclude" feature.  I had excluded a directory that contained a capitalized directory in the path, and later noticed that it was saved in all lowercase.  I think that this was causing the backup process to fail, since it was trying to exclude a path that did not exist.  I went back and edited this path name manually and this seemed to make the difference between a processes that claimed to be running and one that actually was.

Apologies if some of this was covered in the posts above.  I gave a quick scan but didn't get to read the entire thread.  I hope this helps someone in the future.  There doesn't seem to be much else out there for Ubuntu backup utilities with a friendly GUI like sbackup right now.

---

### Post by Edward Hatfield on 2007-07-30
I've been having the same problems with sbackup and, for me, the answer was to create the '[places]' section in '/etc/sbackup.conf' with the entry 'prefix = /usr'.  That made it all work for me.

---

### Post by jonrkc on 2007-08-24
I've rapidly read this whole thread and will go back and re-read it, but in my first reading I didn't find any solution to my problem.  I'm receiving the "Another sbackup daemon is already running; exiting" message when attempting to do sbackup as a cron job.  Yet I can run it manually just fine.  This just started happening on Aug 3 and I have made no changes to my system that I'm aware of (some change had to have been made, though).  

I even stopped the dbus daemon and tried to run sbackup as a cron job, and it still behaved in this odd way.  With ps ax I can see nothing in the list of processes that would obviously be confused as a sbackup daemon.  

I completely removed (purge option) sback and reinstalled it.  Same situation.

Totally mystified at the moment.

EDIT for update: Have now read the entire thread for the second time.  Still mystified.  Still able to run from command line as root, "/usr/sbin/sbackupd" and it backs up just fine to the directory I've been using all along, with the same options I set it up with to begin with.  Just won't run automatically because it thinks it's already running!

---

### Post by robinlennox on 2007-09-15
I was having the same issues but got it to work finally...

What I did was:

1. Remove Simple Backup
2. Remove the file /etc/sbackup.conf
3. Installed Simple Backup
4. Created a Folder where i wanted it to be using my own login details (Not Root)

The only Issue I've had, is if I decide to move to a diffrent folder it all stops backing up again so i need to go through the process above... again!

---

### Post by jonrkc on 2007-09-15
Isnt' it strange behavior?  Such a useful program, but not too cooperative!

I'll try what you did and see if that solves it for me.  Meanwhile I've been doing daily backups OK using the "at" command.  I put it in my .xinitrc file so that it gets done.  If I didn't turn the machine off at night of course, it wouldn't work except the first day....

Even so, SimpleBackup thinks there's another sbackupd running EVERY TIME, and says it's exiting, but it really doesn't exit; it backs the files up.  Sometimes twice!  :)

And yesterday I got mailed messages -- FOUR of them -- that another sbackupd was running, I'm exiting -- but only one backup was done.  

Strange.

---

### Post by Zill on 2007-09-15
robinlennox:  As Sbackup works as root, your following line worried me...
> 4. Created a Folder where i wanted it to be using my own login details (Not Root)
SBackup (v0.9-1) is the latest version for Dapper (v6.06) and should work "out of the box".  It may be worth testing the program again with all the **default** settings, including the destination directory as /var/backup (owned by root).
When the program runs OK with the default settings it should then be possible to tweak it one step at a time until the configuration is as you like it :-)

---

### Post by robinlennox on 2007-09-15
> **Zill said:**
> robinlennox:  As Sbackup works as root, your following line worried me...

SBackup (v0.9-1) is the latest version for Dapper (v6.06) and should work "out of the box".  It may be worth testing the program again with all the **default** settings, including the destination directory as /var/backup (owned by root).
When the program runs OK with the default settings it should then be possible to tweak it one step at a time until the configuration is as you like it :-)

Hi Zill,

I'm running 7.04 just haven't updated my profile to reflect that!

I think it's very strange that i need to create a folder in with my user permissions... seems to be that the program is running using my login.... Wired!

This is when Windows Schedule Manager becomes useful! :lolflag:

---

### Post by Zill on 2007-09-15
Robin,  Did you install SBackup from the standard repos in the usual way? i.e. with synaptic or apt-get as root?  If so then I am puzzled as to how you can run it as a user :confused:

When you run Simple Backup Config from the Admin menu does it first ask for your user password?

---

### Post by robinlennox on 2007-09-15
> **Zill said:**
> Robin,  Did you install SBackup from the standard repos in the usual way? i.e. with synaptic or apt-get as root?  If so then I am puzzled as to how you can run it as a user :confused:

When you run Simple Backup Config from the Admin menu does it first ask for your user password?

I used synaptic, i am running the program in privileged mode (root), however it wouldn't backup unless the backup folder was created by a user.... I don't understand this either....

---

