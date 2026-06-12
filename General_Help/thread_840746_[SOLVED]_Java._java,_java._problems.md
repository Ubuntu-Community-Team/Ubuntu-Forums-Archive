---
title: "[SOLVED] Java. java, java. problems"
date: 2008-06-25
forum: General Help
---

### Post by carl99fan on 2008-06-25
I am installing ubuntu 8.04 on a friend's computer.... I CAN NOT figure this java out.... I don't remember it being this hard when I did MY computer.

Every time I install a new program it seems, it has a problem, keeps telling me to go to the java site and download the jdk or something.. 
then I need to assign it to root.root... I don't understand what to do.

I still need to install a few more apps, if anyone knows what I am doing wrong.... please help.

[IMG]http://i198.photobucket.com/albums/aa208/carl99fanipo/ubuntuhelp-1.png[/IMG]

Also I HAVE downloaded from the java site.... against my better judgment, and I put them in my home folder.....
NAMED:

jdk-6u6-linux-i586.bin
jdk-6u6-linux-i586-rpm.bin

---

### Post by spiderbatdad on 2008-06-25
what i usually do is ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by carl99fan on 2008-06-25
> **spiderbatdad said:**
> what i usually do is ```
sudo apt-get install ubuntu-restricted-extras
```

I know I know!! lol

I have that, but I tried again for good measure This is a C&P from my terminal:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by spiderbatdad on 2008-06-25
Not sure. I haven't had to do this to install java doc, It is only the documentation, but what seems to be requested is to unzip the package...you can do with right click. Then, if it is on your desktop, cd to Desktop, and sudo chown root:root jdk-6....the_full_filename. Then: sudo cp -p ~/Desktop/jdk-6... /tmp
Then reinstall restricted extras
hope that makes sense.

---

### Post by carl99fan on 2008-06-25
> **spiderbatdad said:**
> Not sure. I haven't had to do this to install java doc, It is only the documentation, but what seems to be requested is to unzip the package...you can do with right click. Then, if it is on your desktop, cd to Desktop, and sudo chown root:root jdk-6....the_full_filename. Then: sudo cp -p ~/Desktop/jdk-6... /tmp
Then reinstall restricted extras
hope that makes sense.

You have given me a lot to work with.
I see the answer, I just need a little more knowledge to execute it! lol
I remember reading bout the cd-desktop deal when reading on how to compile packages......

Thank you, I will figure it out now.

---

### Post by carl99fan on 2008-06-25
Well I am already confused....

I have downloaded a .bin file.
not a zip

---

### Post by spiderbatdad on 2008-06-25
bin files are executable file type...like an  installer. You generally need to make them executables with the command:```
sudo chmod a+x filename
```To change directory to work with files located on the desktop, the command is ```
cd Desktop
```remember capitaliization matters is linux commands and filenames.

Your normal working directory is /home/username,  so if the file is in your home folder, no need to cd to desktop.

perhaps you could post the name of the bin file you have? If you are unsure what it is. Otherwise run it...make it owned by root, move it to /tmp, then
```
cd /tmp
sudo ./filename
```

Good luck.

---

### Post by carl99fan on 2008-06-25
unclear on how to make own root

I will post the files cause I have two of them and unclear which to use.

I also just moved them to the desktop lol
file:///home/kerry/Desktop/jdk-6u6-linux-i586.bin


file:///home/kerry/Desktop/jdk-6u6-linux-i586-rpm.bin

---

### Post by carl99fan on 2008-06-25
I have made them executables. That was fun!
is it the /temp in the var section of the file system? can I click and drag them there if it is?

---

### Post by carl99fan on 2008-06-25
OK I get it.... I just don't understand this root thing.

---

### Post by spiderbatdad on 2008-06-25
```
cd Desktop
sudo chown root:root jdk-6u6-linux-i586.bin
sudo chmod a+x jdk-6u6-linux-i586.bin
sudo mv jdk-6u6-linux-i586.bin /tmp
cd /tmp
sudo ./jdk-6u6-linux-i586.bin
```

I think that should do it, but not sure what we are doing.lol. This looks like a file to run or install java, not the doc files. I don't think it will do any harm to run this program, though. If nothing else, it's practice moving and manipulating file permissions.

Rmember the tab key will auto-complete file names for you, to help prevent typos, and ensure you are writing legitimate commands from the correct working directories.

---

### Post by spiderbatdad on 2008-06-25
> **carl99fan said:**
> I have made them executables. That was fun!
is it the /temp in the var section of the file system? can I click and drag them there if it is?

You can cut/paste...drag/drop files to the root directory if you launch the nautilus file browser in super user mode:```
gksu nautilus
```But be careful in this mode. You will have the ability to edit any root file you open.

---

### Post by carl99fan on 2008-06-25
I have learned a lot!! It made me agree to terms and then IT found the file was corrupted so I am downloading a fresh one.... should I remove the old one? and if so how.

---

### Post by spiderbatdad on 2008-06-25
so from your desktop...if the file is still there, or in any directory, you can enter```
ls -l
```That will list the files on your desktop ( or whatever directory you are in) and show you the owner and permissions. The jdk file should say root:root. The permissions are read write exectute (rwx) in order of User, Group, Other. so you should see something like : rwxr-xr-x. This means: read write execute, for owner, and read, execute for group and others.

---

### Post by leejack43 on 2008-06-25
Nokia Phones
Nokia 1112
Nokia 1200
Nokia 1208
Nokia 1650
Nokia 2310
Nokia 2610
Nokia 2630
Nokia 2760
Nokia 3109 Classic
Nokia 3110 Classic
Nokia 3110 Evolve
Nokia 3500 Classic
Nokia 5070
heriplazaplusltd
Nokia 5200
Nokia 5300 XpressMusic
Nokia 5310 XpressMusic
Nokia 5500 Sport
Nokia 5610 XpressMusic
Nokia 5700 XpressMusic
Nokia 6080
Nokia 6086
Nokia 6110 Navigator
Nokia 6111
Nokia 6120 Classic
Nokia 6121 Classic
Nokia 6131
Nokia 6233
Nokia 6267
Nokia 6280
Nokia 6288
Nokia 6300
Nokia 6301
Nokia 6500 Classic
Nokia 6500 Slide
Nokia 6555
Nokia 7373
Nokia 7390
Nokia 7500 Prism
Nokia 7900 Prism
Nokia 8600 Luna
Nokia 8800 Arte
Nokia 8800 Sapphire Arte
Nokia 8800 Sirocco Edition
Nokia E50
Nokia E51
Nokia E61i
Nokia E65
Nokia E90 Communicator
Nokia N70
Nokia N73
Nokia N76
Nokia N77
Nokia N78
Nokia N81
Nokia N82
Nokia N92
Nokia N93
Nokia N93i
Nokia N95 8gb
Nokia N96

Nokia Music Phones

---

### Post by spiderbatdad on 2008-06-25
> **carl99fan said:**
> I have learned a lot!! It made me agree to terms and then IT found the file was corrupted so I am downloading a fresh one.... should I remove the old one? and if so how.


Just run gksu nautilus if you like graphical...navigate to the file, right click, and move to trash.

---

### Post by carl99fan on 2008-06-25
> **spiderbatdad said:**
> You can cut/paste...drag/drop files to the root directory if you launch the nautilus file browser in super user mode:```
gksu nautilus
```But be careful in this mode. You will have the ability to edit any root file you open.

WOW!
P O W E R!!


dang, I Keep losing connection, strong storms in the area...

---

### Post by carl99fan on 2008-06-25
Creating jdk1.6.0_06/jre/lib/deploy.jar

Java(TM) SE Development Kit 6 successfully installed.

Product Registration is FREE and includes many benefits:
* Notification of new versions, patches, and updates
* Special offers on Sun products, services and training
* Access to early releases and documentation

Product and system data will be collected. If your configuration
supports a browser, the Sun Product Registration form for 
the JDK will be presented. If you do not register, none of
this information will be saved. You may also register your
JDK later by opening the register.html file (located in 
the JDK installation directory) in a browser.

For more information on what data Registration collects and 
how it is managed and used, see:
[http://java.sun.com/javase/registration/JDKRegistrationPrivacy.html](http://java.sun.com/javase/registration/JDKRegistrationPrivacy.html)

Press Enter to continue.....


THANK YOU!!

I have learned a LOT more usefull information here then I learned all weekend last week.

---

### Post by carl99fan on 2008-06-25
DANG!!!

Just tried to install something and got this AGAIN!!!

WHAT DOES IT WANT FROM ME!!?? LOL

[sudo] password for kerry: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
kerry@kerry-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by spiderbatdad on 2008-06-25
Not sure what you're trying to install that is causing the problem...are you working from synaptic package manager?

Are you trying to run java applets from a web site?

Sorry this is giving you such a hard time. Installing sdk is usually routine. If you open synaptic package manager, scroll down to sun-java-6 and see what is installed...I just use the jre java runtime environment. I there a reason you need the development kit?

---

### Post by spiderbatdad on 2008-06-25
k. I followed the link to the sun java site. You should have scrolled to the Java SE 6 Documentation, I believe. It is a zip file. Still waiting for it to download...the instructions do not seem to follow what you posted earlier. Let you know in a sec.

---

### Post by carl99fan on 2008-06-25
> **spiderbatdad said:**
> Not sure what you're trying to install that is causing the problem...are you working from synaptic package manager?

Are you trying to run java applets from a web site?

Sorry this is giving you such a hard time. Installing sdk is usually routine. If you open synaptic package manager, scroll down to sun-java-6 and see what is installed...I just use the jre java runtime environment. I there a reason you need the development kit?

NO no reason... That time it was frostwire, but sea monkey and amarok music program, anything that uses java......is not installed on this unit...

Like I said I worked just fine on MY computer, I don't understand what this is all about.

under package manager I haev EVERYTHING sun-java-6 installed....
even jdk...jre, fonts doc everything... I have nothing java 5 installed.

---

### Post by carl99fan on 2008-06-25
I have had the same problem in add-remove, package manager, and terminal
same results any program.... I am downloading the docs now...

---

### Post by spiderbatdad on 2008-06-25
I'm not sure what to suggest. I would use the search tool under the places menu and search sdk of jdk in the file system looking for an uninstaller. I would open synaptic and completely remove all those sun-java-6 packages.

Then install ubuntu-restricted-extras. I'm usually very careful about installing anything that isn't in the repos, due to the problem of removing the stuff...so IDK what to do with that bin file you ran...you can navigate and remove it from /tmp...I'm not even sure it installed anything system wide...doesn't seem to have. Anyway good luck...off to bed.

---

### Post by carl99fan on 2008-06-25
> **spiderbatdad said:**
> I'm not sure what to suggest. I would use the search tool under the places menu and search sdk of jdk in the file system looking for an uninstaller. I would open synaptic and completely remove all those sun-java-6 packages.

Then install ubuntu-restricted-extras. I'm usually very careful about installing anything that isn't in the repos, due to the problem of removing the stuff...so IDK what to do with that bin file you ran...you can navigate and remove it from /tmp...I'm not even sure it installed anything system wide...doesn't seem to have. Anyway good luck...off to bed.

Well thanks again for all your help.....
Rather have a linux problem than a Windows problem anyday.
take it easy

---

### Post by jamesstansell on 2008-06-25
> **carl99fan said:**
> DANG!!!

Just tried to install something and got this AGAIN!!!

WHAT DOES IT WANT FROM ME!!?? LOL

[sudo] password for kerry: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
kerry@kerry-desktop:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

There are a lot of people that don't understand this package.  The thing is, in your case you need to just tell the system that you don't want the sun-java6-doc package installed.
```
$ sudo apt-get remove sun-java6-doc
```

Does that get it to stop complaining to you?

The thing is, for the proprietary Sun packages, they wouldn't give a license to allow Ubuntu to ship the documentation.  But it seemed helpful to some people to create an installer package that would automate installing and removing the documentation.  The hard part is it requires that you download the doc archive manually first.

These days it's just better for people that want the documentation to install the openjdk-6-doc package.  This is a normal package that already includes the actual docs.  As far as I know they are essentially the same as what you used to have to download manually.

But it sounds like you probably aren't interested in these docs anyway.

---

### Post by carl99fan on 2008-06-26
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-doc is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.

Sooooo, I guess I never had it!! :confused::confused::confused:

I don't want it or I do want it I don't know. I do know this computer will not be doing any tricks. I will try to install some more programs that use java.. In fact I will remove amarok and reinstall.

---

### Post by carl99fan on 2008-06-26
Thank you.
I learned a lot from this thread. I don't have a clear understanding of what happened here, but I can install what ever I want now, and everything is working just fine. My buddy will be very happy I have offered to install this on a friend's computer, his children will be using it for their music, and myspace and what not. He was tired of dealing with the viruses on this machine, and with old Windows ME on this unit before, the viruses were out of control, and was beyond repair. Without getting all the restricted extras installed properly for him, this unit would most likely be headed to the trash, as I'm sure he would not spend the time to figure this out.

UBUNTU Forums :guitar:

---

### Post by jamesstansell on 2008-06-27
What happened is that somewhere along the line the package management system thought you wanted (or maybe needed?) to have the -docs packages installed.

The apt-get removed command had a side-effect to tell it that, no, you don't want it installed.

I'm sure there are other ways to tell it that, but that was probably the easiest, most direct way.

Glad things are working for you now!

---

### Post by dubhear on 2008-08-04
sudo ./filename
The best thing ever!

I'm so happy right now

---

