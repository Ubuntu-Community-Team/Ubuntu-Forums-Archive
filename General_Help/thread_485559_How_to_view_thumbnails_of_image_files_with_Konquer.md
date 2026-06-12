---
title: "How to view thumbnails of image files with Konqueror?"
date: 2007-06-27
forum: General Help
---

### Post by monocongo on 2007-06-27
One thing I miss from Windows is the ability to open a folder full of image files and view them all at once as thumbnails.  Is there a way to configure or modify Konqueror to do that?

Thanks in advance for any suggestions.

--James

---

### Post by cookies on 2007-06-27
Konqueror thumbnail previews all file types that it can by default.... What, are the previews not showing?

---

### Post by monocongo on 2007-06-27
No all I see when I open a folder full of JPGs are the little icons for an image next to the file names.  This is all I get regardless of the view mode I choose.  

--James

---

### Post by swisscow on 2007-06-27
Two things.

Check the view...preview menu - are pictures selected?

The other is Tools....Create Image gallery - not exactly a preview but pretty cool anyway.

---

### Post by monocongo on 2007-06-28
Thanks for the tips swisscow.  There's no preview menu option under the view menu, not with my Konqueror anyway.

I did find a preview menu under  Settings->Configure Konqueror.  I chose media under local protocol, but later unselected it, as it didn't appear to have any effect.  The only one chosen under local protocols is file.

I'm not sure if this is a result of monkeying with the above settings, but I've noticed that if I hover over an image's file name a thumbnail will appear with the file information.  Although this isn't exactly what I want (I really want to see thumbnails of all image files in the directory when I open the directory), it's more than I thought I had when I originally posted this thread.

--James

---

### Post by monocongo on 2007-06-28
Something else I just noticed -- I can see the thumbnail preview for the image files in a directory on one of my hard drives, but thumbnails for the image files on a SD disk (the disk I use in my camera and which is inserted into a media reader on my computer) aren't available.  Maybe this is because some thumbnail information was somehow added to the image files on the hard disk, perhaps when I previously viewed the folder while using Windows?

--James

---

### Post by swisscow on 2007-06-28
You say there is no preview in the view menu?

I've just had a look and when Konqueror is in web browsing mode that is the case e.g. when I am writing this. When it is in file management mode I do have the preview option in the view menu. You can switch between the two using Settings....Load View Profile.... 

I've just tried a media card (not SD - don't have any) and it previews for me.

Sorry I can't help any more.

---

### Post by Abelius on 2008-03-06
> **monocongo said:**
> I did find a preview menu under  Settings->Configure Konqueror.  I chose media under local protocol, but later unselected it, as it didn't appear to have any effect.  The only one chosen under local protocols is file.

Well, this is an old post, but I've just had your same problem, and I can tell you that "media" ***needs*** to be selected for the thumbnails to work.

Don't ask me why (the technical reason), 'cause I'm a newbie with Linux, but that worked for me, and was the only thing I reconfigured. Don't leave it unselected, friend. :)

Cheers!

---

### Post by qurk on 2008-04-29
Go to settings, configure konqueror, previews and meta-data, and increase maximum file size.  Hope that helps :)

---

### Post by StiltonSandwich on 2008-06-03
> **Abelius said:**
> Well, this is an old post, but I've just had your same problem, and I can tell you that "media" ***needs*** to be selected for the thumbnails to work.

Don't ask me why (the technical reason), 'cause I'm a newbie with Linux, but that worked for me, and was the only thing I reconfigured. Don't leave it unselected, friend. :)

Cheers!

You'll notice that, when viewing the contents of removable media, Konqueror is using the "media" protocol (media:// in the address bar). The purpose of said protocol appears to be to hide the mountpoint of the memory card/USB stick/external disk so as to provide a consistent means of accessing it (automatic mountpoints aren't necessarily the same each time), although I don't really know, so don't hold me to that. It is also possible to navigate to the SD card in the filesystem, using the file protocol, at /media/disk or whatever, which would result in previews without selecting media as an allowed protocol.

I typically also select "fish" for previews while browsing files over SSH, and "obex" for browsing photos on my bluetooth phone. You could choose "smb" if you want to view previews in a Windows/SMB shared folder. You have to decide whether you prefer speed or previews, though, with these non-local protocols.

---

