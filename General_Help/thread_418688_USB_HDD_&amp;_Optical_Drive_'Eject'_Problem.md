---
title: "USB HDD &amp; Optical Drive 'Eject' Problem"
date: 2007-04-22
forum: General Help
---

### Post by Dissel on 2007-04-22
[SIZE="2"]Last week I Upgrade to Ubuntu 7.04...It was a Fresh install to make sure all stuff work perfectly....

[B]In my case It can  automatically mount external USB drive,but it can't be Unmountable...i,e when ever I click "Eject", A pop-up window stated "It can't be eject' and it again auto run the drive partition.

If I power off the USB drive then there is a warning message appear about serious damage and data loss. [/B]

There is no such issue in Ubuntu 6.10 i,e 'Edgy Eft'

**same thing happen when I want to Eject the Optical drive tray,and It pops up "there is no media in the drive".So every time to use the drive I need to press the button in the drive**

Please experts....help me out....What I did wrong ?


[/SIZE]

---

### Post by henrik_daver on 2007-04-22
I have the same problem, at least with the optical drive (haven't tried any usb connection yet). it works if i use the terminal, but not by clicking the optical drive icon in nautilus. i get the message "could not mount medium" - "there probably is no medium in the unit" (translated from swedish, so it might not be just those words). any suggestions?

---

### Post by evilc on 2007-04-22
This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

---

### Post by Dissel on 2007-04-23
> **evilc said:**
> This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

[SIZE="2"]Why I move the file ? If I rename it,will It work ?[/SIZE]

---

### Post by mdurham on 2007-04-23
> **Dissel said:**
> [SIZE="2"]Why I move the file ? If I rename it,will It work ?[/SIZE]

I think that's what it's doing.

---

### Post by Dissel on 2007-04-23
[SIZE="4"][COLOR="RoyalBlue"]@evilc......Thanks Man for your nice help,It work now for me too...You save my system...Thanks again for your reply[/COLOR].[/SIZE]

[SIZE="2"][COLOR="DarkRed"]Any solution about optical drive "Eject" problem[/COLOR][/SIZE]

---

### Post by evilc on 2007-04-23
No problem glad I could help

---

### Post by xadder on 2007-04-23
This problem is catching lots of people out I think, so presumably Ubuntu will fix it. For now I am just doing df to get the name of the drive and e.g. sudo eject /dev/sdc1.

Odd that the icon doesn't do this properly.

---

### Post by Dissel on 2007-04-23
[SIZE="2"]Thanks @xadder for your Idea to use comand prompt

After a long trial and error I sucessefully use the comand.

I have only one Optical drive so for me comand is like this 

[B]In Terminal ---->

sudo eject /media/cdrom    <For Ejecting drive tray>


sudo mount /media/cdrom  <For Inserting drive tray>[/B][/SIZE]

---

### Post by kunchi on 2007-04-23
I have the same problem, I connect the USB just fine and then at times I am told it can't be ejected and keeps reconnecting it.

Also I notice that the drive will become unreadable after its been connected so long...

HELP!

---

### Post by arron on 2007-04-25
Sweet!  Worked for me, thanks!

---

### Post by gh0st on 2007-04-27
I have this problem as well, I've just tried moving that file via the terminal and it doesn't seem to have worked for me. I did have the drive mounted at the time and maybe it will work when I unplug it and remount it later. We'll see.

I've created a little shell script on the desktop to unmount the drive for now but I hope the Ubuntu team will sort it out soon. It seems a lot of people are having the same problem.

---

### Post by ccfiel on 2007-04-29
evilc your solution solve my problem. ubuntu rocks! :)

---

### Post by jackmc on 2007-05-08
awesome, thanks a lot :)

---

### Post by gbeppe on 2007-05-08
> **evilc said:**
> This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

It works!
Beside the fact that now the system ask for "unmount" instead of "eject"....and ask to empty the Trash before to unmount.

thanks

---

### Post by gh0st on 2007-05-09
Forget my earlier post. The solution did work for me but not until I'd unmounted the drive in the terminal and then reconnected it.

evilc you rock man thanks :)

---

### Post by titus1950 on 2007-05-09
> **evilc said:**
> This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

Thank you evilk!....it simply works perfectly...

---

### Post by Sionide on 2007-05-16
I've been having this trouble too. Not only would my external USB hard drives not eject properly - they'd leave their /media/xxxx folder behind, meaning next time you plug it in, it gets the folder name /media/xxxx_ and /media/xxxx__ and so forth - I've been having to remove these manually as root..

Even after moving the 10-storage-policy.fdi file, I still get a "cannot remove directory" error and an error with no message(!) But it does seem to be removing the directory. This is a little frustrating - it always worked fine on Edgy..

---

### Post by dagrump on 2007-05-20
A quick Thank You to evilc, your advice fixed my laptop's issue w/ usb drives. One more stumbling block out of the way.

---

### Post by evilc on 2007-05-20
> **dagrump said:**
> A quick Thank You to evilc, your advice fixed my laptop's issue w/ usb drives. One more stumbling block out of the way.

No problem, we are all here to help each other.:grin:

---

### Post by dxdemetriou on 2007-05-22
There are times that needed the eject and others the umount
Can I add both of them when I right click on icon, or to make some script?
It's difficult for someone to remember what sd?? must eject, that eject is useful for external disks to power them down.
The other about umount is when somebody wants to umoun a specific partition and not the whole disk.
Now about the bug, we have modify/move the fdi policy file, but what will come out with new updates/upgrades?
Thanks

---

### Post by a_vold on 2007-06-02
I used the command

 sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

Is it possible to rename the "storage-policy" file back to *.fdi? After the command it is now known as *.fdi.bak, and the unmount choice is gone.

Does anyone know a way to unmount\eject the USB HDD so that it automatically will automatically shutdown securely like in windows xp?

---

### Post by evilc on 2007-06-03
> **a_vold said:**
> I used the command

 sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

Is it possible to rename the "storage-policy" file back to *.fdi? After the command it is now known as *.fdi.bak, and the unmount choice is gone.

Does anyone know a way to unmount\eject the USB HDD so that it automatically will automatically shutdown securely like in windows xp?

On the desktop icon for the USB if you right click it you should have the option to unmount it.

---

### Post by newtanker on 2007-06-04
> **evilc said:**
> This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

Having this issue with my sansa mp3 player (at first, tested with a usb key and its doing it there too) so tried moving the policy file, problem is, i have no osvendor/storage-policy.fdi file at all.....any suggestions?

---

### Post by newtanker on 2007-06-04
i have edited the /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi file several times trying to get this to work, even to the point as to downloading the newest version (complete with line numbers, which may be my problem....)  Anyone have a copy of this file that works?

---

### Post by newtanker on 2007-06-06
Tracked this down a little, if rebooting in text mode it gives an error of cannot remove directory /media/Sansa040e250 : does not exist.  Seems the os is picking a malformed configuration file reading the space between Sansa and e250 to be a 040.  Problem is, I cant locate that...any ideas?

---

### Post by SonicSteve on 2007-06-27
> **evilc said:**
> This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

I find this very curious, I ran this command and confirmed that it did what it was supposed to. However it didn't work for me. This can't be the source of the bug, I wonder if something needs to change with Gnome, or are there KDE users and Xfce users with this same issue.

I'm tempted to install the KDE packages to see if that might help. The trouble is that I prefer the feel of Gnome. 

Although this may be redundant to say, I never had this trouble with 6.10, just with 7.04

---

### Post by SonicSteve on 2007-07-06
Update!
I'm not sure why this is but...
Sometimes when I right click on the volume icon it says "eject" 
Other times and less often it says "unmount volume" 

If it says eject I might as well not try, it doesn't work ever.
When it says "unmount volume" it works perfectly

Why is it alternating between the two?

I don't know if it has to do with GLdesktop aka desktop effects. It was only a few days ago that  I turned it off to test things without it.

Edit;
After using the unmount volume option it seems to ;
cause Nautilus to slow down to a crawl.
It doesn't matter what I try to load from the places menu it is slower than a snail.

If I plug the usb drive back in without restarting X the eject option is back instead of the unmount option.

Pretty weird stuff!!!
I'm going to test this with restarting X before and after and every other variable I can think of.

---

### Post by SonicSteve on 2007-07-06
OK so here it is.
 I don't know how or why the "unmount volume" comes and goes. Nothing I do seems to make it come and go as an option in the right click context menu. 
When the option is there it seems to properly unmount the usb drive, however it does very badly slow down nautilus. It becomes unusable. 
Restarting X  (ctrl alt bckspce) doesn't speed up nautilus, a full restart seems to be the only way to bring it back. Some times after restarting X in this scenario I get this error message;

[ATTACH]37462[/ATTACH]

I am very tempted to load the KDE desktop and see if Konqueror has these same issues. I'll let you know if  I do.

---

### Post by stoffe on 2007-07-07
I have the same issue. Looks like it might be this bug: [https://bugs.launchpad.net/ubuntu/+source/eject/+bug/108643](https://bugs.launchpad.net/ubuntu/+source/eject/+bug/108643)

---

### Post by kolinab on 2007-09-29
Whoops, sorry for the double post.

---

### Post by kolinab on 2007-09-29
> **evilc said:**
> This worked for me. 
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak

Nice little fix, thanks!

---

### Post by mve-lamb on 2007-10-31
Hi, I have tried the solution here but do'not help me because I'm with UBU 7.10- the Gutsy may be?
tried this ```
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak
``` , but gave me an error "no such file", i went manualy to this folder but didn't find ```
10-storage-policy.fdi
```
and look around in my /media/ folder and found two hidden files there .hal-mtab and .hal-mtab-lock , second one was empty, but the first .hal-mtab has fallowing
> /dev/sdb1	1000	0	vfat	noexec,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec	/media/USB2IDE
/dev/sdb1	1000	0	vfat	nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec,usefree	/media/USB2IDE
/dev/sdb1	1000	0	vfat	nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec,usefree	/media/USB2IDE
/dev/sdb1	1000	0	vfat	nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,exec,usefree	/media/TRANS2GB_ 

I've made backup sudo cp /media/.hal-mtab /media/.hal-mtab.bak
and after that I deleted contents of .hal-mtab and save it. sudo gedit /media/.hal-mtab
now it's working for me, thanks to led me to solution with your posts.

From now on, when I'm writing or deleting files/folders to external USB disk or flash or whatever I'll use "unmount option" :)



Lamb:lolflag:

---

### Post by kolinab on 2007-10-31
Interesting - because I have no problem in Gutsy. There is no 'eject' option for me. Only one for 'unmount.' But that is what I want in any case . . . 

Cheers for Gutsy.

---

