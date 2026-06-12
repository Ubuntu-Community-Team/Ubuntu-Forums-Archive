---
title: "sandisk sansa e260 and banshee"
date: 2008-06-23
forum: General Help
---

### Post by trmentry on 2008-06-23
I just picked up a Sandisk Sansa e260.  I set it to MSC mode and connect it to my laptop and Ubuntu sees it and starts up Rythmbox and I can see the files on it.  

I can browse it like a flash drive as well.


The problem is I would like to use Banshee, and when I exit Rythmbox and start up Banshee, the Sansa will go disconnected and icon on desktop to use like flash disk will go away as well.

banshee will then complain about MTP.  

I have to disconnect the sansa and reconenct it to see it again.  

Any ideas?

I'm on 8.04.

---

### Post by fallingleaf on 2008-06-23
I found this: [http://www.silwenae.org/blog/?p=604](http://www.silwenae.org/blog/?p=604)
> Do you have a Digital Audio Player (DAP) / MP3 player that is a USB mass storage device that isn’t recognized in Banshee?

Check out the Banshee DAP Guide and follow this how-to:

    Alternatively or in addition to the above step, you can have Banshee recognize a USB drive as an audio device by placing a file called .is_audio_player in the device’s top-level directory (eg /media/IAUDIO/). If you leave it blank, Banshee will use default values for handling the device. If your device puts its music in particular folders, requires music be placed in folders of only a certain depth (eg only one folder deep), or handles formats other than or in addition to MP3, you can enter key=value pairs into the .is_audio_player file, eg

    audio_folders=MUSIC/,RECORDINGS/
    folder_depth=2
    output_formats=application/ogg,audio/x-ms-wma,audio/mpeg

    Only those three keys are currently usable. Note they are the same as the keys in the HAL specification (linked above) without the portable_audio_player. prefix.

It worked once after I followed those instructions, but hasn't worked again.  I have a Sansa e250 with Rockbox installed.

---

### Post by trmentry on 2008-06-23
> **fallingleaf said:**
> I found this: [http://www.silwenae.org/blog/?p=604](http://www.silwenae.org/blog/?p=604)


It worked once after I followed those instructions, but hasn't worked again.  I have a Sansa e250 with Rockbox installed.

hrmmm... still no joy.  :(

Here is a screenshot of what Banshee is telling me.  If I switch the USB settings in the Sansa to MTP Banshee sees it but can't connect.

I loaded Rockbox on the Sansa but had a rough time figure out how to get it to play.  I need to play with it a bit more.

---

### Post by lddm00 on 2008-09-23
I can't get my sansa e260 to mount in Ubuntu 8.04. I don't know why Ubuntu doesn't recognize it, even don't appear in lsusb

---

### Post by bvc310 on 2008-11-04
I have the exact problem. I am running 8.10 and my sansa e260 with rockbox is not recognized. In MTP mode it crashes banshee and in MSC mode it flashes connected disconnected before it finally goes disconnected. Anyone have a clue. Ill keep trying to figure it out and post if i find any answers.

Brian

---

### Post by gravometric on 2008-11-05
I have the exact same problem as BVC, but I am on Hardy 8.04.  I'm in MTP mode, and this worked once upon a time because I transferred files to the Sansa.  I have just plugged it in again after a long time and I can't mount it.  I do see it in lsusb however.
```
Bus 007 Device 006: ID 0781:7420 SanDisk Corp. Sansa E200 series (mtp)
```

---

### Post by doug1212 on 2008-11-16
I believe that libmtp in Hardy is a bit broken for some sansa players, there are some instructions for a bit of a hack/fix on the sansa forum:

[HTML]http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&message.id=1407&query.id=2379#M1407[/HTML]

I have a fuze and this workaround seems to be ok, if you try watch out for the typos, should be so.7 not so.6 etc.

---

### Post by lil_rich on 2008-12-03
Does anyone know if this fix is still relevant for libmtp version 3.3? Rhythmbox and Amarok both crash when trying to transfer music.

Cheers,
Rich

---

### Post by kasio on 2008-12-04
In Banshee, go to Edit > Preferences > Extensions, scroll down to iPod and MTP device support and disable them, then restart Banshee. That worked for me.

---

### Post by hardy24 on 2009-01-09
I have a sansa e260 and I am running Ubuntu 8.10.
The sansa must be switch to USB mode MSC.

After connecting the sansa 2 USB devices appear in nautilus but nothing more.

So we have to make the system that it is mounting the device correctly.

Make a new directory:

```
sudo mkdir /media/sansa
```

Check which devices are used by the sansa with:

```
sudo fdisk -l
```

Now we have to edit the file /etc/fstab
```
sudo gedit /etc/fstab&amp;
```

And put the following line at the end of the file, assuming that the first drive of the sansa was found at /dev/sdf1 with the fdisk -l command:

```
/dev/sdf1	/media/sansa	vfat	rw,user,noauto,exec	0	0
```

After editing the file /etc/fstab you have to reboot because this is a static table.

You can also try it by hand with 
```
sudo mount -t vfat /dev/sdf1 /media/sansa
```

If you want to mount it as normal user use the tool pmount. Normally this is not installed on the machines.
```
pmount -t vfat /dev/sdf1 /media/sansa
```

Normally that's it, now the sansa icon should appear on the desktop after connecting the device.
Don't forget to unmount the device before disconnecting.

Unfortunately I experienced some problems that it looked that the sansa was just mounted as read-only.
The reason for that was that some files were corrupted. So I connected the sansa to a Windows system and issued the command:

```
chkdsk /F e:
```

Now it worked fine on Ubuntu as well.

---

