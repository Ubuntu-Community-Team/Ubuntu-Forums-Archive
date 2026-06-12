---
title: "64bit users, we want to hear from you!"
date: 2008-02-24
forum: General Help
---

### Post by ago on 2008-02-24
If you have an AMD64 machine, an Intel Core Duo + or any other 64 bit machine and have tried Wubi 8.04 rev431+ with latest amd64 ISO, please let me know if it worked for you or not!

NOTE amd64 should also be used on Intel 64 bit machines.

---

### Post by plethorex on 2008-02-25
I couldn't personally get it to work (AMD Athlon 64 X2 6000.)  I downloaded the Ubuntu ISO (hardy-desktop-amd64.iso), it went through the install process, but after I restarted and selected Ubuntu from my boot screen, it crashed to a hanging black screen forcing a restart.

I believe this was using Hardy alpha 5.  Also of note, I have an 8800GT, which is notoriously horrible on linux so far.  I can't install 7.10 using Wubi either, hangs at boot screen, then gives me a GDM failed to load error, crash and hang at unloading process.

Edit:  I realize I wasn't very specific.

Crashes at Checking Installation, Computing the new partitions.
Crashes to Installation has failed, log information stored to suchandsuch.zip (which doesn't exist, even though it says it does.)

---

### Post by evan d on 2008-02-25
> **plethorex said:**
> I believe this was using Hardy alpha 5.  Also of note, I have an 8800GT, which is notoriously horrible on linux so far.  I can't install 7.10 using Wubi either, hangs at boot screen, then gives me a GDM failed to load error, crash and hang at unloading process.

Hrm, I wonder if you're getting bit by [this bug]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/147623").  It might help to remove the "quiet usplash" part of the kernel command line parameters.  You can do this when you arrive at the grub countdown by pressing escape, then e on the boot entry, then arrow down to the kernel line and press e again.  Make the change then press enter, then b to boot.

Of course this will probably do nothing for it crashing at the "computing partitions" stage, but I'd need to see /var/log/syslog and /var/log/installer/debug from the installation environment to diagnose that further.  Do you have another machine you can transfer the log files to via ftp or scp?

---

### Post by plethorex on 2008-02-25
> Hrm, I wonder if you're getting bit by this bug. It might help to remove the "quiet usplash" part of the kernel command line parameters. You can do this when you arrive at the grub countdown by pressing escape, then e on the boot entry, then arrow down to the kernel line and press e again. Make the change then press enter, then b to boot.

When pressing escape at the initial grub countdown (of 2 seconds, which was a bit difficult to catch at first) I'm not given an option to change the parameters, at least not that I can see.  It gives me 4 options of boot.lst to choose from (2 of which don't exist, 1 of which will bring me to the Ubuntu installer GUI, 1 turns my monitor off?).  The final 2 options are reboot and halt.  When I installed 7.10, I remember having to use the text-based installer to get into Ubuntu, then had to use Envy to force new drivers.  This doesn't seem to be an option with alpha 5 so far.

> Of course this will probably do nothing for it crashing at the "computing partitions" stage, but I'd need to see /var/log/syslog and /var/log/installer/debug from the installation environment to diagnose that further. Do you have another machine you can transfer the log files to via ftp or scp?

I'm assuming I'd need a computer also running Ubuntu to transfer the files off?  I have a laptop but have been weary of installing.  When the installation fails, it gives me directions to check /ubuntu/installation-logs.zip, however that file doesn't exist on my computer (from within Windows, at least.)

---

### Post by ago on 2008-02-25
Press esc at the countdown and select verbose mode. 

At the crash, do NOT restart, see if you can get to a terminal by using ctrl+alt+del. If you can the log is in /var/log/syslog. 

You may want to edit C:/ubuntu/install/custom-installation/hooks/failure-command.sh and replace it with this: 

[http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/download/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt/failurecommand.sh-20080212005749-tq96v0ekmwilovnc-1/failure-command.sh](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/download/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt/failurecommand.sh-20080212005749-tq96v0ekmwilovnc-1/failure-command.sh)

This will make any log after the crash appear in C:\ubuntu

---

### Post by plethorex on 2008-02-25
> **ago said:**
> Press esc at the countdown and select verbose mode. 

At the crash, do NOT restart, see if you can get to a terminal by using ctrl+alt+del.

When pressing control+alt+del after the crash, it gives me a warning:

"System is rebooting NOW!  Control + Alt + Delete pressed..."

And after 10 or so seconds, it restarts.

> You may want to edit C:/ubuntu/install/custom-installation/hooks/failure-command.sh and replace it with this: 

[http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/download/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt/failurecommand.sh-20080212005749-tq96v0ekmwilovnc-1/failure-command.sh](http://bazaar.launchpad.net/~ubuntu-installer/wubi/hardy/download/agostino.russo%40gmail.com-20080225023058-shsf3oawibio0nxt/failurecommand.sh-20080212005749-tq96v0ekmwilovnc-1/failure-command.sh)

This will make any log after the crash appear in C:\ubuntu

This worked!  I have attached the entire installation-logs.zip file to this message (hopefully) if anyone wants to take a look.

---

### Post by ago on 2008-02-25
Thanks a lot!

Can you please also post C:/ubuntu/custom-installation/preseed.cfg (after removing the password)?

---

### Post by plethorex on 2008-02-25
> **ago said:**
> Can you please also post C:/ubuntu/custom-installation/preseed.cfg (after removing the password)?

I had to rename the file to preseed.txt so that the attachment manager would allow me to upload it.  Not sure if I got the password out of it, I deleted the entire useraccount section.

---

### Post by ago on 2008-02-25
Hmm as expected there is no swap file in there... That looks like a wubi bug. I will have a look soon.

---

### Post by ago on 2008-02-25
Can you pls try 434 and post your preseed again?

[http://wubi-installer.org/devel/minefield/Wubi-8.04-alpha-rev434.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04-alpha-rev434.exe)

---

### Post by plethorex on 2008-02-25
Preliminarily, it won't even begin to install.  Run 434, choose to install on D drive, crashes at "Retrieving installation files, resume supported Ubuntu 8.04."  Visual Studio says, "An unhandled Win32 exception occured in Wubi-8.04-alpha-rev434.exe [2952]."

I will try a few more times, change some of the options.

---

### Post by mikedep333 on 2008-02-25
> **ago said:**
> If you have an AMD64 machine, an Intel Core Duo + or any other 64 bit machine and have tried Wubi 8.04 rev431+ with latest amd64 ISO, please let me know if it worked for you or not!

NOTE amd64 should also be used on Intel 64 bit machines.

I hate to be picky, but it is not used on core (1) duo machines.

[QUOTE="Wikipedia"]
It is used in newer versions of Pentium 4, Pentium D, Pentium Extreme Edition, Celeron D, Xeon, and Pentium Dual-Core processors, and in all versions of the Core 2 processors.
[/QUOTE]

IMHO, you should explain on [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) that it will default to AMD64 on such machines, and that is generally considered desirable.

---

### Post by ago on 2008-02-26
> **plethorex said:**
> 
I will try a few more times, change some of the options.

Can you please redownload wubi434? Previous one was no good.

---

### Post by plethorex on 2008-02-26
> **ago said:**
> Can you please redownload wubi434? Previous one was no good.

Well, whatever you did was mostly successful.  However, I think my issues have gone beyond Wubi and now are Ubuntu itself.

The installation was successful, I think.  Right as the installer finished (cleaning up) it flashed an error message which didn't stay on the screen more than a 1/10th of a second, so I'm not sure what it said.  My monitor went into power saving mode, and I couldn't recover.  Upon restart, choosing any option from GRUB gives this error:

> kernal /boot/umlinuz-2.6.24-8- generic root=UUID=40c05d9c05d99cc loop=/ubuntu/disks/root.disk ro quiet splash

File not found

Not sure what to do to fix that issue.  Also, if I try to use the alternative package to install Ubuntu, it won't even install.  Gives another, similar, file not found error.

---

### Post by ago on 2008-02-26
> **plethorex said:**
> Well, whatever you did was mostly successful.  However, I think my issues have gone beyond Wubi and now are Ubuntu itself.

The installation was successful, I think.  Right as the installer finished (cleaning up) it flashed an error message which didn't stay on the screen more than a 1/10th of a second, so I'm not sure what it said.  My monitor went into power saving mode, and I couldn't recover.  Upon restart, choosing any option from GRUB gives this error:



Not sure what to do to fix that issue.  Also, if I try to use the alternative package to install Ubuntu, it won't even install.  Gives another, similar, file not found error.

When you boot, select Ubuntu, then press esc at the countdown
then select the first option, and press "e" to edit
select the line that starts with "root" and press "e" to edit
it should be

root (X,Y)/ubuntu/disks

X = disk number -1
Y = partition number -1

e.g. if wubi is on disk 1, partition 2

root (0,1)/ubuntu/disks


Press enter to save, and "b" to boot

Pls let me know what value was in there originally and with what value you can boot instead

---

### Post by plethorex on 2008-02-26
> **ago said:**
> Pls let me know what value was in there originally and with what value you can boot instead

Value was (0,0)
Value needed to be (1,0)

This message is being sent from within Hardy, so... success!

---

### Post by ago on 2008-02-26
Can you pls post the content of /boot/grub/device.map

and of

cat /proc/mounts | grep host

and 

zip of /var/log/installer

---

### Post by slayer666 on 2008-02-26
Why not add the option to choose 32bit or 64bit in wubi?
Wubi can activate the option if a 64bit cpu is present, if not then N/a.

---

### Post by ago on 2008-02-26
> **slayer666 said:**
> Why not add the option to choose 32bit or 64bit in wubi?
Wubi can activate the option if a 64bit cpu is present, if not then N/a.

On 64bit machines (includes intel) wubi will use a 64 bit ISO by default (which is a sane thing to do), unless it finds a predownloaded ISO/CD with 32bit OR it is started with "--32bit". If you are picky enough not to want 64bit builds you surely will have no problem starting a program with an extra argument. 

During the testing stage the 64bit ISO did crash in VM (but not on real iron). So we are investigating if it is a problem we should be concerned about, that's why I started the thread asking people with 64bimachines + 64bit ISO to provide feedback.

plethorex problems by the way are unrelated to 64 bit arch.

---

### Post by plethorex on 2008-02-26
> **ago said:**
> Can you pls post the content of /boot/grub/device.map
and of
cat /proc/mounts | grep host
and 
zip of /var/log/installer

Here is 2/3, I'm still not smart enough to figure out how to archive the installer files, I get permission denied and I don't know the exact commands in the terminal to fix it.  Doh!

---

### Post by ago on 2008-02-26
thx 

What do you get from 

cat /proc/mounts | grep host

and can you also post /boot/grub/ment.lst

---

### Post by ago on 2008-02-26
> **plethorex said:**
> Here is 2/3, I'm still not smart enough to figure out how to archive the installer files, I get permission denied and I don't know the exact commands in the terminal to fix it.  Doh!


sudo zip -r logs.zip /var/log

Note your password may also be in the log if you run it the installer in verbose mode, you might want to remove it first from /var/log/installer/debug

---

### Post by plethorex on 2008-02-27
> **ago said:**
> What do you get from 
cat /proc/mounts | grep host

/dev/disk/by-uuid/40C05D9DC05D99CC /host fuseblk rw,nosuid,nodev,user_id=0,group_id=0,allow_other 0 0

Everything else is attached.  Hope this helps with whatever the issue is, feel like I'm a hassle right now, haha.

---

### Post by ago on 2008-02-27
Hmm update-grub fails...

---

### Post by ago on 2008-02-27
Please copy and paste the following code within a Ubuntu terminal (inside a wubi installation).

```

sudo sh -c "
mv /boot/grub/menu.lst /boot/grub/menu.lst.bu
sed -i 's:set -e:exec > /tmp/update-grub.log 2\>\&1 ;set -x:' /usr/sbin/update-grub
yes | update-grub
zip /tmp/update-grub.zip /tmp/update-grub.log
sed -i 's:.*;set -x:set -e:' /usr/sbin/update-grub
mv /boot/grub/menu.lst.bu /boot/grub/menu.lst
"

```

Then attach /tmp/update-grub.zip

---

### Post by plethorex on 2008-02-27
> **ago said:**
> Then attach /tmp/update-grub.zip

And here you go.

---

### Post by ago on 2008-02-27
Thanks a lot, will keep you posted

---

### Post by ago on 2008-02-27
Thanks a lot, will keep you posted

---

### Post by alelondon on 2008-02-28
installed 434 but tried the alpha 5 RELEASE (not daily build) on a toshiba tecra m7 core 2 duo t 5500 nvidia quadro. 
never got to GUI.
if u want more details or me to try ANYTHING just ask.
im ready to help.

---

### Post by ago on 2008-02-28
Hit esc after selecting Ubuntu (during the countdown)
Try selecting safe graphic mode

---

### Post by Dencrypt on 2008-02-28
I am running Kubuntu Hardy Alpha 5. I originally installed Alpha 4 but has updated since. Havn't had any real problems at all. X-server crashed when I updated the kernel to -8 but that was fixed by re-installing Nvidia-drivers and fixxing X-server through recovery mode.

Other than that. I even have 64-bit java and flash working now in ubuntu :)

---

### Post by wingmanjd on 2008-02-28
Hello, I couldn't get Wubi to work after patches were installed.

I used Wubi-8.04-alpha-rev439.exe to install the AMD 64 bit, 15Gb version.  First boot-up went fine (neat desktop, btw).  GDM loaded fine, and I allowed the tracker to index my drive.  I performed updates through synaptic, but libxklavier12 failed to install (it's a documented bug in Hardy, I believe).  I installed wine and compiz config.

On my attempt to reboot, the gdm shut down, but got hung up afterward and didn't reboot.  I cold rebooted and tried to access ubuntu again, but I received lots of tty[various numbers] errors

tty# respawning too fast, stopped

I cold rebooted again since ctrl-alt-del wasn't working and then I received:

Cannot create temp file.

I have not yet tried rev440 (as it was not released at the time of this writeup)

---

### Post by wingmanjd on 2008-02-28
I had that same problem.  The later releases seemed to fix this problem for me.

---

### Post by wingmanjd on 2008-02-28
I just tried rev440.  The previous bug I mentioned did not arise, but I still have the same error on reboot.

init: unable to execute /sbin/getty for tty[various numbers]: Input/Output error
tty[#] stopped
tty[#] respawning too fast, stopped

Any suggestions?

---

### Post by ago on 2008-02-28
Does that happen after upgrading the kernel or regenerating the initrd?
TTY stuff is not the error per se. You may want to boot in verbose mode by hitting esc at boot and editing the boot option "e". Remove "quiet splash"

---

### Post by wingmanjd on 2008-02-28
Unless synaptic is updating the kernel, this is not what is being done.  I'll attempt verbose mode.

---

### Post by nekra on 2008-02-28
AMD 64 with Windows 32 running, with the last Hardy alpha 5 there
seems to be no installation:
After download and install/reboot, going to ubuntu with all 4 boot-options it gives 'error 13' 'Invalid or unsupported executable format'
There is only the download log.

---

### Post by ago on 2008-02-28
Pls try uninstalling and reinstalling wubi 443

---

### Post by plethorex on 2008-02-29
Tried to boot Ubuntu this morning, am now receiving a grub error, menu.lst not found.  Is there a way to reinstall this file (so I can boot Ubuntu) or do I need to reinstall the whole Wubi installation?

Not quite sure what prompted the error, I haven't modified anything since I made the zip files for Ago.

---

### Post by ago on 2008-02-29
The booting menu.lst is in /ubuntu/disks/boot/grub/menu.lst
The one used for installation is in /ubuntu/install/boot/grub/menu.lst this one though is deleted upon succefful installation.

---

### Post by wingmanjd on 2008-02-29
Wubi version:Wubi-8.04-alpha-rev443.exe

Now on update, openoffice.org-hyphenation-en-us fails.

---

### Post by plethorex on 2008-02-29
All 5 menu.lst options fail at boot screen, file not found on each of them.  Gonna just uninstall and wait for the RC, it was worth a shot. :)

---

### Post by wingmanjd on 2008-02-29
I still have the tty errors on bootup after the update.  I guess I'll keep an eye out for new releases as well.  Can't wait!

Thanks for all your help

---

### Post by lond on 2008-02-29
I still can't start ubuntu.
It looks like the virtual ubuntu-disk is corrupt and read only???

wubi 443 - amd64

---

### Post by nekra on 2008-02-29
> **ago said:**
> Pls try uninstalling and reinstalling wubi 443

Tried this a few times, but always the same.  
I noticed 'Grub' in 'Disks' is empty!

---

### Post by ago on 2008-03-01
> **nekra said:**
> Tried this a few times, but always the same.  
I noticed 'Grub' in 'Disks' is empty!

That is only filled during installation
So you should have either /install/boot/grub/menu.lst or disks/boot/grub/menu.lst but not both

---

### Post by nekra on 2008-03-01
> **ago said:**
> That is only filled during installation
So you should have either /install/boot/grub/menu.lst or disks/boot/grub/menu.lst but not both

I downloaded the i386-cd and with the same installer had ubuntu running out of the box in 10 min. (32 bits).

---

### Post by acowboydave on 2008-03-01
Getting an error after a update "unable to execute sbin/getty..see attachment, running Alpha 5..installed using Wubi from the DVD. The problem is only happening when using the 2.6.24-10 kernel..when I drop down to the 2.6.24-8 everything is OK.

---

### Post by alexedwin on 2008-03-02
I am looking at running Ubuntu 7.10 64 bit.

My MB is an ASUS P5P800 - VM
CPU is Intel Pentium D 2.66 ghz
with 2 gig ram

According to the specs I have checked up on I have a 64 bit M/C

Is this correct ?

TIA

Alex

---

### Post by ago on 2008-03-02
> **acowboydave said:**
> Getting an error after a update "unable to execute sbin/getty..see attachment, running Alpha 5..installed using Wubi from the DVD. The problem is only happening when using the 2.6.24-10 kernel..when I drop down to the 2.6.24-8 everything is OK.
Might be a temporary regression in the kernel. Will double check anyway.

---

### Post by acowboydave on 2008-03-02
> **ago said:**
> Might be a temporary regression in the kernel. Will double check anyway.
Hello, thought I would touch base with you, there was a upgrade of the kernel to 2.6.24-11 did a reinstall and saw that, problem fixed at least with my lap. ;-)

---

### Post by Virgilius on 2008-03-03
Ubuntu works fine, but I still have no sound and I have to start or restart Compiz manually every time I switch on my box. I haven't gotten a clue about how to upgrade my kernel though.

---

