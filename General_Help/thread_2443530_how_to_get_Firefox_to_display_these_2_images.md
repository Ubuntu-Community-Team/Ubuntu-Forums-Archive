---
title: "how to get Firefox to display these 2 images"
date: 2020-05-16
forum: General Help
---

### Post by Skaperen on 2020-05-16
how can i get Firefox to display these 2 images, 1 at a time, directly, so i can use Firefox's display magnification that i am already accustomed to?  it is trying to run an application for them.  the web site with the 2 images is [here]("https://www.findagrave.com/memorial/141099909/brice-howard").

---

### Post by monkeybrain20122 on 2020-05-16
You mean like the attached screenshots?

That is a pretty morbid website.

---

### Post by Skaperen on 2020-05-16
yes, like those 2 ... i have the image URLs.  but when i try to get Firefox to display those, it asks me which external application to use (i want to use Firefox).  it also gives me the option to save the image.  this is not the only page with this issue.  many sites have this issue.  i just want to enlarge the image to look at it more easily and Firefox can do that if it will just display it.  otherwise it's a hassle to find the file and the right option on the convert command and then the display command.

this website is a popular website for genealogy research.  this particular page is my great-great-grandfather.  i have info online [here]("https://www.wikitree.com/wiki/Howard-22149").

---

### Post by monkeybrain20122 on 2020-05-16
I didn't do anything special, I just clicked the image and it showed up like that. 

Maybe you have some addon that interferes with it or your profile is corrupted? 

Test this way:
close firefox.  
open the file manager, show hidden files (ctrl + h or from menu) find the folder .mozilla (see the "." in front) rename it something else like .mozilla-bk
now start firefox to see if it works.

to go back to old profile
close firefox,
delete .mozilla
rename .mozilla-bk back to .mozilla.

---

### Post by Skaperen on 2020-05-17
no addons.  here is what a fresh mozilla does when i have it go to the image URL which you can see in [this screenshot]("http://ipal.net/u/20200517141634032324790.png") which is 1920x1080 (HD 2k).  i upgrade regularly and did one last night just after midnight preceded and followed by a reboot.

---

### Post by Holger_Gehrke on 2020-05-17
Not much you can do about it, it's a server-side misconfiguration. For some of the images it sends a content-type of 'binary/octet-stream' instead of 'image/jpeg'. Even if you copy the image-url and open it in a new tab Firefox will offer to download it. You could set it to open with firefox (it will then download the image to /tmp and open it from there) or you could use the zoom on the page with the image or you could use XFCE's zoom (alt+mouse wheel).

Holger

---

### Post by Skaperen on 2020-05-17
so, how does **monkeybrain20122** manage to get them to directly display?  how can i do "*You could set it to open with firefox (it will then download the image to /tmp and open it from there)*"?

---

### Post by Skaperen on 2020-05-17
it should just internally download enough of it to figure out if it can do something with it and at least include that as a choice in that prompt.  once it sees what kind of JPEG it is, and can display it, it should at least know it can.  having MIME types and other features of a rich media world seems to have encouraged lazy software.

---

### Post by monkeybrain20122 on 2020-05-17
What happens if you try with a live usb? I did and it still works.

---

### Post by Holger_Gehrke on 2020-05-17
> **Skaperen said:**
> so, how does **monkeybrain20122** manage to get them to directly display?
If you look at the screenshots and not just at the thumbnails you can see that it's just the javascript image viewer on findagrave.com which you can activate by left-clicking on an image and which doesn't play nicely with zooming since it's just a div overlayed on the page.

> **Skaperen said:**
> how can i do "*You could set it to open with firefox (it will then download the image to /tmp and open it from there)*"?

By selecting "Open with"->"Other"->"Show all applications"->"firefox" (actual wording of these options might differ, I'm translating from the German UI in my Firefox) in the  dialog you posted. And doing that is not really a good idea since firefox remembers that choice and "binary/octet-stream" is a catch-all type usually used for files you can't show in the browser and want / need to download.

Holger

---

### Post by Holger_Gehrke on 2020-05-17
> **Skaperen said:**
> it should just internally download enough of it to figure out if it can do something with it and at least include that as a choice in that prompt.  once it sees what kind of JPEG it is, and can display it, it should at least know it can.  having MIME types and other features of a rich media world seems to have encouraged lazy software.

No, the whole point of the mime-type system is for the server to do the work of finding out the type once and storing it and for the clients to be able to trust this type data.

Also, if you left click on the image and open it in the JavaScript viewer **then** right click on the image in the viewer and select "Show Graphics" and middle-click on that it will open the image in a new Firefox tab, because if you do it like that the server sends a different (correct) type. It is either a misconfiguration or developer laziness on part of the makers of the web site.

Holger

---

### Post by norobro on 2020-05-17
> **Holger_Gehrke said:**
>  It is either a misconfiguration or developer laziness on part of the makers of the web site.
+1

In the lower right corner of the viewer window is a hyperlink "View original". After clicking on the link I can enlarge the image with ctrl++ or right-click, copy the url and bring it up in a new tab.

---

### Post by Skaperen on 2020-05-18
> **monkeybrain20122 said:**
> What happens if you try with a live usb? I did and it still works.

it's a bit complicated due to the way my free internet access works.  web access only works through a misconfigured proxy.  so i get around it with a VPN.  i'd have to set that up on the live to get normal web access here.  and i'd still want to solve it here where i'm running a more recent Firefox.

---

