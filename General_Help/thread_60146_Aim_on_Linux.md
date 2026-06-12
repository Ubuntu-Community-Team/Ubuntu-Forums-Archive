---
title: "Aim on Linux"
date: 2005-08-26
forum: General Help
---

### Post by organdonersteve on 2005-08-26
I used to have Gaim on here(it was bundled when i installed ubuntu) then i was told that there were 67 upgrades i should get so i downloaded them.  Since that happened gaim seems to be gone.  I figure that since Aim is the only messenger i use i will just switch to that.  i downloaded the aim-1.5.286.tgz file and extracted it to the desktop (it seems that that is the only place i have permission to put anything on my computer) and now i cant get anything o happen.  I'm pretty sure that I still need to install it but i cant figure out how.  i have tried all the sudo commands i can think of with no luck.  Im new to Linux and if i cant get this working i will have to admit defeat and switch back to windows, because that is my only way to communicate with my girlfriend who just moved away to collage.

thanks for any help.

---

### Post by varunus on 2005-08-26
gaim is gone?  Did you get hit by the current bug that's in backports?  Try installing gaim again from synaptic, if it complains, force the version down to the "hoary-security" version.

---

### Post by th3p14gu3 on 2005-08-26
While I have never used the linux aim client, and have no idea how to help you there, I have a couple of sugestions to try, to get gaim working:

Maybe just the menu entry got removed ( or moved ), try typing gaim in a terminal or the run box.

Or goto synaptic and reinstalling it.

Gaim also has an autopackage installer thing on their site, you could try that. ( all though, you won't be able to installing anything with apt-get that depends on gaim after this. )

---

### Post by organdonersteve on 2005-08-26
[QUOTE=th3p14gu3]

Gaim also has an autopackage installer thing on their site, you could try that. ( all though, you won't be able to installing anything with apt-get that depends on gaim after this. )[/QUOTE]

i tried that and when i clicked open on the mozilla download manager it gave me this:

 gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.

i know that gedit is a word processor thing so i dont think that was the right thing to do.  what is?

on the topic of linux aim the website says this :

Download and Install 1.5.286
 
						
  Platform 	  OS 	  Distribution 	  Instructions
   Intel 	
	   Red Hat 6.0 and above
           SuSE 6.4
           Mandrake 7.0    rpm 		   Installation Instructions
  	   Debian 2.1 	     deb 	         Installation Instructions
  	   Debian 3+ 	     deb 	        Installation Instructions
  	   All other OS        tgz 	   Installation Instructions

which of those do i use for ubuntu? i tried the other os and these were the directions after that:

Installation Instructions for TGZ (All other OS) for 1.5.234
1.  	Log in as root.
2.  	cd /
3.  	Download AIM onto your system
4.  	On the command line, type gunzip command as shown in the example: gunzip -c aim-1.5.234-1.i386.tgz | tar xvf -, where 1.5.234-1 represents the AIM version and release numbers
5.  	To run AIM, log in as a regular user, and type "/usr/local/bin/aim" on the command line.


step 2 did nothing and when i typed step 4 into the command line it said not found


thanks so much for the help guys.

---

### Post by organdonersteve on 2005-08-27
sorry to bump this but can anyone help me?

---

### Post by welsh_spud on 2005-08-27
Try starting synaptic, then doing a search for gaim, if the box next to it is filled in, type gaim in a command line and it should bring it up.

If the box next to Gaim isnt filled in, then sellect it and then click the tick to install it again.


If failing that, you may want to use the TGZ package you said you downloaded.

To install it:

**1. Log in as root.** 
This is easy, just type in sudo at the command line then enter you username password

**2. cd /** 
Simple enough, just type cd / to change directory

**3. Download AIM onto your system** 
You've said you have already done this, so I think you will need to switch to the directory you downloaded the file to. I believe you said it was to the desktop, so type in command line:
```
cd /home/<your username>/Desktop
``` 

Keep this command line open, we will need it in a minute.

[B]4. On the command line, type gunzip command as shown in the example: gunzip -c aim-1.5.234-1.i386.tgz | tar xvf -, where 1.5.234-1 represents the AIM version and release numbers
[/B] 

Now then, what it wants you to do here is to uncompress the file (Unzip it basically). There are two ways to do this, from the command line, or from nautilus (The file manager for Ubuntu)

To do it from nautilus, go to Places > Home Folder, then go to the desktop. You should see you file there (I think its a box with TGZ written on it, but i may be wrong). Right click it, and select uncompress  or decompress whichever is there  :? 

You will now have a new folder on the desktop. Go back to the command line window, and type in
```
ls
``` 

This will bring up every folder in your location. The folder you just made will be somewhere, so copy its name and type in 
```
cd <name of folder>
``` 

In this folder, I am guessing there will be a file named 'aim', so open up nautilus, navigate back to the folder and see if there is a file called aim, right click it, and sellect properties. Click the permissions tab, make sure that the file is executable, and close nautilus. Go back to the command line and type
```
/home/<user name>/Desktop/<AIM folder>/aim
``` 

That should bring up AIM

If you have any problems with this, dont hesitate to ask.

--Sorry for the hazzy-nes of the whole post, im not at my ubuntu laptop right now, so this is all from memory :)

---

### Post by organdonersteve on 2005-08-30
[QUOTE=welsh_spud]


In this folder, I am guessing there will be a file named 'aim', so open up nautilus, navigate back to the folder and see if there is a file called aim, right click it, and sellect properties. Click the permissions tab, make sure that the file is executable, and close nautilus. Go back to the command line and type
```
/home/<user name>/Desktop/<AIM folder>/aim
``` 

That should bring up AIM

If you have any problems with this, dont hesitate to ask.

--Sorry for the hazzy-nes of the whole post, im not at my ubuntu laptop right now, so this is all from memory :)[/QUOTE]
 i was doing really well untill the last step, i think i was anyway...

the aim file uncompressed inot a folder called usr, inside that was a folder called bin, (that has only a file called aim in it) and 1 called local (with tones of files in it.  i checked permissions tab and it looked ok, but when i typed your last command i got this: [b]root@ubuntu:/home/ian/Desktop/usr # /local/bin/aim
bash: /local/bin/aim: No such file or directory
[/b]

---

### Post by mhearn on 2005-08-31
[QUOTE=organdonersteve]i tried that and when i clicked open on the mozilla download manager it gave me this:

 gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog.[/quote]

Follow the instructions here:

   [http://autopackage.org/docs/howto-install/](http://autopackage.org/docs/howto-install/)

You only need to do that once. After you follow these instructions for the first time, you will be able to open autopackages directly from your web browser.

---

### Post by varunus on 2005-09-04
OK, all of the problems with gaim were from a bug in backports.  Just reload in synaptic, and install the gaim package again (use reinstall if you have to).  It should definitely work; gaim is included with ubuntu.

---

### Post by organdonersteve on 2005-09-05
thanks guys, im back up now. i appreciate the help.

---

