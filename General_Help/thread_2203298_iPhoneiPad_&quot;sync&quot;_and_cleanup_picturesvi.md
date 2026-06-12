---
title: "iPhone/iPad &quot;sync&quot; and cleanup pictures/video"
date: 2014-02-02
forum: General Help
---

### Post by rmarc71 on 2014-02-02
I fight this periodically, but it got more annoying with iOS7.  My wife has iphone/ipad.  I have zero Mac's or windows boxes in the house.
She fills up her storage frequently and has me clean off the pictures to my server.  I had been doing this using VMPlayer with iTunes, but that's slow and a PITA.

After doing some research I found this:
[http://askubuntu.com/questions/414490/ubuntu-13-04-13-10-wont-trust-iphone](http://askubuntu.com/questions/414490/ubuntu-13-04-13-10-wont-trust-iphone)

(I'm running 13.10 server).

With that, and libimobiledevice-utils and ifuse, I was able to see the device plugged in and mounted as /media/iPhone.  The iPhone asked if I wanted to trust the computer (selected yes).
Paired with the device.
idevice_id -l (gives the udid of the device)
idevicepair pair -u <udid>
Mount the device
mkdir /media/iPhone
ifuse /media/iPhone

cd /media/iPhone

/media/iPhone# ls -l
total 0
drwxr-xr-x 3 root root  102 Feb 16  2012 AirFair
drwxr-xr-x 2 root root   68 Feb  2 14:17 Airlock
drwxr-xr-x 4 root root  170 Sep 20  2012 Books
drwxr-xr-x 4 root root  136 Feb  2 14:39 DCIM
drwxr-xr-x 3 root root  136 Feb  2  2014 Downloads
drwxr-xr-x 3 root root  136 Jan 16  2012 HighlandPark
drwxr-xr-x 6 root root  204 Feb 20  2012 iTunes_Control
drwxr-xr-x 2 root root   68 Sep 19 20:38 LoFiCloudAssets
drwxr-xr-x 9 root root  748 Feb  2 14:41 PhotoData
drwxr-xr-x 3 root root  102 Sep  8 12:08 Photos
drwxr-xr-x 4 root root  136 Sep 20  2012 PhotoStreamsData
drwxr-xr-x 2 root root 1088 Jan 15 10:30 Purchases
drwxr-xr-x 2 root root  170 Nov  1 20:58 Radio
drwxr-xr-x 2 root root  476 Feb  2 14:17 Recordings
drwxr-xr-x 2 root root  102 Feb  2 14:11 Safari


I moved all the photo dirs from the device to my servers pictures directory
mv DCIM/10* /pictures/<somedir>/

Now that that was off, I had to clear off all the thumbnails.  It seems to keep stuff in many locations:

rm -rf PhotoStreamsData/<somenumber>/10*
rm -rf PhotoStreamsData/.MISC
rm -rf PhotoData/Thumbnails/V2/DCIM/10*
rm -rf PhotoData/Thumbnails/V2/PhotoStreamsData/<somenumber>/10*
rm -rf PhotoData/*.ithmb
rm -rf PhotoData/Photos* (this removes the sqlite databases)

You could always save this stuff somewhere if you are uncomfortable deleting, but this cleared it all out for me and things seemed to be working still.

R. Marc

---

