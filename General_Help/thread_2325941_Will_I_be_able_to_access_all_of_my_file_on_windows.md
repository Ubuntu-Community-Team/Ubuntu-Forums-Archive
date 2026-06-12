---
title: "Will I be able to access all of my file on windows NTFS partition?"
date: 2016-05-26
forum: General Help
---

### Post by taylor19 on 2016-05-26
So my PC is infected and rather than just trying to remove the virus, I would like to just nuke windows and reinstall. Obviously I have loads of files that I need backed up and I don't want to back them up while booted into windows. Using lubuntu installed on an external HDD (Ubuntu doesn't want to install), would I be able to view every single one of my files that are on my HDD with windows installed to it? Will there be some files that just won't show up because I'm on Linux? I need to know because I don't know right off hand what files I want.

Any help is appreciated. Thanks

---

### Post by howefield on 2016-05-27
Yes, you'll be able to view your data on the Windows file system from a Lubuntu live media and copy what you need to some other destination for backup. It might be a different story if you have used some application to lock your data folders.

---

### Post by Yellow Pasque on 2016-05-27
Also, beware of fast startup/shutdown depending on what version of Windows you're running (8 or later IIRC). If you have that enabled, Windows won't cleanly unmount the NTFS volume when you shut down. Then, when you go to mount it in Linux, it will probably refuse and tell you to run chkdsk in Windows.

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Mark Phelps on 2016-05-27
If the PC is running Win8x or newer, then sorry, the answer is NO.

Why?

Because Win8x and newer automatically enable FastStartup -- which is a new form of hibernation in which the Windows filesystems remain mounted, even when Windows is not running.

Since you can not mount the same filesystem twice, any attempt to then mount that filesystem in Linux will fail -- and you will not be able to read or open any of the files.

---

