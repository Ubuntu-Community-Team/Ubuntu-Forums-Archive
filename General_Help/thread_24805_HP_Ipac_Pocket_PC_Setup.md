---
title: "HP Ipac Pocket PC Setup"
date: 2005-04-08
forum: General Help
---

### Post by Meetze on 2005-04-08
I've followed the instructions found in source forge as well as this website for setting up Multisync and the SynCE command line utility.  It seems to me that the plugin for Mulitsync - SynCE has no configuration file in the GUI that I can see.  I have not found any documentation on it either.  Is there a verbose guide out there on setting up these two progs with Evolution?  I'm missing a step somewhere.  

The pocket pc sets up fine and is recognized - loads with synce-serial-start.  But the SYNC command doesn't seems to not activate the plugin after setting up the pair for SynCE -- > to -- > Evolution.  There seems to be no communication to the device at all.  

I read at the SourceForge that there was a mediation program called the synce-matchmaker.  However, this prog isn't present in the repository.

I also noticed that none of the synce tools are available from the root console after installing the synce package from the repository.

I think I've reveiled my lack of education on the subject.  Maybe someone might be able to flip me a few cents.  

Thanks in advance.

---

### Post by endoscient on 2005-04-08
[QUOTE=Meetze]I've followed the instructions found in source forge as well as this website for setting up Multisync and the SynCE command line utility.  It seems to me that the plugin for Mulitsync - SynCE has no configuration file in the GUI that I can see.  I have not found any documentation on it either.  Is there a verbose guide out there on setting up these two progs with Evolution?  I'm missing a step somewhere.  

The pocket pc sets up fine and is recognized - loads with synce-serial-start.  But the SYNC command doesn't seems to not activate the plugin after setting up the pair for SynCE -- > to -- > Evolution.  There seems to be no communication to the device at all.  

I read at the SourceForge that there was a mediation program called the synce-matchmaker.  However, this prog isn't present in the repository.

I also noticed that none of the synce tools are available from the root console after installing the synce package from the repository.

I think I've reveiled my lack of education on the subject.  Maybe someone might be able to flip me a few cents.  

Thanks in advance.[/QUOTE]
 The same exact thing happens to me.. Anyone know why?

---

### Post by joshmachine on 2005-04-09
Welcome to hell friends.  

OK it's not really hell, but I had a mofo of a time getting this up and running.  OK ready for fun?  let's go.


Problem one.  the whole synce bits are divided into many seperate packages.  here are the ones that you will want to have a complete system

Actually problem one is that there are a lot of details missing from documentation etc.

synce-multisynce-plugin package picks up all the libraries that you need, but there some tool prerequisites as well. the packages are 

librapi2-tools:
this has some command line tools to install software, let to you pocket pc copy files, etc.  check out synce.sourceforge.net for some OK documentation about what tools are available, or just list the files in the packages and figure it out for yourself.

Note: All of the tools as released by the synce folks are prefixed with "synce" in the debian packages.  Some of the scripts are still expecting the old names (no "synce") you may have to update them manually. 

Note: synce-pcp copies files to and from the device.  You MUST prefix the ipaq device path with a colon ":"  


librra0-tools:
This is where "synce-matchmaker" comes from it has to run before you can do anything with activesynce.  This is creates a pair in the devices registry and tells it it's cool to synce with.  the command is way simple.  connect your device.  
it's been a while since i've done this but I think the command to create the pair is 

>>synce-matchmaker create [1|2]
you get two reg entries so you can sync your device to two different machines.

Ummm....

I think that's it.

The syncing can be a little funky between the evolution and the device so I usually create a seperate addressbook/tasks/calendar just for the device.  

See how far that gets y'all.  Let me know when you get there, then we can talk about connecting over wifi  W00T!

cheers.

---

### Post by Meetze on 2005-04-11
Nice answer.  I'll see what I can come up with.

Thanks!

---

### Post by Meetze on 2005-04-11
I was able to get my pocketpc to sync my contacts with evolution.  That was a breakthrough.  Now I want to transfer files back and forth from the PDA.  Both the librapi2-tools and librra0-tools are loaded, however, I don't have access to commands such as pcc, pls, or even pstatus.  After doing a search on the drive, none of these commands even list.

---

### Post by joshmachine on 2005-04-11
if you ever want to know what a package makes available you can simply issue the following command

$ dpkg -L  [package-name]

doing this for librapi2-tools shows the following (among others)

/usr/bin/synce-install-cab
/usr/bin/synce-list-programs
/usr/bin/synce-pcp
/usr/bin/synce-pls
/usr/bin/synce-pmkdir
/usr/bin/synce-pmv
/usr/bin/synce-prm
/usr/bin/synce-prmdir
/usr/bin/synce-prun
/usr/bin/synce-pstatus
/usr/bin/synce-registry
/usr/bin/synce-remove-program


I guess you missed it in my earlier post, but the debian maintainer has renamed all of the scripts (I assume to avoid name clashes).

Note that some of the scripts are broken (they are expecting to call other unprefixed commands.) I don't recall which ones, but the failure will be obvious. You will need to open the script in a text editor and fix manually (just add the "synce-" prefix and it'll work fine.

Also note that you can copy things both ways but the path on the device *must* be prefixed with a colon ":"  and spaces must be escaped with a backslash "\" i.e.

$ synce-pcp an.mp3 :/My\ Documents/My\ Music   

Cheers

---

### Post by Meetze on 2005-04-12
This helped alot. Thanks again.

---

### Post by Meetze on 2005-04-14
[QUOTE=joshmachine]

I guess you missed it in my earlier post, but the debian maintainer has renamed all of the scripts (I assume to avoid name clashes).

Note that some of the scripts are broken (they are expecting to call other unprefixed commands.) I don't recall which ones, but the failure will be obvious. You will need to open the script in a text editor and fix manually (just add the "synce-" prefix and it'll work fine.

Cheers[/QUOTE]

I did miss that.  Mabe you could link it for me.  I don't know enough about this system to understand what your talking about here completely.  What file am I looking at to see where these changes need to occur?  Will I need to uninstall the librapi2-tools and reinstall after I make the changes to this file? - or is it not that easy?

---

### Post by joshmachine on 2005-04-16
[QUOTE=Meetze]I did miss that.  Mabe you could link it for me.  I don't know enough about this system to understand what your talking about here completely.  What file am I looking at to see where these changes need to occur?  Will I need to uninstall the librapi2-tools and reinstall after I make the changes to this file? - or is it not that easy?[/QUOTE]
 No you won't need to uninstall anything. You will be making changes to the files in the librapi2-tools distribution.  this means that if you make changes and then the package is updated your changes will be lost.  This is bug in the debian packages.

For expample "synce-install-cab" is for installing programs on the ipaq.  This is a script located in the /usr/bin directory.  It calls other programs in the distribution (like "pcp") but it uses the old names.  

Before you can use it you have to change it to use the new names.  

Ex. 

Line 19 of /usr/bin/synce-install-cab
${exec_prefix}/bin/pmkdir /Windows/AppMgr 2>/dev/null

but in the current distro the command has been renamed to synce-pmkdir so you would have to change it to 
${exec_prefix}/bin/synce-pmkdir /Windows/AppMgr 2>/dev/null

You will know it when you run these programs (there are man pages on all of them) as you will get errors about "pmkdir" command not found etc. etc.  Then just open the command you just ran 

$ which [command-name] 

will give you the path to it, and fix it up.

Cheers

---

### Post by hanzj on 2005-12-03
[QUOTE=joshmachine]
The syncing can be a little funky between the evolution and the device so I usually create a seperate [sic] addressbook/tasks/calendar just for the device.  
[/QUOTE]

What do you mean by funky? What happens?
And how do you create sep*a*rate addressbook/tasks/calendar? On the PDA? Or on Evo?

---

### Post by joshmachine on 2005-12-03
Seperate addressbook etc in evolution. 

The funkiness is limited to duplicated entries. 

Cheers,
Josh

---

