---
title: "UBUNTU 18: Alternatives to the default file software"
date: 2019-10-30
forum: General Help
---

### Post by nocruoro on 2019-10-30
Still working on restoring my data from my old pc onto my newly repaired ubuntu 18.04 installation. 
Unfortunately my Samsung Galaxy A40 2019 phone can't stay awake for more than 10 minutes of inactivity before the screen times out while **"connected to brand the new usb cable"** and the default file copying system seems too slow to finish preparations for copying from my phone (10.52 Gigabytes (17.458 files, 455 folders)) before it becomes inactive since it is still preparing before the minutes are up. Even trying 2 folders from phone is very slow to  begin. 
I dont have a usb device with the same files at the moment so i cant transfer yet from any friend with windows.

The files are travel photos but they take up a lot of room on my phone.

Any advice for looking in the ubuntu software store. or trusted ubuntu download sites? The default preparation for copy process in the nautilus file manager system between phone and pc is so slow and even unresponsive!

---

### Post by uRock on 2019-10-30
I use PCmanFM. It is still slow, though. It's the nature of the beast.

---

### Post by nocruoro on 2019-10-30
> **uRock said:**
> I use PCmanFM. It is still slow, though. It's the nature of the beast.

Just looked for it, this one doesn't seem to start copying or make a difference (somehow it was included in the installation. could it be clashing with nautilus for processing speed for this?)

---

### Post by uRock on 2019-10-30
> **nocruoro said:**
> Just looked for it, doesn't seem to start or make a difference

As I said, it's still slow. This has been the case on Windows and Linux machines that I've used for file transfers from phone to PC.

Plan B) Don't let the screen fall asleep. Mine only stays active for 3 minutes, so I am used to reaching over tapping the screen to keep it going.

---

### Post by Holger_Gehrke on 2019-10-30
mtp is a file-transfer protocol masquerading as a drive. And the fact it's using gvfs doesn't exactly help. The fastest and most reliable way I've found to use it is to use the file-manager to mount the phone and then do the actual copying in the shell. The mount point is a directory in /run/user/<numerical user id as given by 'id'>/gvfs/. So to get all the pictures from my phone I'd do something like 'cp /run/user/1000/gvfs/mtp\:host\=%5Busb%3A003%2C010%5D/Interner\ gemeinsamer\ Speicher/Pictures/* .' (edit: of course you don't have to type a long path like that ... file name completion in the shell using the tabulator key ...) and after a few minutes the pictures are in the current working directory.

Back on Ubuntu 12.04 I used go-mtpfs, a tool to mount mtp through fuse (without gvfs). It's in the repositories but I haven't used it in the last three or four years.

Holger

---

### Post by The Cog on 2019-10-30
Thanks, Holger_Gehrke - that's good info. 
But in this case, even though command-line tools don't spend so long thinking about it before they start copying, there is still a chance that the phone will sleep before all the transfer is done. Maybe using rsync instead of cp it will be possible to repeat the command and continue with the next batch of files (with rsync skipping the completed copies). 
Just a thought.

---

### Post by CatKiller on 2019-10-30
I think you're barking up the wrong tree; your choice of file browser on the desktop likely has nothing to do with it. You can keep the screen awake just by doing activity on your phone, but the screen doesn't need to be awake to do a transfer, and even if it were awake your phone would still just be sitting there not transferring the files for longer.

MTP is a pain at the best of times, and phone OEMs *love* to monkey with standard stuff so that you'll install whatever whizz-bang software they promote instead. You'll likely have much better luck if you can get your phone into USB Mass Storage mode so that it's just transferring a bunch of files rather than doing a bazillion loops of "ooh, it's a picture! can I handle this picture?"

You may also find it quicker to just dump stuff over the network rather than use a cable. Something like SFTP requires zero cooperation from the OEM, so it's generally low-friction even if it is theoretically slower.

---

### Post by uRock on 2019-10-30
> **CatKiller said:**
> <snip> You can keep the screen awake just by doing activity on your phone, but the screen doesn't need to be awake to do a transfer, and even if it were awake your phone would still just be sitting there not transferring the files for longer.<snip>

<snip>You may also find it quicker to just dump stuff over the network rather than use a cable. Something like SFTP requires zero cooperation from the OEM, so it's generally low-friction even if it is theoretically slower.

My phone locks the data connection with the PC when the screen locks.

I am interested if anyone wants to recommend and SFTP client for Android. I've started a thread [here]("https://ubuntuforums.org/showthread.php?t=2430315"), as I don't want to hijack this thread.

---

