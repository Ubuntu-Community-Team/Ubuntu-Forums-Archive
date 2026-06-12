---
title: "nautilus freezes in home folder"
date: 2007-02-27
forum: General Help
---

### Post by seshomaru samma on 2007-02-27
Lately I have a strange phenomenon , sometimes when I click on my home folder nautilus opens and freezes for the longest time . If I restart X I get this message when I try to log into gnome " i've detected a panel already running , will now exit" and gnome shows up except without any of the desktop icons and nautilus freezes if I open it. Only a hard reboot solves it.
if i run nautilus from the terminal , i get no errors but it still freezes

this happens in icewm as well

---

### Post by SynapseR on 2007-08-09
I have exactly the same problem.
Someone help please !!

---

### Post by vexorian on 2007-08-09
try goign to nautilus preferences and turn previews off.

Also, if nothing helps, do sudo apt-get install thunar

and use thunar for browsing files.

If you got thunar browse your home folder and check if you don't have a big SVG out there, it seems they cause nautilus freezes.

---

### Post by SynapseR on 2007-08-09
Problem Solved !!
The issue was folder permissions. Somehow files/dirs in my home dir were changed to root owner.

So after doing 

```
sudo chmod 755 -R /to/mydir/dir/
```

and

```
sudo chown userid:userid  -R /to/mydir/dir/
```

It works perfectly.

Maybe you should try that samma.

---

### Post by dkr on 2007-08-15
Hi,

I had the same problem.

It turned out that it is caused by Open office Writer files (.odt) or pdf files exported with Open office.

When I remove this files from my home folder, remove the .thumbnails folder and killall nautilus the problem is gone.

Obviously I would like to go on using OpenOffice files. (Yes, I know I could switch off previews but I would like to avoid that.)

Does anybody know what component does the thumbnail creation for nautilus so I can dig a bit deeper there? Or does anybody know how I can force nautilus to start from the console and give me some output (I seems to detect that there is another nautilus process running and attaches itself to that)?

My OpenOffice Version is: 2.2.0-1ubuntu4
My nautilus version is: 1:2.18-1-0ubuntu1

I attached an empty odt and pdf file which cause the crash for me.


Best,

Dirk

---

