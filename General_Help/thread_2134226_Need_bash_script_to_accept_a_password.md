---
title: "Need bash script to accept a password?"
date: 2013-04-10
forum: General Help
---

### Post by Ice On Fire on 2013-04-10
Hi guys, 

So, I have the following task:

I need to run a script when the machine starts up - which one of the commands is: 

```
 sudo umount /dev/sdb1 
``` 

As you can see - I need temp root for this command. (And others in the script) 

Storing the password in the script seems like a massive security hole / issue. I was wondering if there is another way around this issue?

Thanks guys!

---

### Post by ajgreeny on 2013-04-10
I am sure there are other ways, but one possible way is to add that command, minus the sudo prefix, as a separate line, to **/etc/rc.local** just above the "exit 0" line.  As that file is executed as root at boot time it will run that command without a problem.

Can I ask why you need or want to do this in the first place?  There may be other or better ways to deal with the problem.

---

### Post by rnerwein on 2013-04-10
> **Ice On Fire said:**
> Hi guys, 

So, I have the following task:

I need to run a script when the machine starts up - which one of the commands is: 

```
 sudo umount /dev/sdb1 
``` 

As you can see - I need temp root for this command. (And others in the script) 

Storing the password in the script seems like a massive security hole / issue. I was wondering if there is another way around this issue?

Thanks guys!
hi
if you umount the device on startup why not managing with the /etc/fstab. look for the line with /dev/sdb1 and add the option "[COLOR=#ff0000]noauto[/COLOR]"
(e.g.: UUID=blablablu /anywhere extN defaults,noauto ......).
if you want to mount the partition later type: sudo mount /anywhere
ciao

---

### Post by Ice On Fire on 2013-04-11
Hi guys, 

I'm new-ish to Linux and I thought a script would be the best way to get the results I want. 

Let me explain what I need to do - maybe there is a much easier way to accomplish this? 

I have a media centre running Ubuntu 12.10. There are three extra internal drives with my media on it. I also, use Plex media Server to stream to content to my Xbox 360. 

The problem: 

Upon every reboot, I have to do this: 

Manually mount all three drives by clicking their icons in the Unity bar along the left (Haven't had a chance to change DE to Gnome) 
Then I need to unmount these drives.  

Then, I open terminal and use the following commands: 

```
 
sudo mount /dev/sdb1 /home/media/Desktop/One 
sudo mount /dev/sdc1 /home/media/Desktop/Two 
sudo mount /dev/sdd1 /home/media/Desktop/Three 

``` 

The reason for this is due to the drives being in NTFS format. Plex cannot access these drives with the correct permissions as they're NTFS. So, instead of coping all data off and reformatting to Ext4 - I do it this way. I have no way to copy that amount of data off the drive. 

After the drives have been mounted to the folders - Plex works just fine. 

The reason I have to mount them and then unmount them is I tried manually mounting them once via Terminal like so: 

```
sudo mount /dev/sdb1 /home/media/Desktop/One 
``` 

However it complains it does not know sdb1 

if I do: 

```
 df-h 
``` 

I mount them using the Unity bar icons - these drives don't show up 

There must be an easier way to do this? 

Sorry if this is really n00b - I am trying to learn as much as I can as I enjoy Linux. 

Thanks all!

---

### Post by Ice On Fire on 2013-04-11
Any ideas? 

Thanks guys

---

### Post by steeldriver on 2013-04-11
> **Ice On Fire said:**
> Any ideas? 

You should be able to add the devices to your /etc/fstab file so that they get mounted to your chosen mount points on boot - instead of automounted in /media/ which is likely what's happening now (which is why you need to keep unmounting / remounting them)

---

### Post by Ice On Fire on 2013-04-11
Okay, let me look into that. 

Does the drive names ever change upon boot up? 

For example - will my 500GB hard drive always show up as /dev/sdb1 - unless I change the SATA port?

---

### Post by steeldriver on 2013-04-11
yes it's best to use the UUID rather than the /dev/sdX name for exactly that reason -there's a walkthrough here with examples

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by pfeiffep on 2013-04-11
I'm not a prolific coder, but during my experiences with Sun - Unix I seem to remember that we used [COLOR=#a52a2a]*expect *[/COLOR]in scripts, you might install it and try it out
```
sudo apt-get install expect
```

---

### Post by nothingspecial on 2013-04-11
> **Ice On Fire said:**
>  I have no way to copy that amount of data off the drive. 



If you do not have a copy of that data then one day you will loose it, but anyway, yes fstab is the way to go either using uuid or labels

---

### Post by Ice On Fire on 2013-04-11
> **steeldriver said:**
> yes it's best to use the UUID rather than the /dev/sdX name for exactly that reason -there's a walkthrough here with examples

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Awesome, thanks for the link! 

> **pfeiffep said:**
> I'm not a prolific coder, but during my experiences with Sun - Unix I seem to remember that we used [COLOR=#a52a2a]*expect *[/COLOR]in scripts, you might install it and try it out
```
sudo apt-get install expect
```

I will keep that in mind, thanks! 

> **nothingspecial said:**
> If you do not have a copy of that data then one day you will loose it, but anyway, yes fstab is the way to go either using uuid or labels

And you're correct - there is no backup of me media data at this time. However, it's not critical data. Still, a valid point. 

Thanks guys. 

Will look at this tonight.

---

### Post by Ice On Fire on 2013-04-20
So this is what I did:

Made a mount point for each drive:

```
 sudo mkdir /mtn/drive_label 
``` 

Then I got the UUID's of each drive

```
 sudo blkid 
``` 

Then I added this info into /etc/fstab/ 

Rebooted and happy days - works fine. Also, Plex sees the folders without any hassles!

Thanks for all the help gents, much appreciated!

---

