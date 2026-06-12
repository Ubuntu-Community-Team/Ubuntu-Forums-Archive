---
title: "Sharing Thunderbird Folders"
date: 2007-10-17
forum: General Help
---

### Post by measekite on 2007-10-17
Before Linux, I was running Thunderbird on Win2k.  Now I am moving to Linux Ubuntu Feisty but I do switch back and forth between platforms and will do so for some time.

**Question:**

I would like Thunderbird Windows and Thunderbird Linux share the same folders, contact lists, and setting that are stored on my ntfs drive.  I have already taken those steps that allow me to read and write data to ntfs drives from Linux.

[COLOR=Red]Does anyone know if this is possible and how to do this?[/COLOR]  If so please post a short howto.

---

### Post by LanDan on 2007-10-17
never tried it with NTFS, but then it wasn supported yet....should work now i think

just open thunderbird and go to your account setings and set the path to your local directory

---

### Post by kellemes on 2007-10-17
From Linux start thunderbird from the commandline with "thunderbird -profilemanager" .. create a new profile and point to the profilefolder used by Thunderbird on Windows.. probably something like "C:\Documents and Settings\username\Application Data\Thunderbird\Profiles\whn7sdsdf3".
On next startup you'll be sharing your data for both systems.

---

### Post by fjgaude on 2007-10-17
> **kellemes said:**
> From Linux start thunderbird from the commandline with "thunderbird -profilemanager" .. create a new profile and point to the profilefolder used by Thunderbird on Windows.. probably something like "C:\Documents and Settings\username\Application Data\Thunderbird\Profiles\whn7sdsdf3".
On next startup you'll be sharing your data for both systems.

Yep, I've doing this for several now with Thunderbird, both with WinXP and Ubuntu, and when the folder gets over about 500,000 megabytes, I rename it to ".old" and then delete while in Thunderbird all the things I don't any longer find current. And then if I think of something that came up a year or so ago I go to the old folder using the profile manager. Works fine. I have the same folders on all three of my computers with about seven partitions total. Use Unison to keep them insync.

---

### Post by measekite on 2007-10-18
> **kellemes said:**
> From Linux start thunderbird from the commandline with "thunderbird -profilemanager" .. create a new profile and point to the profilefolder used by Thunderbird on Windows.. probably something like "C:\Documents and Settings\username\Application Data\Thunderbird\Profiles\whn7sdsdf3".
On next startup you'll be sharing your data for both systems.

While I would appreciate a more step by step approach I do need some additional Thunderbird help.

I downloaded a tar file for thunderbird 2.  I extracted the contents of the tar file.  Now I do not know what to do.  If I need to compile the contents I need a step by step approach for all of the following.

1. Compiling the contents of the tar file if that is what needs to be done.
2. Installing the software
3. Installing the choices in the menu system
4. Then the stuff that was referred to above.

Please I need a step by step approach.  While I have used visual studio compilers for vb.net I know nothing about C, C++ or Java.  I also do not know Python or any of the Linux programs.

Your help or anybody's help would be sincerely appreaciated.

---

### Post by LanDan on 2007-10-18
OK, think you make it way to difficult for yourself ;)

you CAN go to a web site and download the source packages to install these....but nobody does this  since there is a much easier way

first thing you do is open up a program called synaptic and use the search function to find thunderbird, just select it to install and click the apply button and off you go, 

the above takes care of step 1 2 and 3

step 4 is the easy part ;)

---

### Post by measekite on 2007-10-18
> **LanDan said:**
> OK, think you make it way to difficult for yourself ;)

you CAN go to a web site and download the source packages to install these....but nobody does this  since there is a much easier way

first thing you do is open up a program called synaptic and use the search function to find thunderbird, just select it to install and click the apply button and off you go, 

the above takes care of step 1 2 and 3

step 4 is the easy part ;)

That is what i initially thought of doing.  However, only Thunderbird 1.5 is available.  I want to use Thunderbird 2.0 as I do in Win2k.  That version is not available.

So I think I need the help so I can do it the long way.

---

### Post by kellemes on 2007-10-18
> **measekite said:**
> That is what i initially thought of doing.  However, only Thunderbird 1.5 is available.  I want to use Thunderbird 2.0 as I do in Win2k.  That version is not available.

So I think I need the help so I can do it the long way.

I can't help you with installing Thunderbird 2 on Ubuntu since I'm using another distro atm, surely there are some howto's.. or even repositories available so you can install point-click?

Just a couple of links that *may* help.. the first is probably the most useful.
[https://help.ubuntu.com/community/ThunderbirdNewVersion]("https://help.ubuntu.com/community/ThunderbirdNewVersion")
[http://ubuntuforums.org/showthread.php?t=413908]("http://ubuntuforums.org/showthread.php?t=413908")
[http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/]("http://ubuntu-tutorials.com/2007/05/18/manually-install-thunderbird-2-ubuntu-704/")

---

