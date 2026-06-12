---
title: "Can't Connect iPhone to Ubuntu laptop via USB"
date: 2020-08-06
forum: General Help
---

### Post by arius88 on 2020-08-06
Hello!  Currently I have a second computer taking up space in my room just so I can use windows to get photos off of my iPhone. I'd like to get rid of that extra computer, but unfortunately I've never been able to get my linux computer to read the phone. I started using Ubuntu somewhere around 11.04, and after upgrading to 18.04 this is the closest I've come to having it import photos off my iPhone: it will now acknowledge that the phone exists and offer to import photos with Shotwell. Then it gives me two errors:  1. Sorry could not display all the contents of "iPhone": failed to get folder list: -10: Timeout reading from or writing to the port  2. -53: Could not claim the USB device  And my only option is to click on "OK" even though it's not OK. (A "Bummer" button would be more appropriate, IMO. Or a "That's A Bummer, Ubuntu, But I'm Sure You Did Your Best" button.)   I'm using Ubuntu 18.04, and I have an iPhone 5.   Any help would be appreciated. Thanks!  - A

---

### Post by arius88 on 2020-08-06
P.S. I did find this work around:   sudo usbmuxd -u -U usbmux   in this thread: [https://ubuntuforums.org/showthread.php?t=2376741&highlight=USB+iPhone](https://ubuntuforums.org/showthread.php?t=2376741&highlight=USB+iPhone),   but I'd rather not have to do that every time I want to import photos. Is there a way to make it permanent or include it in the grub (I'm sort of talking out of my ass here but I think that makes sense) or something?  edit: also this only worked once and then I couldn't get it to work again.

---

### Post by oldfred on 2020-08-06
I just did this with Kubuntu & my iPhone.
It now shows added folders over just the photos.

I had to install these, my orginal list had some that would not install with 20.04, but once I removed those, it worked. I think this was final list.
sudo apt-get install ideviceinstaller libimobiledevice-utils ifuse libimobiledevice6  libplist3

First time:
  sudo mkdir /mnt/iPhone
sudo chown  $USER:$USER /mnt/iPhone 
sudo chmod  a+rwX,o-w /mnt/iPhone

idevicepair pair
ifuse /mnt/iPhone/
to unmount:
fusermount -u /mnt/iPhone
idevicepair unpair

I have my phone set to use .jpg, but my wife has .heic, so I had to convert those files with heif-convert.

---

### Post by arius88 on 2020-08-07
After doing everything Fred suggested, except the stuff under "to unmount," I had "SUCCESS" pairing the phone with my computer.   But it still won't read the files.  I unplugged the phone and plugged it back in and achieved a new level of error message: "Unhandled error message: No such interface `org.gtk.vfs.Mount' on object at path /org/gtk/vfs/mount/1"   What does this mean and how do I fix it?

---

### Post by arius88 on 2020-08-07
Update: I rebooted the computer and was able to get photos off my iPhone! Hopefully it continues working. I'll report back if there's more issues. Thanks again, oldfred!

---

### Post by oldfred on 2020-08-07
Glad it worked, you can change to Solved, so others may find this thread.

---

