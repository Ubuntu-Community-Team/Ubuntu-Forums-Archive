---
title: "Accessing Files on the Windows 7 Partition"
date: 2012-12-11
forum: General Help
---

### Post by richgeasey on 2012-12-11
I just installed Ubuntu on my Win 7 system. How can I find and access my files from all my Win 7 apps (such as images and music).

How and/or where can I find and access them?

Thanks!

---

### Post by papibe on 2012-12-11
Hi richgeasey.

Open the Nautilus (file Manager) and go to 'Computer'. There it should be a disk called either OS, Windows or C. Double click on it and you'll have access to your Windows files.

I'd recommend jumping quickly to your Windows user home directory, as you are seeing the root of your C:, thus you won't delete an important system files.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by richgeasey on 2012-12-11
OK, I open up the File Manager (I assume it is the launcher icon Home Folder). While there is a heading for Computer it does not list any folder location matching what you suggest. I looked under file system and did not see anything there either.

---

### Post by papibe on 2012-12-11
Use the Nautilus menus to get there. You are looking for the 'Go' menu.

There are a few alternatives:
[LIST]
[*]While on Nautilus, hold the Alt key. The menus will appear on the top Unity bar.
[*]While Nautilus is current window selected, hover your mouse over the Unity bar.
[*]Press the shortcut Alt+G to get directly to the menu.
[/LIST]Let us know how it goes.
Regards.

---

### Post by richgeasey on 2012-12-11
OK, a little closer. I did the Alt and selected Go and got to the Computer screen.

I selected the HD icon and it says it is unable to mount it. I am assuming this is a likely reason it is not otherwise showing.

Thanks for the help!

---

### Post by papibe on 2012-12-11
Try double click on it to get to your files (maybe it is already mounted).

If not, could you post the error message? (an screenshot)

Regards.

---

### Post by richgeasey on 2012-12-11
I double clicked it and same issue.

---

### Post by richgeasey on 2012-12-11
I should also note that there is no information on the drive in the properties section. It should be able to easily pick up the make and model and all of that normal stuff.

It is not picking something up correctly somewhere along the line it seems.

---

### Post by papibe on 2012-12-11
Is this a regular install or a Wubi one?

---

### Post by richgeasey on 2012-12-11
wubi

---

### Post by papibe on 2012-12-11
Oopsy.. wrong method then.

Wubi way:
[LIST]
[*]Go to Computer.
[*]Get into 'File System'
[*]Look for a directory named 'Host'.
[*]Double click on on it.
[*]You'll be on your C:
[/LIST]
Let us know how it goes.
Regards.

---

### Post by richgeasey on 2012-12-11
Got it, thanks!

Seems it ought to work a little easier, but this will be OK.

Appreciate the help!

---

