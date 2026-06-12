---
title: "TOP 10 Suggestions/Problems for a Windows2Ubuntu Switcher"
date: 2007-03-08
forum: General Help
---

### Post by TDK800 on 2007-03-08
Switched from Windows XP, my first day on Ubuntu, some first impressions/thoughts:


1. Installing Fonts - Windows Core Fonts (Tahoma, Verdana, etc) alternatives - I read MS license prohibits distribution of Tahoma with Ubuntu, but how-about a close look-alike font with a different name for improved readability for Ex-Windows users. Seriously I've been at it for 2 hours and I still haven't figured out how the hell do I get the .ttf fonts I downloaded and saved to desktop to the Fonts:/// window, drag and drop doesn't work :S ...and when I went to the /usr/share/fonts in Krusader, all the different fonts are in separated directories?!? :S

2. Installing Themes - Desktop Background, Menu Layout, Menus and Toolbars, Font, Screen Saver, Screen Resolution, Sound, Theme, Windows, and Emerald Theme Manager once Beryl gets installed. Pretty confusing for a first-timer I'd say. And when I click to Install New Theme - What's the theme file format one should look for?

3. GAIM - Possibility to make the buddy icons smaller in Gaim messenger (e.g. MSN Messenger size) - heck of a lot of scrolling to go through 100+ contacts to see who's online.

Also, feature that allows to block/unblock contacts through right-click menu.


4. Beryl - how to install it? Couldn't it be included with Ubuntu by default? I know it still not a finished project, but seriously, it's a pain to install manually for any newbie and all the cool beryl effect videos floating around is one of the main reasons many people switch.

5. Package Management - There's apt-install, apt-get, synaptic, add/remove packages, having to add repositories for every new app through synaptic or through editing a text file in terminal, or through Software Sources, or through Software Preferences as the tutorial on unbuntu.org showed :S

6. When clicking on .txt file asks whether to run or display every time, I'm sure there's some setting, but wouldn't it be easier to just have a always display .txt by default setting?

7. FireStarter Firewall manager installed by default, I know kernel firewall is included and active, but a lot of users have ZoneAlarm installed on Windows, so this would be probably a good idea, I like to sometimes easily check what's going on and to be able to easily block stuff through GUI without starting messing with IPtables on my first day with Linux.

well, probably gonna find more stuff to complain about later, hehe :)

---

### Post by AZzKikR on 2007-03-08
> **TDK800 said:**
> 6. When clicking on .txt file asks whether to run or display every time, I'm sure there's some setting, but wouldn't it be easier to just have a always display .txt by default setting?

I think this is because you tried to open a .txt file which resides on a FAT32/NTFS partition. These files are always executable, IIRC, thus it asks you whether to display, or run it. Try creating a file on your desktop with a .txt extension. When double-clicked, you'll see it will be opened in the system's default text editor :)

---

### Post by anaconda on 2007-03-08
.txt files that are copied from fat32 partition are marked as executables.. so ubuntu cant know it it is a script that you want to run or is it just a txt-file you want to read..

this fat32 partitions limit.. fat32 doesnt have access control..

in windows executables are marked as .exe .com or .bat .. ubuntu doesn't need those.. executables are marked as executables

---

### Post by dannyboy79 on 2007-03-08
> **TDK800 said:**
>  Switched from Windows XP, my first day on Ubuntu, some first impressions/thoughts:


1. Installing Fonts - Windows Core Fonts (Tahoma, Verdana, etc) alternatives - I read MS license prohibits distribution of Tahoma with Ubuntu, but how-about a close look-alike font with a different name for improved readability for Ex-Windows users. Seriously I've been at it for 2 hours and I still haven't figured out how the hell do I get the .ttf fonts I downloaded and saved to desktop to the Fonts:/// window, drag and drop doesn't work :S ...and when I went to the /usr/share/fonts in Krusader, all the different fonts are in separated directories?!? :S
You drag and drop doesn't work because this is an admin task, you're trying to save files into a secure admin location, this is on purpose. you wouldn't want anybody to be able to just put some file that's named tahoma.ttf which is actually a hidden trojan that executes in the background when you apply it. You need to go to a terminal and type in gksudo nautilus, this will open a nautilus windows with "root" privlages. read about sudo to understand better, don't just take my word for it.

> **TDK800 said:**
>  2. Installing Themes - Desktop Background, Menu Layout, Menus and Toolbars, Font, Screen Saver, Screen Resolution, Sound, Theme, Windows, and Emerald Theme Manager once Beryl gets installed. Pretty confusing for a first-timer I'd say. And when I click to Install New Theme - What's the theme file format one should look for?themes are kept in zip files, you would simply download the theme, and you can simply drag the downloaded theme right into your dialalog box for changing themes, then you would select that one if you want to activate it. All this stuff you're simply saying how hard it is. Well come on, it's your first day!!!!!!! You're working in a NEW OS!!! I don't ever recall seeing any claims that stated, "hey come to ubuntu, it's easy and it's just like winbloz"! So my point here, LEARN how to do this stuff before saying how hard it is.


> **TDK800 said:**
>  3. GAIM - Possibility to make the buddy icons smaller in Gaim messenger (e.g. MSN Messenger size) - heck of a lot of scrolling to go through 100+ contacts to see who's online.

Also, feature that allows to block/unblock contacts through right-click menu.

I have used Gaim but since I only had a couple friends entered I didn't have the problem you have mentioned so I can't speak on any of this but gogle will I am sure have your answers.

> **TDK800 said:**
>  4. Beryl - how to install it? Couldn't it be included with Ubuntu by default? I know it still not a finished project, but seriously, it's a pain to install manually for any newbie and all the cool beryl effect videos floating around is one of the main reasons many people switch.
as you very well know it's in beta form so it would never be in ubuntu by default. and even then, I don't know if it will be. there are min requirements for vid cards etc etc, so not everyone wants to have the glitz and glamor of seeing raindrops on your scrreen, being able to turn your screen and see the side of a cube etc etc. AGain, read the CORRECT how-to and it's not that hard at all. You can't just expect to come from a totally different OS and just know how to do things right away, that's just not realisitc.


> **TDK800 said:**
>  5. Package Management - There's apt-install, apt-get, synaptic, add/remove packages, having to add repositories for every new app through synaptic or through editing a text file in terminal, or through Software Sources, or through Software Preferences as the tutorial on unbuntu.org showed :S

Now this is the greatest feature about Ubuntu, MOST of the time you don't have to go to a website or a store and buy the software, then run the .exe and so on and so forth, you simply install it from the either 1 of the ways you mentioned. apt-install and apt-get are the same thing, in fact I have never heard of apt-install, do you mean apt-get install? also, synaptic is merely the gui for controlling what you install. the add/remove packages is a faster way to do it then entering synaptic and adding repo's is not hard and this gives you WAY more choices to software so why are you complaining about this???? SOmetimes something isn't in the repo, so you have to install from source, again, it's free, so learn CORRECTLY how to do it and just do it. As far as editing text files from the terminal, this is how a lot of pref's and whatnot are setup in linux, this is just the way it is!


> **TDK800 said:**
>  6. When clicking on .txt file asks whether to run or display every time, I'm sure there's some setting, but wouldn't it be easier to just have a always display .txt by default setting?
this is because the file has it's attributes set as executable. when you click on an executable you may want to be able to edit it and NOT run it, so this is a good thing. if you don't like that then you can change all your .txt files that came over from winbloz, so that they don't have the executable attribute to them, that would be sudo chmod uga-x blah.txt. here is a link for your to again, LEARN. [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilesp.html)

> **TDK800 said:**
>  7. FireStarter Firewall manager installed by default, I know kernel firewall is included and active, but a lot of users have ZoneAlarm installed on Windows, so this would be probably a good idea, I like to sometimes easily check what's going on and to be able to easily block stuff through GUI without starting messing with IPtables on my first day with Linux.
NOT everyone likes gui's. there is a firewall by default in ubuntu, it's called iptables. again, LEARN about it. ubuntu is NOT suppose to be "like" winbloz. you want to check whats going on then there are many commands to do this. 1 would be sudo netstat -pant, this will show you all the ports that are listening on your machine. sudo iptables -L will show you if you have any firewall rules set. Again, you just got to linux, you need to do some reading and all these suggestions/problems will be answered.

> **TDK800 said:**
> well, probably gonna find more stuff to complain about later, hehe :) 
do some reading before you do please, you'll be able to make more informed suggesitons and possibly point out real problems, not just problems that you think exist because you don't know how to solve them yet.

---

### Post by TDK800 on 2007-03-08
1. Tried the nautilus

user@PC:~$ gksudo nautilus
(nautilus:8570): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:8570): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

In file browser copying still doesn't work.... can't log in as root either when computer starts only allows user login.


2. Downloaded theme and dragged zip to install new themes window
[http://www.gnome-look.org/content/show.php?content=54227](http://www.gnome-look.org/content/show.php?content=54227)

Said .src is unrecognized :S

Tried the same with Windows Professional Theme
[http://www.gnome-look.org/content/show.php?content=53906](http://www.gnome-look.org/content/show.php?content=53906)

Again, showed png, xml files, tried the xml as the most logical choice, agan unrecognized.

Not sure actually what the KDM is, didn't see a menu item Gnome Themese on gnome-look.rg


5. 7. I'm quite familiar with the package management and IPTables firewall config - been managing our linnux servers through SSH for 4-5 years... I'm just saying I'd like to use Linux on desktop too, contribute to it, and have my friends switch too, but things could be made a LOT easier/user-friendlier. It's currently easier for me to do most of the stuff through terminal though GUI's exist for most of what I need, just too "complicated".

I first installed Centos 4 (Fedora 3) as my desktop... and from there to Ubuntu from user perspective, it's imho. a big step forward, like from Windows 3.1 to Windows 98. And if I get some MS fonts, themes, and Beryl installed, it would even kick XP's *** :)

I'm just saying, I will get used to the differences, but many users like me who have used Windows for years and years for everyday desktop... They will probably switch back to windows.... as the initial experience is worse than windows.

Everything in the install process was awesome, got all installed in only 20 minutes... until I saw how ugly (different) FireFox showed my favorite pages, so the windows alternative fonts is really a must for baiting over win users.

I recommended having the FireStarter available in default packages because I encountered the problem where I added FireStarter to session startup and it said the user doesn't have permission to start it... I searched and a lot of people have had the same problem... so was just one idea to make the ride/switch smoother.

Conclusion: Choice doesn't have to be hard! :)

---

### Post by dannyboy79 on 2007-03-08
it appears as though you have a dbus issue. I am not sure how to fix this but it is an issue that needs to be fixed! the theme issue, I am not sure why you're having issues, the first them you linked to was a .tar.gz, all you have to do is drag the tar.gz and place it right into the gui for picking a new theme, don't try to put it into a folder within nautilus. themes are very easy to install. have you read a tutorial on it yet? firestarter can't be started by a user because this is again, an admin task. i do wish you success though and by all means, bring your friends over but you do have to realize that just because linux is becoming a better desktop os, it's not advertized as being "like" windows.

---

