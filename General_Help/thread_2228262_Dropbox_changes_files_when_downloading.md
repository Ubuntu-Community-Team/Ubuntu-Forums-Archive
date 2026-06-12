---
title: "Dropbox changes files when downloading"
date: 2014-06-06
forum: General Help
---

### Post by mathijs4 on 2014-06-06
Hi, i'm new to the Ubuntu community and i encountered something annoying.

I installed dropbox and synced my dropboxaccount (with some shared folders) to a folder (located on another logical NTFS partition so Windows can acces it to). After a while i noticed everytime dropbox downloads a file, the file gets altered and then back uploaded to the shared folder. (peoples i share with where complaining abount constantly updates to files by me) Not a big problem so far because i seems to happen only one time. 
Later that day someone of the people i share with who also runs Ubuntu start syncing with my changes. Now the annoying thing started: his dropbox also altered the files while downloading and uploaded it back to the folder. This resulted in mine dropbox noticing the file was changed, downloading, altering and uploading it again. I think you see the problem over here: dropbox was constanly changing the same files.

I looked a little deeper into it before posting here. With files original from not linux OS it happened once (their dropbox didn't changed the files back). With Linux it kept happening. I also discovered the permission of the files at my pc are different than the permission of the files of the other guy with Ubuntu. So i'm guessing dropbox downloads the file, Ubuntu notices the different permissions, changes them, dropbox notices something on the file has changed and uploads it again. (I can be wrong) I tried to change the permission of my files to the same as the permission of the other Ubuntu person, but Ubuntu didn't let me do this (I'm new to Ubuntu, so i didn't realy found how to fix this). So i don't now if it would work with the same permissions on both sides.

Does anyone knows how to fix this in a decent way? I mean not just changing my permissions (although it would be a plan B solution), otherwise everyone in the shared folder needs to have the same permissions.

thx

---

### Post by bapoumba on 2014-06-06
I *think* it has to do with you syncing files located on an ntfs partition from Ubuntu. Linux permissions are not handled by ntfs.

I share folders with users regardless of their OS, including Windows, and I use dropbox from Ubuntu, MacOS and phone. The idea is that one OS gets to sync from within its own folder tree and file system. You should install the dropbox client on Windows with your own account and sync from there. One client per OS, within its own file tree and permissions setup.

---

### Post by mathijs4 on 2014-06-07
Any idea how i can solve this so i can still acces the dropbox file from both windows and Linux? I'll do some tests later thus day te see of the ntfs partition realy is the problem.

---

### Post by bzhao on 2014-06-07
I agree with what bapoumba is saying,  I am using dropbox like that
Don't share the dopbox folder across OS.

---

### Post by mathijs4 on 2014-06-07
The problem is my dropboxfilder is kinda big, so splitting this folder would mean downloading it twice on my pc.

---

### Post by bapoumba on 2014-06-07
> **mathijs4 said:**
> The problem is my dropboxfilder is kinda big, so splitting this folder would mean downloading it twice on my pc.

Well, if both OS are on the same machine, I can understand that, but i'm afraid there is no other way.

Using an external drive to move out one of your own dropbox folders is risky, the drive needs to be mounted before the dropbox client starts running and should not get disconnected while dropbox is running. Found this while looking how to move the dropbox folder :
[https://www.dropbox.com/help/89/en](https://www.dropbox.com/help/89/en)

---

### Post by mathijs4 on 2014-06-07
I suppose there is no other way. Thanks for helping me out :D Although when someone does come up with a way of having only one dropbox folder for both OS on dualboot, please share it with us :)

---

### Post by bapoumba on 2014-06-07
> **mathijs4 said:**
> I suppose there is no other way. Thanks for helping me out :D Although when someone does come up with a way of having only one dropbox folder for both OS on dualboot, please share it with us :)
You're welcome.
Well, that feature will have to come from dropbox themselves :)

---

