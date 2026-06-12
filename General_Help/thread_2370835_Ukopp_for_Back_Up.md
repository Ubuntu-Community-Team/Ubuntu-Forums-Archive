---
title: "Ukopp for Back Up"
date: 2017-09-07
forum: General Help
---

### Post by SpikeLS6 on 2017-09-07
I have lost my commercial back provider. I found Ukopp in the Ubuntu Software and bought a new Kingston 64Gb USB 3.0 Stick to use exclusively for backing up Ubuntu; I use Ubuntu for all my major computing at home.

Ukopp shows choices of NTFS and ext2 to format the new USB stick. I know that Ubuntu 17.4 uses ext4. Can I use the ext2 and if not how do I format the new stick with ext4?

When I first tried to use the new stick, Ubuntu never saw it. Chatting with Kingston they said I have a Linux problem and try it with Windows. I did and formated it into NTFS. Worked but does me no good for Ubuntu.

Are there any better ideas on backing up or other fairly easy to use Linux software programs?

---

### Post by speartip on 2017-09-08
Firstly, have you tried to use gparted to format the stick? If your backup is purely used by and on linux, then use ext4. If you may want to restore to Windows then NTFS.
To your backup. Backintime is simple & effective. However if you wish to do a bit of learning, Areca is one of the best. You can get it from here:
[http://www.areca-backup.org](http://www.areca-backup.org)
I have backed up & restored from Areca numerous times without issue. The documentation is fairly good.

---

### Post by SpikeLS6 on 2017-09-08
Checked out BackInTime, but remember from my previous homework that I did not like it. I would like to try the Areca and went to the Source Forge site you recommended to get it, but it seems the download is for Windows with JAVA something. It is not one for Ubuntu?

I tried Gparted to format the USB stick in ext4, but it did not want to do that. I even followed some online directions from a Ubuntu help site. What night I be doing wrong?

---

### Post by speartip on 2017-09-09
Linux version is there, if you click download on the left, areca-7.5, You'll see the linux versions at the bottom.
just extract the folder in your downloads folder, & either click areca.sh or open a terminal in the folder, and run ./areca.sh
You will need java installed for it to run properly.

As for your usb stick, will the disks program see it & format it?

---

### Post by SpikeLS6 on 2017-09-09
Did everything in your latest reply, but the Areca sh did not work either by double clicking or using the Terminal command. The error says it is not a Debian Package and can not be installed. I have tried to check if JAVA is on this PC; which version of JAVA should I have and where can I get it? I did not find anything in the Ubuntu Software Folder, and Synaptic has many to chose from, but which one/ones should I install?

Thank you.

---

### Post by speartip on 2017-09-09
icedtea-8-plugin is the one in the repos, however you are probably best with the official Oracle one from here:
[http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)
Once installed Areca should work from a terminal.

---

### Post by SpikeLS6 on 2017-09-09
I did a "java -version" because I could not get your link to JAVA 8 to install and found I already have JAVA 1.8.0-131 installed.

I have done "./areca.sh" and a  "./bin/run_tui.exe", but neither will start the Areca program.

I have the extracted files in a folder; is there an installation command I am missing?

---

### Post by speartip on 2017-09-09
You are opening a terminal in the areca directory aren't you?

---

### Post by speartip on 2017-09-09
When you say you could not get the link to java 8 to install, what do you mean?
It's quite simple & straightforward.
I'm not trying to be condescending here, but looking at your last post you have been using Linux for nearly 8 years, so am I correct in assuming that you are fairly up to scratch with terminal use & running scripts etc..

---

### Post by SpikeLS6 on 2017-09-09
I have lots of holes in my ubuntu experience.

I went to the Home/Areca Folder have it extracted in, right clicked Open in Terminal, typed in "./areca.sh and got the following: "No Such File or Directory."

I went into the folder another level to Home/Areca/Areca.sh file. That error comes up the same "No Such File or Directory". Some files did not show the Open in Terminal command when I right clicked.

I found that I already have JAVA 1.8.0-131 installed.

Irma is not too far south of me so I may lose power in the next bunch of hours. If so, I'll try this again once power is restored. Thank you for helping.

---

### Post by speartip on 2017-09-09
No you don't click any file. Go into the areca folder that you extracted. You will see in there the areca.sh file. Right click on an empty space in the folder, & "open terminal".
So in a terminal you will see:
[SIZE=2]```
xxxxx/Downloads/areca$
```
Then type:
```
./areca.sh
```
The program should now start, although as I mentioned earlier you might need the official Oracle Java.
So you need to do:
```
[FONT=&amp]sudo add-apt-repository ppa:webupd8team/java[/FONT]
```
```
sudo apt update
```
```
[FONT=monospace]sudo apt-get install oracle-java8-installer[/FONT]
```

Then try again.

To be honest I know you've mentioned that you don't like the program, but for ease I would use backintime, it should do everything you want.
If you have any issues please post back.
[FONT=monospace]
[/FONT][/SIZE]

---

### Post by SpikeLS6 on 2017-09-09
I tried first to download and install Java 8, but got this right off the bat: "Important!!! For now, you should continue to use Java 8 because Oracle Java 9 is available as an early access release! You should only use Oracle Java 9 if you explicitly need it, because it may contain bugs and it might not include the latest security patches! Also, some Java options were removed in JDK9, so you may encounter issues with various Java apps." Guess that means I already have Java 8.

Back to the Areca Folder, double clicked to get the files and folders that have been extracted, right clicked on the file "areca,sh". I do not see a Bring up in Terminal selection, just a Open in Archive Manager, or Open with Other Application. When I right click for instance the Bin Folder, I can Open in Terminal and it comes in the Bin Folder. Inputting the areca.sh command, however, I get "Command not found".

Maybe I should just go back to backintime.

---

### Post by speartip on 2017-09-09
> [COLOR=#000000]"Important!!! For now, you should continue to use Java 8 because Oracle Java 9 is available as an early access release! You should only use Oracle Java 9 if you explicitly need it, because it may contain bugs and it might not include the latest security patches! Also, some Java options were removed in JDK9, so you may encounter issues with various Java apps." [/COLOR]

Thats just a standard warning message, before you add the ppa, because the ppa contains java 7/8/9. And 9 is still early in development. But you'll be using 8.
You should have just pressed enter & added the ppa.

> [COLOR=#000000]right clicked on the file "areca,sh". I do not see a Bring up in Terminal selection, just a Open in Archive Manager[/COLOR]

Read my last post again, you don't right click on any file or folder.

> [COLOR=#000000]Maybe I should just go back to backintime.[/COLOR]

I think that's probably best.

---

### Post by SpikeLS6 on 2017-09-09
OK, time to give up. Irma is getting closer and power will become a factor.

I'll try the BackinTime (already gone over the documentation) and I also have ukopp reading my USB 3.0 stick; just need to add some exclusions to cut down on the unnecessary files.

Thank you for all your help. I will mark this thread as solved.

---

