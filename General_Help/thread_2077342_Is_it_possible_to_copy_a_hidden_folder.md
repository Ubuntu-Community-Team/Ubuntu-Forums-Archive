---
title: "Is it possible to copy a hidden folder?"
date: 2012-10-28
forum: General Help
---

### Post by halfhearted on 2012-10-28
I am trying to copy the .mozilla folder. The reason I am doing this is that on my Asus Eee PC 901 I managed inadvertently to fill up the SSD (it's only 3.5GB) that the system is on while I was attempting to install ubuntu-restricted-extras. This led to a horrible crash. The system attemts to start with low res drivers but cannot and does not respond if I 'OK' this option.

I have a number of bookmarked links in Firefox that I need for work and which took a long time to find. I don't think I could do it again. I don't want to lose the bookmarks. I am told that Firefox bookmarks are in .mozilla. I am running Ubuntu from an installation disk and navigating onto the SSD in the Asus where the old system is. I can see .mozilla but cannot open it no matter what I do. Permission is denied. I thought that if I copy it to a USB flash drive I might be able to open it somehow later and get to the bookmarked links. I am resigned to reinstalling Ubuntu 12.10 but do not want to lose the bookmarked links.

From the User folder I tried to use - - -

sudo cp * -a .mozilla /media/NewVol/MOZ

this where /media/NewVol/MOZ is the path to the folder on the USB flash drive where I am attempting to store the contents of .mozilla. This returned "Operation not permitted". Thanks for any help.

---

### Post by 3Miro on 2012-10-28
The command should be:
```
cp -r .mozilla /some/mew/place
```
I don't think you need sudo to do this.

Hidden folders can be copied like any other folder. The only special thing about them is that you need to hit Alt+H in Nautilus to see the folder.

---

### Post by Vaphell on 2012-10-28
cp -r does recursive copying of the whole subtree

```
cp -r .mozilla /media/NewVol/MOZ
```
so you say you can't even do ```
cd .mozilla
``` ? that would be strange, but if that's the case, maybe you can chown the dir recursively (change ownership to the current user)?
```
chown -R $USER:$USER .mozilla
```?

---

### Post by CaptainMark on 2012-10-28
If your on a live cd have you correctly followed the instuctions on how to mount the correct drive, this can usually be easily done by bringing up the file manager and clicking on the 500GB Hdd option in the left panel, then navigate to your home folder and hit ctrl+H you should see the .mozilla folder there and be able to move it

---

### Post by Rebelli0us on 2012-10-28
You can copy your entire profile from Mozillas/Firefox/<profile name>, just drag & drop in File Manager / Nautilus. But shut down Firefox first, because it wont let you copy while it's running.

---

### Post by halfhearted on 2012-10-28
Thanks very much everyone. I appear to be getting there with your suggestions. Vaphell, you were right. It is complicated because I am using the installation CD to get a system up. This creates me as ubuntu@ubuntu while the .mozilla hidden folder I was trying to get the bookmark backups from is owned by my original user, which is user1. So, I had to do this ---

sudo chown -R ubuntu:ubuntu .mozilla

This has changed the permissions so that now .mozilla is owned by the user created by the installation disk. That means I can "cd .mozilla" and "dir .mozilla". I will try to copy the bookmark backup files to a usb drive. How do I get the .json files into a form the Firefox can use? In fact, what is a .json file?

---

### Post by Vaphell on 2012-10-28
can't you simply backup whole dir and then copy it back to your brand new $HOME? firefox should pick everything up like nothing happened.

---

### Post by halfhearted on 2012-10-28
Amazing. It worked. I now have the bookmarkbackups folder on my usb drive. It contains 10 files with names like "bookmarks-2011-12-10.json". Does anyone know how I can get the actual URIs out of these files? What's a .json file? Thanks for any help.

---

### Post by halfhearted on 2012-10-28
Sorry Vaphell, I missed that. Which directory are you suggesting I should copy? Do you mean the whole .mozilla hidden directory?

---

### Post by Vaphell on 2012-10-28
technically your profile should be stored in **~/.mozilla/firefox/<random_garbage>.default** but backing up whole .mozilla is fine. Firefox should detect that the profile dir exists and use it with no hassle.

---

### Post by halfhearted on 2012-10-29
I replaced the old .mozilla folder with the new one and it worked fine. Thanks to everybody.

---

