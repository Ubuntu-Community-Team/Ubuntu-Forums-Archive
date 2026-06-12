---
title: "Clone settings into a fresh Ubuntu install"
date: 2008-02-25
forum: General Help
---

### Post by OvenMitt Bandit on 2008-02-25
I've seen threads explaining that all you need to do to keep your settings is to copy your /home folder and your /etc folder to a USB or external drive and then copy them back after an install. Is this all that you need to do? I noticed that the versions mentioned in those threads were older ones, like Hoary and Breezy. Has anything changed since then?

I will be doing a complete reformatting of my Hard Drive, a complete wipe. I'm going to install Win XP, then install Gutsy and set up a dual boot. After all is reinstalled, all I have to do is copy my /home and /etc folders back? Any other folders I should worry about that may have settings in them that I would like to keep?

Thanks for the help.

---

### Post by Het Irv on 2008-02-25
I don't know if the procedure is the same, but I have run across a great program that you can use to backup and reinstall Ubuntu pretty quickly.  QuickStart 6.0 (see sig)  is build around what you need and the developer is very active in that thread, he will be able to help you with any problems you might have.

---

### Post by OvenMitt Bandit on 2008-02-25
I will be completely wiping my hard drive, so it sounds like that would delete this software as well. I may just not be understanding the procedure though.

---

### Post by Het Irv on 2008-02-25
Store the files for the program where ever you have the backups stored,  then you can run the program from the external drive or wherever it is.

---

### Post by Therion on 2008-02-25
> **OvenMitt Bandit said:**
> I will be completely wiping my hard drive, so it sounds like that would delete this software as well. I may just not be understanding the procedure though.
I think the idea would be to download Quickstart NOW, do a backup via Quickstart, perform the reformat & reinstall, and finally reinstall Quickstart to restore your backup.

---

### Post by peedeeramone on 2008-02-25
i want to do something similar... I want to essentially move my install to a new pc. I have made changes to files not contained in /home so i was just looking for the easiest way to do it.  I do have another partition too, so perhaps i should just do a HD copy...

---

### Post by Het Irv on 2008-02-25
> **Therion said:**
> I think the idea would be to download Quickstart NOW, do a backup via Quickstart, perform the reformat & reinstall, and finally reinstall Quickstart to restore your backup.

Quickstart does not need to be installed on the computer, I believe that it just runs scripts in the terminal.  The link in my sig is to the thread started by the developer.

---

### Post by OvenMitt Bandit on 2008-02-25
Oh ok, so I can just put my entire / folder on another disk, wipe, then use Quickstart to restore my backups onto the fresh install?

Nevermind, it seems that the program will make the backup for you also. Cool.

---

### Post by OvenMitt Bandit on 2008-02-26
Alrighty, I am on a fresh install of Win XP right now. I backed up my / folders using that QuickStart program onto an external drive. I would like to install Xubuntu this time, would I still be able to bring back my files and settings using QuickStart? Or would that not work because Xubuntu doesn't use Gnome?

---

### Post by Het Irv on 2008-02-26
You should probably post this question on the other thread, but I think the only thing that you could restore would be the home folder, and even then I am not sure.

---

### Post by OvenMitt Bandit on 2008-02-26
I am trying to install Ubuntu now, but the partitions aren't working like they did the first time. When I installed before it gave me a slider for me to choose how much disc space to take away from my Windows partition and give to Ubuntu. All it is now is my 400GB (which is my entire hard drive) Windows partition, and 8MB of unallocated space. It won't let me set up an Ubuntu partition without wiping out my freshly installed Windows XP. What should I do?

---

### Post by randiroo76073 on 2008-02-26
Windows is like that, it will eat your whole drive if you let it.  I usually use a live cd and then use gparted to setup my partitions the way I want[I am multibooted with 2 win parts, #2 is like a home part in linux, my docs and all prgms I install, never loose them thatway] and 4 linux distros, each with a root & seperate home partition.  My "C:" drive is only 10gb & win2 is 50gb.  Linux root is 15gb, home is 50gb.
HTH

---

### Post by OvenMitt Bandit on 2008-02-26
Gparted won't let me resize my Windows NTFS partition at all. I ran chkdsk, rebooted a few times, still won't let me. I have no idea what to do.

---

### Post by Het Irv on 2008-02-27
How many partitions do you have?  I remember I ran into an error when I tried to have more than Four.

---

### Post by OvenMitt Bandit on 2008-02-27
Only one. A 400GB NTFS partition, and that's it. Unless 8MB of unallocated space counts.

Edit: I wiped my hard drive again, and at the Windows partition editor, I specified an exact amount to be formatted to NTFS. Something I should have done the first time.:roll: Then it was as simple as just selecting the "Use largest continuous free space" option for my Ubuntu partition. Problem solved!

---

### Post by Het Irv on 2008-02-28
No unallocated doesn't count.... Have you defragged windows?  It is best to defrag at least twice before trying to change a windows partition.

---

### Post by perixx on 2008-02-28
> OvenMitt Bandit: I'm not quite sure what happened, but it didn't restore anything.
Hi, I've read your other posting; did you recover your stuff onto the same branch and versoin from where you backed it up from (Ubuntu)? Because, if you used Xubuntu to recover, your settings will likely not have any effects (Xfce config files are different from Gnome and KDE). 

Haven't used Quickstart yet (and probably won't do so, because it's not open source), but you should have at least your personal files back in your /home folder (provided that it's got the same username).
Can you access the backed up content directly from where Quickstart has stored it? If so, you can always get your personal files back this way.

I'd recommend a backup tool like 'SBackup' or 'HomeUserBackup(?)' for incremental backups...

perixx

---

### Post by OvenMitt Bandit on 2008-02-28
I didn't install Xubuntu, I just reinstalled Ubuntu. I found out why it didn't restore my /home directory, though. There was nothing in the archive it made. I should've checked it before I reformatted, so I lost everything in my /home folder. Oh well. There wasn't anything too terribly important in there, not anything irreplaceable.

I think that QuickStart is open source, it was programmed by the guy who made the thread about it. 
> I've written a script to expedite some things I do on my computer. If interested, you're welcome to download and use it

I could be wrong, but that seems like open source to me, unless the guy sells it somewhere.

---

### Post by perixx on 2008-02-28
Sorry to hear that all data is lost...

Well, give SBackup or HUB a try, perhaps. Of course, I've heard a lot of good stuff about Quickstart and it surely is a very simple to use, yet feature-rich app.

But it's not open source, so it seems; there has been a discussion on the app's thread about this several times... 
If I understood correctly, then this script is invoked from some server via internet - you cannot download the script itself, so you have no access to the source code directly. Even if you could, it's not open source - that's what the programmer says for himself:
[http://ubuntuforums.org/showpost.php?p=4224206&postcount=423]("http://ubuntuforums.org/showpost.php?p=4224206&postcount=423")

Just my personal point of view, but I don't see why such a basic app for an open source project needs to be closed source. I don't want to support such trends, thus, won't use it. There are a lot of other ways to do the same stuff...

perixx

---

### Post by Het Irv on 2008-02-29
> **OvenMitt Bandit said:**
> I didn't install Xubuntu, I just reinstalled Ubuntu. I found out why it didn't restore my /home directory, though. There was nothing in the archive it made. I should've checked it before I reformatted, so I lost everything in my /home folder. Oh well. There wasn't anything too terribly important in there, not anything irreplaceable.

I think that QuickStart is open source, it was programmed by the guy who made the thread about it. 


I could be wrong, but that seems like open source to me, unless the guy sells it somewhere.

It's not open source, he won't release the code, but it is free of charge.

---

