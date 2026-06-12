---
title: "computer no longer will display photos"
date: 2023-08-21
forum: General Help
---

### Post by jgw on 2023-08-21
This computer will no longer display photos and I don't know why.  I have just re-constituted this computer (re-installed ubuntu 22.04.3, etc).  Now, when I try and display photos each one is treated as if its a folder instead of a photo.  I have tried several things off the net and nothing worked.  I suspect that I might have installed something that has caused this but I have no idea what it might be.  I have looked a the gnome extensions and they look allright to me but, still, I wonder.  

Thoughts?

---

### Post by yancek on 2023-08-21
Do you mean  that you have photos in some directory in your /home/username directory (or elsewhere) and that they do not open when you click on them?  I'm not sure I understand what you mean by being treated as a folder rather than an image file.  What exactly happens?  Have you tried right clicking on a photo image and see if it shows to open with Image Viewer? If it is not set correctly, you can select to open with another application and select the proper software.

---

### Post by jgw on 2023-08-21
Yep - I have tried everything.  I have a folder with a bunch of photos.  they are treated as if they were just regular folders.  If I click on one of them it comes up as if it was a regular empty folder as well.  Its very strange.  Its like the time in the top bar.  I wanted it to be am/pm, its not.  Checked settings and its set right but getting ignored. There was also a 3 line choice which gave me many (normal) choices. I choose preferences and the following were on: 
document statistics
external tools
file browser panel
modelines
open links
sort 
spell checker

There was also other choices but nothing of interest.  I also changed my display driver from nvidia to the other and it made no difference at all.  I also install darktable and it will show a photo.

I am tempted to try and replace the existing ubuntu with a new one.

I also noticed that I have a tiny red dot in the top bar which said I have an error.  Here is the error:
reg@videos:~$ apt list --installed
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I tried to open status but ubuntu said it was an unknown file type.  There was also an status_old file.  They both had the same time on them.  I am tempted to get rid of the bad one and rename the old one. So, I deleted the status file and tried to rename the old one to 'status'.  The only problem is that I don't have 'mv' and can't figure out how to install it.

Thoughts?

---

### Post by The Cog on 2023-08-22
Thy this: Right-click an icon of a photo, to get a pop-up menu of options. Select "Properties". Make sure that under Basic, the Type is reported as an Image file, and if not then look for further help here. If it is recognised as an Image file, click Open With and select your chosen viewer program, and set that as default.

---

### Post by HermanAB on 2023-08-22
The likely problem is that the file type and programs associations (MIME types) are messed up.  Some googling will  show you how to fix it.

Until then, simply launch a photo viewer/editor (e.g. Gimp) and then use its file menu to find and view pictures.

---

### Post by jgw on 2023-08-22
I figured out the thing about the status and status_old.  I deleted the bad status, renamed the status_old to "status" and saved it.  The problem went away.  Just became a super user and changed the name of status_old after I deleted the other one.  I should have saved it in case but took a deep breath and did it.  Never did figure out how to install "mv".

---

### Post by jgw on 2023-08-22
Thaink you for for the suggestion.  I did as you said and when I did I actually got a picture!  I then opened a file with a bunch of jpg's and every one was presented as a photo!  System solved!

---

### Post by jgw on 2023-08-22
I just turned on the computer and then went to a page of photos.  I recognized .png photos but not .jpg photos - they consider those to be: "plain text document (text/plain)".  I have no idea why. 

Thoughts?

---

### Post by HermanAB on 2023-08-23
The MIME type association of JPG files messed up.  Do as The Cog suggested above to fix it. “Right click, open with, … default…”

---

### Post by jgw on 2023-08-23
Yesterday it was working fine and recognizing all pictures and photos.  The system thinks that its an empty text file (plain text document (text/plain))  I then tried to open a .jpg file with gimp and got:
Empty input file
gimp message
Opening '/home/greg/wallpaper/2011.788.JPG' failed:
JPEG image plug-in could not open image

So, I know my system can recognize photos, etc. because it would do it yesterday.  then I turned off my machine and then started it again and it could no longer recognize photos.  If gimp can't recognize a photo then something is seriously wrong.  

Then, for the heck of it, I re-started my machine, nothing changed, EXCEPT it now recognizes photos.  I have something very strange going on.  

Thoughts?

---

### Post by ajgreeny on 2023-08-23
What output do you get from commands ```
file /home/greg/wallpaper/2011.788.JPG
ls -l /home/greg/wallpaper/2011.788.JPG
```

---

### Post by jgw on 2023-08-23
I kinda fixed the problem.  I moved all the drives (30) to another computer and moved its 2 drives to the bad computer.  This fixed the problems and everything is working just fine.  Have no idea why but I thought I would do it and it worked!  I took care of my problem (kinda)

Thank you all for all the help.  I feel a little embarrassed about this but I did what I did and it worked.   Thanks again!!

---

### Post by jgw on 2023-08-26
Thank you for the reply.......

Here is what you asked:
greg@greg-System-Product-Name:~$ file /home/greg/wallpaper/2011.788.JPG
/home/greg/wallpaper/2011.788.JPG: empty
greg@greg-System-Product-Name:~$ ls -l /home/greg/wallpaper/2011.788.JPG
-rw-rw-r-- 1 greg greg 0 Oct  3  2011 /home/greg/wallpaper/2011.788.JPG

The wallpaper file is full of wallpapers....

I decided to redo my entire machine, including ubuntu.  Now I no longer cannot see photos but I can only see one of my drives and I have 3 of them.  I can put them all on an external and they all work just fine.  I have swapped out connectors, etc. to no avail, still fighting the good fight.  I am also dealing with two machines and they are both behaving in exactly the same way.  The Ubuntu I used was ubuntu 22.04.04

---

