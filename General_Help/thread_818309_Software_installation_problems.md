---
title: "Software installation problems"
date: 2008-06-04
forum: General Help
---

### Post by Mastrius0713 on 2008-06-04
Here is the deal, This morning I installed the latest system updates, later this morning I was attempting to install an app through the Add/Remove dialog, I clicked on the app I wanted to install and told it to add. But now instead of asking me for my password, it just sits there. a small box at the bottom said "Starting Administrative Application" but vanished a moment later. When I tried to test the update manager, I clicked on check for updates and it was doing the same thing. So why is this happening?

---

### Post by jimv on 2008-06-04
What happens if you open a terminal and type

sudo apt-get update

---

### Post by Mastrius0713 on 2008-06-04
says:
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release                                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [88.6kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [6653B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [20.6kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [906B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [37.5kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [6560B]      
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [8037B]   
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [1234B]   
Fetched 229kB in 52s (4390B/s)

Just now after using that command the thing let me use a force quit. but when I restarted the update manager it went back to doing the same thing.

:confused:

---

### Post by rraj.be on 2008-06-04
What do you mean by force quit.

It Forced you to quit terminal or package manger.

---

### Post by Mastrius0713 on 2008-06-04
the force quit was for the update manager window. I had pressed the X buttin to close but it didn't do anything untill the process in the terminal window finished.

---

### Post by jimv on 2008-06-04
What's in your hosts file?

You can get that with:

```
cat /etc/hosts
```

---

### Post by Mastrius0713 on 2008-06-04
I typed in that code, but it says no such file or directory.

---

### Post by rraj.be on 2008-06-04
You shouldnt close the update manager.

It will automatically install all downloads and then it will be asking you to carry on further or not.

I think that you have interrupted in the middle of install.


Still i cant get where you are sticked and when you have closed your manager.

---

### Post by jimv on 2008-06-04
Hmmm, that's odd.  What happens if you try pinging your own machine?

```
ping localhost
```

Also, if you go to System > Administration > Network and click on the Hosts tab, is there anything in there?

---

### Post by Mastrius0713 on 2008-06-04
The only reason I was trying to close the update manager was because it froze after I told it to check for updates. (as I said before) I couldn't make it close normally even after I clicked the X button and even the System monitor didn't allow me to close it. The Add/remove software was doing the same thing. The force close box didn't show up until the sudo apt-get update command finished.


BTW what is the Administrative Application and why does it vanish?

The Synaptics Package Manager doesn't run either. the 'Starting Administrative Application' bar shows for a few seconds, goes away, and the package manager doesn't run.

---

### Post by jimv on 2008-06-04
Mastrius, I think this is because your hosts file is missing.

Do this in a terminal:

Create the hosts file:

```
sudo nano /etc/hosts
```

In the hosts file, type these entries:
```

127.0.0.1 localhost
127.0.1.1 whatever-your-computers-name-is
```

Press control+x to exit nano, and then hit y to save the file.


The Administrative Application just means that it's an app that needs you to type in your password to run.

---

### Post by ChameleonDave on 2008-06-04
Enter this:

```
sudo apt-get upgrade
```

Tell us what the output is.  Does it upgrade your software, or does it complain?

---

### Post by Mastrius0713 on 2008-06-04
I tried to make the hosts file, but it says it can't write it.

Second I already used the 'sudo apt-get upgrade' command that worked already.

BTW what is the Administrative Application and why does it vanish?

The Synaptics Package Manager doesn't run either. the 'Starting Administrative Application' bar shows for a few seconds, goes away, and the package manager doesn't run.

---

### Post by ChameleonDave on 2008-06-04
> **Mastrius0713 said:**
> I tried to make the hosts file, but it says it can't write it.

Second I already used the 'sudo apt-get upgrade' command that worked already.
Are you 100% sure that you have tried "sudo apt-get upgrade" and not just "sudo apt-get update"?

What happens when you type "sudo synaptic" into the terminal?

If you need to completely reinstall Synaptic, you can do it like this:

```
sudo apt-get remove --purge synaptic
sudo apt-get install synaptic
```

---

### Post by Mastrius0713 on 2008-06-04
Okay the Synaptic Manager is running now. I ran it from the terminal. I also tested it on one of the other ubuntu machines, the 'Administration Application' is the applet that asks for the password. But why isin't it running like it should? I believe thats what is causing the problem, because it always quit before asking me for a password and the apps waiting for me to confirm my password end up sitting around and waiting, and cannot be closed except by a shutdown. So, what do I do about the 'administration app'?

---

### Post by Mastrius0713 on 2008-06-04
Guess I'll have to reinstall the OS.

---

### Post by ChameleonDave on 2008-06-04
> **Mastrius0713 said:**
> Guess I'll have to reinstall the OS.

There is absolutely no need to do that.

You can start any application with admin privileges just by putting "sudo" before the name of the command.

I'm sure that with a tiny bit of patience, your problem can be fixed.

---

### Post by Mastrius0713 on 2008-06-04
Maybe. But not all programs are like that. The 'add/Remove programs' window doesn't require a password untill you have finished selecting the programs you want to use. but thats where the problem comes in. If you can't type in your pass to allow the files to install let alone allow the app to continue with normal functions what good is it?

---

### Post by ChameleonDave on 2008-06-04
> **Mastrius0713 said:**
> Maybe. But not all programs are like that. The 'add/Remove programs' window doesn't require a password untill you have finished selecting the programs you want to use. but thats where the problem comes in. If you can't type in your pass to allow the files to install let alone allow the app to continue with normal functions what good is it?

To run that program, type this:

```
sudo adept_installer
```

---

### Post by Mastrius0713 on 2008-06-05
Okay. I tried the command sudo adept_installer and it says command not found.

---

### Post by Mastrius0713 on 2008-06-05
I just wish someone could tell me how to fix the Administration Application so that I don't have to go through the mess of trying to run non-existent commands. :P

> joseph@joseph-laptop:~$ sudo adept_installer
sudo: unable to resolve host joseph-laptop
[sudo] password for joseph: 
sudo: adept_installer: command not found
joseph@joseph-laptop:~$

---

### Post by ChameleonDave on 2008-06-05
> **Mastrius0713 said:**
> I just wish someone could tell me how to fix the Administration Application so that I don't have to go through the mess of trying to run non-existent commands. :P
I don't know anything about that, because it's a GNOME thing.

I do know that if that command doesn't work, it's probably because the shell path is screwed up for root.  Try this instead:

```
sudo /usr/bin/adept_installer
```

If it's not installed, do:

```
sudo /usr/bin/apt-get install adept_installer
```

---

### Post by ironspeeder on 2008-06-05
I've got the same problem.  Tried everything just like Mastrius and I still can't get the package manager to come up.  I think it's due to a bad release of something a couple of days ago.

Well the last item above ...
gave me ths ...
Couldn't find package adept_installer

but I see this ... 
sudo: unable to resolve host Virtual01
Any clue where to go from here?

---

### Post by zaviera on 2008-06-05
just use the command line..
do # apt-get update
and maybe
do # apt-get upgrade

choose the repository that closed with your location for quickly upgrade.

note: i'm sorry if my english bad :)

---

### Post by ChameleonDave on 2008-06-06
> **ironspeeder said:**
> I've got the same problem.  Tried everything just like Mastrius and I still can't get the package manager to come up.  I think it's due to a bad release of something a couple of days ago.

Well the last item above ...
gave me ths ...
Couldn't find package adept_installer

but I see this ... 
sudo: unable to resolve host Virtual01
Any clue where to go from here?
Host problem with sudo?

There are threads about that on these fora.  Try this one: [http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo+hosts](http://ubuntuforums.org/showthread.php?t=723361&highlight=sudo+hosts), or do a search.

---

### Post by cariboo on 2008-06-06
Paste the following in a terminal:

```
cat /etc/hosts
```

you should see something like this:

```
<------------------cut---------------->
127.0.0.1	localhost
127.0.1.1	intrepid
<-----------------cut---------------->

```

In your case intrepid should be replaced with with what you named your computer when you installed Ubuntu.

If it isn't, open your favorite text editor as root and add it to /etc/hosts.

Jim

---

### Post by Mastrius0713 on 2008-06-07
How does one even log in as root? It tells me it can't do it from the login screen.

---

### Post by Mastrius0713 on 2008-06-07
Great! now the console isn't recognizing any of the commands. There are obviously some very dire issues with this operation system, and untill their fixed, trying to use it will be futile.

---

### Post by ChameleonDave on 2008-06-07
> **Mastrius0713 said:**
> Great! now the console isn't recognizing any of the commands. There are obviously some very dire issues with this operation system, and untill their fixed, trying to use it will be futile.

No commands?  Not even "cat /etc/hosts"?  Not even "ls /etc"?  In that case, it's probably irreparable.  Reinstall from the Live CD.


> **Mastrius0713 said:**
> How does one even log in as root? It tells me it can't do it from the login screen.

Logging in as root from the log-in screen is disabled in Ubuntu for security reasons.  But that's not what you're being asked to do.  To run a command as root, just put "sudo" in front of it.

To edit your hosts file, enter the following:

```
sudo nano /etc/hosts
```

You may replace "nano" with your favourite text editor (vim, emacs, cream, gedit, kwrite, mousepad, etc).

If it fails (because of the problems with "sudo" that you are trying to fix), then boot from a live cd, find the partition in question, navigate to "etc" and edit "hosts".

---

### Post by brigadoon on 2008-06-07
As a precaution check the hard drive for errors. Also, do you know what type of file system you installed on? I've had hardware and disk format issues that have caused issues with several operating systems. If the hardware has issues it could result in what you are seeing. Linux uses ext2 or ext3. FAT32 is a good working file system. NTFS works well with WIN2000 or XP. My first Ubuntu install was with a NTFS file system and I had nothing but problems. A clean install on a repartitioned and reformatted drive with ext3 fixed some random problems I was having at the time.

If you do decide to repartition and reformat remember to backup important links, passwords, files, etc... before you do. Good luck.

---

### Post by JakeRich on 2008-06-08
@Mastrius0713, just so you don't feel like the Lone Ranger, I have exactly the same problem. Update Manager starts, says there are updates available but when I click on the button to start the updates I get the Admininistrative Application box on the bottom bar and nothing. I, too, cannot close Update manager, nor does it respond to anything except a process kill.  Synaptic Package Manager acts the same way. The Administrative Application program simply doesn't run to present the password box.  To make sure I wasn't moving too fast, I let it run, thinking that perhaps it had something it needed to do before I got the prompt. I let it run 24 hours and I still had the spinner on Update Manager. I'm reinstalling Heron now, but if this doesn't work I'm going back to 7.04.

---

