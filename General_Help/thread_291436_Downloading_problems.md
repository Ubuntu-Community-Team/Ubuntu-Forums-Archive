---
title: "Downloading problems"
date: 2006-11-02
forum: General Help
---

### Post by PrinceArithon on 2006-11-02
Ok I just pulled the biggest noob mistake in the book...but let me explain.

Alright I Was having a problem downloading.  Somethings would download others wouldn't.  I would get a permission error and things like that.  No matter that I was using sudo or not.  Now this is what my error was.

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main mozilla-thunderbird 1.5.0.7-0ubuntu1 [10.7MB]
Fetched 10.7MB in 5m9s (34.7kB/s)
Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 128498 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.5.0.7-0ubuntu1_i386.deb) ...
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Could not open logfiles!
Invalid permissions? Maybe you need: chown havp /var/log/havp
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
subprocess post-installation script returned error exit status 1
Setting up mozilla-thunderbird (1.5.0.7-0ubuntu1) ...

Errors were encountered while processing:
havp

Yay ok so I the suggestion on the board was it could be from ClamAV ok so I got rid of my ClamAV and all that and I Was still getting this error.  So I found where havp was all over my system and got rid of it.  Well now I can't download a thing...this is the error I get now

Reading package lists... Done
Building dependency tree... Done
dnsmasq is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up havp (0.79-1) ...


Actually it's not an error it's just a pure failure.  So can anyone tell me how I can get this havp back onto my system and working properly so I don't have to deal with this problem anymore??  I just upgraded to Edgy and this was my only error, well I kinda made it worse, so I need some help here.  I haven't used Windows in nearly a month and I'd hate to go back to the need of using it now...

---

### Post by deepwave on 2006-11-02
From the installer, you got a message:
Could not open logfiles!
Invalid permissions? Maybe you need: chown havp /var/log/havp

Did you try running sudo chown havp /var/log/havp?

Or maybe sudo dpkg-reconfigure havp.

---

### Post by PrinceArithon on 2006-11-02
well I just tried the reconfigure havp, and it seemed to work....so all I can say is thank you!!!  I just hope I don't run into any more problems with this


EDIT:  No it's not working at all I know for sure I have totally deleted the havp off of my system and now I need to know how to get it back  LOL.  I told you it was a total noob move lol

---

### Post by PrinceArithon on 2006-11-02
Bump....sorry I'm just kinda anxious to get this fixed

---

### Post by deepwave on 2006-11-03
So whenever you do sudo apt-get install havp, you get the same error?

Also why do you need havp?  Most people don't need proxies in general, or Linux antiviruses.  Are you trying to setup a filtering email server for Windows clients???

Anyways I tried installing havp myself and I get this:
Setting up havp (0.79-1) ...
Starting havp: Starting HAVP Version: 0.79
Filesystem not supporting mandatory locks!
On Linux, you need to mount filesystem with "-o mand"
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error processing havp (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)

Removing havp with sudo apt-get remove havp results in:
Removing havp ...
Stopping havp: invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing havp (--remove):
 subprocess pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.79
Filesystem not supporting mandatory locks!
On Linux, you need to mount filesystem with "-o mand"
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)

It seems like a problem with the havp init-script.  Possib reasons:
- init-script was meant for sysvinit no upstart
- the package manager borked the package.

Going off to figure this thing out.

---

### Post by deepwave on 2006-11-03
Managed to purge my installation of havp, in the following manner:

sudo rm /etc/init.d/havp (this was the real culprit)
sudo apt-get purge havp
sudo rm /var/log/havp

Not sure what my problem is.  Just know that the init-script doesn't like the way my filesystem is mounted.

@PrinceArithon:
Unless you want to run a proxy and filter virus-ladden emails, this package is not useful.

Don't know how to fix this, other than filing a bug report or manually playing around with the init-script.

---

### Post by PrinceArithon on 2006-11-03
Thanks for the help.  Right now I'm at work and I can't get to my computer at home, but this maybe what I needed.  The problem is right now I can't download anything it dies in the middle of it installing ever since I got rid of this havp.

Thanks for the commands I can put in to get rid of it all together.  I will try it later and let you know how it worked.  

Again thank you so much.

---

