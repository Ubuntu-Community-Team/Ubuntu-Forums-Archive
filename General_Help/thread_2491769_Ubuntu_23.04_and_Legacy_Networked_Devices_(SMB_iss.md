---
title: "Ubuntu 23.04 and Legacy Networked Devices (SMB issue?)"
date: 2023-10-19
forum: General Help
---

### Post by akmartinez12 on 2023-10-19
Hello everyone,

Forgive me if this has been answered but I can't seem to find a specific fix for my situation and I've tried a few.

I'm relatively new still so I may need some specific instructions.

I'm using Ubuntu 23.04.

I have an Epson WorkForce WF-3540 multi function device.  I scan my documents and they get stored onto a locally installed memory card.
In Windows I can browse my local network and connect to the MFD memory card and copy/move the files down to my local system.

I converted to Linux and make it my main driver now.

I can't seem to connect to the MFD and access the memory card.  When I go to the Files program I can see the "EPSON WF-3540 Series" device listed and when I click on it I receive the following message after a while:

Opening "epson0fc3bb.local (smb)".
You can click cancel...

then

Unable to access location
Failed to retrieve share list from server:  Connection timed out

I can see the device on the network from my Windows systems and access the memory card.

I tried to install smbclient and edit the /etc/samba/smb.conf file to include "client min protocol = NT1" just under the [GLOBAL] heading section, restarted the system and it still did not work.

I also tried to connect with smb://ipaddress and it  still did not work.

Any help would be appreciated or even if there is another document to refer to and try I can.  I'm just afraid of mucking up the smb.conf file that it just won't work.  I did make a back up of it.

---

### Post by ap10707 on 2023-10-19
Hello!

I'd say start with the following:

_**Update all the necessary packages:**_

```
sudo apt update
sudo apt install cifs-utils smbclient
```
_**Check your SMB version:**_

You mentioned that you have set the client minimum protocol to NT1. Modern devices may require a higher version of SMB. Try using SMB2 or SMB3 by modifying the /etc/samba/smb.conf file like so:
```
client min protocol = SMB2

OR

client min protocol = SMB3

```
[U][B]Restart your samba services after making the changes:
[/B][/U]
```
sudo service smbd restart
sudo service nmbd restart
```
_**Test your connection to see if you are good post changes:**_

```
smbclient -L //ipaddress -U username
```

If you are still having issues, check and see if the firewall (ufw) may be causing the issue

```
sudo ufw disable
```
If that works, add inbound/outbound rules to ufw for your SMB

_**If all else fails, you can mount the shares manually:**_

```
sudo mount -t cifs -o username=your_username,password=your_password //ipaddress/share /path/to/local/folder
```

I absolutely do not recommend manually mounting shares with cleartext credentials. You can do it as a test, but if the connection is successful, modify by storing your creds in fstab so that it will AutoConnect on each reboot for you:

```
_**sudo (nano or vi) the etc/fstab file and enter the following inside the file:**_

```
//x.x.x.x/myshare /mnt/myshare cifs credentials=/home/your_username/smb-credentials.txt 0 0
```

Hope this helps! This was always tricky for me too when I was new to Linux. It always sounds like someone speaking latin.

---

### Post by TheFu on 2023-10-19
> **ap10707 said:**
>  
[U][B]Restart your samba services after making the changes:
[/B][/U]
```
sudo service smbd restart
sudo service nmbd restart
```


This is useless for client access issues.  The samba.conf file oddly is used for the min client setting, but nothing else. The samba service/server if it exists isn't involved at all with linux as the client.

23.04 support ends in January, so you'll need to move to 23.10 before the end of this year. Just FYI.  And support for 23.10 ends in June, so you'll want to move to 22.04, which is an LTS with at least 3 yrs of support before June. People new to Ubuntu don't always know the support periods are so very short for non-LTS releases.  Don't wait until after support ends to migrate. It becomes harder then.

23.10 is really new now. About 2 weeks since release, so maybe wait another month for any huge issues to be handled before migration.

I know nothing about connecting to a printer/scanner to get stuff of it.  Is there no method that will write to a USB flash drive or SDHC card when connected instead?  My next scanner will NOT require any computer to be connected to work. Scanning is still a dark art for some hardware + OS configurations, I'm sad to say.  I know they are working on Driverless Scanning like they solved driverless printing about a decade ago, but the industry hasn't all caught up.

---

### Post by MAFoElffen on 2023-10-19
@ap10707 --

Welcome to the Forum. Since you are new. 

You probably have not read the posting guidelines, because you have overlooked a Forum policy of posting all commands and raw output "within CODE Tags".

Please go back and edit your post to reformat that and add code tags, by using "Go Advance" where it will retsart the editor in the Advanced Editor, Selct the commands, then select the "#" Icon to wrap the selected text within CODE Tags...

WQE would appreciate your help in correcting your post.

---

### Post by akmartinez12 on 2023-10-20
This particular MFD has both a USB and SD card option and I do scan to the memory card but wanted the convenience of just connecting to it via the network and retrieving the data instead of removing the card, inserting it into another USB card reader and replacing it onto the scanner when done.

I was using 22.04LTS and decided to give 23.04 a try and so far I like it.  While this is most likely a separate topic/issue I thought I should be able to upgrade from 23.04 to 23.10 on the fly.  So far when I check for updates through the Software App it says I'm up to date.  Is there a specific way I need to update to 23.10 on top of 23.04?  Can I just download 23.10 and run the installer and have it install on top of 23.10 retaining the current settings from my 23.04 install?

---

### Post by akmartinez12 on 2023-10-20
My apologies, I'll review the guidelines and do my best to correct the issue as soon as possible.

---

### Post by akmartinez12 on 2023-10-20
I will review your suggestions/instructions and follow them and update as soon as I can.

Thanks!!!  I appreciate it!

---

### Post by TheFu on 2023-10-21
It would really help if you quote a bit of the post your posts are responding to, so people can follow along.

---

