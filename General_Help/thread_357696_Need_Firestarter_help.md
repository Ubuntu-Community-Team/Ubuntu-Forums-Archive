---
title: "Need Firestarter help"
date: 2007-02-10
forum: General Help
---

### Post by DougieFresh4U on 2007-02-10
Firestarter was working up till a couple of days ago. I started getting error message pertaining to it not detecting Ethernet (I'm online at the same time-go figure that one) so I know Ethernet is working. I uninstalled Firestarter and reinstalled and now this is what i get from terminal (installed from synaptic)::::dougie@DougiesToyBox:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up firestarter (1.0.3-1.3ubuntu2) ...
 * Starting the Firestarter firewall...                                                                                 [fail] 
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~$ sudo dpkg --configure -a
Setting up firestarter (1.0.3-1.3ubuntu2) ...
 * Starting the Firestarter firewall...                                                                                 [fail] 
invoke-rc.d: initscript firestarter, action "start" failed.
dpkg: error processing firestarter (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 firestarter
dougie@DougiesToyBox:~$

---

### Post by Maestro23 on 2007-02-10
What happens when you try this:

Did you install it via synaptic in the first place?

---

### Post by DougieFresh4U on 2007-02-10
Thanks for reply!!I used Synaptic to remove then the reinstall. Still doesn't want to install

---

### Post by DougieFresh4U on 2007-02-10
Bump :popcorn:

---

### Post by DougieFresh4U on 2007-02-10
Again it gets Bumped:guitar:

---

### Post by spelingchampeon on 2007-02-10
I am a Linux wannabe, having tinkered with different issues over the last year...so my troubleshooting is limited...

I was under the impression that Firestarter runs during boot.. but just checked my processes that are running and its not there. Oh well.. thats probably a good thing for this issue.

Does the SYSTEM LOG have anything in there to help troubleshooting? Have you tried STRACE yet? Its a pretty good tool for finding out what is happening when you are having hardware-software issues. When I was having issues with another program, I ran strace with the following command:

*strace -t -o test.txt firestarter  *

The -t will assign a timestamp to each occurance, and the -o is followed by whatever filename you want to use. Keep in mind, if the program is not running, using STRACE will start the program upon hitting the enter button. When you get the error, you might have to run a search for the text file.. I cant remember where it dumped it on my account. 

GL

---

### Post by llamakc on 2007-02-10
Are you running Firestarter on Edgy or Fiesty? It worked out of the box for me on Edgy. If Fiesty, you should post this over in that forum or check out bug reports on launchpad too.

BTW, I checked and there are bugs out there.

---

