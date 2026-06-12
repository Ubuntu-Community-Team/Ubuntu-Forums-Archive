---
title: "Odd question about image urls"
date: 2016-01-23
forum: General Help
---

### Post by Dave_Langston on 2016-01-23
I've only recently switched my laptop from win10 to unbuntu_studio. Naturally the are a lot of things I need to learn and that's why I've here when I can't figure something out by myself.

But here's one thing I am struggling with, but perhaps no one else will see it as important but for me it is.

I often have to take images from one place on the internet and post them on another. In my past world of Windows I could do this simply by copying the path to an image (url) into the explorer open dialogue. Example; Lets say it's Facebook - so you click on "add image" select an image from your computer, except here I would simply paste the image url and it would be uploaded. But when I choose to add an image in ubunto the is no option to copy the url just option for places to select the images from in the file manager.

Does anyone know how I can get around this? as without it I'll need to copy each image to my laptop then upload and then delete from my laptop. It may should trivial but not if you do it often enough.

---

### Post by TheFu on 2016-01-24
Unix systems use "select / paste" as the method that other systems use as "copy/paste".  Just selecting any text should be enough for it to be in the "x-buffer" and ready to be pasted using the middle-mouse button.

Don't know if that helps or not.  If you are looking for an auto-upload-to-somewhere-else using a URL ... that isn't the way I'd do it.  I'd write a tiny script to grab the interesting URLs from a page, then push those somewhere else. It would take about 3-30 min to create the script (URL parsing can be non-trivial), but after that, the script would work for any page on that specific source website.  With Unix, we think differently.  Trying to do things exactly the same way you did it on "other OSes" usually leads to frustration.  

I'm not saying there are tools to do what you want the old way - just saying I don't know any beyond the obvious, right-click cntl-a or right-click --> Share stuff that I'm certain you've seen and used. This is browser specific and most browsers have addon/plugins for added image/video handling.  I've never used facebook, so don't know how that works there or on any other "social" website. Sorry.

[http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - people ask me how to learn Linux enough that I wrote a blog article with specific links to read in specific order to get your mind right. Hope those help. You've probably already seen the first few.

---

### Post by JOHN_ELLIS on 2016-01-24
Hi,

I think I understand your question.

Can't you just right click the image you want, save it is a jpeg or whatever file type you are using and when you want to upload it again, go through the file explorer and select the image you saved.

Hope this helps

John

---

### Post by pfeiffep on 2016-01-25
> **Dave_Langston said:**
>  <snip>
I often have to take images from one place on the internet and post them on another. In my past world of Windows I could do this simply by copying the path to an image (url) into the explorer open dialogue. Example; Lets say it's Facebook - so you click on "add image" select an image from your computer, except here I would simply paste the image url and it would be uploaded. But when I choose to add an image in ubunto the is no option to copy the url just option for places to select the images from in the file manager.

Does anyone know how I can get around this? as without it I'll need to copy each image to my laptop then upload and then delete from my laptop. It may should trivial but not if you do it often enough.I think I understand ... here's my proposed solution. 
I'm using:[INDENT]Ubuntu 14 LTS with gnome-session-flashback desktop environment (metacity)
Fire Fox 43.0.4
[/INDENT]
When I right click an image I am presented with a list of options - I chose _**copy image location**_
I believe a similar option is available in Chrome

---

