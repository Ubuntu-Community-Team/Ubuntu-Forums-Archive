---
title: "Is there a way to make a directory not appear if nothing is mounted to it?"
date: 2012-12-10
forum: General Help
---

### Post by Roasted on 2012-12-10
Simple question here... Let's say /media/storage is your primary target to mount a 1 TB hard drive. Your actual OS is running on an internal drive 80 GB in size. Of course when mounted, anything you dump in /media/storage goes to the 1 TB drive. When not mounted, anything you put in /media/storage effectively goes onto your 80 GB drive, since nothing mounted to /media/storage would make the 80 GB drive be the new home for that directory.

Is there a way to make "storage" simply not appear if nothing is mounted to it, as a clear and obvious way that your 1 TB drive is not mounted?

---

### Post by mcduck on 2012-12-10
Depends on what kind of setup youa re running and what exactly you want to achieve.. 

Anyway, don't mount the drive using fstab or create the mount point, but leave it to the automatic mounting instead. And then set the drive's label to "storage" to make the automount system mount it as "/media/storage". That way the mount point will only exist when the drive is connected and mounted.

---

### Post by Roasted on 2012-12-10
> **mcduck said:**
> Depends on what kind of setup youa re running and what exactly you want to achieve.. 

Anyway, don't mount the drive using fstab or create the mount point, but leave it to the automatic mounting instead. And then set the drive's label to "storage" to make the automount system mount it as "/media/storage". That way the mount point will only exist when the drive is connected and mounted.

I'm glad you brought that up. I never thought of that. In fact, I just conducted a little test here and I'm kind of surprised at the results. I did this because I was in the IRC chat talking to some people about this and they gave me a new idea. Their idea was to rsync the data to one directory lower. In other words, /media/storage is the mount point, but rsync to /media/storage/data instead. That way if the drive in question is missing, "data" should be gone, therefore the sync would fail. That sounds great in theory, but when you actually try it, it's very different.

Keep in mind, all of this is done using rsync as root. I'm using root because I have multiple user accounts to back up, so it was easier for me to create an ssh key pair for root (had to do it manually, since ssh-copy-id requires root login which doesn't exist on Ubuntu) and just run the whole sha-bang as root. In my little experiment though I was using my laptop and a flash drive to simulate the actual situation I'd be applying this to.

Both scenarios were using the same rsync command.
Both scenarios were using root to execute the command.

The command:
> 
rsync -az --delete --progress /home/jason/Desktop/ /media/flashdrive/storage/


If I plug in the flash drive and let it auto mount (the drive is named flashdrive, so it mounts to /media/flashdrive automatically), I can successfully rsync data to it as root. If I unmount the flash drive (right click the icon in the Unity bar and hit eject) and rsync the data as root, it fails, giving me errors. This is good because it won't turn around and fill up my main hard drive which /media/storage would thereby reside on.

If I mount the flash drive via terminal, sudo mount /dev/sdb1 /media/flashdrive, and rsync via root, it works fine. If I unmount the drive via sudo umount /media/flashdrive, then rsync again as root, it actually rsyncs all of the data over, thereby dumping it on my main hard drive.

So you have two scenarios. In one, rsync as root just doesn't care and barges its way in and syncs the data. On the other one, if the system auto mounts the drive, it's as if it doesn't care if you're rsyncing as root. If the directory doesn't exist, it won't auto create it, unlike the other option.

Can anybody shed some light on this?

Thinking about it now, it sounds like it would make more sense to have my drive named accordingly to what I want it to mount as. For example, instead of using fstab to mount the drive as /media/storage, I should name it "storage" and let it auto mount when I plug it in, just as the suggestion above. I'm failing to see what downside there is to this?

---

### Post by HermanAB on 2012-12-10
Yup, you are beginning to see the light.  Name the volume properly and let the DE system automounter handle it, then add an if directory exist statement before the rsync command.

[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)

---

### Post by Roasted on 2012-12-10
> **HermanAB said:**
> Yup, you are beginning to see the light.  Name the volume properly and let the DE system automounter handle it, then add an if directory exist statement before the rsync command.

[http://tldp.org/LDP/abs/html/fto.html](http://tldp.org/LDP/abs/html/fto.html)

I apologize, but looking at that link you provided I'm not entirely sure if I follow exactly how I would formulate the if statement to ensure the drive is mounted... then proceed to the actual rsync...

EDIT - What about this? Looks like it's working.
> 
#!/bin/bash
if [ $(mount | grep -c /media/STORAGE) == 1 ]
then
touch /home/jason/Desktop/HELLOTHISWORKED.txt
else
echo "/media/STORAGE already mounted"
fi


Then I can just whip it up like:

> #!/bin/bash
if [ $(mount | grep -c /media/storage) == 1 ]
then
rsync -az --delete /media/storage/ root@192.168.1.150:/media/NAS/backup/
else
echo insert-whatever-command-to-email-me-subject-RSYNC FAILED
fi


---

### Post by JKyleOKC on 2012-12-10
Try reading "man test" and look at the "-d FILE" option. There's no need to bother with mount and grep to determine whether the directory exists.

---

### Post by Roasted on 2012-12-11
> **JKyleOKC said:**
> Try reading "man test" and look at the "-d FILE" option. There's no need to bother with mount and grep to determine whether the directory exists.

The thread has kind of shifted gears since the start... as I'm now trying to determine if the hard drive mounted to said directory exists. Mostly because one of the two boxes I'm working with is a Raspberry Pi which does not support automatic USB mount, so I'm still going to utilize fstab for that.

---

### Post by JKyleOKC on 2012-12-11
Actually I have my USB devices mounted through fstab rather than through the automounting capabilities, with the "noauto" option so that they don't hold up booting and the "user" option so that they don't require root privileges to be mounted. The "-d" option to "test" could be used with a full path to your mount point on the Pi, and should still show whether the named directory existed, I believe. If the drive wasn't there, I would expect the test to show that it didn't exist -- but this is guesswork, untested...

---

### Post by Cheesemill on 2012-12-11
The way I tend to handle this sort of situation is as follows.

First create your mount point (/mnt/data in this example).
Then with the device *unmounted* create a file in the directory, for example:
touch /mnt/data/unmounted
Now if you need to check whether the drive is mounted or not you can do a quick check to see if the unmounted file exists (it won't be visible once your drive is mounted):
```
if [ -f /mnt/data/unmounted ]
then
  echo "Drive is unmounted"
else
  echo "Drive is mounted"
fi
```

---

### Post by Cheesemill on 2012-12-11
> **JKyleOKC said:**
> I believe. If the drive wasn't there, I would expect the test to show that it didn't exist -- but this is guesswork, untested...

See my post above.

The test you are describing would return the same value whether the drive was mounted or not, the mount point still exists whether or not anything is mounted under it or not.

---

### Post by JKyleOKC on 2012-12-11
Elegant solution, Cheesemill!!!

To explain for the benefit of others who may come across this thread later, here's why it works: If the device is actually mounted to the mount point, the empty file "mounted" is hidden from the system and the "if" test will report that the file doesn't exist. However, if the device is not mounted, then the file will show up to the test action. It's not at all obvious at first glance, and unless you understand that mounting the device hides the original content of the directory looks like nonsense.

I wish I had thought of it!

EDIT: Actually the directory I was suggesting to test for was located only on the external drive, not in the mount point itself, as suggested much earlier in the thread. However your solution is much cleaner...

---

### Post by Roasted on 2012-12-17
I ended up whipping up this script, which is actually braindead easy once you include the mount-detection portion of it as suggested earlier.

> 
#!/bin/bash
if [ $(mount | grep -c /media/storage_II) == 1 ]
then
rsync -a --delete /media/storage/ /media/storage_II/
fi


There's my script for all who's curious.

Line 1 simply ensures that storage_II is mounted. 1 is mounted, and == means that it must equal 1 in order to move on. After that, you have the "then" factor which flows into the actual rsync command. -a keeps the permissions, ownership, timestamps, etc, and --delete makes sure that storage_II isn't holding on to files that storage no longer has.

Overall, this works quite nicely. Very happy with it.

---

