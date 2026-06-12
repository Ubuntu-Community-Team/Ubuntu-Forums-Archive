---
title: "Protecting a custom .desktop file from apt"
date: 2015-04-23
forum: General Help
---

### Post by Andrew_Lucas on 2015-04-23
Hi all,

The title more or less says it all. I'm using Zotero, a bibliography manager, from a PPA. By default, the .desktop file that comes with the PPA (for some reason...) uses an icon that is both ugly, and not the official Zotero icon (it uses the dictionary icon).

I edited the .desktop file to use the zotero.png file included with the software. However, when the software is updated ('apt-get upgrade') this overwrites my file with a new one pushed out by the PPA.

Is there a way of protecting my edited file from apt? I've tried a sym-link, so the .desktop isn't actually in the /usr/share/applications directory but this hasn't worked (I think I put it in the /opt directory where Zotero is installed, and I think the script from the PPA starts by removing the 'old' Zotero from /opt and then downloading and unpacking a new one).

Is it just a case of putting my .desktop file somewhere it won't be overwritten - maybe in ~/.zotero or somewhere like that? Or do I need to play with apt?

All suggestions appreciated. :)

---

### Post by dino99 on 2015-04-23
if that ppa is not updated so often, then it seems easier to tweak it again after the upgrade is done. Better is post a request to the ppa maintainer. Changing that .desktop location will probably never works anyway as it will be recreated (or fail with an error) by the ppa script, and disturbing the default system choice is not a clean idea.

---

### Post by deadflowr on 2015-04-23
Copy the .desktop file from where ever it is into the user's .local/share/applications folder.
code]cp /usr/share/applications/app-name.desktop ~/.local/share/applications/[/code]
This file will be unaffected by any overrides or updates and the desktop file will remain as you have it.

After you move it, remove the icon from the desktop/launcher/panel, if you have one there and try re-adding it.
Sometimes, though, this can give you dupilcates.
I tend to open the one in the user folder with gedit and change the name; usually by adding something simple like My to the front.
This way I know it is the right one.

---

### Post by pqwoerituytrueiwoq on 2015-04-23
you can put it in /usr/local/share/applications/

---

### Post by Bucky Ball on 2015-04-23
Did you install the standalone and/or Firefox versions from [here]("https://www.zotero.org/download/")? I am a heavy Zotero user and have never come across this problem in all the years I've been using it. :-k

There is no PPA required to install the official Zotero packages. You should be able to click 'Add-ons' in Firefox and do a search for Zotero and install that way. The standalone is a .tar.gz from memory. 

If you didn't install from the above link I recommend doing so and seeing if the problem persists. The altered logos, etc., in the version you're using don't sound promising.

---

### Post by Andrew_Lucas on 2015-04-24
> **dino99 said:**
> if that ppa is not updated so often, then it seems easier to tweak it again after the upgrade is done. Better is post a request to the ppa maintainer. Changing that .desktop location will probably never works anyway as it will be recreated (or fail with an error) by the ppa script, and disturbing the default system choice is not a clean idea.

It's not often updated, but it's often enough that this would be a pain in the backside :P.
So long as the script complaining doesn't have any other problems, it putting out an error at the end doesn't bother me in the slightest. I'll know what it's about, I'll know that I'll have made it complain, and that it's not because the installation has gone wrong etc.
I understand that generally it's a good principle not to stick one thing on top of another when fixing, but I'm assuming that with something as innocuous as a .desktop file it won't make a difference.

> **deadflowr said:**
> Copy the .desktop file from where ever it is into the user's .local/share/applications folder.
code]cp /usr/share/applications/app-name.desktop ~/.local/share/applications/[/code]
This file will be unaffected by any overrides or updates and the desktop file will remain as you have it.

Copy rather than move? :S Is this just to create a 'fixed' icon that I can mv back after an update?

EDIT 1: Ahh, I see! I didn't know the system looked there as well as in /usr/share/applications for .desktop icons too! :D I've got a lovely new icon now, thanks!

> **deadflowr said:**
> 
After you move it, remove the icon from the desktop/launcher/panel, if you have one there and try re-adding it.
Sometimes, though, this can give you dupilcates.
I tend to open the one in the user folder with gedit and change the name; usually by adding something simple like My to the front.
This way I know it is the right one.

I've edited the file with nano to be 'how I want it'. If I remember after the next update, I'll have a backup to restore from...but is there a more permanent fix (so I won't have to restore after the update, and the system will know not to overwrite and/or execute the part of the installation script involving .desktop files)? Cheers anyway, man.

EDIT 2: I'm assuming I will get a duplicate when it updates, but it's easy enough to just rm that file (certainly less of a pain and than manually faffing with the .desktop each time). I'm going to mark this as solved, thanks!

> **pqwoerituytrueiwoq said:**
> you can put it in /usr/local/share/applications/
Uhm, I'm not sure you read the question...I know where .desktop files go ;)

> **Bucky Ball said:**
> Did you install the standalone and/or Firefox versions from [here]("https://www.zotero.org/download/")? I am a heavy Zotero user and have never come across this problem in all the years I've been using it. :-k
There is no PPA required to install the official Zotero packages. You should be able to click 'Add-ons' in Firefox and do a search for Zotero and install that way. The standalone is a .tar.gz from memory. 
If you didn't install from the above link I recommend doing so and seeing if the problem persists. The altered logos, etc., in the version you're using don't sound promising.

Yeah, I did too for a long time (more or less doing exactly what the script does: downloading the standalone from the site you gave, then sticking it in /opt and creating a .desktop icon), but then I discovered [this]("https://launchpad.net/~smathot/+archive/ubuntu/cogscinl") PPA. Basically, I'm using it over the manual installation because 1) it lets me update Zotero with the rest of the system and 2) it lets me pull in OpenSesame (I'm a psychology student, and that's used a lot in designing/building experiments). The maintainer of the PPA as far as I can tell is the bloke who develops OpenSesame, which is pretty widespread in psychology...so I trust the PPA. OpenSesame in particular pulls in a lot of python dependencies, which presumably I'd have to hunt down and install one by one if it wasn't for the PPA.

---

### Post by pqwoerituytrueiwoq on 2015-04-25
> **Andrew_Lucas said:**
> 

Uhm, I'm not sure you read the question...I know where .desktop files go ;)



i think you skimmed that file path and missed the /local/part of it
that is the system wide override folder, that is where you put manually installed launchers for file you installed manually for example

---

