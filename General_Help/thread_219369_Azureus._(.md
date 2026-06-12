---
title: "Azureus. :("
date: 2006-07-19
forum: General Help
---

### Post by Roasted on 2006-07-19
I just downloaded Azureus. I'm on Ubuntu. I got this fricken error that won't go away unless I restart. Once I start Azureus, it's there until I reboot.

The error goes as follows:

Azurues did not shutdown tidily. Check home/jason/.azureus/logs/save for diagnostic log files and consider reporting them to the Azureus team if this is the result of an application error. Also check the wiki (see the help menu) for 'Azureus Disappears.'

How do I get rid of this? :(

---

### Post by meng on 2006-07-19
If I understand your problem correctly, a solution is to open the System Monitor and end/kill the java process that is running Azureus.

The problem with the Dapper repository Azureus is that there is no icon that docks to panel, and if you accidentally close the window rather than using the exit option, then Azureus is still running in the background and when you restart, it will be considered to have not shut down tidily. Then problem number two is that when you run Azureus that next time, the popup window that gives you the helpful message can't be closed!

A way of overcoming this problem is to overwrite the Azureus2.jar file with a more recent version, which can be downloaded from [http://azureus.sourceforge.net/index_CVS.php](http://azureus.sourceforge.net/index_CVS.php)

---

### Post by clparker on 2006-07-19
Is there any way other than this to just install it, and make it work? Problem is that this workaround makes the user install a beta CVS file. Not good, anybody else have any ideas? Who here has azureus working like a champ?

---

### Post by meng on 2006-07-20
There's often more than one solution to any problem. One could try, for example, downloading the official sourceforge 2.4.0.2 tar.bz2 file and using the Azureus2.jar file in that. That could work, although it's ever so slightly more fiddly. Myself, I'm not averse to running a beta version.

---

### Post by stabface on 2006-07-20
I did this and it works very well this is how i did it

close Azureus 

download the file from the link above, 
save the file to desktop, rename file to Azureus2.jar,
the open a terminal and type this

cd to Desktop
```

sudo cp -rv Azureus2.jar /usr/share/java/ 
```

---

### Post by Koziasty on 2006-07-24
It is not working, I'm afraid... The warning is still up, and cannot be hide. I also get updata notfication from azureus and cannot click on neither of the buttons. Hope you'll help, regards
Koziasty

-----------------EDIT--------------------
Sorry, it does work, It was only me not thinking. I repeat: this solution does work.

Regards

---

### Post by buyu on 2006-07-27
I can shut it down cleanly with file -> exit

Ray

---

### Post by QwertyManiac on 2006-07-31
Thanks for the solution, I was experiencing the same problem. Wish the uTorrent comes soon for Linux too.

Btw - You dont have to restart to get rid of the error if it appears, just go to System > Administration > System Monitor and kill Azureus/Java things.

---

### Post by Roasted on 2006-07-31
Hm. I came across this thread and thought "Oh yeah I completely forgot about my Azureus problem." 

Evidently so did Azureus. I reopened it, no errors. The only errors I got were the firewalled issues, which for some reason I still can't figure out.

I used the directions straight from this portforwarding site to clear the ports for Azureus. I followed them 110% perfectly. Yet I still get errors. I'm thinking about just ditching Azureus, cause I had this problem on Windows. Can anybody help?

---

### Post by jagaholic on 2006-08-11
Worked great here, thanks :D

---

### Post by PacShady on 2006-08-16
Hey

I had the same problem, which irritated me because using Kubuntu the error blocks the entire system tray in KDE. After checking the Azureus forums, the solution for me was to download the BETA jar file and overwrite the original with it. So far, no problems!

'Shady

---

### Post by em3raldxiii on 2006-09-04
This doesn't seem to quite fix the problem for me.  I have Azureus running, and all is happy.  Then I switch desktops (crtl-alt-right), then I switch back (ctrl-alt-left).  No Azureus window.  It's still running in the background, of course, just that the GUI is gone.  So in order to have the GUI show up again, I have to **killall java** in the terminal window, then restart Azureus.  I get the obligatory error message still, but I can click the hide button and it works.

*EDIT*:  I am retarded - there is now an Azureus icon in my TOP taskbar beside my little mail icon, just to the right of my clock.  Good thing I pay attention, hey?  So yes, this fix DOES WORK.

---

### Post by jaredvolkl on 2006-09-05
Worked for me too, thanks!

---

### Post by danembraceddc on 2006-09-09
Works like a charm for me too. Thanks.

---

### Post by EdThaSlayer on 2006-09-13
I also have that problem!(had it for quite a while i have to say)
...and all i did was log off from GNOME

---------------------------------
-iam not using Azereus anymore nowadays...

---

### Post by bastupungen on 2006-09-21
Such an easy fix... why isn't this fixed in the ubuntu downloadable package. And don't say that its an beta, please. There seems to be more obvious bugs in the package then this "Beta"

---

### Post by watlings on 2006-09-30
Thanks Meng & Stabface!  Did the trick!:-D

---

### Post by hihihi on 2006-10-01
this works. thanks
RECOMMENDED

---

### Post by jdong on 2006-10-02
> **bastupungen said:**
> Such an easy fix... why isn't this fixed in the ubuntu downloadable package. And don't say that its an beta, please. There seems to be more obvious bugs in the package then this "Beta"

The ubuntu azureus package is a mess. Unless we want azureus in multiverse, we must be able to compile azureus with GCC Java. This has not been a fun task, but Fedora has done most of that patching work already. However, we need SWT 3.2, which in turn requires eclipse 3.2, and now we need to import eclipse 3.2 into Edgy.

Even with all that said and done, there are around 17 compile errors in the plugins, and I am brushing up my Java knowledge, learning how to write Azureus plugins, and pulling out my hair all at the same time :)


So in other words, I'll probably jump off a bridge before I ever package Azureus for Ubuntu. This is my official resignation from trying to get it to work for Edgy. Go download your own azureus :)


Signed,
A very tired jdong who has spent around 10 hours trying to package Azureus 2.5.0.0 :)

---

### Post by nyy3321 on 2006-10-04
i initially had the lower-right popup problem, but i deleted the version of azureus up on the synaptic manager and dled azureus 2.5 from [www.getazureus.com](www.getazureus.com).
But the problem now is, whenever i dl a file w/ azureus, it does not appear on "My Torrents", but i do know that the file is being downloaded. So i can dl files, but i cant see if i'm 20% done or 80% done or find out any other information from within the azureus "my torrents" tab. i think the problem is that i didnt know how to install azureus from just the .tar so when i untared it, it went to my desktop where i just double-clicked azureus. the desktop folder where the application is, is not communicating with the .azureus folder in my home folder, which is where the torrents and plugins and junk are.

Any suggestions???

---

### Post by Jorge on 2006-10-04
This worked for me, let see if this is useful for anyone else, as mini How-To:

1.Install azureus from the synaptics packages (this will ensure a tidy installation, with correct directories and entries).
2.Download the latest azureus release from [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php), it should be a tar.bz file.
3.Open the tar.baz file with file roller, extract the contents to a temporary directory (there is just one archived directory: /azureus
4.Make a backup copy of the Azureus2.jar (just in case!): 
```
$ sudo cp /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar_backup
```
5.Copy the new azureus jar file to that destination, from your temporary directory. This will update your main application file:
```
$ cd /temporarydirectory/azureus
$ sudo cp -rv Azureus2.jar /usr/share/java/ 
```
6.Copy the complete content of the /azureus directory (from the temporary location) to .azureus directory in your home. This will complete the azureus installation, because there are some libraries azureus need to run properly and update in the future. You can use the file manager (nautilus) to do that, because you don't need root privilegies to copy to the .azureus dir in your home. (If you cannot see the .azureus dir, press Ctrl+H in the file manager to reveal hidden files)

(Please forgive any misspelling, English is not my native language. And correct any error, please.):D

---

### Post by gigiya on 2006-10-05
Another fix for the unremovable error popups is to go to About > About Azureus.  It somehow makes the hide button work.

---

### Post by nyy3321 on 2006-10-05
Hey Jorje,

Thanks, your HOWTO worked perfectly. now i can see my torrents just fine. :p

---

### Post by silverag on 2007-10-28
> **Jorge said:**
> This worked for me, let see if this is useful for anyone else, as mini How-To:

1.Install azureus from the synaptics packages (this will ensure a tidy installation, with correct directories and entries).
2.Download the latest azureus release from [http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php), it should be a tar.bz file.
3.Open the tar.baz file with file roller, extract the contents to a temporary directory (there is just one archived directory: /azureus
4.Make a backup copy of the Azureus2.jar (just in case!): 
```
$ sudo cp /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar_backup
```
5.Copy the new azureus jar file to that destination, from your temporary directory. This will update your main application file:
```
$ cd /temporarydirectory/azureus
$ sudo cp -rv Azureus2.jar /usr/share/java/ 
```
6.Copy the complete content of the /azureus directory (from the temporary location) to .azureus directory in your home. This will complete the azureus installation, because there are some libraries azureus need to run properly and update in the future. You can use the file manager (nautilus) to do that, because you don't need root privilegies to copy to the .azureus dir in your home. (If you cannot see the .azureus dir, press Ctrl+H in the file manager to reveal hidden files)

(Please forgive any misspelling, English is not my native language. And correct any error, please.):D

hello, i m a first time user for ubuntu, current version is 7.10 64bit..
=( i did exactly what you have suggested but my Azureus still does not run..
whenever i double click on a torrent file, nothing happens. Azureus does not even show up in the System Monitor > Processes
i have also tried [http://www.ubuntux.org/how-to-install-p2p-bittorrent-client-azureus](http://www.ubuntux.org/how-to-install-p2p-bittorrent-client-azureus)
although Azureus link is under the Applications > Internet menu, clicking on it does not launch Azureus.
Can someone help me fix this issue? Thankz =)

---

### Post by jenhsun on 2007-10-28
> **Roasted said:**
> I just downloaded Azureus. I'm on Ubuntu. I got this fricken error that won't go away unless I restart. Once I start Azureus, it's there until I reboot.

The error goes as follows:

Azurues did not shutdown tidily. Check home/jason/.azureus/logs/save for diagnostic log files and consider reporting them to the Azureus team if this is the result of an application error. Also check the wiki (see the help menu) for 'Azureus Disappears.'

How do I get rid of this? :(

Give Deluge a try.
You can see this thread.
[http://ubuntuforums.org/showthread.php?t=576473](http://ubuntuforums.org/showthread.php?t=576473)

---

### Post by jdong on 2007-10-28
Hi, everyone,

Please see bug [https://bugs.edge.launchpad.net/ubuntu/+source/azureus/+bug/57875](https://bugs.edge.launchpad.net/ubuntu/+source/azureus/+bug/57875) in Launchpad. For the past week or so I've been working on a fix to Azureus and have found the solution. Currently I'm pursuing the path to gutsy-updates...

---

### Post by silverag on 2007-10-28
> **jenhsun said:**
> Give Deluge a try.
You can see this thread.
[http://ubuntuforums.org/showthread.php?t=576473](http://ubuntuforums.org/showthread.php?t=576473)

oh well.. so far Deluge works fine for me.. thankz for the recommendation..
=)

---

### Post by Jorge on 2007-10-28
> **silverag said:**
> 
although Azureus link is under the Applications > Internet menu, clicking on it does not launch Azureus.
Can someone help me fix this issue? Thankz =)

Oh boy, this was an old thread... 

Silverag, I think you don't have the Java package installed... Use Synaptic to install the ubuntu-restricted-extras (that's a meta-package that install a lot of restricted plugins and codecs you will need to have a working computer: Java, Flash, etc., etc.) 

Have fun with Ubuntu!

---

