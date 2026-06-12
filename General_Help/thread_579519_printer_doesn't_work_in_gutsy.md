---
title: "printer doesn't work in gutsy"
date: 2007-10-18
forum: General Help
---

### Post by tubunu on 2007-10-18
After upgrading to Gutsy my HP DeskJet 710C printer refuses to work. I tried deleting it and then adding again, but no luck.. :( It is recognised in the system, but "print test page" doesn't do anything. Anyone knows how to fix it? Thanks!

---

### Post by Bablefish on 2007-10-18
Repeat this to yourself adding anything in Linux is a !@#$^&!!!!! What your really going to have to do is check the HP site and find if there is a Linux driver. If there is none your out of luck.

---

### Post by mybunche on 2007-10-18
There is a bug in for this.

[HTML]https://bugs.launchpad.net/ubuntu/+bug/133982
[/HTML]

---

### Post by mybunche on 2007-10-18
Somemore info from google searches. Someone posted a fix. See:

[https://lists.linux-foundation.org/pipermail/printing-user-hp/2006/007859.html](https://lists.linux-foundation.org/pipermail/printing-user-hp/2006/007859.html)

---

### Post by NeillHog on 2007-10-21
Also using Kubuntu and also with a Deskjet 710c. Also does not work.
Just to be sure -
When I chose "add a printer" I select "local printer (parallel ....)" and then I am offered LPT #1 under parallel or "HP Deskjet 710C under others.
Which should I select?

Thanks!

What does it mean "there is a bug in for this" ? Is it likely to be fixed or will I have to wait half a year for a new version?

Thanks!

---

### Post by AKoine on 2007-10-21
@mybunche : as said in the bug page, changing the version number in /etc/pnm2ppa.conf (as suggested in the webpage you've posted) no longer works. So, no solution for the moment ... very annoying ...

---

### Post by NeillHog on 2007-10-22
I tried canging the .conf file and it did not work for me either.
This is going to be an expensive upgrade if I have to buy a new printer :(

---

### Post by seamuso on 2007-10-22
purge all your print jobs first, then

tail -f /var/log/cups/error_log

try printing .. see what errors it spits out .. when my printing fubar'd, I found this ..

```
E [11/Oct/2007:07:35:13 -0600] Filter "foomatic-rip" for printer "PhotoSmart-C5100" not available: No such file or directory
E [11/Oct/2007:11:35:03 -0600] Filter "foomatic-rip" for printer "PhotoSmart-C5100" not available: No such file or directory
E [11/Oct/2007:20:37:35 -0600] [cups-driverd] Unable to open PPD directory "/opt/share/ppd": No such file or directory
E [11/Oct/2007:20:37:58 -0600] CUPS-Add-Modify-Printer: Unauthorized
E [11/Oct/2007:20:38:00 -0600] Filter "foomatic-rip" for printer "Photosmart_C5100" not available: No such file or directory
E [11/Oct/2007:20:38:36 -0600] Resume-Printer: Unauthorized
E [11/Oct/2007:20:38:44 -0600] Unable to execute /usr/lib/cups/filter/foomatic-rip: No such file or directory
E [11/Oct/2007:20:38:44 -0600] [Job 21] Unable to start filter "foomatic-rip" - No such file or directory.
E [11/Oct/2007:20:38:51 -0600] Unable to execute /usr/lib/cups/filter/foomatic-rip: No such file or directory
E [11/Oct/2007:20:38:51 -0600] [Job 21] Unable to start filter "foomatic-rip" - No such file or directory.
E [11/Oct/2007:20:39:51 -0600] Unable to execute /usr/lib/cups/filter/foomatic-rip: No such file or directory
E [11/Oct/2007:20:39:51 -0600] [Job 21] Unable to start filter "foomatic-rip" - No such file or directory.
E [11/Oct/2007:20:40:06 -0600] cupsdAuthorize: Local authentication certificate not found!
E [11/Oct/2007:20:40:06 -0600] cupsdAuthorize: Local authentication certificate not found!
E [11/Oct/2007:20:40:06 -0600] cupsdAuthorize: Local authentication certificate not found!
E [11/Oct/2007:20:40:09 -0600] cupsdAuthorize: Local authentication certificate not found!
E [11/Oct/2007:20:40:09 -0600] cupsdAuthorize: Local authentication certificate not found!
E [11/Oct/2007:20:40:09 -0600] cupsdAuthorize: Local authentication certificate not found!
E [11/Oct/2007:20:40:12 -0600] cupsdAuthorize: Local authentication certificate not found!

```one of the updates for the beta had goofed something up .. I suspect it was the missing foomatic-rip executable .. :lolflag: got that fixed and away I went with printing again.

Not saying that's your problem, but if you post the error log that happens, someone might be able to sort out what's happening.

---

### Post by AKoine on 2007-10-22
Personally, I got it fixed. :

First attempt :
```
sudo aa-complain cupsd
```
I tried again to print something. It worked.

I uninstalled my printer (System>Administration>Printing, or something like this, mine is in French, select your local printer, and click delete).

Reboot.

Reinstallation of the printer (Sytem>Administration>Printing, I clicked "New", and this time, I did not choose the Hp port thing, but LPT#1, since my printer is connected with parallel port, then HP and eventually 710C. Since then, it seems ok.

Hope this'll help.

---

### Post by NeillHog on 2007-10-22
sudo aa-complain cupsd
also worked for me :-)

I tried the test page and it did not work.
After sudo aa-complain cupsd it worked.

Strange.

I assume that I will have to do this after every new start - or is there a "batch file" that is run on every start up that I can get to do this automatically.

Sorry - still an Ubuntu newbie :-)

And Thanks!

---

### Post by Robin T Cox on 2007-10-23
AKoine - thank you for an excellent post! I had been tearing my hair out over this, and now my HP DeskJet 710C also works OK.

---

### Post by TheThinker on 2007-10-24
Great! I can't wait to test out Akroine's suggestion on my Dad's HP Deskjet 720C computer too. It may not be 710C, but hopefully it should work.

---

### Post by my3ke on 2007-10-26
> **TheThinker said:**
> Great! I can't wait to test out Akroine's suggestion on my Dad's HP Deskjet 720C computer too. It may not be 710C, but hopefully it should work.

FWIW, I tried it with my old 720c and this solved the problem.  Kinda got my goat that for the last two versions this worked on it's own, and now it's having issues again.

Makes me want to fire up my dot-matrix printer again.

my3ke

---

### Post by tubunu on 2007-10-27
> **AKoine said:**
> Personally, I got it fixed. :

First attempt :
```
sudo aa-complain cupsd
```
I tried again to print something. It worked.

I can confirm that this command fixed my problem. THANKS! Now, I haven't tried rebooting, but hopefully it'll work after that.

---

### Post by durand on 2007-10-28
Works here as well, thanks a lot!

---

### Post by TheThinker on 2007-10-29
My HP Deskjet 720C now works with that command as well. Shouldn't this be placed in the Ubuntu Wiki or documentation site?
Tubuntu, please mark this thread as "solved". Thanks

---

### Post by escrivner on 2007-11-06
I am a complete Ubuntu newb.  In Feisty 7.04 everything worked very well.  I upgraded to Gutsy 7.10 about two weeks ago and the printer no longer works. 

I tried the delete, reboot, reinstall routine to no avail.  I then tried the other solutions suggested in this thread.  Any other ideas?  I am so new at this that I am not sure I correctly re-installed my printer.  It is connected to my LPT1 parallel port.

---

### Post by secular on 2007-11-10
I have an HP Laserjet 1200 and, with Gutsy, and had to use the*** "sudo aa-complain cupsd"*** command in Terminal each time I booted up. (Thanks, AKoine!) I was using the HP Laserjet 1200 Postscript (recommended) driver and tried others.

After the latest round of updates, which included some CUPS updates, I still had to use the*** "sudo aa-complain cupsd"*** command in Terminal each time I booted up. I tried changing drivers again, though, and found a solution:

I changed to the ***HP Laserjet 1200 Foomatic/hpijs*** driver and now print seamlessly, even after rebooting several times.

I don't know how to explain this--it was just trial and error--but I hope it helps someone with the same or similar printer.

Regards....

---

### Post by njKeever on 2007-12-12
Wow, this simple code fixed my Deskjet 712C printing problems after literally HOURS of searching for a fix. Please, put this in a prominent place to save others the hassle. Thank you so much!

---

### Post by j8a on 2008-04-15
[http://www.openprinting.org/download/foomatic/](http://www.openprinting.org/download/foomatic/) contains the latest foomatic drivers 
or
apt-get install foomatic-db* from the console prompt
Hope this help!

---

### Post by alloydog on 2008-05-28
I had the same thing, though I use distribution ([**_Debris_**]("http://debrislinux.org/")) *loosely* based around Ubuntu, it uses the same repositories.

I have a HP PhotoSmart C4380 printer.  The printer worked OK with the generic Laserjet driver, but after I upgraded to 1.01, the printer wouldn't print properly with the Laserjet driver.

I installed the HP PPDs in the *Gusty* repository, but then I got the error message about the foomatic filter not being being found.

I then installed [FONT="Courier New"]hpijs[/FONT] and [FONT="Courier New"]hpijs-ppds[/FONT] and everything works fine.

There is also [FONT="Courier New"]foomatic-db-hpijs[/FONT] in the repository but I haven't tried that yet.

---

