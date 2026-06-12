---
title: "Trying to recover data from Access-Your-Private-Data.desktop - can't get into Unity"
date: 2014-11-29
forum: General Help
---

### Post by g-me-i on 2014-11-29
[COLOR=#333333][FONT=UbuntuRegular]I have 3.5 year old Lenovo Thinkpad w/ an i5 running Windows 7 and previously Ubuntu 10.04, each on it's own 50/50 partition of a 500GB HDD. I rarely use this laptop because the battery is pretty much shot and the plug was bent on a falling off an ottoman accident so it has to be rigged in just the right way to register it is plugged in. I'm planning on reformatting it completely but a long time ago I transferred like 200GB of media onto the Ubuntu partition when freeing up space on an external while traveling and I'd like to try to recover whatever is on there, though it isn't the end of the world if I lose it.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]DISCLAIMER: I am a Ubuntu novice. Used it at work for almost a year but never got too far into learning how to operate from the command line. Was mainly running Salesforce from the browser.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]The first issue I encounter was not remembering the password (or just inputting it incorrectly because for some reason there was a lag and necessity to hold down each key to get it to register - only on the login screen, not in the shell). I reset the password in the shell to fix this.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After I attempt to login, I get the error "Could not update ICEauthority file /home/username/.ICEauthority." The screen then proceeds to just be the wallpaper with no GUI. I was wondering if there was an issue with Unity so I tried to login with the 2D interface, recover mode, etc. I didn't make any progress here.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Next I tried to use Ext2explore to access the files from my Windows partition, but I wasn't able to locate the media. I copied the whole partition and it was only 3GB so I was missing something there.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Then I tried to see if I could upgrade from a bootable USB. I had just set up Ubuntu on a new desktop I purchased for RoR development so I had it handy. There was not the option to upgrade, only install alongside the two OSs.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I then looked into upgrading from the shell. I kept running into 404 errors when running sudo get-apt update and I discovered I needed to change all the urls in the source list that had outdated urls to old-releases.etc. I did this through nano and proceeded to be able to upgrade. I upgraded three or four times (can't recall, was doing all sorts of multitasking yesterday) to finally get it to 14.04. Each time I upgraded, I tried to login afterwards, but I kept getting stuck in a login loop and could only login via the shell.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Before, during, and after these upgrades, I tried ecryptfs-recover-private both from the live USB and from the shell on the actual partition. I was not able to remember the key and I wasn't able to unwrap the key successfully either when I tried that. I've tried copying my home/username directory as well as tinkering with the .Xauthority troubleshooting. I also installed Cinnamon and tried to access my desktop through that, but I am back to "Could not update ICEauthority file /home/username/.ICEauthority."
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Instead of researching question after question while going back and forth between other tasks, I'm looking for some advice on how to tackle this issue straightforward. Thanks for reading![/FONT][/COLOR]

---

### Post by oldfred on 2014-11-29
If it was just the login password, you could reset that. But if used for encryption then you have to have the correct passphrase. That is the entire purpose of encryption is to prevent anyone from accessing data that does not know passphrase. 
Unless NSA wants to see your data, and it is willing to dedicate a super computer for a couple of days, there in not much we can suggest. 
With Encryption you have to have very good backups as any file corruption, forgotten passwords etc will prevent access to the encrypted data.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

