---
title: "Have exec script - need to make exec icon on desktop"
date: 2014-11-22
forum: General Help
---

### Post by kent41 on 2014-11-22
Situation - I have an executable script that works and returnes a DNS ip address.
 
However I have tried to create a icon on the desktop to run the script from reading other
post but have not been successful. 

Is it possible to do this? and how?

Thanks
Kent

---

### Post by monkeybrain20122 on 2014-11-22
Make a .desktop file to invoke the script. Open a text editor to create a text file with this template

```

[Desktop Entry]

Comment=
Encoding=UTF-8
Exec=bash /path/to/script
Hidden=false
Icon=/path/to/icon
Name=
Terminal=false
Type=Application
Version=
Categories=

```

Here /path/to/script is the path to where the script is stored. E.g if you make a directory called bin in your home and put it there the path would be /home/yourusername/bin/script.sh where script.sh is the name of your script.

You can make an icon if you have a pictiure and use its path in the "Icon=" line

Save the file with extension .desktop, then right click it, make it executable (from Properperties > Permissions or something like that, depending on your File manager) Then put it in the hidden folder  .local/share/applications in your home (press ctrl+ h or choose 'show hidden' from file manager's menipt i to see it)

Now the launcher will show up in your menu or the dash depending on your DE. From there you can put in on the desktop like you would with other applications. The exact way to do it depends on your DE.

Edited: BTW make sure your script has permission to execute. Either do it like above for the .desktop file or chmod u+x in the terminal.

---

### Post by agillator on 2014-11-22
I cannot speak for other distros, but in Ubuntu you can also right click on the desktop and select 'Create Launcher' on the menu.Then fill in the information asked for in the dialog. The 'Command' box is for the command to start the script as if you were starting it from the command line. Click the 'Icon' button and select an icon or enter the path of the image you want to use as the icon. Click OK and the system creates the .desktop file for you mentioned in the above response. Either way works fine. But, as MonkeyBrain mentioned, the script must have the execute permission set.

---

### Post by kent41 on 2014-11-22
Monkeybrain
Thanks for getting back to me so soon. it's been a few years since
I used Ubuntu. I have been using Puppy Linux but i needed a opt system
that has more options than Puppy and Ubuntu seems to have what I need.

Current system is Ubuntu 14.04

I created the script from the template you provided but i'm not sure
if I have it populated it correctly. Also put the picture and your script in .local/share/applications.
also scripts are executable.
but I don't see anything in the desktop or in the lancher.

where do I go from here?
Thanks again
kent



[Desktop Entry]

Comment=
Encoding=UTF-8
Exec=bash /home/kent/Bin/DNS-Look.sh
Hidden=false
Icon=/home/kent/.local/share/applications/cardinal.jpg
Name=
Terminal=false
Type=Application
Version=
Categories=

---

### Post by kostkon on 2014-11-22
Make that desktop file executable and move it to your Desktop folder.

---

### Post by kent41 on 2014-11-22
hi kostkon
ok i moved the file dns.desktop to the desktop folder. now it shows up on the desktop but when i click on it nothing happens.
is something wrong with the file. i posted it in my first post;
thanks for any help.

edit: sorry i mean my second post for dns.desktop

---

### Post by monkeybrain20122 on 2014-11-22
The .desktop should go to .local/share/applications (the icon can be anywhere, I usually put it in /home/username/share/icons, I have compiled things so it was created at some point, you can create it yourself)

Make sure your .desktop file is executable (check Properties > Permissions)

To check if it works click it. 

From here there are different ways to make it appears on the desktop, depending on your DE (which one??) I wouldn't recommend putting the .desktop file in the desktop folder because it wouldn't appear in the menu sysrem that way.

Edited: make sure your script works first.

---

### Post by kostkon on 2014-11-22
> **kent41 said:**
> hi kostkon
ok i moved the file dns.desktop to the desktop folder. now it shows up on the desktop but when i click on it nothing happens.
is something wrong with the file. i posted it in my first post;
thanks for any help.

edit: sorry i mean my second post for dns.desktop
It's probably working, but if you want to have it open a terminal window every time you click on it, then set the Terminal parameter to true, i.e.
```
Terminal=true
```

---

### Post by kostkon on 2014-11-22
You could also add the following lines in your script
```
sleep 2 #sleep for 2 secs
exit
```
and you won't have to click the close button to get rid of the terminal window.

---

### Post by kent41 on 2014-11-22
> **kostkon said:**
> It's probably working, but if you want to have it open a terminal window every time you click on it, then set the Terminal parameter to true, i.e.
```
Terminal=true
```

i set terminal to true and now it brings up a terminal and ask for passwd, after you enter a passwd it goes away. maybe i should add some delay. in the script?
how to add delay?
thanks

---

### Post by mc4man on 2014-11-22
Is the location of your script as written in the .desktop correct?
(- you posted Bin, most people would create ~/bin

---

### Post by kent41 on 2014-11-22
OK now the script exec but ask for passwd, the sleep works great. 
where would  I put passwd=XXXXXX so i would not have to manually enter passwd?

also the Icon on the desktop is blank, is there a special . extension or is .jpg ok

thanks so much for the help looks like were just about there


edit: I took out the sudo and now it works ok except the blank Icon

---

### Post by mc4man on 2014-11-22
.jpg should be ok (outside possibility that a weird size *may* be an issue
More likely there is some mistake in path and or filename, so double check that closely
(when I want a full path to a filename sometimes I just drag & drop the file/icon on to an open terminal then copy it minus the start & end apostrophes

---

### Post by kent41 on 2014-11-22
> **mc4man said:**
> .jpg should be ok (outside possibility that a weird size *may* be an issue
More likely there is some mistake in path and or filename, so double check that closely
(when I want a full path to a filename sometimes I just drag & drop the file/icon on to an open terminal then copy it minus the start & end apostrophes

is there a dir in 14.04 that has icons or pic?
my cardinal has 2.6mb, it mybe to large.

thanks for your help.
kent

---

### Post by kostkon on 2014-11-22
> **kent41 said:**
> is there a dir in 14.04 that has icons or pic?
my cardinal has 2.6mb, it mybe to large.

thanks for your help.
kent
You could try resizing your icon and saving it as png.

Otherwise, /usr/share/icons/ has got plenty of icons.

---

### Post by mc4man on 2014-11-22
/usr/share/icons /usr/share/pixmaps /usr/share/app-install  are 3 places

(- /usr/share/pixmaps  - if you use or place an icon there then you don't need to full path in a .desktop, just icon name+extension will work. Overall though always better to full path the Icon= line in a .desktop

I would at the least just pick one & see if it works.. ( you can also find icons online - 48x48 or 64x64 are reasonable for a .desktop icon though you're not limited to those sizes by any means

---

### Post by kent41 on 2014-11-22
Looks like the problem with the icon was my pic was too large.  All seems to be working ok.
also once you get one of these scripts to work on your desktop the following ones will be
easy. ha ha

Thanks to all who helped me get the job done. it was much harder in puppy to do the same thing.

Kent  :D

---

