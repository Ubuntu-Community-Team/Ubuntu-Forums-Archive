---
title: "My whole trashcan process is hosed (Edgy)"
date: 2006-12-07
forum: General Help
---

### Post by Jim March on 2006-12-07
Folks, everything connected to the trashcan is just...well, trashed.

I don't have a trashcan at all at the moment.

When I try and add one to the taskbar, I get:

```
The panel encountered a problem while loading "OAFIID:GNOME_Panel_TrashApplet".
```

...and then in smaller letters on the same popup:

```
Do you want to delete the applet from your configuration?
```

Choices are "delete" and "don't delete".

Reading in other threads, I tried the command:

   sudo dpkg-reconfigure gnome-applets

...which netted me:

/usr/sbin/dpkg-reconfigure: gnome-applets is broken or not fully installed

Grrr.

It gets better.  If I run Nautilus as my regular user account and do the "empty trash" command under the file menu, I get a popup saying:

```
ERROR WHILE DELETING: "/lost+found/#4718757" cannot be deleted because you do not have permissions to modify its parent folder.
```

If I say "skip", I get an endless string of these.  Grrr some more.  So I tried "sudo nautilus" and gee, guess what, "Empty trash" is GREYED OUT from the menus!!!

Color me perturbed at this point.

Yes, I DID at one point try and delete files from a removable media SD card.  Yes, I know there's a bug report related to that.

Any ideas how I can recover?

Sidenote: yes, the whole "deleting from removable media" thing should be set to "really delete it and force the user to be careful" rather than this buggy mess we're dealing with now.

---

### Post by CatKiller on 2006-12-07
> **Jim March said:**
> So I tried "sudo nautilus" and gee, guess what, "Empty trash" is GREYED OUT from the menus!!!

You should get into the habit of using **gksudo** for graphical applications that you'd like to use root for. (see [here]("http://www.psychocats.net/ubuntu/graphicalsudo") for details)

The reason you didn't have the Empty Trash option as root is probably because root doesn't have anything in their wastebasket. You could instead use **gksudo nautilus** to delete the things that are in your ~/.Trash directory. And if you've deleted things from other partitions, the .Trash-yourusername directory on that partition too.

I don't know how you could have broken your gnome-applets package.

---

### Post by Adramelech on 2006-12-07
maybe reinstalling ubuntu-dsktop?

---

### Post by Jim March on 2006-12-07
Catkiller: OK, I see what you mean re: gksudo but it didn't help.

I got two different error messages, but it still seemed to run OK.  Except "empty trash" is gray.

The second message is one I've been getting lately when I "sudo nautilus":

```
(nautilus:8572): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
```

The new FIRST error is even weirder:

```
(nautilus:8572): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

So...heck, something is indeed wrong here.

I went back and tried to add other "toys" to my panel.  Some load OK like "fish" but others give similar errors such as:

```
The panel encountered a problem while loading "OAFIID:GNOME_GWeatherApplet".
```

and:

```
The panel encountered a problem while loading "OAFIID:GNOME_CPUFreqApplet".
```

OK...so...I seem to have two problems here: 

1) whatever is affecting sudo/gksudo nautilus (no errors on plain ol' Nautilus)

2) my "gnome bits" have gone all wonky.

And I probably have a #3 "underlying issue with my trash" as all this started while trying to delete the contents of an SD card...

Adramelech: could you give more details on "reinstalling ubuntu-dsktop"?  Because I tried:

```
jim@evobeast:~$ sudo dpkg-reconfigure ubuntu-dsktop
Package `ubuntu-dsktop' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: ubuntu-dsktop is not installed
jim@evobeast:~$
```

Huh?

---

### Post by CatKiller on 2006-12-07
The error message you get with **gksudo** is "normal". It's a low-priority bug that the message doesn't mean anything. It's disconcerting, but you should use gksudo in preference to sudo for graphical applications regardless.

The message when you use **sudo** might be more signicant, but I don't know what it means, so it might not be.

Have you removed the things that are in your wastebasket yet?

Also, there was a typo in Adramelech suggestion - the package is called **ubuntu-desktop**. I don't know that it would help though.

The fact that you ended up with something in lost+found may well be your fundamental problem. As I understand it, that directory is where bits of files end up after they are fished out of the filesystem by **fsck** after a bad shutdown or what-have-you.

---

### Post by Jim March on 2006-12-07
OK, typo corrected but...

```
jim@evobeast:~$ sudo dpkg-reconfigure ubuntu-desktop
Password:
/usr/sbin/dpkg-reconfigure: ubuntu-desktop is not installed
jim@evobeast:~$
```

Can anyone tell me how to install and/or reconfigure it?

---

### Post by CatKiller on 2006-12-07
> **Jim March said:**
> Can anyone tell me how to install and/or reconfigure it?

You could try ```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by Jim March on 2006-12-08
Ah.  OK, first off, thanks!

Second...you were close, but "reinstall" did nothing.  The same changed to "install" however seems to have worked like gangbusters.

```
jim@evobeast:~$ sudo aptitude reinstall ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
ubuntu-desktop is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jim@evobeast:~$ sudo aptitude install ubuntu-desktop **<-- here's where I altered the command...**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  gnome-orca onboard python-at-spi python-beagle python-virtkey 
The following NEW packages will be installed:
  deskbar-applet gnome-applets gnome-orca onboard python-at-spi 
  python-beagle python-virtkey rhythmbox totem ubuntu-desktop 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 1038kB/4035kB of archives. After unpacking 17.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com edgy/main deskbar-applet 2.16.0-0ubuntu4 [199kB]
Get:2 http://us.archive.ubuntu.com edgy/main gnome-applets 2.16.1-0ubuntu3 [398kB]
Get:3 http://us.archive.ubuntu.com edgy/main python-at-spi 0.5.5-0ubuntu1 [61.2kB]
Get:4 http://us.archive.ubuntu.com edgy/main gnome-orca 1.0.0-0ubuntu4 [283kB]  
Get:5 http://us.archive.ubuntu.com edgy/main python-virtkey 0.41ubuntu1 [13.1kB]
Get:6 http://us.archive.ubuntu.com edgy/main onboard 0.85 [25.4kB]              
Get:7 http://us.archive.ubuntu.com edgy/universe python-beagle 0.2.9-1ubuntu3 [47.0kB]
Get:8 http://us.archive.ubuntu.com edgy/main totem 2.16.2-0ubuntu1 [11.1kB]     
Fetched 1038kB in 27s (37.7kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package deskbar-applet.
(Reading database ... 178457 files and directories currently installed.)
Unpacking deskbar-applet (from .../deskbar-applet_2.16.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package gnome-applets.
Unpacking gnome-applets (from .../gnome-applets_2.16.1-0ubuntu3_i386.deb) ...
Selecting previously deselected package python-at-spi.
Unpacking python-at-spi (from .../python-at-spi_0.5.5-0ubuntu1_i386.deb) ...
Selecting previously deselected package gnome-orca.
Unpacking gnome-orca (from .../gnome-orca_1.0.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package python-virtkey.
Unpacking python-virtkey (from .../python-virtkey_0.41ubuntu1_i386.deb) ...
Selecting previously deselected package onboard.
Unpacking onboard (from .../archives/onboard_0.85_all.deb) ...
Selecting previously deselected package python-beagle.
Unpacking python-beagle (from .../python-beagle_0.2.9-1ubuntu3_i386.deb) ...
Selecting previously deselected package rhythmbox.
Unpacking rhythmbox (from .../rhythmbox_0.9.6-0ubuntu4_i386.deb) ...
Selecting previously deselected package totem.
Unpacking totem (from .../totem_2.16.2-0ubuntu1_all.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.30_i386.deb) ...
Setting up deskbar-applet (2.16.0-0ubuntu4) ...

Setting up gnome-applets (2.16.1-0ubuntu3) ...

Setting up python-at-spi (0.5.5-0ubuntu1) ...
Setting up gnome-orca (1.0.0-0ubuntu4) ...

Setting up python-virtkey (0.41ubuntu1) ...

Setting up onboard (0.85) ...

Setting up python-beagle (0.2.9-1ubuntu3) ...

Setting up rhythmbox (0.9.6-0ubuntu4) ...

Setting up totem (2.16.2-0ubuntu1) ...
Setting up ubuntu-desktop (1.30) ...
jim@evobeast:~$ 
```

---

### Post by Jim March on 2006-12-08
Right.  So far ALL I've done is copy'n'pasted that terminal session and wrote these two messages to this thread.  I did NOT have Firefox running while actually doing the commands.  I'm now gonna close out, reboot, try and get my trashcan back.  Wish me luck :).

---

### Post by Jim March on 2006-12-08
Right.  Good news #1, the durn thing booted.

Good news #2, I have a trash can.

Alarming news: here's what's in it.  Yikes.  Attachment "mytrashcan.png"...dunno if it will appear inline or as an attachment yet...

---

### Post by Jim March on 2006-12-08
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=20725&d=1165558198[/IMG]

---

### Post by Jim March on 2006-12-08
Ummm...like, help?

---

### Post by Jim March on 2006-12-08
I think my computer is using the term "PWNED!".

At me.

Sigh.

---

### Post by CatKiller on 2006-12-08
> **Jim March said:**
> ubuntu-desktop is not currently installed, so it will not be reinstalled.

I guess you removed it previously by removing one of its dependencies then - possibly Totem or Rhythmbox? If you're using Gnome, then you had ubuntu-desktop installed at one point. I notice that you also reinstalled deskbar-applet and gnome-applets through this procedure.

> **Jim March said:**
> Yikes.

Quite. That would make it difficult to empty the wastebasket.

You still haven't said if you've looked in the .Trash directories yet.

---

### Post by Jim March on 2006-12-08
> possibly Totem or Rhythmbox?

Errr...I don't seem to recall doing so, but it's possible...

This may also be connected to a series of crashes sometime shortly after I bumped up to Edgy from Dapper.  After a couple of system updates about...hmmm...a week later it started to stabilize and I haven't had *crashes* since.  So that's good.

In case it ain't clear yet, THANK YOU for your help so far.  Mucho appreciated.  It's a pain but I am making progress :).

Finally...where would I find the ".trash" directories?

I just did "gksudo nautilus" and told it to look for hidden files.  Right off root I find a .trash with...ye Gods, 319 items.  The first...call it 50 or so are directories, all empty, with names like "#4718757".

Then a buttload of files, similar names to the directories, file types are...some plain text (looks like fragments of EMail stuff?), lots of "link to object code"...sizes are all over the map.  Some "link to shared library", some "link to executable", some "program", some "unknown".  

Awww man, what the heck is this stuff?  Please tell me it's likely COPIES of crap rather than "shotgun holes" blown out of both data and programs?

I found another .trash under file system, /home/jim/.Trash - empty thank His Noodliness.  Any others I should check?

Thanks!

---

### Post by CatKiller on 2006-12-08
There will be a .Trash folder in each user's home folder (this includes /root/.Trash for things deleted by root). Each partition may also have a .Trash-*username* folder for each user, including root.

The fact that you had crashes in the past is probably the cause of these files - and potentially your problems now, I suppose. When fsck is run after a crash, any buggered files are put into [/lost+found]("http://www.openaddict.com/documents/Linux-Filesystem-Hierarchy/lostfound.html") for inspection. The fact that they are in root's .Trash folder suggests that you've deleted these fragments as root through Nautilus. Which I think should be OK, but I've not had to do so, so I could well be wrong.

Once you've emptied the .Trash folders (moving the lost+found stuff if you think you can use it), if the wastebasket is still showing the contents of your filesystem, then you still have another problem (although I don't know what it might be).

The page I linked to, that explains what /lost+found is, suggests that you use the information about the affected files to reinstall the affected packages. Personally, I'd *always* feel that the filesystem was suspect, so I'd now salvage the data that I could and re-install, to have a filesystem I could be confident in. But that's me.

---

### Post by laosboyme on 2007-01-02
hey guys try this one!!

code:
 > sudo apt-get gnome-applets :KS :KS 

Maybe this will solve you're problems

---

