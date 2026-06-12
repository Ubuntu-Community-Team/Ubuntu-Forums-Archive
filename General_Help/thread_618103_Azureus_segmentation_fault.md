---
title: "Azureus segmentation fault"
date: 2007-11-20
forum: General Help
---

### Post by superwad on 2007-11-20
Ok, so I had Azureus manually installed from the SF download in my ~ and everything was working fine.  Then I upgrade to 7.10 and suddenly it stops working.  It simply won't load any more.  So, I finally get around to removing all my Java and killing the install of Azureus.  I then enable the backports, install Java 1.5 from Sun, and install Azureus 2.5.0.4.  Everything works wonderfully!  For a day.  I didn't do anything except update the DNS servers in my network manager, and then Azureus crashed.  Whenever I attempt to start it, I get:

```
wad@mainbox:/usr/bin/azureus$ ./azureus
Starting Azureus...
Loading Azureus:
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java -Xms16m -Xmx128m -cp "/usr/bin/azureus/Azureus2.jar:/usr/bin/azureus/swt.jar" -Djava.library.path="/usr/bin/azureus" -Dazureus.install.path="/usr/bin/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
./azureus: line 112:  9820 Segmentation fault      (core dumped) ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.
```

Now, it wasn't always this message.  It was basically the first couple lines, followed by a seg fault message.  Not even the logs contained useful information.

I tried:

[Everything in this thread](http://ubuntuforums.org/showthread.php?t=549589&highlight=azureus+segmentation+fault)
[This one too](http://ubuntuforums.org/showthread.php?t=413192&highlight=azureus+segmentation+fault)
[Same deal with this thread](http://ubuntuforums.org/showthread.php?t=25852&highlight=azureus+segmentation+fault)
[Even this one!](http://ubuntuforums.org/showthread.php?t=557595&highlight=azureus+segmentation+fault)

Just in case you don't want to read through those threads, the general resolutions were:

Delete the .azureus folder
Reinstall Azureus from repository
Reinstall Azureus manually from SF code
Replace the repository Azureus2.jar with the one downloaded from SF ([Per this bug report](https://launchpad.net/ubuntu/+source/azureus/+bug/95183))
Delete the logs folder
Double-checked permissions (they're all right I think)
Checked for alternatives for my Java interpreter (I only have Sun 1.5 installed)

For what it's worth, the output of some commands are:

```
wad@mainbox:/usr/bin/azureus$ echo $JAVA_HOME


```
(that's right, there is nothing in that variable)

```
wad@mainbox:/usr/bin/azureus$ java -version
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
```
(yup, no java executable)

However:

```
wad@mainbox:/usr/bin/azureus$ javac -version
javac 1.5.0_13
javac: no source files
*snip parameter explination*
```

(by the way:
```
wad@mainbox:/usr/bin/azureus$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/lib/jvm/java-1.5.0-sun/jre/bin/java). Nothing to configure.
```

here is where my java executable lives)

And finally:

```
wad@mainbox:/usr/bin/azureus$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

So, I gotta admit, I'm stumped.  I don't know quite how to proceed with this, except for hoping for a real port of Azureus to 7.10 sometime soon.

I thank anybody for reading through this, and I hope that I've proceeded with all the due diligence in solving this matter myself that the helpers here probably hope for.

---

### Post by superwad on 2007-11-21
Friendly-bump :)

---

### Post by superwad on 2007-11-23
Reminder bump again.  Perhaps I'm not including enough information?  If I can clarify anything, I'm very anxious to resolve this problem.

Thanks!

---

### Post by geirha on 2007-11-23
Azureus in ubuntu has been broken for a long time, it appears to have been fixed in hardy with the nice changelog line > * The "Ubuntu has working Azureus after 3 years" release (LP: #57875)

Until it gets backported, the "best" way to get it working imo, is to just download the tarball from azureus' website, unpack it on your desktop, open the azureus folder it unpacks, and doubleclick the azureus script to run it.

Oh and the java command should be in your path. Try ```
sudo update-java-alternatives --set java-1.5.0-sun
``` which should fix that.

---

### Post by superwad on 2007-11-23
Well, now I have a java command in my path, which is good.  However, downloading the package from SF and trying to run it still doesn't fix my original problem if it dying.  It's not giving a seg fault anymore, but it still won't load.

---

### Post by geirha on 2007-11-23
Have you tried removing or renaming ~/.azureus? Ubuntu's azureus creates some symlinks and other oddities that the regular azureus don't seem to like.

---

### Post by superwad on 2007-11-25
Yea, I moved my .azureus folder to a backup directory and tried running the SF version.  I still get:

```
wad@mainbox:~/Desktop/Azureus_2.5.0.4_linux/azureus$ ./azureus
Starting Azureus...
Loading Azureus:
/usr/bin/java -Xms16m -Xmx128m -cp "/home/wad/Desktop/Azureus_2.5.0.4_linux/azureus/Azureus2.jar:/home/wad/Desktop/Azureus_2.5.0.4_linux/azureus/swt.jar" -Djava.library.path="/home/wad/Desktop/Azureus_2.5.0.4_linux/azureus" -Dazureus.install.path="/home/wad/Desktop/Azureus_2.5.0.4_linux/azureus" org.gudy.azureus2.ui.swt.Main ''
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
./azureus: line 112: 20622 Segmentation fault      (core dumped) ${JAVA_PROGRAM_DIR}java -Xms16m -Xmx128m -cp "${CLASSPATH}" -Djava.library.path="${PROGRAM_DIR}" -Dazureus.install.path="${PROGRAM_DIR}" org.gudy.azureus2.ui.swt.Main "$@"
Azureus TERMINATED.
```

---

### Post by superwad on 2007-11-26
Well, I just upgraded to the backport version.  I made sure I removed the old source that Synaptic had cached.  I re-downloaded it and installed it, and sure enough I'm still getting a similar error:

```
wad@mainbox:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
^[FchangeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Segmentation fault (core dumped)
```

Is this something I should be posting a bug report on, or is there some way I can get more information to trace the root cause of my problem?

---

### Post by superwad on 2007-11-27
Ok, my friend traced a problem (or what he thought the problem was) to the SWT libraries.  He removed that particular library, and by extension a dozen other libraries and programs.  We then reinstalled the SWT library, Azureus and Eclipse (the error was referencing a Eclipse class/library).  The same problem still occurs.

Furthermore, I don't know where to find any log or debug information.  I can't pass any parameters to Azureus without it beliveing it's a .torrent file I'm trying to open.

What else is there for me to do?

---

### Post by geirha on 2007-11-27
Hm, how about trying a different java? like sun-java6?

I can't understand why it won't work with all the different approaches you've tried. So I guess it must be something wrong with java ...

---

### Post by superwad on 2007-11-28
Installed sun-java6 and changed my default java using

```
sudo update-alternatives --config java
```

and I'm still getting the same message.  For some reason, the first time it hung slightly when loading plugins, but still died.  And no, I don't have any plugins installed, so that probably isn't the issue here.

---

### Post by Ocxic on 2007-11-28
I used to have the same problem. I believe this comes from an error in java when azureus starts up wanting to show a pop-up (like when i gives u a little msg at the bottom of the screen)

 I found that changing to an alternative java with update-alternatives until azuerus opens then I would re-set to the original java in update-alternatives,, try installing a bucnh of java versions from the repos, it's a kind of a pain in the a*s fix but it works.

also I would like to point out that this problem is aparently fixed in the new azureus version,, I would suggest downloading the new version from there web-site and use that.

---

### Post by superwad on 2007-11-28
I would switch to an alternate version, but Azureus crashes very shortly after the splash screen comes up.  

As for upgrading to the new version, I want to keep that as a last alternative.  The community I frequent only recently allowed Azureus 3 and I'm partial to 2.5.0.4.

If I can't get this working, I'm going to nuke this install and start from scratch.  If that doesn't work, I'll have to suck it up and run Azureus on a spare XP computer. And I don't want it to come to that.

Thanks for the help so far.  I'll get on the nuking this weekend and post my results.

---

### Post by cv_zero on 2007-12-12
just to put in my useless two cents, ive had the same problem and tried every approach that 'wad did, and still no azureus for me. considering switching to a computer sci major just to develop a good ,reliable fileshare client for linux.  until then, guru's help us!

---

