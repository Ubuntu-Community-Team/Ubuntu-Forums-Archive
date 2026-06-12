---
title: "Can't read/write to Android MTP devices"
date: 2014-06-22
forum: General Help
---

### Post by halfbeing on 2014-06-22
According to bug #1203704 (sorry, can't paste the link due to a technical problem with the forum) GVFS can now read and write to files shared from Android MTP devices. However I am using Ubuntu 14.04 and I cannot, for instance, open a file located on my Android phone in Eye of Gnome. I get a "failed to open input stream for file" error. Am I doing something wrong, or was the announcement that read and write had been implemented premature?

Is there any way to browse photos and/or videos located on my phone from desktop Ubuntu?

---

### Post by TheFu on 2014-06-22
IME, MTP support is extremely device dependent.  What works with your device, if anything?
For example, I cannot move files within the MTP storage, but can pull a file out, edit it, then move it back.  I have a Nexus4. Also, the Nexus4 didn't work with 12.04 until I patched the driver, but with 14.04 it works the same (though no editing).

The version of android probably matters too.

I'm confused about the copy/paste issue too.  If you run X/Windows, you can select and paste with the mouse alone. No keyboard needed ... just the left button to select and the middle button to paste.  Thanks to fancy copy/paste tools/software, the X-buffer tends to be cleared after 5-10 seconds, however.

---

### Post by coffeecat on 2014-06-22
> **halfbeing said:**
> According to bug #1203704 (sorry, can't paste the link due to a technical problem with the forum) 

There is no problem with the forum that would prevent you from posting a link. I suggest you check which of your browser settings is interfering with you using all the features of the forum. Not only does the forum software permit you to paste URLs, but it automatically adds url tags to make a hyperlink. I presume this is the bug you were referring to:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1203704](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1203704)

---

### Post by philinux on 2014-06-22
OP.

Which android phone have you got?

---

### Post by halfbeing on 2014-06-22
> **coffeecat said:**
> There is no problem with the forum that would prevent you from posting a link. I suggest you check which of your browser settings is interfering with you using all the features of the forum. Not only does the forum software permit you to paste URLs, but it automatically adds url tags to make a hyperlink. I presume this is the bug you were referring to:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1203704](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1203704)

It turned out that Chromium had started misbehaving and needed to be restarted.

---

### Post by halfbeing on 2014-06-22
> **TheFu said:**
> IME, MTP support is extremely device dependent.  What works with your device, if anything?
For example, I cannot move files within the MTP storage, but can pull a file out, edit it, then move it back.  I have a Nexus4. Also, the Nexus4 didn't work with 12.04 until I patched the driver, but with 14.04 it works the same (though no editing).

The version of android probably matters too.

I'm confused about the copy/paste issue too.  If you run X/Windows, you can select and paste with the mouse alone. No keyboard needed ... just the left button to select and the middle button to paste.  Thanks to fancy copy/paste tools/software, the X-buffer tends to be cleared after 5-10 seconds, however.

I've got a Samsung Galaxy S4 running Android 4.4.2. So far I have found that I can drag and drop files in both directions using Thunar. However I have also just found that I can't copy music files to the phone using Clementine. Also – and I don't know if this is connected – I have a problem renaming files on the phone. It is disallowed in all file managers except Samsung's own (which is annoying because Samsung won't let me change the file extensions).

My last phone was an Xperia P and I had a really weird problem with that. I couldn't transfer any image file that had been modified by the Twitter Android app. I assumed that this was a general deficiency, but from what you have said it sounds like it might have been very specific to that phone.

---

