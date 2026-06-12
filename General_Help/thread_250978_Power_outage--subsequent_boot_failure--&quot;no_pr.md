---
title: "Power outage--subsequent boot failure--&quot;no profile for user&quot;--Ubuntu 5.10"
date: 2006-09-04
forum: General Help
---

### Post by computerease on 2006-09-04
This is a lengthy request because it includes what's been unsuccessfully done to recover the system so far.

Before the crash:  The Gnome interface was in use and the programs likely open were Evolution, Opera, GEdit and quite possibly a terminal.
When power returned, on next boot the system would not boot into Gnome. The system failed a file check; "e2fsck could not be run because the drive was already mounted  [Apparently, getting the fs to repair after a crash of this type is no small feat.]"
--------------
Attempted repairs of fs (ext3) with Knoppix and Ubuntu LiveCDs to no avail.  All attempts to execute the process returned very quick responses indicating the drive was clean.  Knowing the process is time consuming, the instantaneous report of "clean" is suspect at best.
In order to get fsck to run and do a repair?
I used the Ubuntu CD and booted to a prompt.  I then used the command
sudo shutdown -rF now
The sudo was probably irrelevant but it's becoming habit.  The -r = reboot and the -F forces fsck to run on the next boot.  [Given the difficulties of this repair, I'm not altogether sure that shouldn'd happen on every boot, PERIOD!]
With the above shutdown command, fsck WILL run.  It REPORTS it has repaired the system but it did not repair the fs properly.  But it did make it possible to reboot the system into a prompt.  Any kernel selection can be so persuaded.  In addition, I was requires to select a fail-safe prompt.
------------------
With my system quasi bootable, it informed me there was no longer a user home directory for my username.  I verified that with ls -aF.  However, I had a backup copy of the directory.  My original was /home/myusername and the backup was /home/home/myusername.  I next created a subdirectory in /home for my username (/home/myusername) and thencopied the backup to the home directory with
sudo cp --copy-contents -p -R -v /home/home/myusername/* /home/myusername
This backup recreated a copy of the username directory in the original home directory.
Next, I ran
shutdown -rF now
This did NOT solve my problem.  After the completion of a forced fsck (which yields no error messages) the boot proceeds and I am informed that e2fsck is not able to complete because /dev/hda1 is mounted. (I have attemted to dismount the drive [sudo umount ...] at the prompt but it continues to be reported as mounted.  Control-D continues the boot.  I am next informed me my .rdmc file was bad.
-------------
I copied an .rdmc file from another Ubuntu installation (a Dapper copy--the failed machine is Breezy).  This got me to a Ubuntu login window (the fsck failure--e2fsck cannot run because drive is mounted, etc., etc., etc.,--is still present) but indicates new failures:
The first message was:
This is the Failsafe GNOME session.  You will be logged into the "Default" session of GNOME without the startup scripts being run.  This should be used to fix the problems in your installation.
We move back to the login screen > Failsafe terminal > Permissions message which reads similarly to the previous message:
This is the ....  xterm session.  You ... a terminal console so you can fix your system if you cannot log in in any other way.  To exit the terminal emulator, type 'exit" and an enter into the windows ...
I would note that a terminal session will recognize the username and password and function accordingly.  It will also ask for the password when sudo it called and I am assuming it executes because if the sudo is not there the commands that require it fail, reporting its need.
-----------------------------
Two messages remain intransigent:
	1.  Your $HOME/.dmrc has incorrect permissions and is being ignored ..., and
	2.  The Gnome session does not last 10 seconds.
This last message suggests to me the session is failing to start, period.

The first ~/sxsession-errors file read as follows:

/etc/gdm/PreSession/Default: Registering your session with utmp
/[same path as above] running: /usr/bin/x11/sessieg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0. Xservers" -l ":0""username"

/etc/gdm/Xsession: Beginning Session setup ...

(gnome session: 8466): libgnomevfs - WARNING **: Unable to create ~/.gnome2 directory: Permission denied

Could not create per-user gnome configuration directory '/home/username/.gnome2/': Permission denied.

What follows is the Gnome failsafe message (again):
Your $HOME/.dmre file has incorrect permissions and is being ignored.  This presents the default session and language from being saved.  File should be owned by user and have 644 permissions.

Subsequent to this I've run chown with -R for the .gnome2 directory (I know--dumb move--it seems to be a per-session directory, not present when a user is not logged in and present when the usere IS logged in--it is not present in the user directory when I'm logged in and absent when I'm not -- but I didn't realize that when I did the permissions thing ), giving ownership both by username and by number.  I've also run chown for the entire user directory, setting permissions as 644, 700 and 744 to no avail.  I've used the command in multiple forms, all to no avail.  The last form was
chmod 700 ~

[I also attempted to remove the directory but was prohibited because it was not empty.  I did not empty it and try again.]

----------------------
I set up a second user with the original username and the number two:  myusername2.  This permits me to boot all the way into gnome desktop, albeit the default configuration.
To accomplish that I did the following steps from the failsafe prompt of the original username:
sudo groupadd groupname   [for the creation of the username2 group
sudo useradd -m -g username2 groupname
id username  [to get the group membership names from the original user so they can be assigned to the new user]
sudo useradd -m -g username2 -G and all of the groups by name, separated by commas with no spaces in between.
sudo passwd username2

Having done that, as noted above, I am able to log into a gnome desktop.  However, if I attempt to use sudo I am told I do not have permission to do that because the user is not listed in the sudoers file.  This is a catch 22 in that one has to be in the file to open the file as su to add the user.

----------------
So far, the successful login of a new user proves that the installation of Ubuntu and the Gnome interface is intact.  However, due to a power failure (there is no UPS protecting the system ... you can bet your bottom dollar there will be in the very near future), the disorderly shutdown of the system left the gnome interface for the logged on user in a corrupted condition.  Given the cause of the problem, and given the number of web discussions I've found with individuals gropping around for a solution, I've concluded this is not an uncommon problem.  (Now that I think about it, I've had the same, or very similar problem before with Mandrake/Mandriva ... which was solved by abandoning the original user.)
------------------------
The latest ~/xsession-errors file read as follows:
/etc/gdm/PreSession/Default: Registering your session with utmp and utmp
/etc/gem/PreSession/Default:  running: /usr/bin/X11sessreg -a -w /var/log/wtmp
/etc/gdm/Xsession Beginning session setup ...
No profile for user "myusername" found
gnome-session 8903: libgnomefsf-WARNING **: Unable to create `?.gnome2 directory: Permission denied.
Cound not create per-user gnome configuration directory '/home/myusername/.gnome2/':  Permission denied.
-------------------
The one appeal for help on this issue, which is apparently the same as the problem I'm chasing is found at:
[http://www.ubuntuforums.org/archive/index.php/t-195258.html](http://www.ubuntuforums.org/archive/index.php/t-195258.html)
There is no reply and it was posted in June.
------------------
One site with a problem similar suggested
apt-get install ubuntu-desktop
That created some interesting varients on the boot but left the original problem intact.
-----------
I suspicion the core of the problem is to be found in the "no user profile" message and that solving this problem will return the boot sequence to normal.  Where ahd how do I tackle the "user profile not found" issue?  I realize there may also be issues concerning 

Thank you in advance for any advise on solving this issue.  I've worked on it several hours a day for better than a week with limited success.

Addendum:
What APPEARS to be uncommon is a definitive solution on its cure.  That which was done above is either the result of following the existing instructions I've found on various pages or what appears to me to be a logical possibility to correct a problem, given the error messages I've encountered.
It would appear to me that, given the potential of inopertune power failure and the inevitable results that can come of that (ergo, the failures listed above which so many have struggled) there should be a relatively straight-forward set of steps to restore the functionality of gnome or whichever of the boot sequence configurational problems such a power outage might cause.
It may be my lack of a sufficiently sophisticated search, but I have not been able to find such a solution on the Ubuntu discussion sites, the Gnome site or, for that matter, on sites that discuss this problem with RedHat, SUSe, Fedora, Debian, Slackware, etc..  I have been both flavor-specific in the searches and generic.
As published resources I'm using Keir's "Beginning Ubuntu," Kiddle et. al.'s "From Bash to Z Shell," Rankin's "Knoppix Hacks," and Shroder's "Linux Cookbook."
I do not want to blow away this installation because it has been significantly configured to my needs and tastes, including a huge software installation base as well as programs specifically configured for my use.
I DO have a backup of home directories and all data (done with scp, sftp and winscp).
HELP!! Please?

---

### Post by Wolki on 2006-09-17
That's quite an interesting case you've got there. something like this hasn't happened to me yet, though I've lost power once or twice...

First, to grant the second user sudo rights, do "su username", then you have a shell as that user and can edit sudoers with "sudo visudo".

If you are logged in as the first user (in a virtual console or as the second user su'ed to the first user), can you enter your home directory? If you do a ls, will it show you what files there are? Can you post the output of "ls -la /home"?

By the way, .gnome2/ should always be there. I suspect there are permission problems.

If everything else fails, you could try to import the settings of the first user to the new user; or maybe better, remove the first user, create it again, and reimport your backups.

Steps to do this:
- have a backup (either of your current home or an older version)
- remove your first user (with userdel or the admin tools from the second user?
- add the first user again
- make sure the sudo rights are present (visudo if necessary), and that the usserid is the same (likely 1000)
- login as that user to see if it worked
- make a quick copy of the fresh home somewhere, in case we need it)
- copy the not hidden files form the backup to yor new first user.
- try and see if it still works
- copy the hidden files from the old to the new user, except the .gnome directories
- see if it still works
- copy the .gnome directories, possibly one subdirectory after the other, and try regularly to see if you can still login
If something fails, restore that stuff from the copy of the empty directory - that file was likely the cause of the problem.

---

