---
title: "Completely Broke Ubuntu..."
date: 2007-02-24
forum: General Help
---

### Post by nzk on 2007-02-24
So my installation was being slow, and someone told me to turn off some unneeded services (Bluetooth, some Accessibility services) and I did. After I rebooted, everything seemed fine, but when I logged in, the Beryl splash screen came up normally, and then froze. I could do nothing but restart X. After going into recovery mode and installing a CLI IRC client, I found out which file needed to be modified to disable the splash screen. I disabled it, and rebooted. When I boot, its not necessarily "frozen", but its the equivalent of molasses. When I try to open a program, it opens but stays minimized, and I can't do anything about it. The clock doesn't even tick. I tried to rotate the 3D Beryl cube, which to my surprise, worked fine. The clock ticked when in the 3D cube mode.

Is there a way to find out what is causing this problem? My computer is basically unusable like this. 

Thanks.

---

### Post by igknighted on 2007-02-24
Can you have a terminal open running top when this happens?  Also, do you remember what else you disabled?  Re-enabling it might bring it back, then remove them one at a time until you find the culprit.

---

### Post by nzk on 2007-02-24
The thing is, I can't enable it at all. To make things easier, _pretend_ that X is broken (its not, but its unusable). As I said, I disabled Bluetooth, Printing, and some Accessibility stuff. I can't run top, since I can't open a terminal.

---

### Post by DagMan on 2007-02-24
Edit:  Try logging into rescue mode at grub if you can't use ctrl-alt-backspace.  You can sign in as your user at the command line and work from there.  Ignore the bit below about GDM until you get your graphics back.

Are you able to get back to a normal non-beryl session, for example select a gnome-session if beryl is running as a session or failsafe gnome  if it is loading on normal gnome startup?   If you can't do this because you're auto logging into gdm, try hitting ctrl-alt-f1 to login at the terminal and sudo /etc/init.d/gdm restart and then you can access your gdm menu by pressing ctrl-alt-f7

Also, if it is a case of beryl being run when gnome starts up, you can remove it at the command line 
cd /home/USERNAME/.config/autostart
ls
then look at the contents of the files
cat FILENAME
until you find the one that has beryl in the line that says EXEC and delete that file.

Mine only has one file that passes off to another script that runs stuff I want to do at startup.  For me it would look like this
```
cd /home/USERNAME/.config/autostart
cat "no name"
```
The file is actually called 'no name' on my system so it needs to be quoted in the terminal since it has a space in it or the system will think there are 2 separate files.
the cat command would just display the contents of 'no name' and I'd see what it had in it, then if that was the right file,
```
rm "no name"
```
again using quotes.

Any way you slice it, it doesn't sound bad.  You should be able to get back in using metacity one way or another.

Also, I had this problem and running beryl with the metacity windows manager worked fine. Try this if you just want to try that first, it would go down like this on my system,
sudo nano /home/user/.beryl-managerrc
then find the line under [wm-settings] that says active_wm=whatever
It's the second line on my system, and set it to active_wm=2
Then ctrl-x to exit and hit Y to save the file when prompted on the way out.
Your's may be differant but from the sound of it, it wouldn't break it any harder to try.

This sounds unrelated to your issue, but maybe not.  If you can't get beryl running again, I had problems with mine freezing sort of like you're talking about and I had to set GDM (login manager in the menu) so the root user could log in.  Log in as root, run beryl as root, log back in with metacity as the normal user and then copy over the configuration files and change the ownerships to me.  You can test this out once you get back into your box by stopping beryl beryl-manager and emerald etc and then running beryl-manager at the terminal with the sudo command.  If all goes well then it will pobably work for you to do this, if not then you have to reboot again is all.

---

### Post by jongkind on 2007-02-24
Assuming that Beryl is autostarted:

I suggest that you reboot in the recovery mode.

After that is done you can remove the autostart beryl command:
sudo rm /home/yourusername/.config/autostart/beryl-manager.desktop

After that you can reboot in the normal mode and after login the default windows manager will take over. Now you can repair your system as desired.

---

### Post by nzk on 2007-02-24
It's not Beryl thats the problem, it has to do that I disabled those services (AFAIK). How can I reenable them?

(I tried logging in to a regular GNOME session, and a failsafe GNOME session)

Ctrl Alt Backspace works, though.

---

### Post by DagMan on 2007-02-24
try 
sudo apt-get install sysv-rc-conf
then 
sudo sysv-rc-conf
and don't enable anything, just have a look and see if anything is familiar to you, to jog your memory about what it was you might have disabled.  Use the arrow keys to scroll down to make sure there isn't more beyond the limit of the screen.  Then post here if you remember what it was.
The reason I say that is because it needs to be enabled at the proper run levels and you will see that there are quite a lot of them.  If you post here and your general hardware, for example if you're using a laptop or desktop, then someone can have a look at the runlevels they have them on with their own system and post them here.
That's the best way I think.

---

### Post by nzk on 2007-02-24
I pretty much remember exactly what I disabled, it was Bluetooth, both Printing services, and the services that have Wheelchair icons. Thats it. I'll try that command and see if there is something I am missing.

---

### Post by nzk on 2007-02-24
Why does this keep happening? I've had to reformat 7 times in less then a year because of these various Ubuntu problems. I haven't even had it installed for 2 weeks this time, and it's broken.

---

### Post by tribble222 on 2007-02-24
I know this isn't a solution to your immediate problem, but with 7 formats in less than a year, you might consider buying an extra hard drive and running rdiff-backup nightly.  That way if you do something that messes up your install and you can't figure out how to repair it, you can just restore the backup and only have lost -in the worst case- the last 24 hours.

If you have enough free space on your current drive you could create a new partition to put the backup on.  Or even just keep it on your same partition, but that's not as good.

---

### Post by nzk on 2007-02-24
Is there some kind of system-restore utility for Ubuntu? 

I have a ext. HDD, is there a guide for this rdiff-backup?

Thanks.

---

### Post by DagMan on 2007-02-25
I'm thinking it's either a hardware failure or incompatability the 7 reinstalls.  Bummer to have a problem like that and not know why.


I can't help.  I have bluetooth disabled as well and I don't know what the wheelchair thing is.

As for the printing services though, there's cupsys and hplip that I know of.
cupsys is enabled on 2,3,4,5
hplip is enabled on the same 2,3,4,5

I can't imagine which one of those would have screwed up your system.  Perhaps whatever the wheelchair thing was.

---

