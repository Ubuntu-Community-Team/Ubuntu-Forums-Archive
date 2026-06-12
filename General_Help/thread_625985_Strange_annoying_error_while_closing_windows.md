---
title: "Strange annoying error while closing windows"
date: 2007-11-28
forum: General Help
---

### Post by mushroomcloudwarrior on 2007-11-28
[IMG]http://i36.photobucket.com/albums/e37/mushroomcloudwarrior/snapshot5-1.png[/IMG]

Every time i try to close a window, Kubuntu gives me this error, i can't do anything but click ok. The drive that i'm on is not even 50% full, so there can't possibly be lack of disc space to store files. Does anyone know why this is happening? it's annoying..

---

### Post by mushroomcloudwarrior on 2007-11-28
Note that it says the message will be displayed only once, it still comes up every time i try to close a Dolphin window (i'm using Kubuntu gutsy 7.10)

Konqueror still seems to work just fine though, no error messages while closing etc.

---

### Post by -grubby on 2007-11-28
that happened to me while I was using  Kubuntu too....unfortunately I decided to reinstall Ubuntu and forgot that I could just delete my ./dolphin folder just for something to try

---

### Post by mushroomcloudwarrior on 2007-11-28
do you think uninstalling and re-installing dolphin will take this away?

---

### Post by -grubby on 2007-11-28
> **mushroomcloudwarrior said:**
> do you think uninstalling and re-installing dolphin will take this away?

did you try my other suggestion yet? and I don't know if uninstalling and reinstalling would fix it or not

EDIT: I'm going to install dolphin to see if this happens to me

EDIT1: funny it doesn't happen to me

---

### Post by mushroomcloudwarrior on 2007-11-29
uninstalling and re-installing did not work for me.

How do i delete the ,/dolphin folder? and what will i be doing by deleting the ./dolphin video?

---

### Post by mushroomcloudwarrior on 2007-11-30
bump

---

### Post by Maragato on 2007-12-05
I am also having this problem, can anyone give me a hint on this?

---

### Post by jperez on 2007-12-06
I found something that worked for me and it might just work for you.

1. Go to /home/<your home folder>/.kde/share/apps/

2. Delete or drag the **d3lphin** folder to the Trash Can.  It will auto replace itself the moment you throw it away.

3. Do it a couple of times, just for good measure.

4. Go into the newly created d3lphin folder

5. Open the bookmarks.xml properties and go to Permissions

6. Make sure it has Owner **AND** Groups to Read & Write.

Close it and then close your Dolphin window.  That should do it.

Jesse~

---

### Post by njyankee on 2007-12-06
I had the same annoying issue.  Mine was caused by incorrect permissions settings on the bookmarks.xml file.  I corrected it by going to that file; accessing via "root" and changing the permissions to be my user name.

---

### Post by kabronkline on 2007-12-29
I had this problem and fixed it by running the following commands in a terminal window:
```

cd $home
rm -r .kde/share/apps/d3lphin

```

---

### Post by Doorslammer on 2008-02-08
same problem  here & the post above mine solved it

---

