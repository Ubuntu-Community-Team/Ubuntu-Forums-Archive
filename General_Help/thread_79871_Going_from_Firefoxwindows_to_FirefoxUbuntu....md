---
title: "Going from Firefox/windows to Firefox/Ubuntu..."
date: 2005-10-21
forum: General Help
---

### Post by ymmotrojam on 2005-10-21
Where do I put my bookmarks file? :)

---

### Post by gbusse on 2005-10-21
In Firefox select Bookmarks > Manage Bookmarks

Then in the Bookmarks window select File > Import then import the bookmarks you exported from the Windows version...

Later,
Gordo

---

### Post by Nomad64 on 2005-10-21
Or if you prefer working with files:

Your bookmarks.html file should go in your profile directory.

From the "Places" drop-down menu on the GNOME panel, select "Home Folder." Once the window comes up, click on the "View" pull-down menu and select "Show Hidden Files" (alternatively, use the CTRL + H hotkey combo). Then find the folder named ".mozilla" and open it. (Remind you of Windows yet?) Open the subfolder named "firefox" and then the subfolder of the current profile in use (usually there is only one).

**Windows Firefox profile dir path:**
C:\Documents and Settings\[user]\Application Data\Mozilla\Firefox\Profiles\[profile name]\

**Linux Firefox profile dir path:**
/home/[user]/.mozilla/firefox/[profile name]/

Be sure that all instances of Firefox are closed then simply replace the bookmarks.html file. Gordo's way works just as well.

---

### Post by ymmotrojam on 2005-10-21
Thanks for the quick response!

---

### Post by Nomad64 on 2005-10-21
I blame the Pepsi I am drinking...

You're Welcome.

---

### Post by gbusse on 2005-10-21
No problem, either one of these suggestions should get you going...

Later,
Gordo

---

### Post by Matt Volatile on 2005-10-21
Is there a way to copy the full profile from Windows to Ubuntu - inlcuding extensions etc.? I have used MozBackup to transfer profiels between windows machines, and Firefox Portable to sync Mac and Windows versions, but I'm not sure of the best way to do this with Ubuntu...

---

### Post by 3david on 2005-10-21
I don't know about the whole profile, but I use the same bookmark file with both version, by adding this to each version's user.js file:

user_pref("browser.bookmarks.file", "/media/hdc5/data/bookmarks.html");

---

