---
title: "Opera 8.0"
date: 2005-04-25
forum: General Help
---

### Post by cmilhaus on 2005-04-25
Linux can be a delight and a frustration, and being still more or less grounded in the Windows world, I can get easily confused and frustrated in doing even simple tasks on Linux.
Attempted to download and install Opera 8.0 on Saturday
I had read through all the postings which pointed to Opera 7.54 and thought OK, lets see if any of this works for me.
It didn't
Keep on getting some form of an error message about Opera 8.0 when attempting to  manouver thr packages, and I am wondering if (a) anyone else is geting the error messages, OR if (b) anyone has had success with installing Opera 8.0 on Ubuntu 5.04?
This is NOT a big issue. I'm new, and I am perplexed. I would apprciate any comments which could point me in the right direction.
Thanks

---

### Post by shakin on 2005-04-25
It worked pretty well for me. I just went to opera.com and selected to download the Ubuntu package (it actually gives you the Debian Sarge package), then after the deb downloaded I installed it with 'sudo dpkg -i {filename.deb}' and it installed.

The one problem I did have is that Opera placed a shortcut in the Debian menu instead of the Ubuntu menu.

---

### Post by kelean on 2005-04-25
I am very happy with Opera 8.  I had one dependency issue that a quick apt-get install took care or and all is fine.  For me OPera is working better on my old slow machine that whet firefox is.  I really like firefox but it is lagging for me in hoary and not sure why.  But its not that bad just an anoycance at times.

---

### Post by TravisNewman on 2005-04-25
[QUOTE=cmilhaus]Linux can be a delight and a frustration, and being still more or less grounded in the Windows world, I can get easily confused and frustrated in doing even simple tasks on Linux.
Attempted to download and install Opera 8.0 on Saturday
I had read through all the postings which pointed to Opera 7.54 and thought OK, lets see if any of this works for me.
It didn't
Keep on getting some form of an error message about Opera 8.0 when attempting to  manouver thr packages, and I am wondering if (a) anyone else is geting the error messages, OR if (b) anyone has had success with installing Opera 8.0 on Ubuntu 5.04?
This is NOT a big issue. I'm new, and I am perplexed. I would apprciate any comments which could point me in the right direction.
Thanks[/QUOTE]
 Might help if you gave us the error messages you were getting. 

I have opera installed for testing things-- can't stand it as my default browser-- but I didn't have any issues installing it.

---

### Post by cmilhaus on 2005-04-26
This is the error message:
root@ubuntu:/home/bobm # sudo dpkg -i opera-static_8.0-20050415.1-qt_en_i386.debdpkg: error processing opera-static_8.0-20050415.1-qt_en_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 opera-static_8.0-20050415.1-qt_en_i386.deb
root@ubuntu:/home/bobm #

Perhaps I am downloading it to the incorrect folder? Firefox was pre-set to download to my desktop, so I created a "my downloads" folder in my home folder. I know, I'm thinking about those Windows again...

---

### Post by DutchLau on 2005-04-26
If you made a "My Downloads" folder in /home/bobm/ then that's what's causing your problem. 

Open a terminal type in: cd/"my downloads" (IMPORTANT use the quotes if you have a space in the filename, and make sure that you capitalize correctly) Type in: ls  (LS - this is to see the list of files in that directory, make sure your file is there and then assuming your file is spelled  opera-static_8.0-20050415.1-qt_en_i386.deb) type in: sudo dpkg -i  opera-static_8.0-20050415.1-qt_en_i386.deb  (That should solve your problem!)  :) ALWAYS make sure to type in the filename correctly  :wink:  

Good luck! Let us know if it worked  :-P

---

### Post by im_ka on 2005-04-26
i've just made the switch to opera as my default browser. it really _is_ fast, has gmail support now, and the ads are okay (unlike in previous versions)

---

### Post by rothbart on 2005-04-26
Agreed, Opera 8.0 is a nice browser.  On any speed machine I've felt it slightly more responsive than Firefox (not to bash Firefox, it's a close 2nd in *my*  book, ymmv).  

I also had no trouble using dpkg to install it.  

One tip I might suggest for people new to dpkg and any other CLI program is to take advantage of the TAB key while typing your commands to auto-complete filenames for you.  If you type "sudo dpkg -i opera" and then hit TAB and it can't fill in the rest of the .deb's filename, that's a real big hint that the file either doesn't exist at all or is not in the current directory.  Not to mention it saves you a lot of typing.  Be sure you realize that TAB will only fill out as much filename as it can until there's more than one possible choice (or if there is only one possible choice, it'll fill it all in).  This is something I've noticed that is tricky for people new to the command line.

Just adding my two cents.

---

### Post by cmilhaus on 2005-04-26
Thanks for all the comments! Dutch, those are some of the clearest suggestions I have ever received. Thank you so much. I will try as soon as I can get home from work.

---

### Post by DutchLau on 2005-04-26
No problem cmilhaus  :)  Good luck with everything!

---

### Post by Dex on 2005-04-26
My opera 8 install seems to be OK but it hangs every time I try to run it initially. During install I get this:
(Reading database ... 61185 files and directories currently installed.)
Unpacking opera-static (from opera-static_8.0-20050415.1-qt_en_i386.deb) ...
Setting up opera-static (8.0-20050415.1) ...

It then goes back to terminal window menu as it was before install

I can't find 'opera' on the taskbar or anywhere else, but found out the actual run file is  /usr/lib/opera/8.0-20050415.1/opera
I also try /usr/bin/opera - and in both cases opera seems to be launching; it is asking how to run it in the first time setup. And it hangs - in both of those links above. 
Why it's doing it.... :( I have to force quit it to get rid of it from the screen.

---

### Post by DutchLau on 2005-04-26
If you are using GNOME, open up a terminal and type in: ' killall gnome-panel '  See if it appears now. 

Otherwise, get gnome menu editor: [http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor)  (Follow all 4 steps - including refreshing gnome-panel) Go to Applications => System Tools => Menu Editor  | Make a new entry Call it "Opera 8.0" or something. Type in 'command' the path to the file that launches Opera, and under category use 'Internet' (if you want) Open up a terminal again and do: killall gnome-panel (refreshes the panel) Applications => Internet => Opera 8.0 or whatever!

Good luck! Let us know if this fixed your problem  :) 

Greets, DutchLau

---

### Post by Dex on 2005-04-26
My problem isn't in setting the opera within the panel submenus (applications/internet/opera) - although I do appreciate the runaround of getting it there - thanks! My problem is opera after seemingly proper installation (doesn't show me any error messages during install, but does the whole thing suspiciously too quickly for some other comparative installs) my opera simply hangs - it does so after initial launch and welcome screen with questions about start page etc... I have to use  'force a misbehaving application to quit' that is installed on my panel. Opera simply won't run and this is the only way I can kill it - command 'killall gnome-panel' works for a few seconds, and then the whole desktop reappears in the same manner with 'hanging' opera. Why can't I run opera?.... is there a log of errors somewhere I could read and post here?

---

### Post by stevetone on 2005-04-27
Dex, you probably have already tried these?

[list]start opera (command "opera") from a terminal and see if any error messages are shown?[/list]

[list]confirmed that you installed the correct version of opera (there are many). I believe that they now have an Ubuntu version (although I installed Debian unstable with no problem)[/list]

BTW, use the script in /usr/bin to start opera -- it sets up a few things before launching the opera binary. I have also found that the Gnome session manager "save desktop" option didn't work so well when (re)starting opera -- I had to manually enter opera into the session manager instead (probably has to do with the aforementioned script).

---

### Post by Dex on 2005-04-27
I tried sarge version (ubuntu) of opera with same results. Before, though, I did not get any different results running opera from command line. This time - it loads but here's the error I get in terminal:
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
opera: [java] Disabling java due to potential problems. If you know
       what you are doing, you can set the environment variable
       OPERA_FORCE_JAVA_ENABLED to '1' to override this.
       Start Opera with '-debugjava' argument for more information.

I have the opera running but looks like it finally is telling me what problem it is. Don't know how to fix this (firefox and epiphany are running OK); will try to rectify according to the error message suggestions,...

---

### Post by Dex on 2005-04-27
I tried to start opera -debugjava and here's what I got in terminal:

Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
opera: [java] There seems to be a preloaded version of Xt.
       There is a workaround for this problem in the opera
       startup script.  If that workaround fails, opera will
       most likely crash every time it tries to use Java.
       The workaround seems to have failed.  Java will be disabled.
       Technical explanation:
       There is a problem with the order of loading Xt and
       Java.  If Xt is loaded before libawt (part of Java),
       Java will crash when it tries to access the screen.
       The workaround is based on using LD_PRELOAD to load
       libawt.so first.

opera: [java] Disabling java due to potential problems. If you know
       what you are doing, you can set the environment variable
       OPERA_FORCE_JAVA_ENABLED to '1' to override this.
       The actual problems should be described above.

---

### Post by 23meg on 2005-04-27
the interface fonts look very blurry OR jagged in Opera for linux (all versions including 8 ), no matter what i've tried. the toolbars and panels in the static qt version seems to look a little better, but then its menus use qt widgets (i think) and they look horrible.

is it supposed to look so bad? does everyone else have this problem? i'd be glad if people submitted their screenshots running Opera! i'll definitely submit some on this thread once i reinstall my Hoary (removed it due to a fatal disk problem recently).

---

### Post by cmilhaus on 2005-04-27
OK, the "new Old Goat" has Opera running on his machine. It went smoothly and I may even be getting over my fear and loathing of the old DOS command language
NOW, I know I can open Opera in a command terminal, it runs, it runs very fleet of foot-in fact-it makes Firefox feel like it has two broken toes. Opera (for me) is clean, rapid and elegant.
How do I create a "program short cut" that I can put on one of my task bars, or program menus?
Again, this "old Goat: would appreciate any assistance you younger guys may have

---

### Post by Dex on 2005-04-27
I can only load opera from root terminal. Here's what terminal sez:
# opera
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
opera: [java] Disabling java due to potential problems. If you know
       what you are doing, you can set the environment variable
       OPERA_FORCE_JAVA_ENABLED to '1' to override this.
       Start Opera with '-debugjava' argument for more information.

/usr/lib/opera/plugins/operamotifwrapper-1: error while loading shared libraries: libXm.so.1: cannot open shared object file: No such file or directory

How do resolve this? apprecite some input, thx :)

---

### Post by Staesys on 2005-04-27
Here's how I fixed mine. Since I could run Opera 8 as the root user from the CLI, I knew that account worked...

Open a root terminal and type **nautilus --no-desktop --browser**

Navigate to the /root/.opera folder and select all, copy. Navigate to your /home/ <user> folder and paste these files into the user home folder. Overwrite all.

I know this is a shotgun approach, but it worked for me.

---

### Post by DutchLau on 2005-04-27
[QUOTE=cmilhaus]
How do I create a "program short cut" that I can put on one of my task bars, or program menus?
[/QUOTE]

Hey Cmilhaus!

Get gnome menu editor like this: [http://ubuntuguide.org/#menu-editor](http://ubuntuguide.org/#menu-editor) (Follow all 4 steps - including refreshing gnome-panel)

Go to Applications => System Tools => Menu Editor | Make a new entry Call it "Opera 8.0" or something. Type in 'command' the path to the file that launches Opera (for me it was /usr/bin/opera), and under category use 'Internet' (if you want) 

Open up a terminal again and do: killall gnome-panel (refreshes the panel)

Applications => Internet => Opera 8.0!

Good luck! Let us know if this fixed your problem

Greets, DutchLau

EDIT: I'd definately keep using Firefox though. Opera has WAY to many obtrusive ads and it doesn't have the plugin support Firefox has. By the way, if you want to get more programs with complete walkthroughs, go to [www.ubuntuguide.org](www.ubuntuguide.org) ! There you can learn how to do SO much with Linux. Have fun!

EDIT EDIT: Mistake in the command.

---

### Post by cmilhaus on 2005-04-28
Thanks for the instructions, I tried those this morning, and it didn't work. I think I am pointing to the wrong file.
Where do good little Linux files go to once they are installed? I can look in /etc/bin when I get home this evening.
I'll get the hang of all this one of thse days. I'm still so "programed" by windows sincw I have to use it all day, and of couse, I would be prone to go tooling around the hard disk looking for the "Program Files" directory, which even an old goat like me knows does not exist!
The Guide is a good idea, as well. Saves me from myself since I'm an old "point and click and crash" type person.

---

### Post by DutchLau on 2005-04-28
Hi Cmilhaus, 

I'm really sorry about that last post. All is RIGHT except the command for the file! It's " /usr/bin/opera " 

Stoopid mistake on my behalf,

Let us know if this helped!

Regards,

DutchLau

---

### Post by Woocash on 2005-05-17
Do You know how to make Opera to act as a default internet browser for Ubuntu? To run URL's from terminals, irc (x-chat), IM apps, email-client?

I've tried to set it in "prefered applications" as a 'opera %s' but it doesn't work...

It works from Tkabber (jabber client) but it has its own option to set it.

---

### Post by Xian on 2005-05-17
[QUOTE=Woocash]Do You know how to make Opera to act as a default internet browser for Ubuntu? To run URL's from terminals, irc (x-chat), IM apps, email-client?

I've tried to set it in "prefered applications" as a 'opera %s' but it doesn't work...[/QUOTE]
That's precisely what I did and my weblinks in Evolution open in Opera 8.

[img]http://img.photobucket.com/albums/v469/camplear/forums/operapref.png[/img]

---

### Post by chuck97224 on 2005-05-17
[QUOTE=kelean]I am very happy with Opera 8.  I had one dependency issue that a quick apt-get install took care or and all is fine.  For me OPera is working better on my old slow machine that whet firefox is.  I really like firefox but it is lagging for me in hoary and not sure why.  But its not that bad just an anoycance at times.[/QUOTE]


I have this dependency:  

"error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory"

How do I fix that?

---

### Post by tread on 2005-05-17
Start synaptic, search for that library and install it.

---

### Post by chuck97224 on 2005-05-17
[QUOTE=tread]Start synaptic, search for that library and install it.[/QUOTE]
  
I tried that but it wasn't there.   Any clues?  TIA

---

### Post by Xian on 2005-05-17
[QUOTE=chuck97224]I tried that but it wasn't there.   Any clues?  TIA[/QUOTE]
[img]http://img.photobucket.com/albums/v469/camplear/forums/operapref1.png[/img]

---

### Post by GriMsb on 2005-05-18
I can only load opera from root terminal. Here's what terminal says:
opera: Preference initialization failure. Generic failure (-1)

I have /home/user/.opera and I have tried all the permissions in /usr/bin/opera.  I am using the last Ubuntu and the last Opera and I am new in linux.

Could you give me any idea? Where must I search the solution?

--> Well, I have uninstalled and installed again, and now everything is OK.  Probably I did something wrong in the previous installation.

---

### Post by dolny on 2005-06-01
Opera freezes on the initial launch. On the user account / root, doesn't make a difference:

Check the screen: [http://www.echostar.pl/~dolny/ubuntu/operaerror.jpg](http://www.echostar.pl/~dolny/ubuntu/operaerror.jpg)

It gives me the same console output as someone pasted before, about java and stuff. ;/

Help! It's my favourite browser.

---

### Post by jannol on 2005-06-12
I got problem with Opera hangs when I installed it but now it works fine, only thing I remember changing between is that I removed flashplayer-mozilla and installed flashplugin-nonfree since I wanted flash to work with sound in opera and now it all seems to be ok. I've used opera for a few days since that and it works great so far.

---

### Post by PeterMoberg on 2005-09-20
I had the same problem, the reason was that I accidently had started Opera as root instead of running it as my user. Then ~/.opera was owned by root and the application couldn't be started as my user. 

"opera: Preference initialization failure. Generic failure (-1)"
Not a very good error message... 

The solution was to chown the ~/.opera to my user.

[QUOTE=GriMsb]I can only load opera from root terminal. Here's what terminal says:
opera: Preference initialization failure. Generic failure (-1)

I have /home/user/.opera and I have tried all the permissions in /usr/bin/opera.  I am using the last Ubuntu and the last Opera and I am new in linux.

Could you give me any idea? Where must I search the solution?

--> Well, I have uninstalled and installed again, and now everything is OK.  Probably I did something wrong in the previous installation.[/QUOTE]

---

