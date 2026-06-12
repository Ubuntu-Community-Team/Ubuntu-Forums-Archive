---
title: "Trouble Installing Dropbox"
date: 2014-10-13
forum: General Help
---

### Post by Quarkrad on 2014-10-13
Running 14.04 - tried installing Dropbox from the s/w centre but it hung.  It seems to be installed (there is a tick against it in the s/w centre) but it is not to be seen and if I try to run it from the terminal I get in a loop*.  So I tried to uninstall it and start again.  If I try via the s/w centre it just sits there as per dropbox.png attached.   After 40mins I gave up with the s/w centre and tried to remove the install via the terminal and got terminal.png below.   There is no indication/prompt what to do re terminal.png below. How can I remove this partial install?  (I tried synaptic - it's tells me to run **dpkg --configure -a** - which gets me to the same point as terminal.png).  * dpkg --configure -a

---

### Post by Quarkrad on 2014-10-13
A red warning trangle appeared and I followed the prompts for a Distribution Upgrade.  Now I'm sitting as per upgrade.png.

---

### Post by Quarkrad on 2014-10-13
Apologies - running 12.04

---

### Post by jamesisin on 2014-10-13
You might try purging it and starting over.  That would likely be *sudo apt-get purge dropbox* in a terminal.

---

### Post by buzzingrobot on 2014-10-13
The name of the package is "nautilus-dropbox",  so use "sudo apt-get purge nautilus-dropbox" to purge it.

That package sets up the file manager (Files aka Nautilus) to work with Dropbox and then runs a script to download the proprietary Dropbox software from a Dropbox repository. It should then execute it, which puts the Dropbox login panel on your screen, and then sets Dropbox to run as a startup application.

Your screenshots show the Dropbox software being downloaded. If that worked successfully and, for some reason, it did not run, search for "Dropbox" and click on its icon.

Since the actual Dropbox code is not included in nautilus-dropbox, I'm not sure if removing the package will also remove the Dropbox software.

---

### Post by Quarkrad on 2014-10-14
I've just tried both of those commands - I get back to the loop described above.

[B]dad@dadubuntu:~$ sudo apt-get purge dropbox
[sudo] password for dad: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/B]

[B]dad@dadubuntu:~$ sudo apt-get purge nautilus-dropbox
[sudo] password for dad: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/B]


If I run the --configure command dropbox is downloaded to 100% and then the terminal just sits there - nothing happens.

---

### Post by vasa1 on 2014-10-14
What happens when you run the basic **sudo apt-get update** and **sudo apt-get upgrade**? Does that run with any errors?

---

### Post by Quarkrad on 2014-10-14
This is the output:

```
dad@dadubuntu:~$ sudo apt-get update
[sudo] password for dad: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dad@dadubuntu:~$ sudo --configure -a
sudo: invalid option -- '-'
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...
dad@dadubuntu:~$
```

---

### Post by slickymaster on 2014-10-14
> **Quarkrad said:**
> This is the output:

```
dad@dadubuntu:~$ sudo apt-get update
[sudo] password for dad: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
dad@dadubuntu:~$ sudo --configure -a
sudo: invalid option -- '-'
usage: sudo [-D level] -h | -K | -k | -V
usage: sudo -v [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-u user
            name|#uid]
usage: sudo -l[l] [-AknS] [-D level] [-g groupname|#gid] [-p prompt] [-U user
            name] [-u user name|#uid] [-g groupname|#gid] [command]
usage: sudo [-AbEHknPS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-C fd] [-D level] [-g groupname|#gid] [-p prompt] [-u
            user name|#uid] file ...
dad@dadubuntu:~$
```

@Quarkrad
I've edit your last post, [adding code tags to your output code]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") and reformatted it removing the use of bold format.

**sudo --configure -a** -> this isn't right. The command you have to run is ```
sudo dpkg --configure -a
```Please run it and post back the output you get.

---

### Post by Quarkrad on 2014-10-14
The output is:

dad@dadubuntu:~$ sudo dpkg --configure -a
[sudo] password for dad: 
dpkg: error: dpkg status database is locked by another process
dad@dadubuntu:~$

---

### Post by slickymaster on 2014-10-14
> **Quarkrad said:**
> The output is:

dad@dadubuntu:~$ sudo dpkg --configure -a
[sudo] password for dad: 
**[COLOR=#ff0000]dpkg: error: dpkg status database is locked by another process[/COLOR]**
dad@dadubuntu:~$

You can not run several packages applications/commands/tools at the same time. Sometimes, it means that synaptic, apt-get or the package update tool are running in the backgroung. Just close other package tools, or wait for them to be finished and dpkg will run. You can run top to see what is running.

---

### Post by Quarkrad on 2014-10-14
Thing is, and I do not know if this is relevant, I have restarted a number of times.  There does not appear to be any processes running (I look in System Monitor) that I have to stop - but there is a big chance I do not know what I'm looking for.

---

### Post by vasa1 on 2014-10-14
What is the output of "lsof /var/lib/dpkg/lock"?

---

### Post by buzzingrobot on 2014-10-14
> **Quarkrad said:**
> 


If I run the --configure command dropbox is downloaded to 100% and then the terminal just sits there - nothing happens.

Search the Dash for a Dropbox icon.  If it's there, click it.  The proprietary Dropbox software will be installed.

The Nautilus-Dropbox package does not contain the actual Dropbox code. That is downloaded from the Dropbox site.

---

### Post by vasa1 on 2014-10-14
And check out the answers to [http://askubuntu.com/q/15433](http://askubuntu.com/q/15433)

---

### Post by Quarkrad on 2014-10-14
dad@dadubuntu:~$ lsof /var/lib/dpkg/lock
dad@dadubuntu:~$ sudo lsof /var/lib/dpkg/lock
[sudo] password for dad: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dad/.gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
dpkg    2282 root    3uW  REG    8,1        0 787724 /var/lib/dpkg/lock


There is a Dropbox icon via the dash and when I click on it I get asked to authenticate it. Authentication is needed to run /usr/bin/dropbox as the super user. When I authorise I'm not sure what happens.  There is no icon in the top panel and no Dropbox folder in my Home directory.   I have used Dropbox for a few years and have it running on a number of other machines.  Something has gone wrong so my plan is/was to purge everything and start the install again.

---

### Post by Quarkrad on 2014-10-14
Re: [http://askubuntu.com/q/15433](http://askubuntu.com/q/15433)

I have read, if not that particular thread, one very similar and tried the commands including sudo rm /var/lib/apt/lists/lock - but I keep coming back to where I am at the moment.

---

### Post by Quarkrad on 2014-10-14
I've just run System Monitor and there was no 2282 process so I run System Monitor again as root and there it was - so I ended the process.  I then ran sudo apt-get update && sudo apt-get upgrade and it ran though.  I then tried sudo apt-get purge dropbox and I got:

dad@dadubuntu:~$ sudo apt-get purge dropbox
[sudo] password for dad: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Back to the loop again where the terminal downloads Dropbox and then just sits there.

---

### Post by Quarkrad on 2014-10-14
Just had a Distribution Upgrade window pop up - see attached.

---

### Post by Quarkrad on 2014-10-14
It's been over an hour now and nothing has happened - the upgrade seems to be frozen as per attached.

---

### Post by slickymaster on 2014-10-14
> **Quarkrad said:**
> dad@dadubuntu:~$ lsof /var/lib/dpkg/lock
dad@dadubuntu:~$ sudo lsof /var/lib/dpkg/lock
[sudo] password for dad: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/dad/.gvfs
      Output information may be incomplete.
COMMAND  PID USER   FD   TYPE DEVICE SIZE/OFF   NODE NAME
dpkg    2282 root    3uW  REG    8,1        0 787724 /var/lib/dpkg/lock


<---snip--->

I would start here, before trying to install anything else.

First try to find out which application it is using apt, with this command in the terminal```
ps aux | grep apt | grep -v 'grep'
```Once you have identified the process running using apt (like apt-get or aptitude), you can kill it using```
sudo kill PID of the process (2nd column in output of ps aux)
```After that you can just remove the lock using```
sudo rm /var/lib/apt/lists/lock
```and then run once again```
sudo dpkg --configure -a
```

---

### Post by Quarkrad on 2014-10-14
Thanks for your help on this.  The output is:

dad@dadubuntu:~$ ps aux | grep apt | grep -v 'grep'
root      3836  6.6  3.0 263644 80956 ?        SNl  15:50   1:28 /usr/bin/python /usr/sbin/aptd
dad@dadubuntu:~$ sudo kill 3836
[sudo] password for dad: 
dad@dadubuntu:~$ sudo rm /var/lib/apt/lists/lock
dad@dadubuntu:~$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process

---

### Post by slickymaster on 2014-10-14
> **Quarkrad said:**
> Thanks for your help on this.  The output is:

dad@dadubuntu:~$ ps aux | grep apt | grep -v 'grep'
root      3836  6.6  3.0 263644 80956 ?        SNl  15:50   1:28 /usr/bin/python /usr/sbin/aptd
dad@dadubuntu:~$ sudo kill 3836
[sudo] password for dad: 
dad@dadubuntu:~$ sudo rm /var/lib/apt/lists/lock
dad@dadubuntu:~$ sudo dpkg --configure -a
dpkg: error: dpkg status database is locked by another process

Hmmmm :confused:

Please re-run```
ps aux | grep apt | grep -v 'grep'
```to get the PID, then instead of kill, let's run it with the '-9' parameter```
sudo kill -9 PID
```That done, please run```
sudo killall dpkg && sudo killall frontend
```and again```
sudo dpkg --configure -a
```

---

### Post by Quarkrad on 2014-10-15
dad@dadubuntu:~$ ps aux | grep apt | grep -v 'grep'
root      2213 41.1  0.7 200852 21356 ?        SNl  08:22   2:27 /usr/bin/python /usr/sbin/aptd
dad@dadubuntu:~$ sudo kill -9 2213
[sudo] password for dad: 
dad@dadubuntu:~$ sudo killall dpkg && sudo killall frontend
dpkg: no process found
dad@dadubuntu:~$ sudo dpkg --configure -a
Setting up nautilus-dropbox (0.7.1-2) ...

Downloading Dropbox... 100% o share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)


I did a search for dropbox and had the attached results.  The Dropbox folder is in /var/lib and the nautilus-dropbox folders are in /usr/share and /usr/share/doc.  Every file seems to be owned by root.

---

### Post by buzzingrobot on 2014-10-15
Tap the Super key, start typing "Dropbox".  If the blue Dropbox icon is displayed, click it.  Does this launch the routine that prompts you for your Dropbox credientials, launches it, and sets it up to run on your system?

---

### Post by Quarkrad on 2014-10-15
The Dropbox icon is displayed in the Dash.  If I click on it I get a window pop up asking me for my authorisation password (which is not normal) - I enter it, the window disappears and nothing ......  It seems to me that although the install process is broken somehow, and I guess this is why I'm having trouble uninstalling everything, what has been installed has been done as root.  All the install files are owned by root - I'm guessing this is why when I click on the icon I get asked for my password.

---

### Post by buzzingrobot on 2014-10-15
> **Quarkrad said:**
> The Dropbox icon is displayed in the Dash.  If I click on it I get a window pop up asking me for my authorisation password (which is not normal) - I enter it, the window disappears and nothing ......  It seems to me that although the install process is broken somehow, and I guess this is why I'm having trouble uninstalling everything, what has been installed has been done as root.  All the install files are owned by root - I'm guessing this is why when I click on the icon I get asked for my password.

Typically, you would not see the usual authentication popup.  You would a see Dropbox popup that invites you to sign in to Dropbox with your Dropbox username and password. After that, you click through a few more questions from Dropbox, and the Dropbox daemon launches and begins to synch files. It also sets up the Dropbox daemon to run automatically on startup.

All files in /usr/bin are owned by root.  Package installations run as root, which is why they request authentication aka require use of sudo. Package removal processes also run as root.

---

### Post by Quarkrad on 2014-10-15
Thanks - I would like to uninstall/purge everything and start all over again.  I'm wondering whether I need to reinstall ubuntu to get over this problem.

---

### Post by slickymaster on 2014-10-15
> **Quarkrad said:**
> dad@dadubuntu:~$ ps aux | grep apt | grep -v 'grep'
root 2213 41.1 0.7 200852 21356 ? SNl 08:22 2:27 /usr/bin/python /usr/sbin/aptd
dad@dadubuntu:~$ sudo kill -9 2213
[sudo] password for dad: 
dad@dadubuntu:~$ sudo killall dpkg && sudo killall frontend
dpkg: no process found
dad@dadubuntu:~$ sudo dpkg --configure -a
Setting up nautilus-dropbox (0.7.1-2) ...

Downloading Dropbox... 100% o share and store your files online. Want to learn more? Head to [http://www.dropbox.com/](http://www.dropbox.com/)


I did a search for dropbox and had the attached results. The Dropbox folder is in /var/lib and the nautilus-dropbox folders are in /usr/share and /usr/share/doc. Every file seems to be owned by root.
So, the lock issue seems to be solved. Great.
> **Quarkrad said:**
> Thanks - I would like to uninstall/purge everything and start all over again.  I'm wondering whether I need to reinstall ubuntu to get over this problem.
In a terminal, run the following:```
sudo apt-get remove --purge dropbox
rm -rvf ~/.dropbox ~/.dropbox-dist
```Remove files from your Dropbox Folder:```
rm -rv ~/Dropbox
```

---

### Post by Quarkrad on 2014-10-15
I restarted the pc before I tried your commands - I have got:

dad@dadubuntu:~$ sudo apt-get remove --purge dropbox
[sudo] password for dad: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dad@dadubuntu:~$ 


Is it time for me to reinstall to save any more of your time?  I have separate / and /home so hopefully replacing / will clear this issue - I appreciate your help so far.

---

### Post by slickymaster on 2014-10-15
> **Quarkrad said:**
> I restarted the pc before I tried your commands - I have got:

dad@dadubuntu:~$ sudo apt-get remove --purge dropbox
[sudo] password for dad: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dad@dadubuntu:~$ 


Is it time for me to reinstall to save any more of your time?  I have separate / and /home so hopefully replacing / will clear this issue - I appreciate your help so far.

Damn, the lock issue isn't solved after all. I wonder how you were able to run **sudo dpkg --configure -a**

Before reinstalling everything, can you please provide us the output of the following terminal commands```

sudo fuser -vvv /var/lib/dpkg/lock
sudo fuser -vvv /var/cache/apt/archives/lock
sudo rm /var/lib/apt/lists/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
sudo dpkg --audit
```

---

### Post by Quarkrad on 2014-10-15
dad@dadubuntu:~$ sudo fuser -vvv /var/lib/dpkg/lock
[sudo] password for dad: 
                     USER PID ACCESS COMMAND
/var/lib/dpkg/lock:  root       2285 F.... dpkg
dad@dadubuntu:~$ sudo fuser -vvv /var/cache/apt/archives/lock
                     USER PID ACCESS COMMAND
/var/cache/apt/archives/lock:
                     root       2279 F.... aptd
dad@dadubuntu:~$ sudo rm /var/lib/apt/lists/lock
dad@dadubuntu:~$ sudo rm /var/cache/apt/archives/lock
dad@dadubuntu:~$ sudo rm /var/lib/dpkg/lock
dad@dadubuntu:~$ sudo dpkg --audit
dpkg: error: unable to open lock file /var/lib/dpkg/lock for testing: No such file or directory

---

### Post by slickymaster on 2014-10-15
Can you please try one last thing before giving up? Can you run```
sudo dpkg -r nautilus-dropbox
```and post back again the output?

---

### Post by Quarkrad on 2014-10-15
dad@dadubuntu:~$ sudo dpkg -r nautilus-dropbox
[sudo] password for dad: 
(Reading database ... 179284 files and directories currently installed.)
Removing nautilus-dropbox ...
Dropbox isn't running!
dpkg: unrecoverable fatal error, aborting:
 unable to install updated status of `nautilus-dropbox': No such file or directory

---

### Post by slickymaster on 2014-10-15
Sorry Quarkrad, but I must confess that now I consider myself beaten. :(

---

### Post by Quarkrad on 2014-10-15
Thank you for your help - much appreciated.

---

