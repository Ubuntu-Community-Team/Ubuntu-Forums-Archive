---
title: "What program to use to extract an &quot;.ear&quot; or &quot;.war&quot; file?"
date: 2006-07-28
forum: General Help
---

### Post by ringding on 2006-07-28
I am trying to find a program that will extract Cold Fusion ".war" and ".ear" files. These are similar to zip files.....I tried "ark",  "Xarchive"......they will not recognize the file extension....."Archive Manager" will decompress correctly but will not work if the archive is on a network share......

Need to be able to extract these archives on a network share drive from local machine.

Any help would be greatly appreciated!!!!

---

### Post by sgtBiafra on 2006-07-28
Archive Manager should have no problem whatsoever. I was able to browse a WAR file that I generated with Eclipse.

If you browse to the location with the Nautilus file manager, does the file appear with a ZIP icon?

---

### Post by ringding on 2006-07-28
I can open the file locally with Archive Manager no problem. Its when I try to do it on a file that resides on a network share. Archive manager opens but I get a grayed out screen....nothing happens.  I am working on fresh install of Dapper.....the icon is the Gnome foot.  No idea why it will not work from a share????

---

### Post by philippe_carlo on 2006-07-28
If all you want to do is extracting, then why don't you use 'unzip' from the command line?

---

### Post by ape on 2006-07-28
These are both variants of a .jar file. (.ear: Enterprise Application Resource and .war: Web Application Resource) that are no different archive wise.  Why not just use the jar command as intended?  'jar -xvf <file.ear>'

---

### Post by ringding on 2006-07-28
Well.....not being a complete expert on Linux.....I know I can do this on the local server..no problem..but I was looking for a way that this can be done through a samba share.....nautilus.

I am connected from my laptop to a linux server via a samba share which is where the ".war" files reside.

 What you described above works fine if I am doing it in the terminal/gui on the server itself......I was trying to get one of the GUI archive programs to handle it while connected through the share from my laptop. This is where my issue resides......

I hope I explained that right........and thank you all for the help so far!!!!

---

### Post by ZephyrXero on 2006-09-10
I'm also having trouble opening .war files :(

My real problem though is that I'm trying to open a .mht file (Microsoft archivied HTML), that my teacher just insists on using. I found a program called KMHTconvert, and it seems to have worked, but all it did was generate a .war file, which I can't open either :( I tried opening it with File Roller and that was a no go, then I tried the jar -xvf command and that didn't work either. All I got was an error saying: "Ick! 0x8088b1f"

I also found an extension for Firefox that is supposed to be able to open these .mht files, but it looks like it only works in Windows :(

Any ideas anyone? thanks...

**Update:** I installed Konqueror, and it supports .war files natively

---

### Post by &#44608;&#51068;&#50689; on 2007-06-12
oops... I have no answer but I have the same trouble... T.T
I am eager to get any solution, too...
Don't give up, God help us some time.

---

