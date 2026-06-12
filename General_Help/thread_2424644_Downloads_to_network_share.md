---
title: "Downloads to network share"
date: 2019-08-12
forum: General Help
---

### Post by digitalknight on 2019-08-12
[COLOR=#333333][FONT=&quot]I have everything working very nicely on Linux but the last piece of the puzzle is downloading to a network share. Frostwire is my preferred app but I have tried 2 others (Deluge, Transmission)  and they also do not let me download to a network share. I spoke with Frostwire and they said:[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]"that's so weird. Maybe you should just make a symlink of the network drive folder to a place that does get listed on FrostWire and set that as the default save folder."[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]So I did that but it still does not show up in Frostwire when I go looking for it? [/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Perhaps I am not making the symlink correctly? I used the "ctl-shift" method. Or perhaps I am not using it correctly? I copied it to the download folder in Frostwire.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Hopefully I can get this last piece of the puzzle resolved as I hate switching back to Win10 just to download something to my NAS drives.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Thank for any pointers,

-DK
[/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-08-12
I have a symlink from /home/username/Downloads on my central server to /home/username on my client machines.  Everything I download goes to the shared directory.  Perhaps it's a permissions problem?

I have no idea what the "ctl-shift" method is since I use the terminal for all such tasks.  The /home directory on my server is mounted at /media/servername on the client in /etc/fstab:

```
server:/home            /media/server   nfs     defaults        0 0
```

Then on the client machine I did

```

cd /home/username
ln -s /media/server/username/Downloads

```

to construct a symlink from my Downloads directory on the server to the home directory on my client.

Notice that I'm using [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo") to share the server's files.  If you're trying to do this with Windows networking, all bets are off, since Windows filesystems don't support *nix symlinks.  You'd need to export the directories on your NAS with NFS.

Everything works flawlessly with this system including downloads from Firefox and from Transmission.

---

### Post by Morbius1 on 2019-08-12
I don't understand the nature of the question.

Which is probably why I don't understand Frostwire's suggestion of a symlink.

If this is a CIFS mount of the NAS share you can mount it anywhere you want to mount it so a symlink to someplace else isn't necessary.

If you are mounting the share through your file manager that may be an issue for this frostwire thingy you mention if it is not "gvfs aware". Or you don't realize that there is a real mount point.

So which is it? File manager mount or CIFS mount?

If you mount the share through your file manager run this command in a terminal after mounting and post the output:
```
ls -al /run/user/$UID/gvfs
```

---

### Post by digitalknight on 2019-08-12
ls -al /run/user/$UID/gvfs
total 0
dr-x------ 4 digitalknight digitalknight   0 Aug 12 10:12  .
drwx------ 9 digitalknight digitalknight 220 Aug 12 10:12  ..
drwx------ 1 digitalknight digitalknight   0 Aug 10 14:57 'smb-share:server=marksnas,share=movies'
drwx------ 1 digitalknight digitalknight   0 Jul  5 16:59 'smb-share:server=tp-share,share=sda1'

---

### Post by TheFu on 2019-08-13
If you use NFS, 99.99999999% of programs won't know that it isn't local storage.
I avoid using CIFS/Samba/gvfs mounts whenever possible, which is usually easy unless Windows is involved.

---

### Post by digitalknight on 2019-08-13
The storage devices are a WD My Cloud 2TB with a 5TB Seagate USB drive attached to it and the other is a 3TB WD USB drive attached the USB port of the TP-Link router.

---

### Post by SeijiSensei on 2019-08-13
If you must use Windows-style sharing, then I recommend Morbius's suggestion.  Mount the remote filesystem directly as /home/username/Downloads.  You'll need to do this in [/etc/fstab]("https://wiki.ubuntu.com/MountWindowsSharesPermanently"), I suspect.

Be sure to back up everything in the Downloads directory first, then delete all the files before mounting with CIFS.

---

### Post by TheFu on 2019-08-13
> **digitalknight said:**
> The storage devices are a WD My Cloud 2TB with a 5TB Seagate USB drive attached to it and the other is a 3TB WD USB drive attached the USB port of the TP-Link router.

Please be very careful using those devices for storage sharing. Both have had firmware issues that made storage available over the internet to unauthorized devices.
[https://thehackernews.com/2018/09/wd-my-cloud-nas-hacking.html](https://thehackernews.com/2018/09/wd-my-cloud-nas-hacking.html)
[https://nakedsecurity.sophos.com/2019/04/02/tp-link-router-zero-day-that-offers-your-network-up-to-hackers/](https://nakedsecurity.sophos.com/2019/04/02/tp-link-router-zero-day-that-offers-your-network-up-to-hackers/)
Different variants of these devices have also been found with security issues, my abandoned tp-link router is included, so I had to pull it.

---

### Post by digitalknight on 2019-08-14
thanks, not to concerned as my internet down here in Colombia is slower than a snail and if they want to try and wait for weeks or months for one of my movies to upload to them all the more power to them... but I think they will find much fast sources... :-)

---

### Post by digitalknight on 2019-08-14
I will give it a shot and see what I can get working... the WD My cloud does also have SSH and FTP access which I could enable if that might make my life easier...

---

### Post by Morbius1 on 2019-08-15
I can't speak to the Frostwire thing but it seems I have Transmission installed on a test box here and it really doesn't like a gvfs mounted ( mounted through the file manager ) share.

So I created a mount point:
```
sudo mkdir /mnt/srv
```
And [highlight]temporarily[/highlight] mounted the share to that folder:
```
sudo mount -t cifs //ubsrv1804.local/public /mnt/srv -o guest,uid=1000,nounix
```
Changed the default download folder in transmission to that folder and it all seems to work:
[ATTACH=CONFIG]283808[/ATTACH]

[ATTACH=CONFIG]283809[/ATTACH]

Based on this:
>  drwx------ 1 digitalknight digitalknight   0 Aug 10 14:57 'smb-share:server=marksnas,share=movies'
Your temporary mount would look something like this:
```
sudo mount -t cifs //marksnas/movies /mnt/srv -o guest,uid=digitalknight,nounix
```

Notes: Depending on the particulars of your network you:

** may have to replace marksnas with the ip address of the nas or if it is designed to work with MacOS the mDNS name ( marksnas.local ).

** If the nas requires credentials replace guest with those credentails: 
```
sudo mount -t cifs //marksnas/movies /mnt/srv -o username=nas-user-name,password=nas-user-password,uid=digitalknight,nounix
```

One other thing. Based on my attempts to help folks using the WD My cloud you are going to have to dumb down the smb version a bit by adding vers=1.0 to the list of options:
```
sudo mount -t cifs //marksnas/movies /mnt/srv -o  username=nas-user-name,password=nas-user-password,uid=digitalknight,nounix,vers=1.0
```
And maybe the security level by adding [highlight]sec=ntlm[/highlight] to the list of options.

---

### Post by digitalknight on 2019-08-15
Thank you! That actually worked great for the WD My Cloud! I think I need to change how I am sharing the drive on the TP router though as it would not work. I think I have to share individual folders on it for it to work instead of the entire drive which shows as "sda1"

---

### Post by digitalknight on 2019-08-16
Is there a way to get the mount to save after reboots?

---

### Post by Morbius1 on 2019-08-16
I don't know which iteration of the mounts I posed about you used so I will use the most complicated one as an example:
> sudo mount -t cifs //marksnas/movies /mnt/srv -o  username=nas-user-name,password=nas-user-password,uid=digitalknight,nounix,vers=1.0
To make this mount at boot time:

*** Edit /etc/fstab

*** And at the bottom of the file add this expression:
```
//marksnas/movies /mnt/srv cifs username=nas-user-name,password=nas-user-password,uid=digitalknight,nounix,vers=1.0,noauto,x-systemd.automount 0 0
```

*** Unmount the share if it is mounted:
```
sudo umount /mnt/srv
```

** Then do the systemd 3-step:
```
sudo systemctl daemon-reload
```
```
sudo systemctl restart remote-fs-target
```
[COLOR=#0000cd]**EDIT**: Made a typo there - sorry. It should have been:[/COLOR]
```
sudo systemctl restart remote-fs.target
```
```
sudo systemctl restart /mnt/srv
```

Then check to see if it mounted correctly in your file manager..

If it does it should mount that way at boot time.

---

