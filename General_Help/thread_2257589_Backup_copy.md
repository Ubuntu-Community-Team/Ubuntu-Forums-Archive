---
title: "Backup copy"
date: 2014-12-20
forum: General Help
---

### Post by briar rabbit on 2014-12-20
Is there a way of copying one computer to another computer?

Both have the same OS, one has been updated.

So, can one computer be copied completely; all the files, folders, updates, applications, programs, videos, music, web browser settings and bookmarks, EVERYTHING all 100GB of it and then put that on the second computer?

---

### Post by DuckHook on 2014-12-21
You are talking about cloning a drive and the old standby in Linux is Clonezilla. Clonezilla is available in the repos. It can also be downloaded as a standalone Live CD/USB from sourceforge [here]("http://clonezilla.org/downloads.php").

---

### Post by sudodus on 2014-12-21
> **DuckHook said:**
> You are talking about cloning a drive and the old standby in Linux is Clonezilla. Clonezilla is available in the repos. It can also be downloaded as a standalone Live CD/USB from sourceforge [here]("http://clonezilla.org/downloads.php").

+1 for Clonezilla

The target drive must be of the same size or bigger.

---

### Post by trag on 2014-12-21
TimeShift will not only create a restore point on your system but now has a handy  feature that will allow you to clone a fully bootable copy of your current system onto a USB for migration to a different 
```
sudo apt-add-repository -y ppa:teejee2008/ppa
sudo apt-get update
sudo apt-get install timeshift
```

---

### Post by stalkingwolf on 2014-12-21
I like clonezilla so much i have it on a flashdrive as well as a disk.

---

### Post by briar rabbit on 2014-12-22
Thanks to all fro the input

I will try the clonezilla.  From what little I have read people are using either tuxboot or Unetbootin to put clonezilla on a USB or ExtHD.

Thanks trag I will see what I can find about TimeShift for later.

---

### Post by sudodus on 2014-12-22
I suggest that you boot Clonezilla from a separate CD/DVD/USB (pen)drive, and use the external HDD as the target drive for the compressed image.

You can use Unetbootin or several other tools to install Clonezilla to a pendrive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by DuckHook on 2014-12-22
I note that your profile summary has you still on 10.04. If this is accurate, then you are running a dead version. 10.04 reached end-of-life in summer of 2013 and you are now at considerable security risk. The recent heartbleed and shellshock bugs ought to be enough to scare anyone, and I strongly encourage you to upgrade, in which case, cloning your drive may be academic. You would be better off installing 14.04 in any flavour, and just restoring your important data from a backup.

---

### Post by DuckHook on 2014-12-22
My bad. Just re-read your first post and I gather that you *are* trying to upgrade, possibly from 10.04 to something recent. If so, then you may be making this too complicated for yourself.

*Provided the above assumption is accurate*, then all you have to do is:

1. Copy the whole /home directory from your old computer onto a USB drive
2. Boot up new computer with a LiveDVD/USB
3. Copy the /home directory from the USB drive onto your new computer
4. *chown* the new /home directory to your user and group id, which is by default, 1000:1000

No need for Clonezilla or any other software for that matter. Just a simple drag and copy from nautilus, or whichever file manager you are using.

Or am I missing something?

---

### Post by sandyd on 2014-12-22
Moved to General Help

---

### Post by briar rabbit on 2014-12-22
Howdee, I can't get anything over on you guys hunh DuckHook. :-)

I did put 14.04 on a USB.  Then I installed it on the laptop.  The first thing I saw was there was no "System > Administration > Disk Utility"  I did see the "Kardushian One Click Comparison Shopping" aka Amazon link.

I am not being rude.  It took a while to get my computer the way I want it. NOW I am suppose to spend who knows how much time getting the thing into a useful condition with a NEW OS. 

I find it very difficult to understand that through all this time of computers, a reliable OS has not come from the minds of so many talented people.  To me a non-techie it looks like a lot of people are having fun doing the thing they love to do.  Which is great and I realize I am benefiting from their efforts, both fun and hard work.  And, that said, it seems too that some times the bugs of yesterday are replaced with the bugs of today.

The things I did 4 years ago; getting the plug-ins to play movies (all different formats, from DVD's, from the internet, from USB drives), playing music (same), the Applications, writing, graphics, etc etc, picture editing, to having every little thing where I want it on my "desktop" - it will take weeks to reproduce.  I do not remember exactly what I did but I do remember it was a pain.  The only way to keep this fresh in the mind is to keep doing it over and over and over (no thanks).  I see the computer as a tool to be used and seldom worked on.  If others want to spend the majority of their time tweaking the tool - I do not have a problem with that - I do have a problem with playing musical chairs and jumping jack desktops.

I have been considering trying to put 14.04 beside the 10.04 and taking the new fangled world in small doses.

I am not sure how this will come across because it seems so many take it for granted that 'you have to have a new OS every 3 years (if not every 6 months)'.

I just wonder 2 things; can you techies really see the forest from the tree images?  And, how the heck will I feel about what I just wrote, 6 months from now.

---

