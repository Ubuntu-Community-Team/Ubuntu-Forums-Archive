---
title: "Unable to complete install: 75% &quot;configuring wvdial&quot;"
date: 2007-09-12
forum: General Help
---

### Post by Asheyla on 2007-09-12
I have tried installing about 4 times now, and each time I hit the same point: 75% of some random part, "configuring wvdial".  It will never (as in, I left it for hours) progress.  

I have an ASUS G2P laptop with an ATI Radeon X1700 graphics card.  If you need more specs I'd be glad to post them.  

I also tried downloading Ubuntu to a CD and booting from it, but it failed as well and I never got past the terminal.  

Please help me!

---

### Post by tuxcantfly on 2007-09-12
> **Asheyla said:**
> I have tried installing about 4 times now, and each time I hit the same point: 75% of some random part, "configuring wvdial".  It will never (as in, I left it for hours) progress.  

I have an ASUS G2P laptop with an ATI Radeon X1700 graphics card.  If you need more specs I'd be glad to post them.  

I also tried downloading Ubuntu to a CD and booting from it, but it failed as well and I never got past the terminal.  

Please help me!

Hmm strange error, I'd think that it would be that you ran out of ram, but given that X1700 GPU, that seems like a rather high-end rig with way more than the needed 256MB, so that can't be the case... Anyhow it seems more like some general Ubuntu issue to me than a Wubi-specific one, since the liveCD didn't boot, maybe just try installing using the alternate CD straight-out and see if it works that way (the alternate iso is at C:\wubi\install\ubuntu-7.04-alternate-i386.iso, just burn that file to a CD and boot from that CD to install), see if you can get it installed that way. If it still doesn't work or install properly with that, I'd just suggest waiting another month until Ubuntu 7.10 is released in October, it might work better with your hardware.

---

### Post by Asheyla on 2007-09-12
Thanks, I'll try out 7.10 when it comes out.

---

### Post by TheFounder on 2007-10-18
ok I tried it as it just came out.. .same problem.. same bug... hangs at 75% of 'configuring wvdial'

I let this thing work for hours... zilch.. nada.. zip...

---

### Post by djh3 on 2007-10-19
I am trying to install feisty from the Alternate CD and I get exactly the same problem as described above.  I am at "75%... configuring wvdial", and the install is completely stalled out.  Has anyone found a solution?

---

### Post by ago on 2007-10-20
Can you try with the LiveCD of Gutsy without using wubi?

---

### Post by djh3 on 2007-10-20
I found this post in another thread and it worked!


  #5  
Old November 6th, 2006
caf0696 caf0696 is offline
First Cup of Ubuntu
	  	
Join Date: Nov 2006
Beans: 1
Re: Installation stalls at 76% on "Configuring wvdial"
I have the same problem, my solution is :
1. press ALT-F2
2. press "Enter", enter command-line mode
3. type "ps", you can see the PID of the wvdial
like below example:

12345 root 2552 S wvdialconf /etc/wvdial.conf

then we know the PID of wvdial is "12345"

5. Kill the PID of wvdial

just execute

kill 12345

12345 is the PID of wvdial we just find.

6. The installation will continute.

Try it!

---

### Post by takvera on 2007-10-22
I just tried upgrading my 4 yr old Compaq 800 notebook from feisty to gutsy and ran into the problem of the process hanging at around 75% of installation at the point of:
 [INDENT]"Setting up wvdial (1.56-1.2ubuntu2) ..."[/INDENT]

After over an hour at this stage I rebooted the machine. I don't have a GUI anymore but can get into recovery mode command line.

I have run
[INDENT] "dpkg - configure -a" [/INDENT]
which starts the install process again but it hangs at the same point:
[INDENT] "Setting up wvdial (1.56-1.2ubuntu2) ..."[/INDENT]

I have tried to go into another terminal using ALT-F2 when it hangs to follow the above instructions  but can't put in any commands in the second or third term screens.

I am still a bit of a noobie with commandline but any help would be appreciated in resolving this bug.

---

### Post by dpol on 2007-10-22
A quick note about the fix above:  the fix works, but if "ps" does not show you the PID for wvdial, try using the "ps -ef" command.  Yes, you'll need to root privileges for this command.  For all you newbies, type: 
sudo ps -ef
<Enter>
then enter your su pw.

---

### Post by ago on 2007-10-22
It would be very helpful to know if you have the same issues with a standard (liveCD) installation or if this is wubi-specific. On top of my head we have no code that should be interfere with wvdial, so I'd expect that to be a general Ubuntu issue.

---

### Post by takvera on 2007-10-22
I resolved my problem with the wvdial package. What I did:

Rebooted into Grub, selected the recovery mode for the previous Kernal version to get to the command prompt. I then ran the following commands:

dpkg - r gnome-ppp        //This removes the gnome-ppp package which is used for dialup
dpkg -r wvdial                //Removes the wvdial package
dpkg - configure -a        //Runs the configuring of all packages.

It then configured all packages with only one error encountered dealing with the drupal-5.1 package. I can resolve this at a later time.

I then shutdown and restarted and it booted through the GRUB into the GUI and loaded my desktop without problem.  Now I have GUTsy Gibon installed.

Heaven knows why I needed to remove the gnome-ppp and wvdial packages to get it to work though.

---

### Post by ago on 2007-10-22
As an excercise can you try now to install wvdial and look at the logs/terminal output to see what happens? It should be easier to do so from a complete system than during installation.

---

### Post by takvera on 2007-10-22
I tried installing wvdial package via synaptic. The installation got about halfway and hung. I had to interrupt the process, which then prduced an error dialog box saying:

E: drupal-5.1: subprocess post-installation script returned error exit status 1
E: wvdial: subprocess post-installation script killed by signal (Interrupt)

See the attached screenshot of the terminal window. Hope this is a help to tracking down the problem.

---

### Post by ago on 2007-10-22
Hmm the wvdial post-installation script seems to go into an infinite loop. Cannot look at it now. But it should be possible to track it down.

---

### Post by looniichoon on 2008-03-19
Thanks for the above tips, they did allow me to get to a solution, however, in case anyone else is still struggling :

On Gutsy 7.10 (on a Dell C840)

I tried the CTRL-ALT-F2 method above which did not seem to continue the configure after killing the wvdialconf process. I then tried the boot to rescue mode to do the dpkg method. There was no gnome-ppp package to remove so I did an :

```
aptitude search wvdial 
```

then:

```
aptitude remove wvdial 
```

which seemed to run a configure. Just to be sure, I tried :
```
dpkg - configure -a 
```had a syntax error so I tried :
```
dpkg --configure -a
``` which didn't seem to do anything (I guess it had been done by the aptitude). However, this had not installed Grub. I could have installed/configured grub manually but I wasn't sure what else may have not been configured.

**What worked for me :**

I started the install again then when it had hung with the wvdial, I did the CTRL-ALT-F2, did :

```
ps -ef | grep wv 
```

I then killed 2 processes, using the pids starting with the process that had "wvdial.postinstall" in it (sorry I can't remember the exact process line)

Then after that killing the "wvdialconf"  process. 

This then continued the install for me.

---

### Post by ago on 2008-03-19
Can you please try 8.04, that should have been fixed

---

### Post by ufischer on 2008-04-01
This seems to be working for me in that after I did this after waiting for about half an hour for something to happen after the alternative 7.10 .iso boot cd install got to installing wvdial, my hard drives started going nuts again so the install is presumeably proceeding apace, but now I can't see what's going on with the install.  I presume there is a simple way to close the CLI window but I don't want to poke around to find it in case I kill the install.   Hmmm the hard disk stopped doing things so I took a chance and eventually found Alt-F1 after typing in exit got me back to what looks like a query screen from the installer.  


> **djh3 said:**
> I found this post in another thread and it worked!


  #5  
Old November 6th, 2006
caf0696 caf0696 is offline
First Cup of Ubuntu
	  	
Join Date: Nov 2006
Beans: 1
Re: Installation stalls at 76% on "Configuring wvdial"
I have the same problem, my solution is :
1. press ALT-F2
2. press "Enter", enter command-line mode
3. type "ps", you can see the PID of the wvdial
like below example:

12345 root 2552 S wvdialconf /etc/wvdial.conf

then we know the PID of wvdial is "12345"

5. Kill the PID of wvdial

just execute

kill 12345

12345 is the PID of wvdial we just find.

6. The installation will continute.

Try it!

---

### Post by purgatoryxpete on 2008-04-25
I just installed 8.04 using the alternate i386 cd on a ~5 year old laptop and I had to kill wvdial in order for the installation to progress past 80%.

---

### Post by ago on 2008-04-25
This is unlikely to be a wubi specific issue, so posting a bug in launchpad and/or asking in the general forum might be a better avenue. In any case it _might_ work if you kill the wvdial process.

---

