---
title: "Kalarm help"
date: 2007-07-13
forum: General Help
---

### Post by Red Moose on 2007-07-13
Hello, 
I'm trying to perform a scheduled feisty to gusty upgrade with Kalarm.  I have to schedule it for 2:00 AM because my internet provider (hughes) won't allow me download large files at any other time.  The problem is, 'apt-get upgrade' requires a root password and If I have to be there to enter it, then I may as well not schedule it. :)  Is there any command to automatically enter the password or any other work around?
Any help at all would be greatly appreciated.
Thanks!

---

### Post by bettlebrox on 2007-07-14
You can use the "at" command to schedule commands to run. I'd don't suggest running an upgrade unattended, but you can use apt-get with the -d flag to only download the packages and you can install them the next day.

E.G.
sudo at 2:00
at>apt-get update
at>apt-get -d -u dist-upgrade

ctrl-d to exit. "sudo atq" will show you the job scheduled to run as root.

---

### Post by Nythain on 2007-07-14
open up a terminal then type
sudo visudo
this should open up the sudoers file in your terminal text editor that is assigned in your whatever file (usually its either nano or vi, but could be different)
then add a line that looks like this:
<username> ALL=(ALL) NOPASSWD: /usr/bin/apt-get
replacing <username> with your account user name... my example:
rune ALL=(ALL) NOPASSWD: /usr/bin/apt-get
rune is my account name

save the changes and exit the editor (in nano this is done with ctl+o  to save teh changes then ctl+x to exit)

this makes it to where that user no longer needs to input a password for the command apt-get

---

### Post by Red Moose on 2007-07-14
Thanks a lot!   I think I'll try Nythain's idea, because I like to use the GUI as much as possible. :)
But, why shouldn't I leave an upgrade unattended?
Also, what's the difference between apt-get upgrade and apt-get dist-upgrade?

---

### Post by Red Moose on 2007-07-14
I think I really messed it up now....
I tried adding that line, but nano wouldn't save it.  I saved it but when I came back the line wasn't there.  So I tried Gedit.  I opened Gedit as root, added the line, and tried to save it.  Turns out I had to change the permissions on it even more to allow the root user to save it.  After that I saved the line in it.  
Now, whenever I try to use sudo it  it tells me etc/sudoers is mode 0660, should be 0440.  I can't do anything the requires root access.  Am I going to have to reinstall?  It seems the only way I can change the sudoers file is login as a root user and I can't do that. 
I really need help, Please!

---

### Post by Red Moose on 2007-07-14
Well, I think I'm going to try a re-install.  Unless anyone has anymore ideas...

---

### Post by bettlebrox on 2007-07-15
Boot into single user mode and chmod the file. I think it's listed as "safe mode" at the boot prompt.

>But, why shouldn't I leave an upgrade unattended?
your upgrading from one version of Ubuntu to another, and important packages might be removed and leave the system unbootable

>Also, what's the difference between apt-get upgrade and apt-get dist-upgrade?
upgrade only upgrade packages, dist-upgrade is to upgrade to a different version of the OS. See the man page:

 upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list.

dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary.

---

### Post by Red Moose on 2007-07-16
Oh, too bad, I already re-installed...
I scheduled to upgrade tonight (or, rather tomorrow morning) to the newest version of feisty with the 'at' command.  I was going to have to download a lot of packages to get Kalarm running anyway.  I'll do gusty the next night if this works out.  I suppose I should just do 'apt-get upgrade' tonight since I'm not actually upgrading the Ubuntu version, just some of the packages, right?  I think that's what I did, but I'm not sure.  'sudo atq' doesn't tell me a whole lot about my scheduled tasks.

Thanks for telling me the difference between upgrade and dist-upgrade.
I'll report back when I can!

---

### Post by bettlebrox on 2007-07-16
> **Red Moose said:**
> Oh, too bad, I already re-installed...
  I suppose I should just do 'apt-get upgrade' tonight since I'm not actually upgrading the Ubuntu version, just some of the packages, right? .
!
I'd just do the "apt-get -d upgrade" as there me some packages that ask questions for configuration.

---

### Post by Red Moose on 2007-07-17
I tried upgrade and it didn't upgrade.  I should just take your advice and to -d. :-)  Where can I find the packages after I download them?
I also managed to get kalarm installed without downloading to much.
Thanks a lot.  I'll let you know if the upgrade works.

---

### Post by bettlebrox on 2007-07-17
The packages are cached in /var/cache/apt/archives . But you don't need to know where they are, just run "apt-get -u upgrade"

---

### Post by Red Moose on 2007-07-18
Oh, thanks! I think I'll try that tonight.  I was going to use kalarm and I managed to edit the sudoers file, but kalarm was giving me errors during the tests.

---

### Post by Red Moose on 2007-07-18
Ok, I tried apt-get -d upgrade.  It didn't download the packages.:( 
Something else I probably should've told you earlier is when I typed the command 'at 2:00' it gave a warning, "warning: Commands will be executed using /bin/sh"  Is that important?:confused:
Thanks a lot for your help.  If we can't figure anything out then I'll just have to wake up at 2:00.  It might be easier than trying to figure out how to schedule this.:)

---

### Post by bettlebrox on 2007-07-19
Or, just install cron-apt ! :)

[http://www.debian-administration.org/articles/162](http://www.debian-administration.org/articles/162)

---

### Post by Red Moose on 2007-07-19
Cool, that might work.  
Last night I had Kalarm set up, and I was pretty sure it was going to work.  Only problem is, I forgot to make sure kalarm was running...
I'll try again tonight.](*,)

---

