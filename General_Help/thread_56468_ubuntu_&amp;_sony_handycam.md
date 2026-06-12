---
title: "ubuntu &amp; sony handycam"
date: 2005-08-12
forum: General Help
---

### Post by finkoisti on 2005-08-12
What sw I should use to record from handycam to HD in ubuntu?

I can use tv card but I would like to use direct connect via USB. ](*,)

---

### Post by finkoisti on 2005-08-13
I'll try to use kino with usb and it gives some kernel error message..
I found somekind of solution with google and it removes the kernel error message but then kino gives information that there isn't any av camera connected...

So how to get it work?

---

### Post by finkoisti on 2005-08-13
[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)

tht's what I'll try last, didn't help me. So I think there is a problem in kernel??
Is new fixed version coming soon or what should I do??

Install windows again :(

---

### Post by claydoh on 2005-08-13
afaik, Sony usb connections from Handycams are not supported in linux :(

For firewire connection to work as a normal user, you will need to change the read/write permissions on  /dev/raw1394:
 >  sudo chmod g+rw /dev/raw1394 

My Sony TRV18 miniDV cam works fine with Kino.
Figuring Kino out will take me some time, as I am at a complete loss when it comes to Video editing so far :)

---

### Post by finkoisti on 2005-08-14
So I can't use that connection where is that mormal USB mark in camera??
I'll have to use that DV connection?

And what driver I should use in Kino?

---

### Post by claydoh on 2005-08-14
As far as I can tell from my brief search, firewire is needed. Maybe different models may or may not work with USB. Mine uses USB 1.1, which would be aweful for video transfer anyway, and I even have trouble sometimes accessing the memory stick using its usb connection (this is a cross-distro issue for me).

As for driver, I just used the defaults in Kino, which is raw1394. I believe dv1394 is for recording **back** to the camera. I have not tried that yet.

---

### Post by finkoisti on 2005-08-15
I have still probles with that thing, using the newest kernel and Sony handycam HC39E, I have try at least 3 different methods what I have found from here and other places..allways get error message no av compliant devices found..

So how to fix it..?

I don't want to move back to WinXP only because can't get that working..

---

### Post by claydoh on 2005-08-15
If you used all the steps listed in your link in your third post, be sure to delete the file /dev/raw1394

 > < sudo rm /dev/raw1394 

then run the script you made to re-create the dev file with the proper permissions (so you won't have to do this after every reboot)

< sudo /etc/init.d/firewire 

Also, you may need to make sure your capture card is working.
 
  > < testlibraw 
 
 will show if a firewire card is detected.
 
  > < sudo lsmod | grep 1394 
 will show if the raw1394 module is loaded.

To see if your camera is supported, try using the tool gscanbus , available in the universe repositories.
 
  > < sudo apt-get install gscanbus 
 Then run the program
 
  > < gscanbus 
 
A little window will pop up with a little penguin icon if your firewire card is detected. Plug in your camera and turn it on, and it will show up there, or at least something will if that is detected, if not I do not know, perhaps the camera is not currently compatible with linux?
 
Be sure to use the "raw1394" driver and not dv1394 as your model doesn't support recording back to the cam via firewire anyway, and that you have set the permissions on it as I described above.

---

### Post by 23meg on 2005-11-14
[QUOTE=finkoisti][http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)

[/QUOTE]
This got mine working with Kino as /dev/dv1394/1. Now, has anyone been able to use the AV/C transport controls? They don't work for me, and I have to manually press play and stop on the camera to do the capture.

---

### Post by pkoufalas on 2005-12-13
This all worked well for me...great, thanks to all who posted!

(I had no /dev/raw1394 and wondered if/how to create it...not knowing why the kernel module didn't do it for me...)

In Kino, AV/C controls worked fine for me...but first I hit the AV/C button on the Capture screen to enable it.

---

### Post by pixelnate on 2005-12-14
Can anyone tell me if this card will work with Ubuntu for video capture with Kino?

[http://www.newegg.com/Product/Product.asp?Item=N82E16815161003](http://www.newegg.com/Product/Product.asp?Item=N82E16815161003)

TIA.

---

### Post by wouterla on 2005-12-14
[QUOTE=claydoh]afaik, Sony usb connections from Handycams are not supported in linux :(

For firewire connection to work as a normal user, you will need to change the read/write permissions on  /dev/raw1394:
[/QUOTE]

FYI, since those devices are liable to be recreated (at reboot, for instance) it might be a better idea to add the relevant groups to you user account in /etc/group.

According to /etc/udev/permissions.rules, the groups you need are 'disk' and 'video' (grep 1394 /etc/udev/permissions.rules), so if your user account is 'wouter' (mine is :-) ), then you'd edit /etc/group ('vi /etc/group'), look for the line that starts with 'disk', and add your user account to it so it looks something like this: 

```
disk:x:6:wouter
```

Same for 'video':

```
video:x:44:wouter,mythtv
```

I have mythtv installed, which also needs access to some (other) video devices.

Another way would be to give everyone access (less secure, I suppose) by changing the relevant entries in permissions.rules to:

```

KERNEL=="raw1394",      MODE="0666", GROUP="disk"
KERNEL=="dv1394*",      MODE="0666", GROUP="video"
KERNEL=="video1394*",   MODE="0666", GROUP="video"

```

---

### Post by sschaper on 2007-05-29
How would I go about loading the raw1394 module in the first place?

---

### Post by wouterla on 2007-05-29
Normally, ubuntu will take care of that for you, if you connect a video camera.

Should this not happen, opening a terminal window and typing:

```
sudo modprobe raw1395
```

should also work

You can check if a module is loaded with:

```
sudo lsmod 
```

so 

```
sudo lsmod | grep 1395
```

should list all relevant modules.

---

### Post by ArtInvent on 2007-06-15
I did a clean install from Edgy to Feisty. 

Intstalling Kino in Edgy - my DV cameras via firewire 'just worked'.

In Feisty, it just didn't work. At all. I had to go through this whole rigamarole just to get the raw1394 driver to work.  PLUS all the info is not on one post, I had to go to about 5 different websites and forum posts to piece the fix all together. Finally deleting the existing /dev/raw1394 and re-running the script 'firewire' did it for me. 

One more thing where things in Edgy just worked and not in Feisty. This is progress?

Anyway, thanks to claydoh and the others for figuring this out.

---

### Post by naszi on 2007-09-28
Hi!

I also did the firewire script, but it worked only after i deleted /dev/raw1394 and run the script again....
Well, now it works, Ubuntu Feisty on Toshiba Satellite Pro notebook with Canon MV700.

Have a nice day!

---

### Post by arethz on 2007-11-02
I have a sony dcr-hc90e camera. After changing the /dev/raw1394 permission, everything works fine and I able to capture video via firewire in Gutsy.. I'm just so lucky.. :popcorn:

---

### Post by zend on 2007-11-20
Same thing for me after upgrading.  Firewire used to work fine, now I have to manually delete: /dev/raw1394 and then run the firewire script.  I wonder why this is?

---

