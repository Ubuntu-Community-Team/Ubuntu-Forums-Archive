---
title: "How to post hundreds of photos on a website?"
date: 2022-12-20
forum: General Help
---

### Post by satimis on 2022-12-20
Ubuntu 22.04 desktop

Hi all,

I have hundreds of old photos and expect creating a WordPress website for posting all of them.  

I have tried following 2 methods:-
1) Install photo gallery packages such as (for example) New Generation galley
But the mini-photos will take up large space of the webpage.

2) Creating slideshow using (for example) OpenShot, uploading it to YouTube and then embedding its URL on the webpage
The disadvantage:
Visitor has to view the whole slideshow before finding the needed photos and capture them with screenshot.

Please advise whether there is a third solution?  Or creating a mini-preview of the slideshow on the webpage?

Thanks in advance.

Regards

---

### Post by Dennis N on 2022-12-21
If you use Google drive, upload all images to a single folder, then share the folder using the "anyone with the link" option. Get and send out the link.

Selecting "grid layout" for the folder will display thumbnails of the images, with links for download each image as well. What I don't know is whether your setting grid layout also makes it the layout for others besides yourself. If not, the viewer can set it.

You have 15 GB of free space on Google drive. You can buy more space from Google if needed.

---

### Post by satimis on 2022-12-21
> **Dennis N said:**
> If you use Google drive, upload all images to a single folder, then share the folder using the "anyone with the link" option. Get and send out the link.

Selecting "grid layout" for the folder will display thumbnails of the images, with links for download each image as well. What I don't know is whether your setting grid layout also makes it the layout for others besides yourself. If not, the viewer can set it.

You have 15 GB of free space on Google drive. You can buy more space from Google if needed.
Hi,

Thanks for your advice.  I never use Google drive before.  It looks similar to Dropbox.

I prefer retaining all photos on my own website which is a private site, not open to public. Only relatives and acquaintance with password can login and browse the website.

The photos are marked with numbers.  They can email me requesting for a copy of the photos

OR
On New Gen Gallery.
They can download them direct on the website

OR
On slideshow, 
they can capture and save the photos direct on the website

Personally I prefer "slideshow" but I can't solve the preview problem.  Otherwise the visitor has to view the complete slideshow.

On googling I found "Shotwell Photo Manager"
[https://shotwell-project.org/doc/html/](https://shotwell-project.org/doc/html/)

and
imageindex - a digital photo gallery tool
[http://www.edwinh.org/imageindex/](http://www.edwinh.org/imageindex/)

Can I use them ?

Regards

---

### Post by dragonfly41 on 2022-12-21
[COLOR=#000000]> I prefer retaining all photos on my own website which is a private site, not open to public. Only relatives and acquaintance with password can login and browse the website.

[/COLOR]These are ideas I am developing for my own purpose:

1. Open an account with Tresorit.com.
You can them place your photos in a Tresorit folder which is synced with Tresorit server in cloud. But importantly all content is encrypted and subject to Swiss  privacy jurisdiction.
Then you can refer  private photo galleries to individuals or groups by sending links.
You can also revoke content.

2. If your preference is slide shows then explore zettlr.com and [read the documentation on  publishing presentations from markdown content]("https://docs.zettlr.com/en/academic/presentations/").

Here you can create your own slideshows and export as Reveal.js presentations.  [https://revealjs.com/](https://revealjs.com/)
These  Zettlr presentations are placed in your Tresorit folder in your local desktop where they are grabbed and synced with your Tresorit cloud account.
Then you just publish  personalised links to your encrypted slideshows. Using Reveal.js you can add commentaries and personalise.

---

### Post by satimis on 2022-12-21
> **dragonfly41 said:**
> [COLOR=#000000]

[/COLOR]These are ideas I am developing for my own purpose:

1. Open an account with Tresorit.com.
You can them place your photos in a Tresorit folder which is synced with Tresorit server in cloud. But importantly all content is encrypted and subject to Swiss  privacy jurisdiction.
Then you can refer  private photo galleries to individuals or groups by sending links.
You can also revoke content.

2. If your preference is slide shows then explore zettlr.com and read the documentation on  publishing presentations from markdown.
Here you can create your own slideshows and export as Reveal.js presentations.  [https://revealjs.com/](https://revealjs.com/)
These  Zettlr presentations are placed in your Tresorit folder in your local desktop where they are grabbed and synced with your Tresorit cloud account.
Then you just publish  personalised links to your encrypted slideshows. Using Reveal.js you can add commentaries and personalise.
Hi,

Thanks for your advice.

I have already done it.  My website is now running on Internet.  Only relatives and friends being invited can login with password and can browse the website.  The password is changed periodically.

My real headache is creating a preview of the slideshow.  Otherwise they have to view the complete slideshow to find out the photos which they need.

Regards

see photo attached

---

### Post by dragonfly41 on 2022-12-21
With a bit of juggling and research you can create an overview in Reveal.js as [shown here]("https://revealjs.com/vertical-slides/").
In other words create a helicopter view of thumbnail photos.

Yet another perhaps simpler idea to explore is to build a container of photos using CherryTree.
This gallery can be password protected (there are four options) and embed a photo inside "nodes" in the hierarchy.

CherryTree can be exported as a series of HTML pages, with a Table of Contents (TOC).

But of course with this approach you cannot revoke published content (as in Tresorit). But you can export Cherrytree content into Tresorit and use the advantage of encryption.

I use tools such as CherryTree and Actiona in a toolchain to automate processes.


P.S. You can also look for and add plugins to Reveal.js presentations. One [example plugin is here]("https://stackoverflow.com/questions/61072343/how-to-make-toc-show-up-in-rmarkdown-revealjs-slides") to give your summary gallery list of contents.

Yet another tool to use is VSCode with Markdown Preview Enhanced installed.  This is similar to Zettlr editor.

---

### Post by Dennis N on 2022-12-21
> I prefer retaining all photos on my own website which is a private site, not open to public.
Your files on Google drive are NOT open to the public. Initially, you are the only person who can see them. You decide by setting the sharing options who can view them.

---

### Post by satimis on 2022-12-21
> **dragonfly41 said:**
> With a bit of juggling and research you can create an overview in Reveal.js as [shown here]("https://revealjs.com/vertical-slides/").
In other words create a helicopter view of thumbnail photos.

Yet another perhaps simpler idea to explore is to build a container of photos using CherryTree.
This gallery can be password protected (there are four options) and embed a photo inside "nodes" in the hierarchy.

CherryTree can be exported as a series of HTML pages, with a Table of Contents (TOC).

But of course with this approach you cannot revoke published content (as in Tresorit). But you can export Cherrytree content into Tresorit and use the advantage of encryption.

I use tools such as CherryTree and Actiona in a toolchain to automate processes.


P.S. You can also look for and add plugins to Reveal.js presentations. One [example plugin is here]("https://stackoverflow.com/questions/61072343/how-to-make-toc-show-up-in-rmarkdown-revealjs-slides") to give your summary gallery list of contents.

Yet another tool to use is VSCode with Markdown Preview Enhanced installed.  This is similar to Zettlr editor.
Hi,

Lot of thanks for your advice.

Still I couldn't resolve how can I create a preview of the slideshow which has been upload to YouTube?

Regards

---

### Post by satimis on 2022-12-21
> **Dennis N said:**
> Your files on Google drive are NOT open to the public. Initially, you are the only person who can see them. You decide by setting the sharing options who can view them.
Your advice noted and thanks

Regards

---

### Post by mIk3_08 on 2022-12-26
> **satimis said:**
> Hi,

Lot of thanks for your advice.
Still I couldn't resolve how can I create a preview of the slideshow which has been upload to YouTube?

Regards

Are you using your current web hosting storage for your photos or you are just uploading your photos to other commercial cloud and run it into your own website?

---

### Post by satimis on 2022-12-26
> **mIk3_08 said:**
> Are you using your current web hosting storage for your photos or you are just uploading your photos to other commercial cloud and run it into your own website?
I'll use the current web hosting storage for my photos.

I'm subscribing share-hosting with unlimited storage. The hosting company counts the number of files upload and there is a limitation therefore I prefer creating slideshows on photos.  On the slideshows I can add background music, subtitles, narration etc.  I'm now searching for a solution to create a preview

Regards

---

### Post by satimis on 2022-12-26
**[COLOR="#FF0000"]Further to my late posting[/COLOR]**

Now I'm doing it in following way;

**[COLOR="#FF0000"]1.[/COLOR]** Create a private website on Internet.  Only invited visitors can browse this private site with password which is changed periodically.  I'm not going to discuss how?  There are methods available on Internet.

[COLOR="#FF0000"]**2.**[/COLOR] All old photos are retained on their own folders, marked, and all old photos are also marked with file and folder names.

**[COLOR="#FF0000"]3.[/COLOR]** For old photos less than 10, I'll post them on "gallery".  Visitors can download the selected photos on their own computer running screenshot.

**[COLOR="#FF0000"]4.[/COLOR]** For old photos exceeding 10, I create slideshow for each folder and upload the slideshows to YouTube.  Then embed the slideshows on the private website.  If visitors need to have the photos on the slideshow, they can request for them by email, indicating the name of the slideshow.  Then I'll email them a .pdf file consisting all photos on that slideshow.  The .pdf files have already been created in advance.

I operate this way sometimes.  Now I'm looking for whether there will be a better way ?

Regards

---

### Post by mIk3_08 on 2022-12-27
> **satimis said:**
> **[COLOR=#FF0000]Further to my late posting[/COLOR]**

Now I'm doing it in following way;

**[COLOR=#FF0000]1.[/COLOR]** Create a private  website on Internet.  Only invited visitors can browse this private site  with password which is changed periodically.  I'm not going to discuss  how?  There are methods available on Internet.

[COLOR=#FF0000]**2.**[/COLOR] All old photos are retained on their own folders, marked, and all old photos are also marked with file and folder names.

**[COLOR=#FF0000]3.[/COLOR]** For old photos less  than 10, I'll post them on "gallery".  Visitors can download the  selected photos on their own computer running screenshot.

**[COLOR=#FF0000]4.[/COLOR]** For old photos  exceeding 10, I create slideshow for each folder and upload the  slideshows to YouTube.  Then embed the slideshows on the private  website.  If visitors need to have the photos on the slideshow, they can  request for them by email, indicating the name of the slideshow.  Then  I'll email them a .pdf file consisting all photos on that slideshow.   The .pdf files have already been created in advance.

I operate this way sometimes.  Now I'm looking for whether there will be a better way ?

Regards
Now, about your website? Are you using content  management system on it? If not, what web programing language platform  are you using? 
> If visitors need to have the photos on the slideshow, they can request for them by email 
Are you considering URL for this slideshow to be shared by your visitors?
Regards and cheers.

---

### Post by satimis on 2022-12-27
> **mIk3_08 said:**
> Now, about your website? Are you using content  management system on it? If not, what web programing language platform  are you using? 

A private WordPress website not open to public.  Only invited visitors can browse this private website with password.

> 
Are you considering URL for this slideshow to be shared by your visitors?

The slideshows upload to YouTube are NOT open to public.  Invited visitors can only browse them on the private website.

[B][COLOR="#FF0000"]Edit-1
===[/COLOR][/B]
I can upload the slideshows direct on the private website.  But the server speed can't be compared to the speed of YouTube website.

[B][COLOR="#FF0000"]Edit-2
====[/COLOR][/B]
It is absolutely impossible stopping 100% redirection.  E.G. Visitors can resend the .pdf files after receipt of the files.

Regards

---

### Post by mIk3_08 on 2022-12-28
> **satimis said:**
> A private WordPress website not open to public.  Only invited visitors can browse this private website with password.


The slideshows upload to YouTube are NOT open to public.  Invited visitors can only browse them on the private website.

[B][COLOR=#FF0000]Edit-1
===[/COLOR][/B]
I can upload the slideshows direct on the private website.  But the server speed can't be compared to the speed of YouTube website.

[B][COLOR=#FF0000]Edit-2
====[/COLOR][/B]
It is absolutely impossible stopping 100% redirection.  E.G. Visitors can resend the .pdf files after receipt of the files.

Regards

The image slideshow will be a video then. I see, you can still upload it to YouTube and make it private. I just don't how to share it with a unique url or the url must have an expiration or something that has a secured purpose of distribution.
Regards and cheers

---

### Post by satimis on 2022-12-28
> **mIk3_08 said:**
> The image slideshow will be a video then. I see, you can still upload it to YouTube and make it private. I just don't how to share it with a unique url or the url must have an expiration or something that has a secured purpose of distribution.
Regards and cheers
Hi,

It is impossible making your private site 100% absolutely private.  The invited visitors can give the login password to their acquaintances.

Regards

---

### Post by mIk3_08 on 2022-12-29
> **satimis said:**
> Hi,
It is impossible making your private site 100% absolutely private.  The invited visitors can give the login password to their acquaintances.
Regards
Yes. I agree with it. All i can say is that belated Merry Christmas and Advance Happy New Year. God Bless. Regards and cheers.

---

