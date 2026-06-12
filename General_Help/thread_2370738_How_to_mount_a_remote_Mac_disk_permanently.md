---
title: "How to mount a remote Mac disk permanently"
date: 2017-09-06
forum: General Help
---

### Post by James Wilde on 2017-09-06
I'm running Ubuntu-mate v 16.04.04 and I have a Mac running Sierra with a usb disk formatted as exfat.  I'd like to be able to permanently and automatically mount the remote usb disk on my linux box, and I'm having more than I think is my share of problems.  Searching in here has not generated any clues.  Perhaps I'm not using the right search criteria.

Thanks in advance for any help.

---

### Post by ajgreeny on 2017-09-06
You will need to install the **exfat-utils** and **exfat-fuse **packages, I think, to be able to mount them.

---

### Post by Morbius1 on 2017-09-06
Are you are trying to automount a USB storage device attached to the Mac from Ubuntu? Or are you trying to mount the USB device on Ubuntu once you moved it from the Mac to Ubuntu?

If this is a network question it's something I've never tried before so I just did this in my own network. I'm assuming that you are using Samba / SMB / CIFS since that is the default file sharing mechanism on both machines. This is what I did on Xubuntu 16.04:

[1] On the Mac my USB disk mounts to /Volumes/ExFat so I added that to the "Sharing" list on macOS.

On Xubuntu:

[2]  I created a mount point:
```
sudo mkdir /media/MacExFat
```
[3] I added this line to the end of /etc/fstab:
```
//dmbp.local/ExFat /media/MacExFat cifs username=smbuser,password=smbuserpw,uid=1000,noauto,nounix,user 0 0
```
[COLOR=#0000cd][I]dmbp is the mac host name.
[/I][/COLOR]
[4] I always check to see if a package is present on Linux machines - it usually is but ...
```
sudo apt install cifs-utils
```
On Xubuntu an Icon appears on the desktop as soon as I save fstab labelled MacExFat. Double click on that and I can access the share. It will also show up on the side panel of my file manager which I can also click on to mount the share. I can read and write to the share / usb device from Xubuntu.

Now I purposely added the noauto and user options and purposely made the mount point under media so that I as an ordinary user could mount this share from my desktop or from my file manager. You could remove both options and have it mount automatically but everything has to be working to pull that off: The mac has to be running, the network stack on the Ubuntu machine must be running before the boot process runs fstab, etc ...

---

### Post by James Wilde on 2017-09-08
Another comment, Morbius1:

Hi Morbius1 and thanks again for your very full reply to my question on mounting a Mac disk on linux. I have one follow-up question. In your line in stab you refer to [COLOR=#000000][FONT=Ubuntu Mono]username=smbuser,password=smbuserpw.[/FONT][/COLOR]

As far as I am aware, Macs don't concern themselves with samba, so I'm wondering which samba user and password you are referring to. Is this just someone who has access to the Mac? Maybe my own account on there?

Thanks in advance

James

---

### Post by James Wilde on 2017-09-08
Ah, I see my first comment didn't make it as I had been logged out!  It was merely a thanks for your reply, and apologies for the delay before I commented.  I'm trying to recover two computers which have gone belly-up!

---

### Post by Morbius1 on 2017-09-08
> **James Wilde said:**
> As far as I am aware, Macs don't concern themselves with samba, so I'm wondering which samba user and password you are referring to. Is this just someone who has access to the Mac? Maybe my own account on there?
The default file sharing mechanism in macOS since Mavericks has been Samba - what macOS calls SMB. If you go to **System Preferences > Sharing > File Sharing > Options **at the top of the box you will see "***Share files and folders using SMB***" as the first choice**. **I assumed that was what you are using.

In my example smbuser and smbuserpw can be your Mac user name and password.  I actually create the smbuser user on all my systems - Windows, Linux, macOS as a kind of guest user. I should have explained that better.

---

### Post by James Wilde on 2017-09-18
Once again I have to apologise for the long delay.  I have a home set-up involving my Mac Mini (where the usb disk is mounted), my Ubuntu-Mate, my wife's Windows 10 box (suck) and her work computer which is also a Mac laptop.  Additionally we have been having great problems which resolved themselves into a problem with the router, which had to be reset and re-configured.  Now everything is working more or less!

Another change:  I emptied the exfat disk and reformatted it as hfsplus journaled, intending that the Mac will have to handle the journaling part.  And strangely I had not noticed that the Mac could handle smb out of the box, so my attempts to mount the disk partition from the Mac usb drive on my Ubuntu-Mate machine have been done with afp.  So now I will try again with smb.

Yippee!  I created a folder on the Mac usb disk partition, then made a line in /etc/fstab like yours, created a folder to mount it on, /home/james/Common-R, then ran 'sudo mount //new-mini.local/Common' and the command found the entry in my fstab and mounted the disk where I want it.  I've also tested that I can write to the disk from the Ubuntu-Mate machine, and that works, too.  I'm as happy as a pig in muck, as they used to say a long time ago when I was young.

Thanks Morbius1.

---

