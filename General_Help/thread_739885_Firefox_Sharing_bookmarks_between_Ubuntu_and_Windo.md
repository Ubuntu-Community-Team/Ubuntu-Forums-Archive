---
title: "Firefox: Sharing bookmarks between Ubuntu and Windows (the whole profile won't work)"
date: 2008-03-30
forum: General Help
---

### Post by Garfield123 on 2008-03-30
Hi all,

I'd like to share my experience on using Firefox on both Ubuntu and Windows.

I tried to share the whole profile folder, but that didn't work very well: every now and then something screwed up, especially when I installed new add-ons.

So I decided I'd share the bookmarks only. To me this makes perfect sense, because I update the bookmarks almost daily, whereas change add-ons or skins very rarely. This way, bookmarks are synchronized automatically, and if I add a skin or an add-on I like to the Linux installation, I'll have to do it manually n Windows - no big deal given how rarely I do that.

First of all, check out [http://support.mozilla.com/en-US/kb/Profiles](http://support.mozilla.com/en-US/kb/Profiles) on how to set and change profile folders.

I have a FAT32 partition which can easily be read by both Ubuntu and Linux. I have a FirefoxWin and  a FirefoxLinux folder, and set up scripts at the boot up and log off of Windows to sync the bookmarks files.

In windows, run gpedit.msc and look for the "script" section.

Add this script at startup (i.e. create a .vbs file with this text and add it):
----------------
dim filesys

set filesys=CreateObject("Scripting.FileSystemObject")

If filesys.FileExists("D:\WinLinuxShare\FirefoxLinux\bookmarks.html") Then

   filesys.CopyFile "D:\WinLinuxShare\FirefoxLinux\bookmarks.html", "D:\WinLinuxShare\FirefoxWin\"

End If
------------------
and this one at log off:
---------------
dim filesys

set filesys=CreateObject("Scripting.FileSystemObject")

If filesys.FileExists("D:\WinLinuxShare\FirefoxWin\bookmarks.html") Then

   filesys.CopyFile "D:\WinLinuxShare\FirefoxWin\bookmarks.html", "D:\WinLinuxShare\FirefoxLinux\"

End If
-----------------

Of course, you can do the same in Linux, it's up to you.

Hope you find this useful!

---

### Post by john_spiral on 2008-03-30
why not try:

[Syncing: [COLOR="Blue"]Share a Firefox Profile Between Ubuntu and Windows[/COLOR]]("http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/")

---

### Post by Garfield123 on 2008-03-30
Like I said, I did try to share the very same folder between Ubuntu and Windows, and it din't work. After a while, I started getting all sorts of weird error messages about add-ons being not properly installed. I did some research, and I found mine was not an uncommon experience.

The whole point of my post was that I tried to share the whole profile folder, it din't work, so I settled for sharing the bookmarks only, and keeping the profiles in two different folders.

Did you have better luck than me sharing the whole profile folder?

---

### Post by KuriKai on 2008-03-30
Some firefox add-ons do not work in linux because they are for the windows version of firefox

---

### Post by technoandymeister on 2008-03-30
I am only very new to Ubuntu and Linux in genera 3 weeks actualll, perhaps I shouldn't be posting yet, but I use Google Browser Sync, a plugin which works with my google user name and sync's bookmarks, cookies and passwords between Windows and Linux Firefox browsers on the 4 Pcs I use, 2 of which are dual boot with vista. Here is the link [http://www.google.com/tools/firefox/browsersync/](http://www.google.com/tools/firefox/browsersync/)  I hope this is helpful, although perhaps not a very technical response :)

---

### Post by Garfield123 on 2008-03-30
As far as I know, the add-ons I have are supposed to work on both Ubuntu and Windows. Indeed, now that I have recreated the Linux profile from scratch and reinstalled the very same add ons, everything works fine. 
The solution I proposed was the only one that worked for me. If you had better luck, good for you! :)

---

