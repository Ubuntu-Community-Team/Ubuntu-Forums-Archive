---
title: "Running a Windows Portable Application under WINE"
date: 2013-05-06
forum: General Help
---

### Post by Iggy64 on 2013-05-06
I have a few Windows portable applications that I would like to run under WINE.  Most of these have simply an executable file (.exe) and a settings file (.ini).  There is no install file (launcher).  In Windows, I would simply create a folder ProgramName under the C:\Program Files folder.  Then I would place the .exe and the .ini file in the ProgramName folder.  To run the program, I would simply run programname.exe.

What is the recommended way to run such a program under WINE?

I believe I can use:

> winefile

to open the Wine File Explorer and launch the programname.exe from there.  But it's not clear how the programname.ini file would be accessed.  Also, the app does not seem to be fully functional this way -- although that may simply be the best it will be under WINE.

So I used

env WINEPREFIX=~/.wine_programname winecfg 

to create a new wineprefix for the program.  I figure I can now copy my files to 

~/.wine_programname/drive_c/Program Files

and then run the program from there.  Does this make sense?  Is there a better way?

[The reason I haven't found out whether the above method works is because I'm also having trouble copying the files to the target folder.  Still working on that.]

---

### Post by Mark Phelps on 2013-05-06
Windows "portable" applications are often "cracked" versions of Windows apps that were modified to prevent requiring activation, or the execution of an installation step that would then attempt to verify a product key or serial number.

To confirm this is NOT the case with the apps you are trying to run, you need to tell us the apps and the version of each.

Then, we may be able to help.

---

### Post by Iggy64 on 2013-05-07
Thank you very much for responding.  When I get home from the job, I will check on the version numbers of the software.

I  am fairly certain that the few portable apps I have are not cracks.  I  always avoided using anything like that, preferring to stick with things  in the legitimate public domain.  The program I am starting with is  called EncSpot Pro, which was originally shareware, but which was made  freely available some years ago.  (The creator published a universal  key.)

However, my question here is a more generic one.  I have, I  believe, good instructions for how to install a normal (registered)  Windows program under WINE.  But I have not found instructions on how to  "install" a "portable" Windows program - i.e., a Windows program that  does not have an installer and does not write to the registry.  

To  install a normal Windows program, I create a wineprefix, then simply  run the installer in the newly created folder.  But, with a portable  Windows app, there is no installer to run.  My question is, do I simply  copy the executable file into the c_drive/Program Files folder?

I  will experiment with that tonight.  I tried yesterday, but was having  problems copying the files. I am trying to solve that issue under a  separate thread in this forum.  It might have something to do with  permissions, and I have a lot to learn about that.

Again, thanks for offering to help.  I will report back with better info and, hopefully, with some progress.

---

### Post by grahammechanical on 2013-05-07
Have you installed any Windows programs under Wine? We get a Windows type Add/Remove Programs dialog where we can browse to the location where the program is stored and click on the exe. That works with a setup.exe. I know that does work. I have never tried it to launch a program. I only have one Windows program. I install it using setup.exe, Intellishield is run and I launch it through its icon.

There is a downloadable wine user guide here:

[http://www.winehq.org/documentation](http://www.winehq.org/documentation)

You may find it better to try to launch the program through the terminal. Any errors will be shown in the terminal and you can use them it work out what went wrong. This is what I see from the wineguide

> If the application doesn&#8217;t install menu or desktop items, you&#8217;ll need to run the app from the command line.
Remembering where you installed to, something like:


$ wine "c:\program files\appname\appname.exe"

will probably do the trick. The path isn&#8217;t case sensitive, but remember to include the double quotes. Some programs
don&#8217;t always use obvious naming for their directories and EXE files, so you might have to look inside the program
files directory to see what was put where.


---

### Post by Iggy64 on 2013-05-07
Yes, I have installed several Windows programs under WINE; but - as noted earlier - all were programs that had installers and write to the registry.  In those cases, I simply created a wineprefix and ran the installer.  But, in the case of portable (non-installed) apps, there is no installer to run.  So I wondered if I simply should copy the files into the c_drive\Program Files folder.  (I haven't been able to try that, since I'm figuring out how to copy files properly in Linux.  I think I have a permissions issue to solve.)

Meanwhile, I did successfully run a portable app -EncSpot Pro - by using

> winefile path/encspotpro.exe

However, EncSpot did not appear to be fully functional.  It's not clear whether this is simply the best it will do under WINE, or if it because there is a better way to launch it.  I will try some of the other suggested approaches when I get home from the job tonight.

Thanks a lot for your suggestions.

---

### Post by Mark Phelps on 2013-05-07
What you will need to do is go to the WineHQ site and look up each of the apps you want to run.  IF listed, that will give you a rating from GARBAGE (worthless) to PLATINUM (all features work).

Anything not listed is not likely to work; anything with a rating lower than GOLD is largely a waste of your time, since so many features will be missing that the app will be all but useless.

For example, the page below is for EncSpot -- and the Bronze rating indicates that trying to use it will essentially be a waste of your time:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=9729]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9729")

---

### Post by Iggy64 on 2013-05-07
Boy, I sure as heck should have thought of that!  I've browsed through some app ratings on that site in the past.  I should have checked it out before I started messing with EncSpot.  Thanks a lot for waking me up.

As I experiment with the possible ways to run portable Windows apps under WINE, I'll try to stick with Platinum or Gold rated programs.

Thanks, again, for your help.

---

### Post by monkeybrain2012 on 2013-05-07
If it works, all you need to do is to go to the folder where the program is and click on the .exe file. :) If that doesn't work you can run in in the terminal with command "wine Pathtoexefile" where pathtoexefile is the path to your exe file and check if it outputs any error message and then hit google. :) Sometimes you may be missing some .dlls which you can install with winetricks.

And yeah of course check the WINEHQ list but sometimes there are workarounds in their forums even when the software is reported to be garbage and those reports are often old, sometimes they may not reflect the reality of running same software under current versions of WIne.

This is a straight forward  support question, whether your software is cracked is none of my business. :)

---

### Post by Iggy64 on 2013-05-07
With help from kind folks in another thread, I learned how to copy my Windows portable files into the c_drive/Program Files folder.  In this case, I am still trying to run EncSpot Pro -- even though it is reported to run poorly under WINE.  At this point, I just want to learn how to launch a Windows portable under WINE.

So now I have c_drive/Program Files/EncSpot/encspot.exe

It does not launch the same way an "installed" Windows program does.  When I click a launcher for an installed program, the program runs.  With this "portable" program file, things are different, even though it is an .exe file.  When I click a launcher, it simply opens the folder (see path, above).  I then have to right click it and choose "WINE Windows Program Loader."  And then EncSpot runs.

As Mark Phelps pointed out, it does not run great -- but it does provide a good deal of information about mp3 files.  Still, some of the info is missing.

The main idea here, though, was to learn about how to run Windows portable apps.  And I have learned a good amount from all those who have chipped in here.  I appreciate that very much.  I also see how much I don't know; so I better start studying some more.

Thanks, again.

---

### Post by monkeybrain2012 on 2013-05-07
You don't need to copy it to the c_drive directory if it is portable. If it works then click on it and it will work. I have two such programs. One is a game, I don't even have it on the same computer. It lives in an external drive. Plug in the drive, open the folder, click the .exe file and that's it. No need to make things too complicated. :)
  
Your software probably just doesn't work in WINE.

---

### Post by Iggy64 on 2013-05-08
Nice.  I was starting to come to that conclusion when I found I needed to run the WINE launcher, even after going through the process of copying the program to the c_drive.  I'm glad you wrote it to explain.  I'll have to try a couple of my other portables the way you suggested.  I wonder if WINE will find the .ini file (if there is one).  I'll try it out tonight.

Thanks much!

---

