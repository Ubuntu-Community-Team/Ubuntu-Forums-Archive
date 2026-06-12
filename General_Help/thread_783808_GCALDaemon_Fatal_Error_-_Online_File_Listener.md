---
title: "GCALDaemon Fatal Error - Online File Listener"
date: 2008-05-06
forum: General Help
---

### Post by munkymac on 2008-05-06
I just upgraded to Xubuntu Hardy from Ubuntu Gutsy (clean install, not upgrade). I got most everything switched over, but GCALDaemon isn't playing nice. I've got it all set up with Rainlendar, but there is no syncing. Whenever I run standalonestart.sh or syncnow.sh, i get the following output:

```
| FATAL | OnlineFileListener | Fatal service error!

  [1 ] net.fortuna.ical4j.data.ParserException: Error at line 1: Expected [-3], read [-1]
  [2 ] at net.fortuna.ical4j.data.CalendarParserImpl.assertToken(CalendarParserImpl.java:370)
  [3 ] at net.fortuna.ical4j.data.CalendarParserImpl.assertToken(CalendarParserImpl.java:404)
  [4 ] at net.fortuna.ical4j.data.CalendarParserImpl.assertToken(CalendarParserImpl.java:389)
  [5 ] at net.fortuna.ical4j.data.CalendarParserImpl.parse(CalendarParserImpl.java:96)
  [6 ] at net.fortuna.ical4j.data.CalendarBuilder.build(CalendarBuilder.java:167)
  [7 ] at net.fortuna.ical4j.data.CalendarBuilder.build(CalendarBuilder.java:149)
  [8 ] at net.fortuna.ical4j.data.CalendarBuilder.build(CalendarBuilder.java:137)
  [9 ] at org.gcaldaemon.core.ICalUtilities.parseCalendar(ICalUtilities.java:150)
  [10] at org.gcaldaemon.core.Synchronizer.syncronizeNow(Synchronizer.java:201)
  [11] at org.gcaldaemon.core.Configurator.synchronizeNow(Configurator.java:1030)
  [12] at org.gcaldaemon.core.file.OfflineFileListener.run(OfflineFileListener.java:56)



```
I was running beta16, and even tried switching back to beta14 just to see if it would make a difference, but it didnt. I've gotten so used to using gcaldaemon that now i'm lost without it. Please, I beg of you, don't make me go back to having to open my browser to edit my calendar.

---

### Post by pur6ezwyx on 2008-05-26
even though i don't know the answer, I was wondering if you could tell me how to install GGACLDaemon.  I'm a newbie, so these terminal commands are confusing.  

Ultimately, I'm following these instructions from MaximumPC
[http://www.maximumpc.com/article/how_to_sync_your_online_and_offline_calendars?page=0%2C2](http://www.maximumpc.com/article/how_to_sync_your_online_and_offline_calendars?page=0%2C2)

but it says I need to intsall GGACLDaemon, so I'm trying to follow the website instructions.
[http://gcaldaemon.sourceforge.net/usage11.html](http://gcaldaemon.sourceforge.net/usage11.html)

I'm running Ubuntu 8.04 Hardy.
This is how I went about it.

1)checked java (1.6 is good)
2) typed cd / to go to root
3)i already have the zip on my Desktop /home/pur6ezwyx/Desktop/the filename
4)i'm still in the root directory so i type 
sudo mkdir -p /usr/local/sbin
5)cd /usr/local/sbin
6)sudo unzip /home/pur6ezwyx/Desktop/gcaldaemon-linux-1.x.zip
7) sudo chmod 777 /usr/local/sbin/GCALDaemon
8. cd /usr/local/sbin/GCALDaemon/bin
9./password-encoder.sh
then it says permission denied
how do i fix this?
is typing sudo the closest thing an ubuntu user can do to "log in as root" as the instructions state?
*edit* how do i put in that code box as well in my posts?

Thanks in advance

---

### Post by munkymac on 2008-05-28
Here's the way I have done it in the past (which doesn't seem to work on my xubuntu install, but worked fine when i was running Ubuntu Gutsy):

1. Download GCALDaemon (mine goes to the desktop)

2. Right-Click on the zipped file and select "Extract Here"

3. Doubleclick on the file created after extraction. It should have a GCALDaemon folder and install.txt inside

4. Open up a terminal, and type the following: 
	```
sudo mv /home/pur6ezwyx/Desktop/"filename" /usr/local/sbin
```
	(Replace "filename" with the name of the file. you can do this by typing "sudo mv" and then dragging the "GCALDaemon" folder into the terminal.

5. Still in the terminal, enter: 
	```
chgrp -R pur6ezwyx /usr/local/sbin/GCALDaemon
```

	Then:
	```
chmod -R g+w /usr/local/sbin/GCALDaemon
```

	Then:
	```
chmod 755 /usr/local/sbin/GCALDaemon/bin/*.sh
```

6. Now enter:
	```
cd /usr/local/sbin/GCALDaemon/bin
```

	Then:
	```
./password-encoder.sh
```

7. You should see the output "Your Google password:"



To answer your other questions-- sudo logs you in as root and keeps you logged in as root as long as the terminal is open. It's safer than actually graphically logging in as root from the login page. If you don't feel comfortable with the terminal, you can swap out "gksudo" sometimes, which will bring up your graphical interface.

In order to offset code in your posts, you can highlight your entry and click the "#" icon at the top of the entry window.

---

### Post by munkymac on 2008-05-28
Also, my next guess is that you will want to make sure that GCALDaemon starts when you start your computer. you can do this by installing the script from this thread [http://ubuntuforums.org/showpost.php?p=4473753&postcount=5]("http://ubuntuforums.org/showpost.php?p=4473753&postcount=5")

Here are changes you will need to make (to steps one and two in the linked thread):

1. download the script to your downloads folder as "gcald" (don't save it as "/etc/init.d/gcald" like he says, because your folder structure is different.

2. Open "gcald" with your text editor. Search for 
```
BASEDIR=/opt/GCALDaemon
```

change it to read ```
BASEDIR=/usr/local/sbin/GCALDaemon
``` and then save.

3. Open a terminal and type/paste in the following:
```
sudo mv /home/pur6ezwyx/Desktop/gcald /etc/init.d/
```

Now follow steps 3 & 4 from the linked post. You should be up and running!

---

