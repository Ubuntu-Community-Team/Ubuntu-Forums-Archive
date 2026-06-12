---
title: "Amarok and SSH Help"
date: 2007-08-18
forum: General Help
---

### Post by RideP2 on 2007-08-18
I have to Ubuntu machines (7.04) in my network, one of them is my main box, with a big hard drive, and all my music. The other is an old laptop with a little 5G drive. I'd like to be able to have my main computers music folder be accesible in Amarok. Like it was a local folder. 

I've already got my main box accesible from my laptop with SSH. Any help on this would be apreciated.

---

### Post by dfreer on 2007-08-18
If you can reach it with SSH, you can mount the remote filesystem using sshfs and fuse. This will help:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_remote_folders_into_local_Ubuntu_machine_.28sshfs.29)
The main thing to note here is that when you get to this command:
```
sudo adduser your_user_name fuse
```
**Replace** the *your_user_name* with your actual user name, that you use to login with.

Hope this helps!

---

### Post by RideP2 on 2007-08-18
Thanks dfreer, I'll check that link out.

---

### Post by RideP2 on 2007-08-18
The name I use to log into with the laptop? Or the remote machine?

EDIT: I got it working. Now to see if I can get Amarok to work with this.

Oh one question, if I make changes to the folder on the main computer, will it get updated on my laptop automaticly?

---

### Post by dfreer on 2007-08-18
Yes, amarok has a feature to automatically watch the folders recursively for changes. This is a good *and* bad thing, at least in my case.

If the remote filesystem is not mounted, amarok will assume all of your music was deleted, and will remove all of it from your media library. And if you have ~30GB's of music like me, you'll have to wait for amarok to rescan your entire collection before you can use it normally again.

Also, I do not believe Amarok will always write to the actual mp3 tag itself, like let's say when you change the album info. If it doesn't, then you will not see these changes reflected on your second machine (which is why I always use easytag to change my ID3 tags).

---

### Post by RideP2 on 2007-08-18
Alright, but what I meant was will the sshfs automaticly update itself. And will it be mounted automaticly after a reboot/login?

---

### Post by dfreer on 2007-08-19
basically, sshfs is the same as an ssh session. So if you change files on the server, and then refresh the folder on the client, you will see the files change. Vice versa as well.

With this method, it will *not* be mounted automatically at reboot/login. There's several things you can do here:

Mount at login, by simply adding the command to your System > Preferences > Sessions.
Mount at boottime, by editing your /etc/fstab file. You might want to google for a guide to do this.

Myself, I like to create a bash script that will handle mounting/unmounting the SSH drive for me.

---

### Post by RideP2 on 2007-08-19
Yeah, I think I'd like to make a script too. 

Do you think it would be hard to make a little script that would mount the drive, then open Amarok. Then when Amarok closes, unmount the drive.

---

### Post by dfreer on 2007-08-19
I don't think it would be too hard, you could either create a desktop icon, or you could even move /usr/bin/amarok, and put the script there, so that everytime amarok is launched it would mount the remote filesystem. Figuring out when amarok closes, however, so that it can unmount the FS might be a bit difficult. I'm pretty sure it can be done, just not sure how ;)

---

### Post by itsJim on 2007-09-03
Trust me, don't use sshfs for this.  sshfs may be good for some things, but accessing and playing your music collection from an sshfs mount is not one of them. I have had nothing but problems with accessing my music via sshfs.

If you want to have a painfree experience do yourself a favor and install mt-daapd:

sudo apt-get install mt-daapd

Also, I'm not sure if it was required but I did install all the recommended and suggested packages as well.

After installing it you will be able to play your collection in any player that supports daap. I use Rhythmbox, but there a bunch of other players that will support it, including win32 applications such as winamp and itunes.

I just learned about this program the other day and I wish I would've known about it before because it would have saved me hours worth of troubles in getting sshfs setup to my liking.

After installing it don't forget to modify the config file in /etc/mtd-daapd.conf

---

### Post by dfreer on 2007-09-03
I cannot seem to find any information on mt**d**-daapd, but I did find some on mt-daapd:
[http://packages.ubuntu.com/feisty/sound/mt-daapd](http://packages.ubuntu.com/feisty/sound/mt-daapd)
[http://www.fireflymediaserver.org/](http://www.fireflymediaserver.org/)

Indeed, it may work better to run a music sharing server instead of using ssh (I've actually been using a samba share myself), so that you don't have to mount the remote filesystem. However, does mt-daap allow you to modify the ID3 tags and add/remove music on the server from the remote client? If so, then I think it would be worth checking out. Otherwise, I'm sticking with Samba.

---

### Post by itsJim on 2007-09-03
> **dfreer said:**
> I cannot seem to find any information on mt**d**-daapd, but I did find some on mt-daapd:
[http://packages.ubuntu.com/feisty/sound/mt-daapd](http://packages.ubuntu.com/feisty/sound/mt-daapd)
[http://www.fireflymediaserver.org/](http://www.fireflymediaserver.org/)

Indeed, it may work better to run a music sharing server instead of using ssh (I've actually been using a samba share myself), so that you don't have to mount the remote filesystem. However, does mt-daap allow you to modify the ID3 tags and add/remove music on the server from the remote client? If so, then I think it would be worth checking out. Otherwise, I'm sticking with Samba.

Sorry about that, updated my post.

I think it depends on the client as far as updating the ID3 tags. I use EasyTAG on the sshfs share that I still have setup, but I would imagine that it depends on the client you are using to update the tags.

---

