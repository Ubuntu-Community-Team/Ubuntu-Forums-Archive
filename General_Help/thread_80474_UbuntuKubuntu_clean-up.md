---
title: "Ubuntu/Kubuntu clean-up"
date: 2005-10-22
forum: General Help
---

### Post by oliwally on 2005-10-22
I was just wondering if K/Ubuntu or linux in general ever needs cleaning up in regard left-over files from installing and uninstalling different apps? If there are left-overs, do they do any harm or slow the system down? How would I get rid of left-overs?

Also, does K/Ubuntu or linux in general ever need defragging like windows does?

I guess what I'd like to know is if K/Ubuntu / Linux ever needs an enema to keep the bowels of the whole thing regular and smooth-running? Are there any laxative-like apps that will clean out the system, to get rid of the.....well,.....dung?

---

### Post by coronya on 2005-10-22
Well it sometimes helps to clean the system a bit. I usually use two programs for this purpose.

1. deborphan (apt-get install deborphan) removes libs that are no longer associated with programs. It is surprisingly accurate. (Do not remove libc6-i686 if it offers you however).

2. localepurge (apt-get install localepurge) removes the locales which you are not using. For example, I speak french, so I keep every en* and fr*. The remaining is removed.

There are also some useful programs in Ubuntu that do a more thorough job, but you need to learn them. I did not personnaly try them.

If you are not afraid to build an application, I would also suggest you search for kleansweep on google. This is a nice linux application that rid you of some annoying leftovers like broken links and empty dirs. However, DO BACKUP if you want to use it since you'll have quite a bit of learning to do :).

If you want a simple and painless solution, deborphan and localepurge do wonder without putting you too much at risk.

Hope it helps,
Richard

---

### Post by Dr. Nick on 2005-10-22
Their is also an option in synaptic for not installed(residual config) those are usually apps you have removed but still have configuration files left behind, I dont have any at the moment so the option is not avaible to me, I think its under the status button.

Here is a GUI for deborphan [http://ubuntuforums.org/showthread.php?t=79028](http://ubuntuforums.org/showthread.php?t=79028) it makes it even easier :)

Unlike windows, Linux doesnt have a registry that gets bloated and drags everything down, Fragemntaion is also a bit better I believe, I have never defraged and not sure if you can, but my system is still running very nice just like when it was installed.

---

### Post by DoeRayMe on 2005-10-22
[QUOTE=Dr. Nick]Their is also an option in synaptic for not installed(residual config) those are usually apps you have removed but still have configuration files left behind, I dont have any at the moment so the option is not avaible to me, I think its under the status button.

Here is a GUI for deborphan [http://ubuntuforums.org/showthread.php?t=79028](http://ubuntuforums.org/showthread.php?t=79028) it makes it even easier :)

Unlike windows, Linux doesnt have a registry that gets bloated and drags everything down, Fragemntaion is also a bit better I believe, I have never defraged and not sure if you can, but my system is still running very nice just like when it was installed.[/QUOTE]

wow thanks for the synaptic, i had nearly 100

---

### Post by Dr. Nick on 2005-10-22
[QUOTE=DoeRayMe]wow thanks for the synaptic, i had nearly 100[/QUOTE]

I havent had any trouble using it, just make sure all of them are not needed first, I should be pretty accurate but their is always a chance it isnt.

---

### Post by oliwally on 2005-10-22
> Their is also an option in synaptic for not installed(residual config) those are usually apps you have removed but still have configuration files left behind, I dont have any at the moment so the option is not avaible to me, I think its under the status button.

Thanks for the help!

I'm not finding the option in Synaptic to get rid of residual files (or perhaps I'm looking straight at it and just don't know it).  I've found the line under the status button that gives the option "installed (local or obsolete)". Is that the one? Do I then just mark them all for complete removal? Is it safe to do so. 

Some more guidance please, I'm a little unsure. Breezy is running well - I don't want to mess it up.

---

### Post by Xian on 2005-10-22
[QUOTE=oliwally]I'm not finding the option in Synaptic to get rid of residual files (or perhaps I'm looking straight at it and just don't know it).  I've found the line under the status button that gives the option "installed (local or obsolete)". Is that the one? Do I then just mark them all for complete removal? Is it safe to do so. [/QUOTE]
Not necessarily. You could also have some legitimate entries.
For example, I have in that list:

Opera
Win32codecs
libdvdcss2
libdivxencore0

I need and use each of these.

There are really only three main things to look for:

1. Packages you have installed but don't need.
2. Packages you have removed but not purged.
3. Orphaned packages.

This is an issue which should generate very little concern on your part. Even if you are a person that has a lot of packages installed on your system, there would typically be very little cruft. Linux is generally very clean when using a good file manager like APT (which is the default in Ubuntu).

---

### Post by Dr. Nick on 2005-10-22
[QUOTE=oliwally]Thanks for the help!

I'm not finding the option in Synaptic to get rid of residual files (or perhaps I'm looking straight at it and just don't know it).  I've found the line under the status button that gives the option "installed (local or obsolete)". Is that the one? Do I then just mark them all for complete removal? Is it safe to do so. 

Some more guidance please, I'm a little unsure. Breezy is running well - I don't want to mess it up.[/QUOTE]

The residual config appears in the side pane at the bottom when clicking status button in the bottom left of the screen. If its not their thier may not be any residual config

---

### Post by oliwally on 2005-10-23
> The residual config appears in the side pane at the bottom when clicking status button in the bottom left of the screen. If its not their thier may not be any residual config

Right, I see it. In the right hand side of the screen there are now lots of packages listed. The line at the very bottom tells me that there are '73 packages listed, 1297 installed, 0 broken, 0 to install/upgrade, 0 to remove'. None of the packages on the right are marked (little square next to them is just blank/white), nor do they seem to be installed (installed Version column is empty). So, does that mean then that all is sweet and I should just leave it alone, or should I select all those packages listed and remove them?

> This is an issue which should generate very little concern on your part. Even if you are a person that has a lot of packages installed on your system, there would typically be very little cruft. Linux is generally very clean when using a good file manager like APT (which is the default in Ubuntu).

Sounds like I should not worry about giving my system an enema cause linux doesn't get clogged up? Would that seem a logical and safe deduction from what's been said in this topic?

---

### Post by Dr. Nick on 2005-10-23
[QUOTE=oliwally]Right, I see it. In the right hand side of the screen there are now lots of packages listed. The line at the very bottom tells me that there are '73 packages listed, 1297 installed, 0 broken, 0 to install/upgrade, 0 to remove'. None of the packages on the right are marked (little square next to them is just blank/white), nor do they seem to be installed (installed Version column is empty). So, does that mean then that all is sweet and I should just leave it alone, or should I select all those packages listed and remove them?


Yeah they will appear as uninstalled, If you right click their will be  a choice for "complete removal" which should purge most if not all of its left behind config files. Once that list is empty the residual config choice will disappear.



Sounds like I should not worry about giving my system an enema cause linux doesn't get clogged up? Would that seem a logical and safe deduction from what's been said in this topic?[/QUOTE]

It doesnt get clogged up like windows with registry bloat, the problem with windows is the registry gets loaded into memory on boot, so alot of old junk in registry in win casuses more ram usage. Linux may get clogged some but shouldnt affect overall system speed

---

### Post by Xian on 2005-10-23
[QUOTE=oliwally]So, does that mean then that all is sweet and I should just leave it alone, or should I select all those packages listed and remove them?[/quote]
The packages listed in the residual config category are there becuase you (or APT) has removed them from the system, but they have not been purged -- which just means that the configuration files associated with those applications remain on your system. This is certainly not necessarily a bad thing and is why removed packages are not purged instead by default. However, you can safely highlight and choose "Mark for Complete Removal" in Synaptic any programs that you know are not wanted and will not be dependent upon any user config in the event of a potential reinstallation.

[QUOTE=oliwally]Sounds like I should not worry about giving my system an enema cause linux doesn't get clogged up? Would that seem a logical and safe deduction from what's been said in this topic?[/QUOTE]
That is basically true. I gave a short list in my above post of the things you might look for, but even if there were instances of each on your system it still would not account for any significant space usage or performance hindrance. There are tools like deborphan to find orphaned packages if you are interested. Personally, I wouldn't give it any notice.

---

### Post by oliwally on 2005-10-24
> It doesnt get clogged up like windows with registry bloat, the problem with windows is the registry gets loaded into memory on boot, so alot of old junk in registry in win casuses more ram usage. Linux may get clogged some but shouldnt affect overall system speed

> That is basically true. I gave a short list in my above post of the things you might look for, but even if there were instances of each on your system it still would not account for any significant space usage or performance hindrance. There are tools like deborphan to find orphaned packages if you are interested. Personally, I wouldn't give it any notice.

Well, that just about settles it for me. I'll leave it alone for now. 

Thanks folks. You have been teriffic and extremely helpful  - true to the Ubuntu Forum spirit. I can't speak highly enough of all the great people who are willing to help out on this forum, and you're right up there with them. Thanks again.

---

