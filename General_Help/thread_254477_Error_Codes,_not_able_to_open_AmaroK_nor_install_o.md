---
title: "Error Codes, not able to open AmaroK nor install or remove any software?!?!"
date: 2006-09-10
forum: General Help
---

### Post by Tamacracker on 2006-09-10
Guy's I Just downloaded and installed AmaroK, dragged my icon onto the right panel in my desktop as you can see... I finally mounted my NTFS HDD so that I'm able to atleast listen to my MP3s. 

When I click on icon I dragged (AmaroK) it gives me an error. After I got the first error I got the little "update" icon popped up into the task bar as you can see on the top panel on the right side. The I run my mouse over the update icon, and it reads: **A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'**

**On this screen shot you can see the errors I'm gettin from two different applications; AmaroK and Software Updates.**

[IMG]http://i62.photobucket.com/albums/h116/Tamacracker/Screenshot-1.png[/IMG]


I'd like for some one do this with me step by step because I've witnessed on other threads where people made mistakes but did not realize it. I'm basically a newbie to Linux in general. So I don't really even know most of the commands I type when I install software or do upgrades... 

Please be patient with me, I'm not too ignorant so dont worry. Also I will copy paste the scripts from the Terminal after I type the commands I am told to type and also post up screenshots. I will not get ahead, whatever command is given to me I will type it and then view it.... and will let you guys choose what's the next proper move. 

Thank you in advance :)

-Tamacracker

---

### Post by Tamacracker on 2006-09-10
From the Software Updates error where it reads to run **sudo apt-get install -f**

I type **sudo apt-get install -f** into the terminal and this is what the outcome is:

[B]tamacracker@tamacracker:~$ sudo apt-get install -f
Password:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tamacracker@tamacracker:~$[/B]



From what I'm told in the update icon, type in **apt-get** into the terminal  to find out the problem, and this is the outcome after I do that:

[B]tamacracker@tamacracker:~$ apt-get
apt 0.6.43.3ubuntu2 for linux i386 compiled on Apr 18 2006 19:46:38
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get( 8 )
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to continue if the integrity check fails
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get( 8 ), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
tamacracker@tamacracker:~$
[/B]

---

### Post by monktbd on 2006-09-10
close all running applications and run

> **Tamacracker said:**
> From the Software Updates error where it reads to run **sudo apt-get install -f**

again from the commandline.
maybe dpkg was still locked becuase you still had the update manager running?

how did you install and download amarok?

---

### Post by Tamacracker on 2006-09-10
Ok I restarted my machine, opened up the terminal and typed **sudo apt-get install -f**

This is the out come:

[B]tamacracker@tamacracker:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python2.4-pyorbit
The following packages will be upgraded:
  python2.4-pyorbit
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/41.6kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
[/B]

At this point... I'm assuming I would type ** Y and hit enter**
I'm not sure though... what do I do from here?

---

### Post by Tamacracker on 2006-09-10
Ok I restarted my machine, opened up the terminal and typed **sudo apt-get install -f**

This is the out come:

[B]tamacracker@tamacracker:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python2.4-pyorbit
The following packages will be upgraded:
  python2.4-pyorbit
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/41.6kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?
[/B]

At this point... I'm assuming I would type ** Y and hit enter**
I'm not sure though... what do I do from here?

I downloaded AmaroK through the Synaptic Package Manager.


I used the **apt-get check** command and this is the outcome:
[B]
tamacracker@tamacracker:~$ check
bash: check: command not found
tamacracker@tamacracker:~$ apt-get check
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
tamacracker@tamacracker:~$
[/B]

---

### Post by Tamacracker on 2006-09-10
Hey!! I figured it out... when I mount my NTFS HDD is causes problems... which sucks because I'm able to access the HDD but then it distorts my operating system (ubuntu)

Well I guess this thread can be closed. Now I gotta figure out how I can atleast transport my MP3s or mount my NTFS HDD safely.

---

