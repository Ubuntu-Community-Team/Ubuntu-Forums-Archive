---
title: "Sharing Thunderbird WITH LIGHTNING between Ubuntu and Vista"
date: 2008-05-20
forum: General Help
---

### Post by flavourmetz on 2008-05-20
Hello folks,

I have a dual boot system running on my laptop (Dell XPS 1530, just for the record) consisting of one major NTFS partition with Vista and general data and Ubuntu 8.04 for my work. I use ntfs-3g to read and write on the NTFS partition under Linux.

For my emails I run Thunderbird on both systems, sharing my email/profile folder between them (I created a symbolic link in the linux thunderbird folder to the windows one), and so far everything has been working flawlessly.

But now there is a problem. Yesterday I decided to switch to Thunderbird's calendar addon **Litghtning**. Here is where the trouble starts. I can install the plugin in both systems, but it comes in two different versions for Linux and Windows. If I install the Linux version in Linux, everything works, but when I boot Vista again Thunderbird has the plugin installed, but it is not working properly. The same happens the other way round.


Is there any workaround? If not I would probably have to try something like sharing my emails but not my settings... Does anybody have any ideas or comments on that?


I really want this to work since in this way I have only ONE application for emailing and calendar stuff complete with google calendar synchronisation on my 2 systems, there is really no better way to think of.


Btw: If anyone is looking for a shiny new Notebook but is afraid of problems running Ubuntu on it, I can only recommend this one. Everything works.

---

### Post by Ng Oon-Ee on 2008-07-01
What I did (between windows and Ubuntu) was to zip up my own XPI containing the files from both the linux and windows versions of lightning. As I recall you had to create a folder which contains dlls for windows and lib files for linux.

Google for it, I'm trying to solve something else right now. I'll check back on this tomorrow, if you still haven't found a way I'll see if I can help with that, I did this like a month ago.

EDIT: Ah, found what you need to do

[http://forums.mozillazine.org/viewtopic.php?p=3176895]("http://forums.mozillazine.org/viewtopic.php?p=3176895")

---

### Post by jvcastle on 2008-07-01
I double boot Ubuntu and Vista on the same machine.  I also use Thunderbird on two work Ubuntu machines and a home XP.  Thunderbird requires a "Mail" folder and a "Local Folders" folder - so I change the configuration on all machines to point to those in my "Documents" folder.  On the laptop this is on the Vista partition for both OS's, and I generally consider what is on my laptop as a "master" copy since I carry that everywhere.  For the other machines, I simply copy those two folders from my laptop.  I don't have any problem with Lightning on the different OS's - not clear of what the problem you are have.  Rather than having to move my calendar, I use the Google calendar plug-in and let all the machines link to that.

---

### Post by Lifelock on 2008-10-01
Hello all, I am new to the forum but it has been a great help up to now. Maybe I can help you out somewhat.

My machine is running dualboot Ubuntu 8.04 and Vista. I needed to share my thunderbird profile including lightning between ubuntu and vista because of my phone. It runs windows mobile and using birdiesync I can synchronise contacts, mail, tasks and calendars of thunderbird and lightning, but only under windows.

Now, the sharing of a thunderbird profile with mails and contacts is well-documented. Sharing the calendar data of lightning works about the same. First, install lightning on both platforms by creating an installer package as described above (I created one for lightning 0.9).

Assuming you have your thunderbird profile on your ntfs drive, you also want to use the lightning data in this profile. In your profile directory under linux (typically /home/<user>/.mozilla-thunderbird/<some_random_number>/), backup storage.sdb (this is the lightning data). Then create a link to storage.sdb on the ntfs-partition (mine was in /mnt/windows/Users/<username>/AppData/Roaming/Thunderbird/Profiles/<some_random_number>) and place this in your linux profile with name storage.sdb. Any changes you make using lightning in linux should now directly be applied to the storage.sdb in the windows profile.

By sharing the lightning profile like this, every time I update my calendar on one OS, it is also updated on the other. I only need to boot into windows and run the synchronisation to get lightning in sync with my phone.

---

### Post by salariua on 2008-10-27
What happens with the display of thunderbird calendar under Ubuntu and what happens under Win? Do you still have the problems with funny display of the calendar under Ubuntu?? As far as I remember I didn't show properlly under Ubuntu if shared with Win.

BTW: I use phone syncronization too but I use "[MyPhoneExplorer]("www.fjsoft.at/")" and that's under windows.

---

### Post by Lifelock on 2009-02-06
Sorry for the late reply, I do not wander about here all that often... I have not noticed any problems with the calendars using this setup. I use lightning at work all day under ubuntu and everything seems to work fine.
Thunderbird all-in-all sometimes feels a bit sluggish, but I am not sure this is normal or caused by sharing the profile.

Under windows, I have not noticed any problems with lightning either, but I only start it for synchronization purposes. I use Birdiesync to synchronize thunderbird+lightning with my windows mobile phone, and with the setup I described, this works great.

The only time I experienced problems with sharing lightning data between windows and ubuntu is when I combined earlier version (<0.9) of lightning. When I made the combined lightning for version 0.9, all the problems had disappeared for me.

---

