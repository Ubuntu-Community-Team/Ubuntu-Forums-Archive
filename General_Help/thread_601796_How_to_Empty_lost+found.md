---
title: "How to Empty lost+found"
date: 2007-11-03
forum: General Help
---

### Post by ReverendJ1 on 2007-11-03
How do I empty the lost+found folder in the terminal? I tried, but it keeps saying 'Operation Not Supported' when I do. I can't open it from nautilus, because it crashes my computer. There is a **lot** of stuff in there that I don't need from a botched hard drive transfer. I believe I tried ```
sudo rm -R -f /lost+found/
```

---

### Post by Pumalite on 2007-11-03
What is it formatted to?

---

### Post by ReverendJ1 on 2007-11-03
It is EXT3.

---

### Post by Pumalite on 2007-11-03
Change permissions to the folder(right click or terminal) and delete.

---

### Post by ReverendJ1 on 2007-11-04
I tried that already. For some reason it doesn't seem to be working. Here is the command I used:```
sudo chmod -R 0777 lost+found
``` When I do that it says: ```
chmod: changing permissions of `lost+found/#46346348': Operation not permitted
``` Any other ideas? It is taking up a lot of space and I know I don't need any of it. Not like I could get to any of it anyway.

---

### Post by Pumalite on 2007-11-04
Where is 'lost+found' located?

---

### Post by ReverendJ1 on 2007-11-04
/media/Shared/lost+found It is on my second hard drive. I haven't used the hard drive on another computer, so I don't know why it's giving me these permission problems.

---

### Post by Pumalite on 2007-11-04
sudo chmod 777 /media/Shared/lost+found

---

### Post by ReverendJ1 on 2007-11-04
Yeah, I've tried that. Still doesn't work. I tried deleting it from nautilus using sudo, but then it says "fileX cannot be deleted because you do not have permissions to modify its parent folder." Does it having something to do with not actually being root, but using sudo? I don't know its kind of confusing.

---

### Post by ReverendJ1 on 2007-11-04
Also, I forgot to say thanks for your help and quick responses. I have been a little slow because I have been trying to work on my car all day, and it takes a long time to touch this folder for whatever reason.

---

### Post by ReverendJ1 on 2007-11-14
Does anyone have any more ideas on this? I booted Damn Small Linux (a live CD distro, Ubuntu live CD won't boot for me) and tried deleting lost+found as root, but I got the 'operation not permitted' error on every file.

---

### Post by ReverendJ1 on 2007-11-26
I am still having trouble with this. Do I need some sort of special program to empty/delete my lost+found?

---

### Post by qqzhenyi on 2007-11-26
Maybe you can boot into LiveCD and try?

---

### Post by ReverendJ1 on 2007-11-26
I thought it would be that easy too. :) As you can see from my earlier posts I tried using Damn Small Linux. Damn Small Linux is a liveCD distro. The Ubuntu liveCD doesn't work for me because I have a GeForce video card. I have also tried Knoppix, another liveCD distro, but that didn't work either.

---

### Post by retrow on 2007-11-26
Instead of booting under the graphical mode, try booting under '*recovery mode*' when you get the grub option at startup. When you log in recovery mode, you are *root user* by default. Try deleting the files or changing their permissions while in recovery mode. Once you are done (and if this works) you can then restart the machine using *shutdown 0 -r* or enter graphical mode by typing in *gdm*.

Try this.

---

### Post by qqzhenyi on 2007-11-26
GeForce video card? You only need console to delete a folder?

Btw I'm using Arch Linux.

---

### Post by ReverendJ1 on 2007-11-26
@retrow - Thank you. I will try it later tonight once I get home. Just to double-check, my commands are right, right?
```
chmod -R 0777 /media/Shared/lost+found
rm -R -f /media/Shared/lost+found
```
This is my second hard drive, hence the /media/Shared.

---

### Post by retrow on 2007-11-26
> **ReverendJ1 said:**
> 
```
chmod -R 0777 /media/Shared/lost+found
rm -R -f /media/Shared/lost+found
```
This is my second hard drive, hence the /media/Shared.
Shouldn't it be something like /media/sdb2/Shared/lost+found, or media/sda2/xxxxx/xxxx depending upon what that drive is named?Its quite unlikely that the drive/partition name is "Shared". I'm not an expert so I won't say its necessarily the problem, but the root of your errors might be due to an incorrect file pathname.

If you are using Nautilus, navigate to that directory and recheck the location.

Next. If you are in recovery mode, you don't have to worry about changing the permissions cause you are a '*root user*' and have the permission to change or delete anything. Or you can just go with *sudo rm -R -f /media/sdxx/Shared/lost+found* and skip the step where you change the permissions.

---

### Post by ReverendJ1 on 2007-11-26
@retrow - No, I wish that was the problem. I always actually cd to the directory to make sure. My drive is in fact mounted to /media/Shared.
As for the changing permissions, that is because I got those weird errors trying to delete it with sudo (see above posts).

---

### Post by smartboyathome on 2007-11-26
Lost and found is part of EXT3, so I don't think it can be deleted.

---

### Post by ReverendJ1 on 2007-11-26
@smartboyathome - I'm not trying to necessarily delete the folder, but I need to empty it.

---

### Post by retrow on 2007-11-26
> **smartboyathome said:**
> Lost and found is part of EXT3, so I don't think it can be deleted.I haven't been in a similar situation myself, but do you think it is impossible to delete files from an ext3 filesystem even if you are a root user in recovery mode?

If thats the case, you can tranfer rest of your files to some other drive (if you have space) and format the partition entirely to ReiserFS using gparted. That way you won't have to worry about the pesky files which are remnants of older installations. The transfer you files back to that newly formatted partition.

---

### Post by smartboyathome on 2007-11-26
Try this:

gksudo nautilus

or

gksudo thunar

(depending on if you use GNOME or XFCE)

And then go into the folder and delete the stuff.

---

### Post by smartboyathome on 2007-11-26
> **retrow said:**
> I haven't been in a similar situation myself, but do you think it is impossible to delete files from an ext3 filesystem even if you are a root user in recovery mode?

If thats the case, you can tranfer rest of your files to some other drive (if you have space) and format the partition entirely to ReiserFS using gparted. That way you won't have to worry about the pesky files which are remnants of older installations.

It isn't impossible to delete files from ext3, it is just you can't delete the lost+found folder.

---

### Post by fourthdimension on 2007-11-30
You can try booting up with a SLAX distro and changing the permissions, then booting back into Ubuntu and emptying it.

---

### Post by ReverendJ1 on 2007-11-30
No offense, but people, please read a thread before posting. 
@Smartboyathome - As you can tell from my previous postings, opening nautilus as root was one of my first tries at this. There are too many files (or something) and it crashes my system. 
@fourthdimension - SLAX is just another live cd distro isn't it? Are there any special tools on it that would be helpful? I have used DSL and Knoppix because I thought maybe I had to actually be root, not using sudo, to empty it for some reason.

I haven't been able to try using recovery mode yet, as I have been having problems with my car (I really need to get a new one) which ranks higher on the priority list at the moment. I don't have any heat right now and it is the beginning of Winter in Michigan. Hopefully I will be able to look at it more this weekend and have some positive results.

---

### Post by ReverendJ1 on 2007-11-30
Also, you can delete the lost+found folder if you want to. It will just get recreated when it is needed. I just double-checked and tried it out on an Ubuntu machine here at work.

---

### Post by ReverendJ1 on 2007-12-12
Oops. I guess I forgot to mention I did try booting into recovery mode about a week ago and it still did the same thing. Is it just me who has ever had this problem?

---

### Post by isecore on 2007-12-12
There is no problem. The problem is that you're trying to delete a folder which can't be deleted. Lost+found is there on any partition with an EXTwhatever-filesystem. If there are things inside it then they're there because the filesystem was checked and it found files which weren't belonging anywhere. Either delete the files INSIDE the Lost+found folder or go through it or whatever - but you can't delete the folder, and even if you somehow manage to delete it, it will get recreated sooner or later.

Just delete the files inside of it if they're causing some vague and unspecified error, and live with the Lost+found folder.

Oh, and you'll need root-privileges to do that.

---

### Post by ReverendJ1 on 2007-12-12
@isecore - I don't mean to sound like a jerk, but please read a thread before posting in it. 

And yes, you can normally delete the lost+found folder (as root), but like you said, it gets recreated the next time it is used. I know this is true, because I have done it before.

I know what these files are, I know that they are not needed and I know that they are not there because my drive is going to fail as some may think.

---

### Post by Pumalite on 2007-12-12
I have found out that lost+found usually concerns only very little information about the drive and appears as a folder every time you format a drive, especially an external one. If you check the weight of the file; it's minimal.( it's supposed to contain 'errors', but i have found it after no errors have been made)

---

### Post by ReverendJ1 on 2007-12-12
In my case it is ~150 **GB**. It was made from a botched file system change/transfer.

---

### Post by Pumalite on 2007-12-12
What else do you have there? Maybe you should just reformat the drive after saving any valuable data.

---

### Post by ReverendJ1 on 2007-12-12
~500 GB worth of stuff (its a 750 GB drive). That's what I am beginning to think (that I should just backup the rest of my data and reformat) as I cannot find any answers anywhere else online that have helped. It is a secondary drive (internal). I have most of my stuff backed up to DVD, but it will take me roughly half a million years to put it all back on from DVDs. :-) That is why I haven't given up on just being able to delete it.

---

### Post by isecore on 2007-12-12
I did read the thread, and I guess something is wrong with my head since several people gave you the same advice as I did, but yet you still insist that's not what you need. Admittedly I am a bit tired, but I find it rather strange that you ask a simple question, get several very straight-forward answers yet insist that's not what you asked for. 

I'll probably sound like a jerk now, but maybe you need to rephrase what it is you need. You wanted to delete Lost+found, was told that it's a virtual impossibility, then was told that you could delete whatever files was inside of it. I didn't imply that your drive was failing or anything, I gave you a straight-forward answer. If you're having issues with your drive then I think the problem is elsewhere then Lost+found.

---

### Post by Pumalite on 2007-12-12
[http://ubuntuforums.org/showthread.php?t=583624](http://ubuntuforums.org/showthread.php?t=583624)

---

### Post by ReverendJ1 on 2007-12-12
@isecore - The name of the thread is "How to EMPTY lost+found". As you can see from my first post > How do I empty the lost+found folder in the terminal? I tried, but it keeps saying 'Operation Not Supported' when I do. I can't open it from nautilus, because it crashes my computer. There is a lot of stuff in there that I don't need from a botched hard drive transfer. I need to empty the folder. When you empty a cup you do not throw it away. I made a typo when **asking if I was using the right command** to empty it, which is when everyone thought I was trying to delete the lost+found folder, which means they didn't read the rest of the post. I had also already stated that it is a FACT that you CAN delete the lost+found folder (I tried it on another machine when people said I couldn't) even though that wasn't even what I was asking in the first place, just to get it out of the way. Whether I delete the folder or empty it is "six of one, half a dozen of the other". It gets recreated, but by deleting it, it should empty it. Every time someone has given me a suggestion I have tried it and reported the results. As far as I can see, my lost+found still has 150GB of stuff in it, therefore I keep asking if anyone has any other ideas, as I wouldn't think it would be this hard to delete some corrupt files.

---

