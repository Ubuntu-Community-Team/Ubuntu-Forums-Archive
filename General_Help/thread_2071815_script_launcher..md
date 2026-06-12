---
title: "script launcher."
date: 2012-10-16
forum: General Help
---

### Post by marjoh05 on 2012-10-16
I want to launch this script with a double click from my ubuntu desktop:
sudo nautilus /srv/samba/innleveringer/

I tried google and found this innleveringer.desktop

The script gets an error, i se it targets my home directory but its stops there.

Is there any other easy way?

I want it to run just as an windows .bat or .vbs

---

### Post by raja.genupula on 2012-10-16
Hi 

sorry man , we are unable to understand your issue properly . could you improve issue with more information ?

---

### Post by PowerBarry43 on 2012-10-16
run these commands from a terminal and it should get you there if I understand your question correctly.
```

sudo cp /usr/share/applications/nautilus-home.desktop ~/Desktop
sudo chown [yourusername] ~/Desktop/nautilus-home.desktop
sudo chmod 755 ~/Desktop/nautilus-home.desktop
sudo gedit ~/Desktop/natuilus-home.desktop
```then edit the "name" line to read "name=whatever you want the launcher to be named"  then paste in the commands you wish to run on the third line after "exec=" instead of nautilus %U

Finnaly save and close gedit and you should have your own custom launcher on your desktop :)

Hope this helps!

Barry

---

### Post by marjoh05 on 2012-10-17
Thanks for reply.

Though when i CP the first line, it wont copy it to the Desktop, and then ofcourse the rest of the code wont work eiter. The code looks okay though.

Im pretty new to ubuntu, so thats why its hard to understand me :) And it is hard for me to understand you too..

Still young and still learning :-)

---

### Post by marjoh05 on 2012-10-17
um, i worked it out somehow. (needed "su" to access desktop in shell).

I used everycode (and they worked) but still there are no Icon on the desktop. Is it hidden? I do see it in shell!

---

### Post by SlugSlug on 2012-10-17
if you used su then it's most likely in /root/Desktop folder or ist now called Desktop inside of /root 

As your user try

sudo mv /root/Desktop/nautilus-home.desktop ~/Desktop/

if not try

sudo cp /root/Desktop ~/Desktop/nautilus-home.desktop

---

### Post by PowerBarry43 on 2012-10-17
hmm all users should have at least read and execute permissions for everything in the /usr/share/applications directory as they need to execute them  to actually run their applications. you shouldn't even need elevated permissions to simply make a copy of any of those launchers provided you copy it to your own desktop. you could try running
```

sudo chmod 755 -R /usr/share/applications
```If all else fails you could run

```
gksu nautilus
```then browse to the /usr/share/applications folder and copy the "home folder" launcher to your desktop through the right click menu.

An option you could use a last resort would be to just have a file on your desktop named eg script.sh containing the lines

```
#!bin/bash
[commands to be executed]
```

then run

```
chmod 755 ~/Desktop/script.sh
```

this will make an executable script but you will have to click run in terminal each time you want to run the commands.

Hope this helps!

Barry

---

### Post by marjoh05 on 2012-10-17
Solution.. i feel so stupid. Im running a Norwegian version of Ubuntu.

I have the Desktop folder, but also "Skrivebord" (thats Desktop in Norwegian).

I should have used "Skrivebord", i made a .SH script and then ran sudo chmod +x script.sh (Suggest from a friend) Now i can run the script with a Icon.

So. Make the script:
#!/bin/bash
nautilus /srv/samba/innleveringer/

save as scriptname.SH

go into terminal

Run:
sudo chmod +x script.sh

Now when you double klick your Icon (script.sh) you will have the choice to open as a document, run in console or just run!

Hope this will be usefull for someone else.

---

