---
title: "Lexmark Z703 and Synaptics Package Manager problem"
date: 2007-02-25
forum: General Help
---

### Post by chriswyatt on 2007-02-25
I tried to install the two packages from this website:

[http://users.cybercity.dk/~dko12479/](http://users.cybercity.dk/~dko12479/)

I converted both packages with Alien, and with converting of scripts enabled, and installed both the packages, the first package appeared to install successfully, though the second gave me an error message, sadly I didn't save the error message.

Then both packages were locked and now I can't use them.  Even worse, I get these two messages when I run the Synaptics Package Manager:

E: The package lexmark-z700-cups-driver needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

And the list of packages is empty :( .

I noticed this afterwards, could this have been the problem?

System Requirements
 1. Linux Kernel 2.4x or higher
 2. GCC 3.2
 3. enscript
 4. magic
 5. Cups  1.1

I'm not sure which of these I have and which I don't :S .

---

### Post by Maestro23 on 2007-02-25
To see if you have those requirements installed, you can go into Synaptic and do a search.  If it is installed, it's box will be checked.  If not, then you need to install it.

---

### Post by chriswyatt on 2007-02-25
But my Synaptics Package Manager is broke and cannot read from the cache, their are no listed packages :'(

---

### Post by Maestro23 on 2007-02-25
> **chriswyatt said:**
> But my Synaptics Package Manager is broke and cannot read from the cache, their are no listed packages :'(

Can you open a terminal do a "locate" on each one?

---

### Post by chriswyatt on 2007-02-25
Hm, not familar with locate, I'm a n00b.  I had a look through bin and lib in the filesystem and it looks like I have GCC and Cups installed.

---

### Post by Maestro23 on 2007-02-25
> **chriswyatt said:**
> Hm, not familar with locate, I'm a n00b.  I had a look through bin and lib in the filesystem and it looks like I have GCC and Cups installed.

Ex:

> locate enscript

---

### Post by chriswyatt on 2007-02-25
Ooh, looks like I have enscript and gcc as well, thanks :) .  Although, it seems I have a newer version, GCC 4.1

---

### Post by Maestro23 on 2007-02-25
> **chriswyatt said:**
> Ooh, looks like I have enscript and gcc as well, thanks :) .  Although, it seems I have a newer version, GCC 4.1

As long as you meet or exceed the requirements. So you did the binary install correct?  The first package installed correctly, but the actual driver install failed?  Hmm... you don't remember the error?

Open a terminal(this might be the right log...not sure. LOL)

> cat /var/log/dpkg.log

See any errors in there?

---

### Post by chriswyatt on 2007-02-25
Nope, it just says 'half-installed lexmark-z700-cups-driver 1.1.1-2' several times:

```
2007-02-25 14:56:03 install lexmark-z700-cups-driver <none> 1.1.1-2
2007-02-25 14:56:03 status half-installed lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:03 status unpacked lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:03 status unpacked lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:03 status unpacked lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:03 status half-configured lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:35 upgrade lexmark-z700-cups-driver 1.1.1-2 1.1.1-2
2007-02-25 14:56:35 status half-configured lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:35 status unpacked lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:35 status half-installed lexmark-z700-cups-driver 1.1.1-2
2007-02-25 14:56:35 status half-installed lexmark-z700-cups-driver 1.1.1-2

```

---

### Post by llamakc on 2007-02-25
Open a Terminal.

Type "sudo apt-get -f install"

and see if that fixes the problem. If so, update your packages with:

"sudo apt-get update"

Now try Synaptic again.

---

### Post by chriswyatt on 2007-02-25
Nope, still not working.  I'll try restarting Ubuntu, it could just be that something's been locked.

EDIT: Still not working.

---

### Post by llamakc on 2007-02-25
So, apt-get -f install doesn't output anything? Have you tried removing the packages and purging them yet?

---

### Post by chriswyatt on 2007-02-25
When I used Sudo apt-get -f install I got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package lexmark-z700-cups-driver needs to be reinstalled, but I can't find an archive for it.

Sorry for not being specific.  I'm not sure how to remove packages and purge them.

---

### Post by llamakc on 2007-02-25
Oh! My bad. You manually downloaded a package and used dpkg -i to install it, correct?

Well remove it with dpkg:

sudo dpkg -r nameofpackage

---

### Post by Maestro23 on 2007-02-25
> **llamakc said:**
> Oh! My bad. You manually downloaded a package and used dpkg -i to install it, correct?

Well remove it with dpkg:

sudo dpkg -r nameofpackage

Also try:

> sudo dpkg -P packagename
or
sudo dpkg --purge packagename


Will get rid of everything including config files for the package.

---

### Post by chriswyatt on 2007-02-25
I managed to purge z700llpddk, but it wouldn't let me purge or remove lexmark-z700-cups-driver because it's in a 'bad or inconsistent state'.

---

### Post by chriswyatt on 2007-02-25
OK, I tried reinstalling the corrupt package using dpkg (still locked on Gnome desktop but I could use it here) and managed to save the error messages this time round, here's what I got:

```
chrisw@chrisw-laptop:~/Desktop$ sudo dpkg --install lexmark-z700-cups-driver_1.1.1-2_i386.deb
Selecting previously deselected package lexmark-z700-cups-driver.
(Reading database ... 125534 files and directories currently installed.)
Preparing to replace lexmark-z700-cups-driver 1.1.1-2 (using lexmark-z700-cups-driver_1.1.1-2_i386.deb) ...
Unpacking replacement lexmark-z700-cups-driver ...
/var/lib/dpkg/info/lexmark-z700-cups-driver.postrm: 2: /etc/init.d/cups: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 2: /etc/init.d/cups: not found
dpkg: error processing lexmark-z700-cups-driver_1.1.1-2_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 2: /etc/init.d/cups: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 lexmark-z700-cups-driver_1.1.1-2_i386.deb
```

Looks like it's having trouble finding Cups.

This may be different to the message before as I uninstalled both packages, it may be relying on the other packages existance, I'll try again in a min with the other package installed.

---

### Post by llamakc on 2007-02-25
Do you have an /etc/init.d/cupsys? Was that package made for Ubuntu?

---

### Post by chriswyatt on 2007-02-25
No, but from the instructions at [http://users.cybercity.dk/~dko12479/]("http://users.cybercity.dk/~dko12479/") he seemed to think converting the package would work:

> Tip for Debian users: Use 'Alien' to convert *.rpm to *.deb or use the tarballs.

Looks like it would only need a slight modification to get going on Debian.

---

### Post by llamakc on 2007-02-25
Well it is looking for an /etc/init.d/cups, my system has an /etc/init.d/cupsys. You could hack the postrm script so that it handles that differently.

---

### Post by chriswyatt on 2007-02-25
Yes, mine has cupsys also, I'm not sure how I'd go about hacking it.

---

### Post by llamakc on 2007-02-25
sudo gedit /var/lib/dpkg/info/lexmark-z700-cups-driver.postrm

Search for where it looks for /etc/init.d/cups and replace that with /etc/init.d/cupsys

Now try installing again.

---

### Post by chriswyatt on 2007-02-25
```
chrisw@chrisw-laptop:~/Desktop$ sudo dpkg --install lexmark-z700-cups-driver_1.1.1-2_i386.deb
(Reading database ... 125566 files and directories currently installed.)
Preparing to replace lexmark-z700-cups-driver 1.1.1-2 (using lexmark-z700-cups-driver_1.1.1-2_i386.deb) ...
Unpacking replacement lexmark-z700-cups-driver ...
 * Restarting Common Unix Printing System: cupsd                         [ ok ] 
Setting up lexmark-z700-cups-driver (1.1.1-2) ...
/var/lib/dpkg/info/lexmark-z700-cups-driver.postinst: 2: /etc/init.d/cups: not found
dpkg: error processing lexmark-z700-cups-driver (--install):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lexmark-z700-cups-driver
```

Almost, it still tries looking for /etc/init.d/cups once.  I'll try editing var/lib/dpkg/info/lexmark-z700-cups-driver.postinst.

---

### Post by chriswyatt on 2007-02-25
That didn't work. Now I get:

```
chrisw@chrisw-laptop:~/Desktop$ sudo dpkg --install lexmark-z700-cups-driver_1.1.1-2_i386.deb
(Reading database ... 125566 files and directories currently installed.)
Preparing to replace lexmark-z700-cups-driver 1.1.1-2 (using lexmark-z700-cups-driver_1.1.1-2_i386.deb) ...
Unpacking replacement lexmark-z700-cups-driver ...
/var/lib/dpkg/info/lexmark-z700-cups-driver.postrm: 2: /etc/init.d/cups: not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 2: /etc/init.d/cups: not found
dpkg: error processing lexmark-z700-cups-driver_1.1.1-2_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 2: /etc/init.d/cups: not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 lexmark-z700-cups-driver_1.1.1-2_i386.deb
```

---

### Post by llamakc on 2007-02-25
See thatdirectory inside of /var/lib/dpkg/? /var/lib/dpkg/tmp.ci/? Are there postrm and postinst scripts in there as well? Edit those and give it one more try.

If this doesn't work, and it could be that with each 'dpkg -i' you're overwriting the scripts with what's in the .deb, there's another way with using 'ar' and 'tar'.

---

### Post by chriswyatt on 2007-02-25
The tmp.ci directory doesn't exist.  What's this ar and tar method?

---

### Post by llamakc on 2007-02-25
It would mean modifying the deb package. I've only done it once. Seems like the easiest thing for you to do would be to just get this package:

[http://users.cybercity.dk/%7Edsl145780/lexmark-z700-cups-driver-1.1.1-1.i586.tar.gz](http://users.cybercity.dk/%7Edsl145780/lexmark-z700-cups-driver-1.1.1-1.i586.tar.gz)

and move it to /

sudo mv lexmark-z700-cups-driver-1.1.1-1.i586.tar.gz /

cd / && sudo tar zxvf lexmark-z700-cups-driver-1.1.1-1.i586.tar.gz

and then get this: 

[http://users.cybercity.dk/%7Edsl145780/z700llpddk-2.0-1.i386.tar.gz](http://users.cybercity.dk/%7Edsl145780/z700llpddk-2.0-1.i386.tar.gz)

cd ~/Desktop

sudo mv z700llpddk-2.0-1.i386.tar.gz /

cd / && sudo tar zxvf z700llpddk-2.0-1.i386.tar.gz

sudo /etc/init.d/cupsys restart

Of course this isn't the DPKG way to handle it, but if you're trying to use software that's not in the repos yet, sometimes you gotta give it a try. Caveat emptor though. Good luck.

---

### Post by chriswyatt on 2007-02-25
Hi, sorry I haven't replied in a long time.  I entered everything above, there were no error messages but the printer hasn't appeared in the Printer manager.  I tried adding a new printer from the Printer manager and strangely two printers were detected, one called 'Lexmark Z700-P700 Series', another called 'Lexmark Lexmark Z700-P700 Series'.  Both of these want to use the My Synaptics Package Manager is working now, so half of the problem is solved.  Thank you very much for your time and effort, much appreciated.

---

### Post by Maestro23 on 2007-02-25
> **chriswyatt said:**
> Hi, sorry I haven't replied in a long time.  I entered everything above, there were no error messages but the printer hasn't appeared in the Printer manager.  I tried adding a new printer from the Printer manager and strangely two printers were detected, one called 'Lexmark Z700-P700 Series', another called 'Lexmark Lexmark Z700-P700 Series'.  Both of these want to use the My Synaptics Package Manager is working now, so half of the problem is solved.  Thank you very much for your time and effort, much appreciated.

So, can you print a test page yet?

---

### Post by chriswyatt on 2007-02-25
Nope, printer isn't showing on the printer manager, I meant to say that when trying to add a printer all I could find is the built in drivers, which are not designed for my specific printer.  I did try this driver and couldn't get anything to print.  Don't know what happened in my last message :confused: .  I suppose it's just a case of registering the newly installed drivers with  the printer manager, but I'm not sure how to do this.

Oh, a strange thing did happen when I was typing the last message, all the characters went right-aligned and when I placed my cursor to the right and typed, the letters appeared at the left :S .

---

### Post by Maestro23 on 2007-02-25
Man, I did a keyword search on lexmark in the forums. Came up with some hits.  If found this How-To(not sure if your model is in here though).  Might want to give it a read and/or run that lexmark search like I did so you can take a look at the other threads.

[http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark](http://www.ubuntuforums.org/showthread.php?t=49714&highlight=lexmark)

Good luck.  I will check back later..

---

### Post by llamakc on 2007-02-25
Chris, you may have to "trick" your system when it comes to the printer. TELL it you're using something similar and load up the drivers that you say the system does see.

---

### Post by Maestro23 on 2007-02-25
> **llamakc said:**
> Chris, you may have to "trick" your system when it comes to the printer. TELL it you're using something similar and load up the drivers that you say the system does see.

You might be right.  I have been reading other distro's forums and Lexmark and Linux just don't mix well.

---

### Post by chriswyatt on 2007-02-25
> **llamakc said:**
> Chris, you may have to "trick" your system when it comes to the printer. TELL it you're using something similar and load up the drivers that you say the system does see.

Nope, didn't work.  I think I might follow that guide that Maestro suggested.  Also, I still have a little problem, that corrupt driver is still hanging around like a bad smell, I installed a program earlier and an error message relating to this driver came up.  How can I get rid of it?  Package manager won't let me uninstall it.  The thing I did earlier, did I manually install this driver, if so, it should have completed the installation anyway?  Sorry if I sound like a complete dumbass, I still haven't got used to this Linux malarkey yet.

---

### Post by llamakc on 2007-02-25
When you did what? Be specific and you'll help yourself. When you used "dpkg --install" or when you followed the commands I posted?

The commands I posted will have no effect on the package management system.

Otherwise, you would need to purge the packaged .debs you downloaded, or converted from RPM's. How to do that was explained earlier in this thread.

dpkg --purge nameofpackage

---

### Post by chriswyatt on 2007-02-26
I installed a package using Add/Remove programs and it keeps reminding me of that corrupt package.  And I did try to purge those packages but it wouldn't let me purge the corrupt driver.

EDIT:  I tried again and got the same result:

```
(Reading database ... 125626 files and directories currently installed.)
Removing lexmark-z700-cups-driver ...
/var/lib/dpkg/info/lexmark-z700-cups-driver.postrm: 2: /etc/init.d/cups: not found
dpkg: error processing lexmark-z700-cups-driver (--purge):
 subprocess post-removal script returned error exit status 127
dpkg - warning: ignoring request to remove 1.1.1-2 which isn't installed.
Errors were encountered while processing:
 lexmark-z700-cups-driver
```

If I did uninstall this would this affect the driver I installed using your method?

---

### Post by chriswyatt on 2007-02-26
OK, I used the sudo gedit /var/lib/dpkg/info/lexmark-z700-cups-driver.postrm to change cup to cupsys like before, the configuration files were deleted and the error message has gone, it still refuses to remove it completely.

---

### Post by chriswyatt on 2007-02-26
Success!  I reinstalled everything using Llamakc's method in case I removed anything important earlier, PPD files were compressed in gzip format, all I needed to do was extract them, thanks for all your help and patience!

---

