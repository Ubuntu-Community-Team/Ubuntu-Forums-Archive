---
title: "Very Slow Shutdown With Dual Boot System (Win10 / Ubuntu 16.04)"
date: 2017-09-05
forum: General Help
---

### Post by gauss4563 on 2017-09-05
Hi,

So I installed Ubuntu 16.04LTS about 7-10 days ago and since then, when I turn the PC down, whether it's Win or Ubuntu, it takes a long time (up 2 mins and I can see errors on Win10 shutdown monitoring, but without app indication and I get unsafe shutdowns on my Ubuntu drive) until it shuts down (I see the ubuntu\win shutting down animation all this time).
The Win10 is installed on Samsung 850 EVO (SSD) and Ubuntu is installed on Samsung 960 EVO (PCI-E NVMe), so it should be much much faster. Can you guys help me figure out why it happens and how can I fix it, please?

Thanks in advance!

---

### Post by oldfred on 2017-09-05
Have you updated UEFI from vendor and firmware from Samsung?
I had to non
       [http://www.samsung.com/semiconductor/minisite/ssd/downloads/software/Samsung_Magician_DC_Linux_64bit.zip](http://www.samsung.com/semiconductor/minisite/ssd/downloads/software/Samsung_Magician_DC_Linux_64bit.zip)
[http://askubuntu.com/questions/808828/how-to-install-samsung-magician](http://askubuntu.com/questions/808828/how-to-install-samsung-magician)

start to see where:
systemd-analyze  
      systemd-analyze blame
systemd-analyze critical-chain

---

### Post by gauss4563 on 2017-09-05
Thanks for the reply!

Well, this "Magician" (which works fine on Win10 and there it showed it has the latest firmware) doesn't even recognize the drives...

I ran the systemd-analyze and that's the output:
[ATTACH=CONFIG]276603[/ATTACH][ATTACH=CONFIG]276604[/ATTACH]

But it shows booting times and not shutdown. Booting time is fine, atm.

---

### Post by gauss4563 on 2017-09-06
Anyone? please?

---

### Post by vidtek on 2017-09-06
gauss-

I have been tearing my hair out with this issue too, mine now SEEMS to be working ok.  I have been tweaking this and that for days trying  to sort it out.  My system is similar to yours, I use a 250 EVO for win 10 and Mint 18.2 dual boot.

There are handy tools for diagnosing slow boots, but none AFAIK for slow shutdowns.

I have done so much tweaking I don't really know what fixed it eventually-or if it indeed is really fixed now.  I trawled through many forums to get a fix, and it seems that every instance is system and hardware dependent-no two problems are the same, but the systems hang on shutdown, some forever like mine, others just take many minutes to shut down.

Off the top of my head, things I remember trying:

Disable usb3 legacy in bios.

use this line for reboot..........."sudo killall mythbackend && swapoff -a && systemctl reboot"       .......if you run mythtv and mysql

try this command for shutdown as well.............."shutdown -P now"

try this for your grub 

GRUB_DEFAULT="0"
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="6"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
GRUB_CMDLINE_LINUX=""


That's all I can remember for now.

Best of luck, Tony.

gauss- just remebered, I disabled my swapfile as well in fstab.  Modern systems with 16gb+ ram don't really need it now anyway.

---

### Post by oldfred on 2017-09-06
Just before you shutdown can you see using top any processes still running?
Do you have lots of foreign connections, like Internet connected backup drive that has to run or even extra flash drives or DVDs connected?
Have you run full fsck on all Linux ext4 partitions. Should not be required, but who knows.

Have you tried a safe forced shutdown and see if it says anything. Do not remember if anything shown if terminal open or not?

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by gauss4563 on 2017-09-06
Thanks for the advice!

vidtek - what do you mean by "[COLOR=#000000]try this for your grub"? how\where do I change that?[/COLOR]

[COLOR=#000000]oldfred - what do you mean by "using top"? [/COLOR]
[COLOR=#000000]I do not have lots of foreign connections. No backup drives, no flash drives and no DVDs connected.
I didn't run full fsck. Should I?
Didn't try safe forcde shutdown. But I will and see if I get something different. 
I never forced shutdown the system, because there was no need (never froze or anything like that), is there a need to do this the REISUB way or is it possible to do it through the terminal?

Thanks![/COLOR]

---

### Post by oldfred on 2017-09-06
Top is a terminal command to show what is running.
top

Htop is another versions, somewhat better, but you have to install it.
sudo apt install htop
htop

control-q to quit above text screens.

---

### Post by vidtek on 2017-09-06
[I][QUOTE=gauss4563;13683843]Thanks for the advice!

vidtek - what do you mean by "try this for your grub"? how\where do I change that?[/I]

This is the file to edit -  /etc/default/grub 

The recommended way is to do it via sudo using nano as the editor. The command would therefore be: sudo nano /etc/drfault/grub

If you are coming from a windaz environment, the command line may be a little daunting though.  You should have thunar or nautilus installed on a vanilla Ubuntu, so a more familiar way for you to edit your files 
would be to hold the alt key down while pressing the F2 key.  In the box which appears type this:  gksudo thunar   or  gksudo nautilus whichever you have installed. This will give you root (administrator) access to your file system.  Then simply navigate to the file /etc/default/grub  

Before you do anything to the file, right-click on it and copy it to a safe location where you can retrieve it easily if the need arises.

Right clicking on it should give you another menu with the option of a text editor.  Choose that and edit away.

Before doing this, try disabling your swap file, that is located in /etc/fstab  (once again back it up first somewhere getatable).

The line you want will look like this:   UID=bb7bf42d-7858-4b9c-b135-a23212b43c24    none    swap    sw    0    0

You will have a different number, every disc partition has a unique UUID number.

I just re-read your original post and realise you have your windaz install on another disc.  Try disconnecting that and see if your machine shuts down ok.

Do the same in your windows system disconnect the ubuntu disc and see if that shuts down better.     Always best to do the obvious stuff first!

Cheers Tony.

---

### Post by vidtek on 2017-09-06
> **oldfred said:**
> Just before you shutdown can you see using top any processes still running?
Do you have lots of foreign connections, like Internet connected backup drive that has to run or even extra flash drives or DVDs connected?
Have you run full fsck on all Linux ext4 partitions. Should not be required, but who knows.

Have you tried a safe forced shutdown and see if it says anything. Do not remember if anything shown if terminal open or not?

       Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Oldfred-

You have helped me in the past, something I have been meaning to ask you, I can never remember the above key sequence, I just do ctrl+alt+SysRq then hit the b key to kill everything, am I storing up problems do you think?

Thanks, Tony.

---

### Post by oldfred on 2017-09-06
The full REISUB is recommended.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]http://kember.net/articles/reisub-the-gentle-linux-restart/
[/URL]

[LIST]
[*]R: Switch the keyboard from raw mode to XLATE mode
[*]E: Send the SIGTERM signal to all processes except init
[*]I: Send the SIGKILL signal to all processes except init
[*]S: Sync all mounted filesystems
[*]U: Remount all mounted filesystems in read-only mode
[*]B: Immediately reboot the system, without unmounting partitions or syncing
[/LIST]

[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by gauss4563 on 2017-09-06
Using the REISUB method shuts down the PC almost instantly. What does it mean?

---

### Post by oldfred on 2017-09-06
Is it killing some background process, or is it one of the other commands?

I did find removing quiet splash on booting, seemed to let me see shutdown also. But with my SSD shutdown was very quick, only a half screen of lines showed before it was off.

---

### Post by gauss4563 on 2017-09-08
The thing is - I can't see whether it kills any background processes because the screen turns black to quickly and is then stuck in the reboot/splash (while shutting down still) screen for a long time.
This screen:
[ATTACH=CONFIG]276643[/ATTACH]

---

### Post by BenginM on 2017-09-08
Hiya, So it's a slow shutdown in both MS windows and ubuntu , and both installed on a samsung SSD! interesting , you may want to check the S.M.A.R.T status on both SSDs.

Is this a desktop or a laptop?

usually, the cause would be a service, an app running in the background, or a zombie process. 

Now, does it shutdown quickly when you preform a shutdown in terminal 
$ sudo shutdown -h now

and while you at it, Create another user account, and  log into it and try to shutdown from that account. Is the shutdown still slow?!

---

### Post by gauss4563 on 2017-09-08
According to SMART, both are in "good" health. 
It's a desktop. 
Maybe, but in both cases I can't find which. On Windows all I can see is that there was an unusually slow shut down, but it doesn't specify the causing process. 
The command didn't change the shutting-down time. 
Creating a new account didn't change the shutting-down time.

No luck, as of now, I'm afraid. Thanks for the advice, though!

---

### Post by BenginM on 2017-09-08
is it slow on reboot as well as shutdown ? 
you may wan to Try this, reboot and from the GNU GRUB menu, highlight the current ubuntu kernel and hit E on the line to edit it, then remove quiet splashthen hit Ctrl+X to boot with the current kernel.
If you shut Ubuntu down now It should shows you at the end what kind of stop job slows down your shutdown procedure. if there is any!
 if there is none , then you should probably run a file system check fsck on the disk ..

from recovery (safe) mode 

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

drop to a root shell , and type:

mount -o remount,rw /
fsck -f
mount -o remount,ro /
sync
reboot

or just select fsck from the menu as shown [here]("http://http://imgur.com/9KUUOHI")

---

