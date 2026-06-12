---
title: "issues with privileges."
date: 2013-08-23
forum: General Help
---

### Post by daniel50 on 2013-08-23
was wondering if someone can help a noob out... i have 10.04 with linuxcnc. it has been working fine for a while, then i couldnt access the folders through my network all off a sudden. i rebooted ubuntu, and then it appears i lost all privileges somehow. if i click on the applications dropdown menu, it shows nothing. If i click on the system tab, it only shows a few items like about gnome or whatever.

I was able to get into terminal with ctr+alt+f1, and i was able to log in, check the groups, and permissions. all seem to be ok, it says i was in the admin group. But still no access to anything. Any ideas?

---

### Post by daniel50 on 2013-08-23
i used to get an apt authentication error on startup, could this be related? i'm trying to run updates now from terminal to see if that helps.

---

### Post by daniel50 on 2013-08-25
Anyone?

---

### Post by Bashing-om on 2013-08-25
daniel50; Hi !

Version 10.04 desktop has reached End Of Life. Do you really want to beat a dead horse ?
It is highly and I mean HIGHLY recommended to upgrade to a current version ... EOL versions do not get any further support or security updates. -> not safe to be on the 'net with it at all .

Back up your files and install !

Else; given reason enough an attempt can be made to fix 10.04 ...but it better be worth the effort.

[INDENT][INDENT]what ya want to do
[/INDENT][/INDENT]

---

### Post by daniel50 on 2013-08-25
Thanks, but linuxcnc is only supported on 10.04, so i I cannot upgrade. This is solely a cnc machine.

---

### Post by ibjsb4 on 2013-08-25
I do not know anything about your cnc software, but I am wondering if you do need the 10.04 desktop GUI.  The 10.04 Server Edition is supported till 2015 and will provide you with a terminal only interface.

And more iffy territory would be updates throught the old-releases channels.

[https://help.ubuntu.com/community/EOLUpgrades#Requirements](https://help.ubuntu.com/community/EOLUpgrades#Requirements)

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by 1clue on 2013-08-25
You might want to download and burn the 10.04 installer CD if you don't already have it, and boot off of it and then try 'repair existing Ubuntu' or whatever it says when it boots.

It might help if I knew exactly what you're doing with it.  Is this a graphical workstation or just an embedded controller style setup, what runs machine tools?  I know what CNC is, but have never seen it in action.  All the machine tools (cad/cam) I've seen you have a workstation somewhere, you put your CAD file on a usb stick or CD or whatever and then walk it over to the CNC where you load it and run it on a simple menu-driven program.

---

### Post by Bashing-om on 2013-08-25
daniel50; 

See the above post ... ok, we can make it to where your machine is of continued use with 10.04.
Let's look at what might be preventing access to the GUI ...post back the output of terminal codes:
```

ls -al ~/.ICEauthority
ls -al ~/.Xauthority

```
Many times the permissions on these files have been changed, preventing access.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by daniel50 on 2013-08-25
> **ibjsb4 said:**
> I do not know anything about your cnc software, but I am wondering if you do need the 10.04 desktop GUI.  The 10.04 Server Edition is supported till 2015 and will provide you with a terminal only interface.

And more iffy territory would be updates throught the old-releases channels.

[https://help.ubuntu.com/community/EOLUpgrades#Requirements](https://help.ubuntu.com/community/EOLUpgrades#Requirements)

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)
It is installed as a package.... linuxcnc and 10.04 together from [www.linuxcnc.org]("http://www.linuxcnc.org"). I don't think you can really do it any other way without knowing what you're doing, which i do not lol

> **1clue said:**
> You might want to download and burn the 10.04 installer CD if you don't already have it, and boot off of it and then try 'repair existing Ubuntu' or whatever it says when it boots.

It might help if I knew exactly what you're doing with it.  Is this a graphical workstation or just an embedded controller style setup, what runs machine tools?  I know what CNC is, but have never seen it in action.  All the machine tools (cad/cam) I've seen you have a workstation somewhere, you put your CAD file on a usb stick or CD or whatever and then walk it over to the CNC where you load it and run it on a simple menu-driven program.
linuxcnc is a machine control program. It's not CAM/CAD. It uses hardware to control a mill or lathe or whatever you decide to build with it. I was unaware of a 'repair existing Ubuntu' function on the installer cd. I'll look into that, thanks!
> **Bashing-om said:**
> daniel50; 

See the above post ... ok, we can make it to where your machine is of continued use with 10.04.
Let's look at what might be preventing access to the GUI ...post back the output of terminal codes:
```

ls -al ~/.ICEauthority
ls -al ~/.Xauthority

```
Many times the permissions on these files have been changed, preventing access.[INDENT][INDENT]just try'n to help
[/INDENT]
[/INDENT]

It says no such file exists for either one.

It's so weird because i literally changed nothing. Didn't delete any files, didn't modify them lately, nothing. All i do is run the mill with this computer.



Thanks for the help so far guys!

---

### Post by 1clue on 2013-08-25
If you KNOW nothing changed on the Linux box, then chances are something changed somewhere else.  This could be a network problem.  Could you have changed access or had an upgrade of some sort on the remote system?

---

### Post by Bashing-om on 2013-08-25
daniel50; Hey ...
Those files should exist !
my output for reference:
> 
sysop@1304mini:~$ ls -al ~/.ICEauthority
-rw------- 1 sysop sysop 23798 Aug 25 10:44 /home/sysop/.ICEauthority
sysop@1304mini:~$ ls -al ~/.Xauthority
-rw------- 1 sysop sysop 103 Jul 10 18:37 /home/sysop/.Xauthority
sysop@1304mini:~$ 
 where "sysop" is my username.

I am going to log out from here and reboot and make sure those files are seen from the text login.

edit: I am back !
One should see those files even from the text log in command line. May I suggest that you may have made typo's.
The "~/" is a shortcut for the path that means "your home directory" that path must be in place.
The file name does begin with the "." character and "ice" is uppercase as "ICE" as well the "x" is uppercase as in "X"

Else; Going to be a pain to re-create those files ? How in the world did they get removed ?

[INDENT][INDENT]I'll be back
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-08-25
Those files are only necessary if you have some sort of X involved.  On an ubuntu server install you wouldn't necessarily have them.

I just checked on one ubuntu server vm I have going, it has .Xauthority but not .ICEauthority.  I'm speculating but I think it has .Xauthority only because I tend to ssh -X <box> instead of ssh <box>.  Can't think why else the .Xauthority would exist.

---

### Post by daniel50 on 2013-08-25
one thing i just noticed is all the folders are grey instead of orange/brown like they normally are. Is this a hint to what's going on?

---

### Post by 1clue on 2013-08-25
> **daniel50 said:**
> It is installed as a package.... linuxcnc and 10.04 together from [www.linuxcnc.org]("http://www.linuxcnc.org"). I don't think you can really do it any other way without knowing what you're doing, which i do not lol


linuxcnc is a machine control program. It's not CAM/CAD. It uses hardware to control a mill or lathe or whatever you decide to build with it. I was unaware of a 'repair existing Ubuntu' function on the installer cd. I'll look into that, thanks!

It says no such file exists for either one.

It's so weird because i literally changed nothing. Didn't delete any files, didn't modify them lately, nothing. All i do is run the mill with this computer.



Thanks for the help so far guys!

So this is the machine that's hooked straight up to your mill or lathe, effectively an embedded controller with a non-graphical human interface.

The more I think about this, the less inclined I am to think this has anything at all to do with your CNC box.  If you didn't change anything here then this is not what broke, unless there's a hardware failure.

Look for recent changes on your network.  Changing a user or group ID on some sort of authentication server (domain, LDAP, NIS, whatever) or on the shared directory, or a password expiration/change might do this.

Ignore the .ICEauthority and .Xauthority files.  If you don't use graphical tools on this box then they have no need to be there.

---

### Post by Bashing-om on 2013-08-25
@1clue I can appreciate what you are saying ... however, correct my error if so, is not the GUI a product of X and as such in order to access The GUI through the X layer .. is not the files .ICEauthority and .Xauthority required to authorize this access ???
Knowing that the GUI is not part of a server install.

[INDENT][INDENT]still learning even after all these years
[/INDENT][/INDENT]

---

### Post by 1clue on 2013-08-25
The system in question is a non-gui system controlling a mill or a lathe, is what the OP said.

If the files are only accessed through a shared (nfs, cifs...) directory, then that has nothing to do with X.

My Ubuntu Server installs all work fine.  I just checked another one, it has neither .Xauthority nor .ICEauthority.

If the GUI is from another system accessing shared files, the .Xauthority and .ICEauthority will be on that box, if it's Linux.  It has nothing to do with the non-gui box.

All that said, if I'm mistaken about the arrangement and the cnc box has a gui then yes it needs the files.

And I just verified my earlier suspicion:  I deleted the .Xauthority from the headless VM I had before, ssh'd into it and it worked.  Neither .Xauthority nor .ICEauthority present.  Then I exited, ssh -X <box> and suddenly .Xauthority shows up.

These files will appear if they're needed.  The absence of these files is a non-issue IMO.

---

### Post by 1clue on 2013-08-25
So, @daniel50:

You seem to be using a GUI-based Linux box to access this CNC system.  Is this true?

What sort of details can you give us regarding your setup?
[LIST=1]
[*]What OS is your workstation?
[*]What OS is your CAD system?
[*]What sort of authentication server is being used?
[*]What changed since this system was known to be working?  This could be something that happened a few days before it stopped.
[/LIST]

---

### Post by daniel50 on 2013-08-25
i don't really know what half of that means. but it works and looks like any other OS i've used for the most part.

---

### Post by 1clue on 2013-08-25
Walk us through the process of using this system.  Start with creating the file that is to be used on the CNC.  At each step, tell us if it's Ubuntu, Windows, Mac, whatever.

Does the CNC box (Ubuntu 10.04) have windows and folders and use a mouse or track pad or track ball, or does it just have text and a keyboard you type commands into?

You mentioned orange/brown folders turning grey.  Where are you sitting/standing when you see this?

---

### Post by daniel50 on 2013-08-26
> **1clue said:**
> Walk us through the process of using this system.  Start with creating the file that is to be used on the CNC.  At each step, tell us if it's Ubuntu, Windows, Mac, whatever.

Does the CNC box (Ubuntu 10.04) have windows and folders and use a mouse or track pad or track ball, or does it just have text and a keyboard you type commands into?

You mentioned orange/brown folders turning grey.  Where are you sitting/standing when you see this?
It's just a text file, .ngc file extension, but can be read and edited in gedit. It's just made on my windows 7 laptop and saved into a shared folder on my mill's PC. I've been doing this the same exact way since 2008 and never had a problem. 
It's a full operating system. Yes, you can use a mouse, has windows and folders, streams movies and music, web browses, etc.

The folders are clearly grey, my lathe is running the same system, completely different color. It's not a monitor issue or anything. 



I reinstalled ubuntu/linuxcnc last night, and that's working fine. Still don't know what went wrong, but at least i can use the machine now

---

### Post by 1clue on 2013-08-26
So the CNC machine is full GUI, and it has a shared folder on it.  You create the file in Windows, drag it over to the shared folder on the CNC and then load it with your CNC software.

I'm sorry I'm not using anything recently with SAMBA on it, but I think this is a permissions issue for file sharing.

The permissions issue is when you copy from Windows to the CNC folder right?  Or is it when you try to load it with the CNC software?

BTW since the CNC is a graphical workstation it should have .ICEauthority and .Xauthority.

But I can't really help effectively with the file sharing.  I use ssh/scp for file transfers.

---

