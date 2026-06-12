---
title: "[SOLVED] Permissions"
date: 2007-07-26
forum: General Help
---

### Post by upthelum on 2007-07-26
I am trying to install themes, colour shemes, boot splash screens etc, but cant download the files to anywhere except my desktop as there seems to be an issue with file permissions. I cant copy/paste them either as the paste option is greyed out. Can someone give me a link to find the correct syntax for taking ownership or modifying permissions on root folders or tell me how to allow downloads to and editing of folders. When i download i am told i dont have permission to save in any directory, except Desktop. I cant browse and select the file as it seems the files have to be in a different directory.

---

### Post by dannyboy79 on 2007-07-26
The first bit of instructions are all for the command line.

well there are several ways to do this but only a couple CORRECT ways. You don't want to change the owner from root on any system type folders, like /tmp or /usr or /root or / or any of those. You can use the chown command to change the owner:group of a folder when using sudo. so the command would be
sudo chown username:groupname /folder/folder

you can see the permissions and owner of any file or folder by issuing the 
ls -la
command so it would be
ls -la /home/username/downloads
Your user's home directory should be owned by you, so you should be able to save it anywhere within this path 
/home/username/blah
(username being the username you chose when you installed ubuntu)

Now to get it so that you can navigate around and copy and paste stuff within Nautilus, you need to launch Nautilus with root privleges using the sudo command BUT you need to use gksudo (explaination sometimes required but I don't feel like looking for it in gogle-so just take my word for it. you always need to launch GUI style apps which require root priveleges using gksudo NOT sudo)
so you would enter
gksudo nautilus
KEEP IN MIND THOUGH, that you now can delete and move ANYTHING and screw up your system so be careful! You want to be careful though creating stuff like folders when in sudo nautilus because it will be owned by root since that's who you're running nautilus as. You can always chown anything and everything as long as you know your sudo password which is NOT the same as root password. Ubuntu doesn't have root password enabled by default.

The way to change permissions is by using chmod. That's a little bit more to explain so I'll point you at a good read to help explain it. it's a cheat sheet but ignore the WinBloz stuff (he he): [http://localtech.us/cheat_sheet.htm](http://localtech.us/cheat_sheet.htm)
That should be it, let me  know if you have anymore q's.

---

### Post by aysiu on 2007-07-26
Read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

But you shouldn't have to install themes system-wide just to use them. If you have a GTK, Metacity, or icon theme, just drag and drop its .tar.gz to the theme manage window that appears after you go to System > Preferences > Themes. If you have a GDM theme, go to System > Administration > Login Window > Install Theme.

---

### Post by upthelum on 2007-07-26
gksudo doesnt work for me for some reason. I took ownership of a folder i created and downloaded a bootsplash to it, thats fine. then when i browse to it to add the splash i cant see it in control center. Is there something wrong with the files, they are tar or zip, or do i have to install them from command line?
This is annoying as i am owner of all folders but cant save to them unless i change permissions and i do not know why the splash files and boot screen files wont work. I'm not a noob but there are many aspects of ubuntu i need to get more familiar with. 
Is there someting wrong with my setup as i dont have System > Preferences in my menu. Also when i open login Window it starts to open but doesnt, gksu comes on the taskbar and then it just closes.
Thanks...

---

### Post by dannyboy79 on 2007-07-26
yes, something is wrong! I had a bug where gksudo wouldn't work with ANYTHING either. I was pissed. I did a reinstall as no one could help me solve it over a weeks time. I would say first try to restart your machine and check out 
dmesg
for errors and also check out /var/log/syslog for errors. you can use Gedit, vi, nano or any editor to view syslog, you can just type in dmesg at the command line to get the output of the startup process but I would definitely say you have something wrong if you don't have system preferences BUT first try to restart your machine.

---

### Post by upthelum on 2007-07-26
No i still dont have System > Preferences

---

### Post by dannyboy79 on 2007-07-26
well I can't tell you what to do other than do a reinstall. sorry

---

### Post by upthelum on 2007-07-26
That'll be do a re-install again. This will be the second one in a week. My my is this the fun i have to look forward to, no comfortable flashy desktop but re-install after re-install, there must be some easier way to install a theme surely.

---

### Post by bodhi.zazen on 2007-07-26
Extract your theme and save it in ~/.theme

~ = /home/username

You might have to make the directory.

---

### Post by upthelum on 2007-07-26
Thanks i'll give it a try tomorrow, im starting to get widgets and other things working so i'm doing something right...

---

### Post by dannyboy79 on 2007-07-27
> **upthelum said:**
> That'll be do a re-install again. This will be the second one in a week. My my is this the fun i have to look forward to, no comfortable flashy desktop but re-install after re-install, there must be some easier way to install a theme surely.

well installing a theme is a totally sperate issue from NOT having a System, Preferences button! Now it may just be that it's hidden within your menu then you can always try to edit the menu BUT again, the choice to edit the menu is located within System, Preferences. HA HA   So what I did was go into my menu editor, then checked out what commands are used to enable the menu editor. Type this in at the command line.

alacarte

this should bring up the menu editor, then go thru that and ensure that Preferences within System is checked so that it shows up in your menu.

If you can't even run alacarte then like I said, you have something wrong and instead of trying to diagnois it for hours or days, you could reinstall but obviously that's up to you. IF your System, Prefs isn't showing and you didn't do anything wierd to make this this way, than who knows what other stuff you'll find along the way that isn't right then before you know it, you customized your system so much that it's more painfull to reinstall later than it is to do it now.

Good luck in whatever you decide.

---

### Post by upthelum on 2007-08-03
Sorry i took so long to get back. I got the permissions issue cleared up and the theme install issue. I ran alacarte and the preferences were ticked already but their still not in the menu. My theme manager has moved too and i cant change the themes i have just now. It tells me to use administrator button but it' not there. Weird i know but can anyone help please?

---

### Post by ccalvinfowler@aol.com on 2007-08-03
I am trying to copy packages from a disk to the /var/cache/apt/archive  but i am not getting any permissions.  since there are several packages to copy i don't want to do them one at a time by typing all of them indivdually under a termnal.  Unlike windows a *.* would copy all files,  what is it for  xubuntu.  or how else can i copy all of them to ths folder.

---

### Post by upthelum on 2007-08-04
Well as i solved the threads title issue, i wont sidetrack any longer and will raise another thread for any separate issues, thanks to all for the help...

---

### Post by dannyboy79 on 2007-08-05
> **ccalvinfowler@aol.com said:**
> I am trying to copy packages from a disk to the /var/cache/apt/archive  but i am not getting any permissions.  since there are several packages to copy i don't want to do them one at a time by typing all of them indivdually under a termnal.  Unlike windows a *.* would copy all files,  what is it for  xubuntu.  or how else can i copy all of them to ths folder.

if all the files were owned by root and you wanted to move them you could always switch to root by issuing

sudo -i
(then enter the sudo password, now you're root so can do anything so be careful not to do a rm -rf /

---

