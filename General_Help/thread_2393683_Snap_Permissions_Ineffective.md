---
title: "Snap Permissions Ineffective?"
date: 2018-06-06
forum: General Help
---

### Post by nhaznar on 2018-06-06
Is anyone able to change snap permissions to allow access to external storage (or change any snap permissions for that matter)?

Clicking on 'permissions' in the software center allows access to the snap permissions.    Changing settings here has no effect.  Reentering 'permissions' the settings are returned to default.  Is this a bug or am I not understanding something?

[ATTACH=CONFIG]280006[/ATTACH]

---

### Post by #&amp;thj^% on 2018-06-06
Some snaps don't have permission's to access removable media. :(
this should be possible for some (I have not tried this alot, infact very few tests)
But for myself I look in "/var/snap/(Your snap here) config/config.php"
and make sure the datadirectory is pointing to the right place.
And then Disable the snap with "sudo snap disable <Your Snap here>"
then I connect my removable media/USB/Drive.
Move (or copy) the current data directory to the new location: sudo mv /var/snap/<the snap you want>/common/<the snap you want>/data /media/my/new/data.
Re-enable the snap: sudo snap enable <the snap you want>.
The database and apps are still in /var/snap/<your snap wanted>/current/. I Strongly suggest you leave them there.
I got the Idea from reading: [https://github.com/nextcloud/nextcloud-snap/issues/150#issuecomment-267641192](https://github.com/nextcloud/nextcloud-snap/issues/150#issuecomment-267641192) 
As far as Gimp I have nothing relevant to add for you.

---

### Post by mc4man on 2018-06-06
Not sure what that permissions thing is about, currently useless.
Open a terminal & run
```
sudo snap remove gimp
```
When that's done run
```
sudo snap install gimp --classic
```
You now should be allowed access to external partitions

---

### Post by nhaznar on 2018-06-06
Thanks for the suggestions- I tried both of the above recommendations, unfortunately no luck. 
 
@1fallen- I would like to access more than just one single external... also phones, usb, etc.
@mc4man- installing 'gimp --classic' does not seem to change file access permissions in my case.

I have uninstalled the snaps in question and installed from the repository or flatpak instead.  This has allowed access to external drives.  

Interestingly, using repositories or flatpak in place of snaps seems to work flawlessly.

BTW, the issue is not just with gimp, but also vlc, libreoffice, clementine, and a few others.

---

### Post by deadflowr on 2018-06-06
use the snap interface protocols.

Should be something like
```
sudo snap connect snap-app:removable-media
```

see the snapcraft docs:
[https://docs.snapcraft.io/reference/interfaces]("https://docs.snapcraft.io/reference/interfaces")

I actually did this:
[https://ubuntuforums.org/showthread.php?t=2392357&p=13768771#post13768771]("https://ubuntuforums.org/showthread.php?t=2392357&p=13768771#post13768771")

And those both did what I wanted in terms of adding the ability to access the removable media.
But only those with locations in my /media folder.
I did not see if a manually mounted location worked or not 
(manual being somewhere like /mnt or /srv or anywhere outside the default /media/user folder location.)

---

### Post by mc4man on 2018-06-06
I tried in an small 18.04 test install as snapd has been removed from my using 16.04 & 18.04 installs.
 There using --classic worked, don't know what you're using.
Also in that 18.04 install the snap vlc works fine on external media without the --classic install option
(- noting that in both cases the external media  (usb drives or other internal partitions) must be user mounted or in case of internal not automounted on boot thru fstab.
 i.e. accessed thru /media/username/...

---

### Post by #&amp;thj^% on 2018-06-06
> **mc4man said:**
> I tried in an small 18.04 test install as snapd has been removed from my using 16.04 & 18.04 installs.
 There using --classic worked, don't know what you're using.
Also in that 18.04 install the snap vlc works fine on external media without the --classic install option
(- noting that in both cases the external media  (usb drives or other internal partitions) [B][U]must be user mounted or in case of internal not automounted on boot thru fstab.
 i.e. accessed thru /media/username/.[/U][/B]..

+1 ;)
I also removed snapd (Core) I have no use for this nonsense. (Security might be better IJDK) I just want to do what "I" need, and where "I" need to do things. :) 
For myself XFCE just fits. ;)

---

### Post by nhaznar on 2018-06-06
I'm on 18.04.   The external media was set to automount on startup to /mnt/External.  Once changed to /media/External everything seems to work perfectly.
Thanks- You folks rock!

---

### Post by mc4man on 2018-06-06
> **1fallen said:**
> +1 ;)
I also removed snapd (Core) I have no use for this nonsense. (Security might be better IJDK) I just want to do what "I" need, and where "I" need to do things. :) 
For myself XFCE just fits. ;)
The security is better but more like a self-fulfilling prophecy. it's possible to have snaps using precomplied binaries with prop source code that's not available & with no viewable build logs. So in that case the sandboxing security is needed.
Prior to snaps I can't recollect a single case of ubuntu/debian repo or even ppa's as having malicious software packages.

---

### Post by #&amp;thj^% on 2018-06-06
> **mc4man said:**
> The security is better but more like a self-fulfilling prophecy. it's possible to have snaps using precomplied binaries with prop source code that's not available & with no viewable build logs. So in that case the sandboxing security is needed.
**Prior to snaps I can't recollect a single case of ubuntu/debian repo or even ppa's as having malicious software packages**.

Could not agree more. I felt like appamor was sufficient and with the ability to run sandboxed applications was secure enough for "my" usage.
Apologizes for straying a bit Off Topic, but good to see others feel the same in this matter. :)
Kind Regards

---

### Post by hrvbid on 2018-12-26
As far to see, snap apps have access to the home dir of the user. But snap also is able to access files outsite home if the user is the owner of the file. It appears that snap does not consider group permissions. Even a user has rw access to a file because of the group membership, the permission error arises. Not really suitable at all.

---

