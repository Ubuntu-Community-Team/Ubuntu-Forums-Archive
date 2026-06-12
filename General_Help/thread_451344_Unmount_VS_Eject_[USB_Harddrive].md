---
title: "Unmount VS Eject [USB Harddrive] ?"
date: 2007-05-22
forum: General Help
---

### Post by fictivetoast on 2007-05-22
Hey guys, perhaps this is a very silly question, but...

What is the effective difference between unmounting and ejecting external media?

I have a Western Digital Passport 160GB USB powered external harddrive, and Ubuntu 7.04 has been playing nice with it for a while now but for one thing: when I right click on the icon on the desktop, I'm given an "Unmount volume" option but no "Eject" option (as I am with USB keys).  

I've thusfar just been Unmounting the device and then unplugging it.. but I can hear a clear whine from the drive when I do this, as the power is cut  It sounds like a hard shutdown - like when I cut power entirely to the laptop and it blinks out with a whine of the fan - and this makes me think that I'm DEFINITELY not doing it right, even if no data destruction occurs since the drive isn't mounted.  Am I wrong on that though?  

Is there no clear way to Eject the drive (and possibly initiate its own shutdown scheme, whatever that may be, in which the power is gently cut) as opposed to Unmounting it and then pulling the plug?  Or is Unmounting the same thing as Ejecting, and is that aweful noise of the harddrive whining down just something I'll learn to ignore?

Thanks in advance!

---

### Post by fictivetoast on 2007-05-22
...anyone?

---

### Post by rocket777 on 2007-05-22
If your device is powered by the usb port itself, and no external power adapter (as many are) then pulling the usb cable will spin down the drive, with the sort of whining sound you mention.

As for eject vs. unmount, not sure. Maybe eject is for things like cd media but why a flash drive would appear different from a usb disk drive, I can't say.

---

### Post by sampohappelil on 2007-05-26
I have the same usb hard drive and have been wondering about the same thing. So far the disk has worked fine even though I have always just unmounted it and then pulled the cable, but sound it makes is not nice. In windows using the "safely remove hardware", the disk stops spinning, even though the drive keeps getting electricity from the USB cable, as a light on the drive stays on. Thus windows probably sends some signal to the drive which makes it power down.

I read somewhere that some other usb storage devices (iPods?) also need some signals sent to them to tell them to shut down. If I've understood correctly this has not yet been very well implemented on linux.

---

### Post by zek725 on 2007-05-27
> **sampohappelil said:**
> In windows using the "safely remove hardware", the disk stops spinning, even though the drive keeps getting electricity from the USB cable, as a light on the drive stays on. Thus windows probably sends some signal to the drive which makes it power down.
If I've understood correctly this has not yet been very well implemented on linux.

I think it cuts off power from the USB port. When safely removed from Windows, my USB Flash/Thumb drive's LED turns off. 

So, I assume, that the synchronization is done or any data that needs to be written is already being transferrred. That, I think, is what the **Unmount** does. However, powering down the device, I have no idea. 

In other words, what is the Ubuntu Linux counterpart for *Safely Remove Hardware* of Windows?

---

### Post by sampohappelil on 2007-05-29
> **zek725 said:**
> I think it cuts off power from the USB port. When safely removed from Windows, my USB Flash/Thumb drive's LED turns off.
No, it doesn't. I might have explained it badly, but there is a led on the drive which stays lid even after the disk has stopped spinning after using the "safe removal" in windows. Thus the disk keeps getting power from the usb cable. It just decides to stop spinning as windows somehow signals to it that it is going to be removed.

I happened to try the disk on my friends mac and there too the disk was spun down while the led kept shining after being "safely removed" the mac way.

It would be nice if this functionality could be incorporated to the way linux handles unmounting external drives powered by the usb. "eject" probably does send something to the drive as the iPods seem to like this (the "do not remove" disappears from the iPod display). Trying to "eject" the WD drive resulted in an error message and left the disk spinning however.

---

### Post by zek725 on 2007-05-29
> **sampohappelil said:**
> No, it doesn't. I might have explained it badly, but there is a led on the drive which stays lid even after the disk has stopped spinning after using the "safe removal" in windows. Thus the disk keeps getting power from the usb cable. It just decides to stop spinning as windows somehow signals to it that it is going to be removed.

I happened to try the disk on my friends mac and there too the disk was spun down while the led kept shining after being "safely removed" the mac way.

It would be nice if this functionality could be incorporated to the way linux handles unmounting external drives powered by the usb. "eject" probably does send something to the drive as the iPods seem to like this (the "do not remove" disappears from the iPod display). Trying to "eject" the WD drive resulted in an error message and left the disk spinning however.

Oh I see. So, your USB Harddrive does not have its own power supply?

---

### Post by fragos on 2007-05-29
Unmout and eject are teminology for the same function.  Eject as a term has been replaced by unmount.  Unmount will insure that everything has been written to your USB drive even poping up a message box if there's a lot to write.  If you pull the USB before its done it will complain with a message.  When USB storage is mounted it will show up in Nautilus under Places and will disappear from that list when the unmount is complete.  I always right click the USB device in the Places list to execute the unmount.  I'm sure there are other opinions on how to do this but what I sugest will work for you.

---

### Post by clem-vangelis on 2007-05-30
hi guys , i have the same harddrive ( WD passport 160 gb ) i notice the sound too and my solution is to use sdparm to stop the hardrive heads , here is my script :

you'll need sdparm ( sudo aptitude install sdparm )

#!/bin/bash
WD=/dev/sdb1
sudo umount $WD
if [ $? -eq 0 ]
then
	echo Stopping heads
	sdparm --command=stop $WD
else
	echo Unmount Failed !
fi

just replace /dev/sdb1 by your WD passport name and then your WD will shutdown silently ( like in windows

---

### Post by sampohappelil on 2007-05-30
Thanks Clem!

Played around with sdparm and that was exactly what I was looking for.:D

How was it that scripts could be added into nautilus and make them run by right-clicking and selecting them? Would it also be possible to get rid of the "sudo" in the umount? I guess this should be possible as nautilus never asks for a passwd for umounting. Or one could of course leave the umount out of script and unmount with nautilus and then run the script just to stop the drive from spinning.

> Unmout and eject are teminology for the same function.

No they are not, at least not according to their man-pages. "Eject" unmountes the device (if still mounted) and then tries to eject the device if possible (for CDROMs etc). As I already mentioned, an iPod, even though it cannot be ejected like a cdrom, reacts differently to "eject" then  to umount.

---

### Post by clem-vangelis on 2007-05-30
i was searching to include this function with nautilus but imho it required knowledge of nautilus events :/ , the temporary solution is to make the following script and place it in /home/yourname/.gnome2/nautilus-script  :
more sympathetic with zenity ( sudo aptitude install zenity ) don't forget to edit /dev/sdb1 by your harddrive node

     **OUTDATED**
[PHP]
#!/bin/sh
#wait for mtab to be updated
sleep 5
#we search an occurency of our harddrive in mtab
UMOUNT=`grep '/dev/sdb1' /etc/mtab | wc -c`
if [ $UMOUNT -eq 0 ]
then
   #we can spindown the hardrive
   sdparm --command=stop /dev/sdb1
   zenity --info --title="Info" --text="You can unplug your Hardrive !"
else
   zenity --error --title="Info" --text="It seems your harddrive isn't unmounted , unmount it then try again"
fi
[/PHP]
in fact we can spin down the harddrive without any problem while he is running but some persons said it could be dangerous so we ebtter have to take care of this little jewel :D so it's better to unmount it ( with that way no processus try to use it )

---

### Post by slumcat05 on 2007-05-30
I also have a WD drive (though mine is a 250GB My Book). Back in Edgy, the right-click menu had an "Eject" option, which unmounted the drive, and presumably sent some signal to the drive to let it know it could power down. There was an audible "click" when this happened. When I first installed Feisty, this was, to put it shortly, broken. The "Eject" option was there at first, but didn't work, an error was reported and the drive re-mounted. Recently it appears to have been fixed (sort of), although now it's only an "Unmount" option, that leaves the drive powered up (i.e. there is no click as the drive spins down and parks). It has been quite a while and there were many reports and complaints of this back when Feisty first came out, but to my knowledge it hasn't been fixed to the point of functionality that it was in Edgy. Who knows. Anyways, my solution, though somewhat annoying, is to simply skip the right-click menu, and eject from the terminal. Works like a charm every time:

```
sudo eject /media/My\ Book
```

or

```
sudo eject /dev/sda1
```

The drive remains "on" (i.e. the power light is still on) as you mentioned, but there is a click indicating the disk has stopped spinning. As far as I know this is the ideal condition for unmounting the drive, so I continue to take the extra step to open the terminal and type out the command. I suppose I could write a script, but I've really just been maintaining hope that they would fix it sooner rather than later. So it goes.

Oh, I almost forgot. For the guy who was wondering about scripts, open Nautilus and click File > Scripts > Open Scripts Folder... put any script you want here (make sure to go to its permissions and make it executable) and it will appear in Nautilus' (and thus the desktop's) right-click menu under Scripts.

---

### Post by clem-vangelis on 2007-05-30
i try with the eject command and it appears that the disk do some click like you said , but still spinning , but to spin it down i still have to use sdparm --command=stop :dev/sdb1 , and i think it's the best way to unplug it 'cause our disk is self powered , i hope that the dev team will make a feature frozen ubuntu version and a big bug correction :D

---

### Post by fragos on 2007-05-30
> **sampohappelil said:**
> Thanks Clem!

Played around with sdparm and that was exactly what I was looking for.:D

How was it that scripts could be added into nautilus and make them run by right-clicking and selecting them? Would it also be possible to get rid of the "sudo" in the umount? I guess this should be possible as nautilus never asks for a passwd for umounting. Or one could of course leave the umount out of script and unmount with nautilus and then run the script just to stop the drive from spinning.



No they are not, at least not according to their man-pages. "Eject" unmountes the device (if still mounted) and then tries to eject the device if possible (for CDROMs etc). As I already mentioned, an iPod, even though it cannot be ejected like a cdrom, reacts differently to "eject" then  to umount.

They are functionally equivalent for for storage devices without ejectable media which was what was being discussed.

---

### Post by clem-vangelis on 2007-06-01
here is the ( temporary )script to** UNMOUNT **and **SPINDOWN **the ahrddrive without being root ( require pmount , zenity and sdparm  , sudo aptitude install pmount zenity sdparm )
[PHP]
#!/bin/sh
pumount /dev/sdb1
#wait for mtab to be updated
sleep 3
#we search an occurency of our harddrive in mtab
UMOUNT=`grep '/dev/sdb1' /etc/mtab | wc -c`
if [ $UMOUNT -eq 0 ]
then
   #we sync the harddrive
   sdparm --command=sync /dev/sdb1
   #we can spindown the hardrive
   sdparm --command=stop /dev/sdb1
   zenity --info --title="Info" --text="You can unplug your Hardrive !"
else
   zenity --error --title="Info" --text="It seems your harddrive isn't unmounted , unmount it then try again"
fi
[/PHP]

---

### Post by pppetter on 2007-06-04
hi there! 

Nice script clem! Just a question, why don't you sync the drive with sdparm --command=sync before you spin it down? That disk doesn't have cache?

---

### Post by clem-vangelis on 2007-06-05
hum i dunno i was thinking pumount was syncing the harddrive , but i will add that in the script thanks !

---

### Post by nick_edwards on 2007-06-06
I created te script in the nautilus-scripts folder as there was no option "File>scripts" then ran the script in terminal and it worked perfectly but if I right click > scripts > unmount WD (my script) it does nothing??? whats going on here

---

### Post by fragos on 2007-06-06
The script menu option won't show up until there are scripts in that folder.  I'd double check the script has execute permission.

---

### Post by nick_edwards on 2007-06-06
Sorry probably not too clear. The script is in the folder and executable, when I type ./unmountWD.sh the drive parks and stops spinning. and when I right click I can select the script but nothing seems to happen. What I have noticed is (I used Clem's script with the sudo umount) it doesn't seem to work without the sudo. and I had previously typed in the passord before running the script so it didn't need to ask again for it, but it doesn't seem to work without the sudo? Howecome I need sudo to unmount the drive? And I presume the right click option then doens't get the rights or prompt for the password.

---

### Post by clem-vangelis on 2007-06-07
use the second one with pumount , works better and without sudo :)

---

### Post by fragos on 2007-06-07
There is a particularly useful script I use that requires login as admin.  It's three lines follow.  You'll notice it uses gksudo.  There appears to be some significance in using gksudo vs sudo but I'm have seen them both work in the same command line statement.  I tend to use gksudo for commands that result in a GUI application but I'm far from the final word on this.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done

---

### Post by jnewm on 2007-12-17
Thanks everyone, the script worked for me on my Lacie Rugged hard drive.  

I have one quick question though, if anyone has the time...  If I just unmount or eject, the hard drive seems to unmount/eject, but keeps on lightly humming (which I assume is spinning).  Then, if I just unplug the drive the USB, it stops humming.  Alternatively, I can use the script above (or just sdparm --command=stop), and the drive stops humming.  So, my question is: is sdparm doing something different then just unplugging the drive without running sdparm, which somehow makes unplugging the drive safer?  

Thanks again!

---

### Post by fragos on 2007-12-17
when you unmount the drive any buffered to write is written.  If there's a large amount of data to be written you will get a popup message telling you to wait until the write is complete.  The spinning of the drive doesn't indicate that the writing isn't complete.  When idle you should be safe to remove power by unplugging the USB or for that mater powering down the PC.  Spinning down a drive is done to save power which your desktop may not bother with.

---

### Post by jnewm on 2007-12-17
Thanks Fragos.  So am I right to think that there is no reason for me to use sdparm?  Thank again!

---

### Post by speedsterdm on 2007-12-25
hello all:

I have the same exact drive. What is the general consesus on the safest way to remove the drive? How do I use the script for sdparm (sorry i am a newbie to this)?

Also, when i try to eject it almost every time it says cannot eject volume. What am I doing wrong? Thanks in advance.

---

### Post by fragos on 2007-12-25
IMHO sdparm isn't required.  External USB disks are very common and sdparm although available isn't installed by default which implies it's use isn't standard fare.  There's no prohibition on unplugging the USB cable hot which also would indicate that sdparm isn't required.

---

### Post by speedsterdm on 2007-12-25
Should I be worried at all about the error message though? It isn't even letting me eject it before I pull it out of the USB.

---

### Post by fragos on 2007-12-25
> **speedsterdm said:**
> Should I be worried at all about the error message though? It isn't even letting me eject it before I pull it out of the USB.

There are a number of posts in this thread and I want to make sure I'm responding to your error message.  Would you please repeat it for me.

---

### Post by ncappel1 on 2007-12-29
> **clem-vangelis said:**
> here is the ( temporary )script to** UNMOUNT **and **SPINDOWN **the ahrddrive without being root ( require pmount , zenity and sdparm  , sudo aptitude install pmount zenity sdparm )
[PHP]
#!/bin/sh
pumount /dev/sdb1
#wait for mtab to be updated
sleep 3
#we search an occurency of our harddrive in mtab
UMOUNT=`grep '/dev/sdb1' /etc/mtab | wc -c`
if [ $UMOUNT -eq 0 ]
then
   #we sync the harddrive
   sdparm --command=sync /dev/sdb1
   #we can spindown the hardrive
   sdparm --command=stop /dev/sdb1
   zenity --info --title="Info" --text="You can unplug your Hardrive !"
else
   zenity --error --title="Info" --text="It seems your harddrive isn't unmounted , unmount it then try again"
fi
[/PHP]

clem-vangelis, thanks for the great script, it worked perfectly for my Western Digital passport (250 GB), which was having the same problem.

---

### Post by cseljatib on 2008-01-27
hi guys,

i understand that clem-vangelis got the solution to this problem (i am also using WD250 GB), however, he mention that we need to use /dev/sda1 or something to show where the external USB hard disk is, and i think that my current PC setting is not like that.

please see my current etc/fstab (after typing '$cat /etc/fstab' at the terminal, and having the USB unit connected), please note that i have a mount point (or something like that) where i can access the files that i have in my Windows XP partition (i called windows)

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
## [it was like this before, CS] UUID=b1e88010-e882-48a9-8968-ee1728942853 / ext3 defaults,errors=remount-ro 0 1
UUID=b1e88010-e882-48a9-8968-ee1728942853 / ext3 defaults,errors=remount-ro,data=writeback,noatime 0

# Entry for /dev/sda1 :
#UUID=C68058F28058EA87 /media/sda1 ntfs-3g defaults,locale=en_US.UTF-8 0 1
# Entry for /dev/sda2 :
UUID=5875-8653 /media/sda2 vfat defaults,utf8,umask=007,gid=46,noauto 0 1
# Entry for /dev/sda6 :
#UUID=bfbd7174-f247-4397-99ee-e850130fd66e /media/sda6 ext3 defaults 0 2
# Entry for /dev/ !! UNKNOW DEVICE !! :
#UUID=1c9f570b-798b-4ae7-b638-624e0d89e2a1 none swap sw 0 0
UUID=da548cea-93da-42f3-93d6-0aa458a87c89 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda6 /home ext3 nodev,nosuid 0 2
none /proc/bus/usb usbfs defaults,devgid=124,devmode=0660,busgid=124,busmode=0770,listgid=124,listmode=0660 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0


I do not how to make the .sh file of clem-vengalis, because i do not know which is the path to my USB hard disk (i think my /dev/sda1 is for the windows folder to my W.XP partition), i know for sure that the USB disk is '/media/WD250CSE'

PLEASe, help me

---

### Post by morgengenuss on 2008-04-02
hi, i would like to contribute a bit to the existing workarounds and also ask for help for fully implementing it.

my idea is to create a udev-rule for wd-passport to have it mounted at the same point every time you plug it in _but also_ to be able to run the following script on plugin (it places a notification-icon in the system tray that tells you that wd-passport is plugged in and that let's you safely disconnect it):

```
#!/bin/bash
# Put a notification-icon into the system tray
zenity --notification --window-icon=/usr/share/icons/UbuntuOS/scalable/places/gnome-fs-nfs.png --text="WD Passport is currently plugged in."

# If you click the icon you're presented the choice of safely removing WD Passport
if zenity --question --text "Do you really want to remove WD Passport (/dev/wdpassport)?" ; then
		LOCATION=$(mount | grep "WD Passport")
		if [ ${#LOCATION} != "0" ] ; then
			pumount /dev/wdpassport 2> ~/wdp.log
		fi      
		if scsi-spin -d /dev/wdpassport 2>> ~/wdp.log ; then
	 	zenity --info --text="Success!\n\nWD Passport can be safely removed now."
    	exit;
	 else
		ERRORS=$(cat ~/wdp.log)
	   zenity --warning --text="$ERRORS\n\nSorry, it seems things are screwed up badly (or WD Passport is simply not connected anymore)."
      fi
  else wdp;
fi

```

basically this script works quite well, but only if i manually execute it. [here]("http://www.reactivated.net/writing_udev_rules.html") it says:
> The functionality introduced here allows you to run a program after the device node is put in place. This program can act on the device, however it must not run for any extended period of time, because udev is effectively paused while these programs are running. One workaround for this limitation is to make sure your program immediately detaches itself.

so: how do i **detach** the script when "udev does not run these programs on any active terminal, and it does not execute them under the context of a shell." ? :confused:

(what i tried up to now
* the ampersand "&" after the script, which usually works in normal terminals
* disown; unfortunately it seems to kill the script.)

and finally here's the corresponding udev-rule:
```
KERNEL=="sd?1",SUBSYSTEMS=="scsi", ATTRS{model}=="1200BEVExternal ",SYMLINK+="wdpassport" RUN+="/usr/local/bin/wdp
```

---

### Post by holli on 2008-04-02
what about a little script that calls your notification script (or better a start-stop-daemon?!), executes it in the background (with ampersand &)and then terminates, so that udev can continue? would that work for you?

---

### Post by morgengenuss on 2008-04-02
i tried a short script that simply executes "wdp" with an ampersand and then exits, but that just caused more and more instances of wdp to be started (in a loop or something) pushing cpu-usage to 100%.

what's a start-stop daemon? is that a script in init.d?

just to be sure, here's the script that calls the script:
```
#!/bin/sh
/usr/local/bin/wdp &
exit
```

---

### Post by morgengenuss on 2008-04-02
ok, i also tried this now:
```
#!/bin/sh
start-stop-daemon --start -b --exec /usr/local/bin/wdp
```

but for some reason the bloody wdp-script keeps running in a loop creating more and more instances of itself...

---

### Post by holli on 2008-04-02
you can also take the scripts in /etc/init.d/ as a reference and try to adapt some of those for your needs... as for the loop, i don't really have an idea why the script is doing this...

edit:
well, about that loop, the only thing i see in your script is:

```
if ... ; then
   ...
  else wdp;
fi
```

you have a recursion in your script and the exit condition:```
 zenity --question --text "Do you really want to remove WD Passport (/dev/wdpassport)?"
``` seems to be never true, so you'll end up with an infinite loop

---

### Post by morgengenuss on 2008-04-02
allright, that might be it. for some reason that was never a problem when executing the script from the shell.

the only problem is, that if i remove the "else" the bloody notification icon disappears. hm, so the question is how can i modify this script so that if i press the cancel button the icon just stays there without being in a loop? (otherwise you would only have one chance to click there and remove wdpassport)

---

### Post by morgengenuss on 2008-04-02
one more thing i noticed is that even if the script is executed the icon doesn't appear in the system-tray, so maybe it's missing the connection to the xserver or something...

---

### Post by holli on 2008-04-02
can you try something like this in your script:
```
zenity --notification --window-icon=/usr/share/icons/UbuntuOS/scalable/places/gnome-fs-nfs.png --text="WD Passport is currently plugged in." > ~/zenity-notification.log
```
so that you can see in the logfile whether there is an error with the xserver connection?

---

### Post by morgengenuss on 2008-04-02
ok, for some reason this doesn't work at all. it seems i can't redirect the output of the zenity-command to a log-file and it seems there is no --verbose option for zenity or anything

i only know that this line isn't executed successfully, because i don't get any echo of
zenity --notification --window-icon=/usr/share/icons/UbuntuOS/scalable/places/gnome-fs-nfs.png --text="WD Passport is currently plugged in.">~/wdp.log &&
echo "the icon should be in place now"

---

### Post by morgengenuss on 2008-04-02
now i got as far as resolving most issues i have.
what helped zenity to be executed was sudoing it and telling it with which user and display to connect it:
```
DISPLAY=:0. sudo -H -u ochosi zenity --notification --window-icon=/usr/share/icons/UbuntuOS/scalable/places/gnome-fs-nfs.png --text="WD Passport is currently plugged in."
```

now: how can i make that bloody icon stay there in case i press "cancel"?

---

### Post by holli on 2008-04-02
try your initial version of the script combined with this display and sudo stuff (in front of every occurence of zenity) and execute it in the background, it should work ok then. the problem before was there, because when zenity failed to start correctly, your script would enter an infinite loop

---

### Post by morgengenuss on 2008-04-02
ok, i have everything figured out now. the script starts whenever my wd-passport usb-hdd is plugged in and the notification icon stays as long as i don't remove the hdd.
[B]
A BIG THANKYOU GOES TO holli![/B] :!:

here's the final version of the script (it assumes you have at least symlinked wdpassport to /dev/wdpassport via udev):

/usr/local/bin/wdp
```
#!/bin/bash
# Put a notification-icon into the system tray
if DISPLAY=:0. sudo -H -u [COLOR="Red"]insert_your_username_here![/COLOR] zenity --notification --window-icon=/usr/share/pixmaps/wdumount.png --text="WD Passport is currently plugged in." ; then
echo "the icon should be in place now"
else echo "zenity error..." ;
fi

# If you click the icon you're presented the choice of safely removing WD Passport
if DISPLAY=:0. sudo -H -u [COLOR="Red"]insert_your_username_here![/COLOR] zenity --question --text "Do you really want to remove WD Passport (/dev/wdpassport)?" ; then
	echo "icon clicked"
		LOCATION=$(mount | grep "WD Passport")
		if [ ${#LOCATION} != "0" ] ; then
			pumount /dev/wdpassport 2> ~/wdp.log
		fi      
		if scsi-spin -d /dev/wdpassport 2>> ~/wdp.log ; then
	 	DISPLAY=:0. sudo -H -u [COLOR="Red"]insert_your_username_here![/COLOR] zenity --info --text="Success!\n\nWD Passport can be safely removed now."
    	exit;
	 else
		ERRORS=$(cat ~/wdp.log)
	   DISPLAY=:0. sudo -H -u [COLOR="Red"]insert_your_username_here![/COLOR] zenity --warning --text="$ERRORS\n\nSorry, it seems things are screwed up badly (or WD Passport is simply not connected anymore)."
      fi
  else echo "cancel button was hit..."
	wdp ;
fi
```
[COLOR="YellowGreen"]
/// I JUST FOUND OUT THE SCRIPT BELOW IS NOT NECESSARY USELESS ///[/COLOR]

now this script is started via another script which is called run_wdpm which logs into ~/wdp.log

/usr/local/bin/run_wdp:
```
 #!/bin/sh
/usr/local/bin/wdp >> /home/[COLOR="Red"]insert_your_username_here![/COLOR]/wdp.log
```

let me know if this doesn't work for anyone! :guitar:

---

### Post by morgengenuss on 2008-04-02
ok, actually you don't need run_wdp - so just change your udev-rule to execute wdp straight away... :)

---

### Post by holli on 2008-04-03
> **morgengenuss said:**
> ok, actually you don't need run_wdp - so just change your udev-rule to execute wdp straight away... :)
nice job! so you say that you don't even need to run your notification script in the background? but isn't that what you wanted to avoid because it would pause the execution of udev? can you plug in other devices and see if that is the case (i.e. new devices aren't recognized anymore or so)? > The functionality introduced here allows you to run a program after the device node is put in place. This program can act on the device, however it must not run for any extended period of time, because udev is effectively paused while these programs are running. One workaround for this limitation is to make sure your program immediately detaches itself.

---

### Post by morgengenuss on 2008-04-03
good point, holli.

as far as i can see (and i've done a bit of testing now)_ it's no problem_ to plugin other usb devices in the meantime and use them, even the according udev-rules are still applied.
[COLOR="SlateGray"](i added a usb stick with a unique symlink in dev and all of that still happened though the wdp-script was running and the rule for the usb-stick was lower on priority than the one for the harddrive/script. number 95 for wdp, 96 for the usbstick)
[/COLOR]


actually: do you (or anyone else here) happen to know whether it could work to simply write a udev-rule that executes a script on ACTION=="remove" that spins-down the harddrive? (the question is, what does "remove" mean here; does it mean unmount? or..?)

---

### Post by holli on 2008-04-03
afaik "remove" in udev means unplugging the device, so trying to spin down the hard drive then would be useless.
from [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) : > You can also use the ACTION environment variable to detect whether the device is being connected or disconnected - ACTION will be either "add" or "remove" respectively.

---

### Post by morgengenuss on 2008-04-03
that's a pain. otherwise this would have been a very nice and short patch...

---

### Post by swordphsh on 2008-04-28
I'm still kind of new with linux, but I read through this thread and am trying to figure it the whole script out. I would like to adapt it to use with a generic external usb hard drive. I'd like to have that icon appear when it is plugged in and the option to unmount and eject/spin-down the drive.

I kinda understand the final script, but I don't think I'm getting the udev rules. I'm having trouble figuring out what goes where; what scripts go in which files, etc. 

If someone could just recap for me and explain a few things like the udev rules that would be great.

Thanks.

---

### Post by morgengenuss on 2008-04-29
hi, just wanted to say that this script is currently broken in hardy (just upgraded) with the old error of reproducing more and more instances of itself.

as soon as i have come up with a solution i'll post it here... :(

---

### Post by Fisslefink on 2008-05-06
Thanks so much to everyone who helped make this into a usable script.  It works fine for me as an 'eject' button from the system tray with the latest script by morgengenuss on Feisty.  The only thing I had to change was the location of the icon... The path others have used did not exist on my system. 
I used /usr/share/icons/gnome/scalable/places/gnome-fs-nfs.svg

**My setup:**
I have a WD MyBook Studio Edition 1 TB drive connected by Firewire 400 to an Asus P4P800-E Deluxe motherboard.  

[COLOR="Red"][B]
But I had another problem:[/B][/COLOR]
The drive did not spin down or go to sleep when the computer shut down.  If I put my ear to the drive, I could hear the drive spinning, even 12 hours after the computer was turned off.  Also, the LED light stayed on.  Spinning constantly (24 hours a day) is sure to reduce its lifespan, and I don't want that.


[COLOR="SeaGreen"]**My solution:**[/COLOR]
I used the scsi-spin commands from morgengenuss's script in a simpler script which is executed on shutdown.  

I wrote a full how-to in a new thread, here: [http://ubuntuforums.org/showthread.php?p=4899207#post4899207](http://ubuntuforums.org/showthread.php?p=4899207#post4899207)

Thanks again to all of you.

---

### Post by fragos on 2008-05-06
Even after shutdown, desktop systems are still partialy powered. For example 5V from USB ports. I always power down on a power strip after shutdown. Saves electricity and is gaurenteed to keep hackers out.

---

### Post by shanepardue on 2008-06-19
So at this point the script doesn't appear to spindown the drive in Hardy. 
Is anyone aware of a solution? Also, is there a way to have it spindown 
while not in use for a certain period of time and come back on when the 
drive is requested?

---

### Post by holli on 2008-06-19
> **shanepardue said:**
> So at this point the script doesn't appear to spindown the drive in Hardy. 
Is anyone aware of a solution? Also, is there a way to have it spindown 
while not in use for a certain period of time and come back on when the 
drive is requested?
in hardy you need to be root to spin down the drive, so the corresponding lines in the script should read something like this:
```
#sync and stop the drive

gksudo "sdparm --command=sync $DRIVE_DEVICE"

gksudo "sdparm --command=stop $DRIVE_DEVICE"
```

---

### Post by shanepardue on 2008-06-19
Hmm..mine still seems to be spinning even after the script tells me it's safe to unplug. here are is content of my script. Thanks!

```
#!/bin/sh
pumount /dev/sdb1
#wait for mtab to be updated
sleep 3
#we search an occurency of our harddrive in mtab
UMOUNT=`grep '/dev/sdb1' /etc/mtab | wc -c`
if [ $UMOUNT -eq 0 ]
then
   #we sync the harddrive
   gksudo sdparm --command=sync /dev/sdb1
   #we can spindown the hardrive
   gksudo sdparm --command=stop /dev/sdb1
   zenity --info --title="Info" --text="You can unplug your Hardrive !"
else
   zenity --error --title="Info" --text="It seems your harddrive isn't unmounted , unmount it then try again"
fi  
```

---

### Post by holli on 2008-06-19
> **shanepardue said:**
> Hmm..mine still seems to be spinning even after the script tells me it's safe to unplug. here are is content of my script. Thanks!

```
#!/bin/sh
pumount /dev/sdb1
#wait for mtab to be updated
sleep 3
#we search an occurency of our harddrive in mtab
UMOUNT=`grep '/dev/sdb1' /etc/mtab | wc -c`
if [ $UMOUNT -eq 0 ]
then
   #we sync the harddrive
   gksudo sdparm --command=sync /dev/sdb1
   #we can spindown the hardrive
   gksudo sdparm --command=stop /dev/sdb1
   zenity --info --title="Info" --text="You can unplug your Hardrive !"
else
   zenity --error --title="Info" --text="It seems your harddrive isn't unmounted , unmount it then try again"
fi  
```
the quotation marks are there for a reason!

```
gksudo "sdparm --command=sync $DRIVE_DEVICE"
```

---

### Post by shanepardue on 2008-06-19
> **holli said:**
> the quotation marks are there for a reason!

```
gksudo "sdparm --command=sync $DRIVE_DEVICE"
```
D'oh! Thank you very much for your help!

---

### Post by Psykotik on 2008-06-22
I've been trying any solution presented here: with no luck.

I opened a bug [on launchpad]("https://bugs.launchpad.net/ubuntu/+bug/241927"), if Mybook users could confirm...

---

