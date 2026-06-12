---
title: "Simple Image Viewer with Delete button Toolbar"
date: 2007-03-17
forum: General Help
---

### Post by pt123 on 2007-03-17
Is there a simple Image Viewer application with a Delete button on the toolbar, or at least one which has a setting to have no confirmation dialog box when the "delete" key is pressed to send the image to the thrash can?

I am writing a simple bash script to open the current wallpaper. 


Eye of Gnome - No button but when I press delete it asks for confirmation of wanting to send it to thrash can.

GQView -  It has an option to remove confirmation delete dialog box, but it does not delete to thrash can but its own thrash folder. Also it is not a simple image viewer as it load with an explorer interface.

I am using Ubuntu, a gnome solution would be preferred.

---

### Post by cookfromfrozen on 2007-03-17
You can turn  off safe delete and delete  confirmation in advanced tab of GQview options.

---

### Post by kerry_s on 2007-03-17
Try looking into feh, it's a great image viewer, has command line options, it's fast.

---

### Post by pt123 on 2007-03-17
> **cookfromfrozen said:**
> You can turn  off safe delete and delete  confirmation in advanced tab of GQview options.

Didn't you read my post

---

### Post by cookfromfrozen on 2007-03-17
> **pt123 said:**
> Didn't you read my post

You said this:

> but it does not delete to thrash can but its own thrash folder

That can be turned off.  I informed you of that.

So yes, I did read your post, and I replied to it.  This will be my last reply however.

---

### Post by anaconda on 2007-03-17
Mirage is good and simple.. and you can disable the deletion-confirmation from the preferences..

My new favourite imageviewer..

---

### Post by pt123 on 2007-03-17
> **cookfromfrozen said:**
> 
So yes, I did read your post, and I replied to it.  This will be my last reply however.

I said I want it to delete to the Gnome Trash can and this doesn't.

I am sorry if I pissed you off, that wasn't my intent.

---

### Post by pt123 on 2007-03-17
> **anaconda said:**
> Mirage is good and simple.. and you can disable the deletion-confirmation from the preferences..

My new favourite imageviewer..

Thanks Mirage looks promising, I will try it out.

Is feh in the reps? I tried apt-get install feh, but no luck.

---

### Post by kerry_s on 2007-03-18
Yes, feh is in the repos, it's in universe, you just need to turn all your repositories on.

---

### Post by pt123 on 2007-03-18
I tried mirage & feh but they also don't delete to the trash can.

But I found that I can open GQView with out the explorer interface using -t. 

I will use that for the time being till I find an app that can delete to the trash can & without the confirmation dialog box.

---

### Post by Ajd on 2007-04-09
I hate to drag up an old post, but gthumb deletes to the trash can and you can turn off the confirmation dialog.

---

