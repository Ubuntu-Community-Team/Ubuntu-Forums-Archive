---
title: "How to store and share old digital photos"
date: 2022-06-15
forum: General Help
---

### Post by satimis on 2022-06-15
Hi all,

What will be an ideal way to store old digital photos and to share the old photos amongst friends and acquaintance

1) My own website
2) Google Photos (iOS, Android)
3) Any other ways?

Store photos on album built on the website
Or
Create slideshow on photos with background music, subtitle, narration added

Any other suggestions?  Thanks

Regards

---

### Post by Dennis N on 2022-06-15
Create a PDF book of photos with commentary. You can use Scribus to do a nice job of it. Done that.

---

### Post by satimis on 2022-06-15
> **Dennis N said:**
> Create a PDF book of photos with commentary. You can use Scribus to do a nice job of it. Done that.
Hi,

Thanks for your advice.

Whether you refer to;

Scribus - Open Source Desktop Publishing
[https://www.scribus.net/](https://www.scribus.net/)

Regards

---

### Post by Dennis N on 2022-06-15
Yes, that's it. It is also in the Ubuntu repository, and a Flatpak I believe. It seemed complicated at first, but it was worth it. There will be tutorials somewhere for sure.

---

### Post by yog-sothoth-cat on 2022-06-15
Put them all into a cloud service like google drive. That way, anyone with the link can access the photos instead of needing a local copy. You just send them the link and they get all the pictures without a hassle.

---

### Post by pantazi on 2022-06-15
Flickr

---

### Post by satimis on 2022-06-15
> **Dennis N said:**
> Yes, that's it. It is also in the Ubuntu repository, and a Flatpak I believe. It seemed complicated at first, but it was worth it. There will be tutorials somewhere for sure.

Scribus is available on repo of Ubuntu 20.04
$ apt policy scribus```

scribus:
  Installed: (none)
  Candidate: 1.5.5+dfsg-6build1
  Version table:
     1.5.5+dfsg-6build1 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```
Or
Install Scribus via PPA

Or
Running Flatpak to install Scribus
Install```

$ flatpak install flathub net.scribus.Scribus

```
Run```

$ flatpak run net.scribus.Scribus

```

Regarding tutorials, there is abundant on Internet, such as;
1)
Scribus In-Depth Tutorial by Donald Emmack
[https://www.tuxmagazine.com/node/1000225/](https://www.tuxmagazine.com/node/1000225/)
2)
Book layout with Scribus [1st Part]
[https://blog.desdelinux.net/en/maquetacion-libro-con-scribus-1/](https://blog.desdelinux.net/en/maquetacion-libro-con-scribus-1/)

etc.
**[COLOR="#FF0000"]I wonder where shall I start ?[/COLOR]**

Following tutorial draws my attention;
How to Prepare a Digital Edition PDF Book With Scribus
[https://www.drivethrurpg.com/shared_images/HowToSCRIBUS-digital.pdf](https://www.drivethrurpg.com/shared_images/HowToSCRIBUS-digital.pdf)

To my understanding I can create a Digital Old Photo PDF book.  [B][COLOR="#FF0000"]Is it correct?
If YES, then I can give this PDF book to friends as "souvenir "[/COLOR][/B]

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
**A further thought;**
I suppose I can use Libre Office to create a PDF book/album, just pasting the old photos on its document.  Then export Libre Office document as pdf file.

If possible, then the solution is much simpler.  I don't need to spend time learning Scribus.

Regards

---

### Post by satimis on 2022-06-15
> **yog-sothoth-cat said:**
> Put them all into a cloud service like google drive. That way, anyone with the link can access the photos instead of needing a local copy. You just send them the link and they get all the pictures without a hassle.
Thanks for your advice.

I have my own websites running on Internet.  I can create a new website particularly for posting old photos.  There is storage limitation on Google cloud but I have no storage limitation on my websites.

I won't just post the old photos on my website.  I would create slideshows on old photos, adding background music, narration, subtitles etc.  In the past, I have done many times creating slideshows on photos.  Besides I'll upload the slideshows to YouTube instead of uploading them to the server of the hosting company of my websites and then embedding the links on my websites.  The server speed of YouTube is much faster.

Regards

---

### Post by Dennis N on 2022-06-16
Did you consider: what if the person you want to view your photos doesn't use a computer? Like your grandparents or great-grandparents? The advantage of desktop publishing software is that the book you create is a printable PDF.

---

### Post by satimis on 2022-06-16
> **Dennis N said:**
> Did you consider: what if the person you want to view your photos doesn't use a computer? Like your grandparents or great-grandparents? The advantage of desktop publishing software is that the book you create is a printable PDF.
Good question.

I'm not going to print the digital photos.  Neither I have a printer.  If they want to view the photos I still have hard copy photos.  The digital photos are created by scanning the hard copy photos.

What I need to consider now is running Scribus to create the PDF album or using LibreOffice to do the job ?  The digital photos can be copied and pasted on LibreOffice document. For graphics I'll run GIMP/Blender etc. to do the job and copy them on LibreOffice document which can be exported as PDF file.

I'm now browsing on Internet learning how other people creating description and attractive wordings on their digital albums ?  Can  you help?

Regards

---

### Post by Dennis N on 2022-06-16
As far as printing goes, you can put the finished PDF document on a usb stick and take it to a print shop or other store that does printing and have them print as many copies as you need.  I once made a family history book to distribute to my relatives as a gift. I do genealogy as a hobby (besides computers!). 

100 years from now, would your website still exist? Or even a computer file? A printed history stands a good chance. Things on paper can last centuries.

---

### Post by satimis on 2022-06-16
> **Dennis N said:**
> As far as printing goes, you can put the finished PDF document on a usb stick and take it to a print shop or other store that does printing and have them print as many copies as you need.  I once made a family history book to distribute to my relatives as a gift. I do genealogy as a hobby (besides computers!). 
Thanks for your advice.  I'm now searching on Internet to see other people's works.  I couldn't invent something from nothing.

> 
100 years from now, would your website still exist? Or even a computer file? A printed history stands a good chance. Things on paper can last centuries.
That is why I prefer building digital slideshows and upload them to YouTube.  A further thought, after centuries who know the people on the slideshows?

Do you have any idea to post the PDF file on my website?  Visitors can read its content by clicking a sample page posted.

Regards

---

### Post by ActionParsnip on 2022-06-16
Could setup a web facing SFTP server with SSH keys as the only authentication method. Users can then mount this remotely an d browse at their leisure

---

### Post by satimis on 2022-06-16
> **ActionParsnip said:**
> Could setup a web facing SFTP server with SSH keys as the only authentication method. Users can then mount this remotely an d browse at their leisure
Thanks for your advice.

I don't know whether the hosting company would allow me to setup SFTP server?  I'm subscribing shared hosting.

I'm now reading following document;
How to Add PDF Files to Websites
[https://www.lifewire.com/add-pdf-files-to-web-sites-2654722](https://www.lifewire.com/add-pdf-files-to-web-sites-2654722)

I can upload PDF files to my website via File Manager on cPanel.  I don't whether it will work?

Regards

---

### Post by HermanAB on 2022-06-16
Possibly the best way to share stuff with friends is with Retroshare.  [https://retroshare.cc/](https://retroshare.cc/)

---

### Post by ActionParsnip on 2022-06-16
If you can SSH to a server then it is already an SFTP server.

---

### Post by satimis on 2022-06-16
> **HermanAB said:**
> Possibly the best way to share stuff with friends is with Retroshare.  [https://retroshare.cc/](https://retroshare.cc/)
Thanks for your advice.

It is not solely for sharing.

I need to post all photos on my website. I have all photos on the PDF file.  It would save me lot of time if I can integrate the PDF file on the website.  Otherwise I have to post all photos on my website again.

Regards

---

### Post by satimis on 2022-06-16
> **ActionParsnip said:**
> If you can SSH to a server then it is already an SFTP server.
I don't have another server.  My local server is NOT running 24hrs.

Another thought, maybe I can run;
```

$ convert -density 300 photo.pdf photo.png

```
It'll convert all pages of PDF file to photo.png files.  Then I can post each photo.png on my website.

Regards

---

### Post by QIII on 2022-06-17
Storing and sharing are really two different things.

You've had several suggestions for sharing.  

Might I recommend that for storage of things that just can't be replaced you use mechanical drives?  Old School Rust has been shown to be stable for decades.  Although I am sure by now that solid state is pretty stable, there is still charge leak-down that can cause degradation over time.  Similar degradation on mechanical drives is far, far slower.  Store more than one copy of everything and do that in different locations if you can.  You don't want a lightning strike on the electrical transformer down the street to obliterate your last few surviving images of Granny.

---

### Post by mIk3_08 on 2022-06-17
> **Dennis N said:**
> Create a PDF book of photos with commentary. You can use Scribus to do a nice job of it. Done that.
Wow. cool stuff. Regards and cheers.

---

### Post by Impavidus on 2022-06-17
Packing all photos in a pdf file makes it easy to send it to some printing service to get a paper photobook, but for on-line distribution it has a disadvantage: people can only download all your photos at once. No matter how much your friends love you, they may not want to see all your pictures. It's best if people can browse them somewhat ordered by subject. Maybe you can move the lower quality pictures to a less prominent position. Before digital photography, people made fewer low-quality pictures than today because you could only put 37 pictures on a roll instead of hundreds, but still.

For photos, png format is much larger than jpeg without a significant difference in quality, unless you want to do further processing of the pictures. Pdf supports a number of compression algorithms to store raster image data, both lossy (the same as jpeg) and lossless (like png) or no compression at all.

---

### Post by dragonfly41 on 2022-06-17
One easy method of creating an online photo (and if you wish commentary) library is to use Markdown editor in association with Markdown Preview Enhanced extension

There are several editors you can use (I try all these)

Atom
Sublime Text
Visual Studio Code

In the Markdown Preview mode you can select output which uses reveal.js library.

[https://revealjs.com/](https://revealjs.com/)

You can publish your image library in any mode you choose. Online slide deck, eBook.

The developer of reveal.js went on to apply this in slides.com as a service but reveal.js is still free.

Pandoc also outputs to reveal.js.


[P.S.] Specifically see embed images here.

[https://shd101wyy.github.io/markdown-preview-enhanced/#/file-imports](https://shd101wyy.github.io/markdown-preview-enhanced/#/file-imports)

[COLOR=#525252][FONT=&amp]@import "test.png" {width="300px" height="200px" title="my title" alt="my alt"}[/FONT][/COLOR]

You can also embed audio commentary or add notes as fragments..


[P.P.S.]

For those using Scribus you can use ScribusGenerator plugin and create a CSV sheet
containing links to all your images. This inserts vars into Scribus image frames.

---

### Post by schwim-dandy on 2022-06-17
I didn't see it get mentioned yet but if you are subscribed to Amazon Prime, they offer free unlimited storage and there's quite a few bells and whistles included.  For instance, once I told the system who grandma was, it sorted through the thousands of images to find her.  Now when her granddaughter searches for grandma, the photos with her found in them are returned.

---

### Post by satimis on 2022-06-17
I have >1,000 old photos to be scanned as digital images on my smartphone

After scanning, the images will be classified into categories;

Group-1
Group-2
Group-3
etc.

I'll copy Group-1 images to LibreOffice Writer, do all editing on Writer  and after finish I'll export the file as group-1.pdf

I'll copy Group-2 images to LibreOffice Writer, do all editing on Writer  and after finish I'll export the file as group-2.pdf

.....  etc.

Then I'll have group-1.pdf, group-2.pdf, group-3.pdf, group-4.pdf.... files

I'll send them as sourvenir to;

Friend-A - group-1.pdf
Friend-B - group-2.pdf group-3.pdf
Friend-C - group-1.pdf group-4.pdf group-5.pdf
Friend-D - group-2.pdf group-5.pdf
etc.

I'll not post all images on my WordPress website.  I'll perform following steps
1) Select the group-x pdf files to be posted on WordPress website

2) Run;
```

$ convert -density 300 group-x.pdf page.png

```
convert all pages of each PDF file as page.png images. 

3) Install "NextGEN Gallery" plugin on WordPress website

4) Upload page.png images to the website

Now people can browse the photos on each page.png image.

The only drawback is the photos maybe small to view without magnifying.

Suggestion would be appreciated.  Thanks

Regards

---

### Post by TheFu on 2022-06-17
> **satimis said:**
> Hi all,

What will be an ideal way to store old digital photos and to share the old photos amongst friends and acquaintance

1) My own website
2) Google Photos (iOS, Android)
3) Any other ways?

Store photos on album built on the website
Or
Create slideshow on photos with background music, subtitle, narration added

Any other suggestions?  Thanks

Regards

For storage, I do this: [https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival)

For sharing with others, it depends.
It depends on how sensitive the photos are, whether they are part of the subject for the photos, and if I care that anyone in the world can see them or not.  Hint: I do.  I'd never post photos on any cloudy service nor would I put them somewhere that a web-search tool can access.

To share with others, I've setup a simple gallery (mine is a custom perl CGI script) that has basic authentication.  I setup subdomains for each specific trip and share those with the people on the trip. This is a copy, not my official storage location and storage. To prevent too much boredom, only the best photos are shared ... unless the subject is one of the people on the trip.

I've also added a few family members to my NextCloud server and shared photos through that.  This way, logins are required ... actually, they have to use a VPN to access it.  Plus, they can upload their trip photos there too.  Some of us travel together to interesting places in the world.

About 24 yrs ago, I was posting all my photos online to a website that I ran.  Web-search tools found it and pulled all the content - without approval.  They ignored the robots.txt instructions.  When I discovered that, I relocated all the images.  An acquaintance at work found my photo gallery and looked through every photo there.  There were thousands.  When someone does that, they think there is more of a relationship than really exists since they know lots about the other person, but not really anything.  Let's just say that having someone show up at your door, late at night, expecting you to invite them in for "something" can happen.  Unwanted advances aren't fun for anyone.  Be careful putting stuff online and available for anyone to see, especially photos.  It might be fine, but my experience says different.

99+% of people in the world are really nice, good people.  But that 1% can really suck.

I've posted a few photos in the forum galleries here, but never with my face or exact home.  Some are from travel and have full GPS and timestamp data inside the photo, which is fine. 

For old family photos/slides, I scanned them all and made DVDs to give to the family at Xmas.  These were Dad's photos mostly of us growing up.  The grandkids seem to like it and get to meet their ancestors.  Before my Mom died, we got her to tell the story behind each photo and each nick-knack in her home.  Knowing "why" the plate on her mantel is so important to her completely changes the worth of the item.  I have a mounted flour bag in a frame from Mom's Dad who I never met. He died before I was born.  But I have audio recordings of her telling a few stories about him, the bag, and how he was in the community the flour mill served.  Without those stories, it is a nice bag to display, but incomplete.

If you want to spend lots of time, you can setup a slideshow with audio for each photo.  Then you can mux the photo+audio into a longer video that can be shared.  Some MP3 players will show an image while playing the MP3 file.  Hummmmmm. I need to check into that.  I know that audio book players do this.

PDF gets abused far too much.  I'm guilty of PDF abuse back in the olden days too.  I've since learned to avoid PDF, especially for images.

---

### Post by web-user on 2022-06-18
You can also try Syncthing to synchronize files/photos between devices. Personally I store all my media on several HDD's

---

### Post by TheFu on 2022-06-18
> **satimis said:**
>  
It is not solely for sharing.

I need to post all photos on my website. 

rsync.  rsync is easier to use  - it is like cp.  Just needs an ssh connection between the 2 systems.  If your shared hosting company doesn't allow ssh connections, time to fire them. Ok, if they didn't have ssh/sftp in 2002, it was time to fire them back then.

Pandoc using whatever markup language you like, can create javascript-based presentations that can be dropped onto a website.  And pandoc can output lots of different formats based on what you need.  At least 20, including HTML, PDF, AsciiDoc, Text and a few different javascript presentations.  I use s5, which is like Reveal.  [https://meyerweb.com/eric/tools/s5/](https://meyerweb.com/eric/tools/s5/)

```
$ pandoc -s -T "$TITLE" --toc --standalone --slide-level=3 -f textile \
    -t s5 $ROOT.md -o $ROOT.html
```

That takes my presentation.md (textile) input, creates an 's5' output file for all slides of levels 1, 2, 3.  I'll have speaker notes at higher levels which don't show up during the presentation, but are there on my screen, not on the projector, when I'm speaking.  I prefer textile over markdown. Tables and images are easier.  Embedding audio/video files is pretty easy too, though I seldom do that.

---

### Post by satimis on 2022-06-18
> **TheFu said:**
> rsync.  rsync is easier to use  - it is like cp.  Just needs an ssh connection between the 2 systems.  If your shared hosting company doesn't allow ssh connections, time to fire them. Ok, if they didn't have ssh/sftp in 2002, it was time to fire them back then.
Thanks for your advice.

I found "PDF Embedder" (WordPress plugin) may help me out

3 Ways To Embed A PDF On WordPress Posts And Pages
[https://www.youtube.com/watch?v=UZTyrNVRhFA](https://www.youtube.com/watch?v=UZTyrNVRhFA)

Now I have purchased a new Samsung Galaxy S22 Ultra (12+256G) mobile phone, having better Lens.  I shall start my adventure, scanning photos with smartphone soon.  It will take a considerable long time to finish scanning 1,000 photos.  I won't wait until finishing scanning all of them to test PDF files installed on WordPress website.

Regards

---

### Post by TheFu on 2022-06-18
If you are going to use PDF as the file format, please force an old version of the standard.  PDF v1.6 is well supported across nearly all platforms.  Don't make people have to use an Adobe addon/software to view it.

---

### Post by kurt18947 on 2022-06-18
> **satimis said:**
> [B][COLOR=#FF0000]Edit
====
.....................................................................[/COLOR][/B]
**A further thought;**
I suppose I can use Libre Office to create a PDF book/album, just pasting the old photos on its document.  Then export Libre Office document as pdf file.

If possible, then the solution is much simpler.  I don't need to spend time learning Scribus.

Regards
SWMBO wanted to do a family history thing. We just scanned and imported pics into a Libre Office Writer document along with explanatory text then saved as a PDF. This wasn't lengthy, maybe 25 pages.

---

### Post by satimis on 2022-06-18
> **TheFu said:**
> If you are going to use PDF as the file format, please force an old version of the standard.  PDF v1.6 is well supported across nearly all platforms.  Don't make people have to use an Adobe addon/software to view it.
Pls explain in more detail.  Thanks

I can upload photos to be shared amongst public to WordPress website but all art works on PDF files can't be displayed.

Regards

---

### Post by kurt18947 on 2022-06-18
> **QIII said:**
> Storing and sharing are really two different things.

You've had several suggestions for sharing.  

Might I recommend that for storage of things that just can't be replaced you use mechanical drives?  Old School Rust has been shown to be stable for decades.  Although I am sure by now that solid state is pretty stable, there is still charge leak-down that can cause degradation over time.  Similar degradation on mechanical drives is far, far slower.  Store more than one copy of everything and do that in different locations if you can.  You don't want a lightning strike on the electrical transformer down the street to obliterate your last few surviving images of Granny.

One other possibility for longer term storage, M DISC? Of course the question there is will anyone in 50 or 100 years know what a DVD or BluRay disc are or have the hardware to play them? The thinking I've seen is that DVD will be viable for quite some time yet. The trick is when the next long term storage media comes along, transfer it. I've seen speculation about this sort of thing and one school of thought is that optical technologies are well and widely documented enough that someone in the future could build some sort of laser scanner that would read DVDs or BluRays without having a physical drive. Whether they'd understand the encoding is another question I guess. For really long term easy readability black and white printing is hard to beat. Original copies of the Magna Carta or Declaration of Independence are still legible. Is there a color printing technology that is color stable over multiple decades?

---

### Post by TheFu on 2022-06-18
PDF is a standard with versions.  It is similar to how HTML2, HTML3, HTML4 and HTML5 are standards.  There is an industry group which sets the standard for the PDF. Adobe is part of that standards committee and certainly has great control over it.

The PDF standard v1.6 has been well supported by F/LOSS programs for a long time. Newer versions of the standard are hit-miss.

By default, if you use the latest version of Acrobat Distiller; that's the original PS-to-PDF printer driver and how PDF files have been made since at least 1994.  Other tools can create PDF files too, just be certain of the PDF standard level that is output.  Going with 2.x versions will mean that fewer people are likely to be able to view those files.

BTW, I worked in electronic documentation for 6 yrs and the team I worked with required all the input documents in PDF.  This was early days for PDF and Adobe Acrobat Reader, which was the only way to view PDF files (proprietary) at the time.  Adobe visited our Govt lab where we showed them how we did more than just allow viewing and stole some of the smart things and some of the dumb things we had created.  Until around 2001, Adobe searching across large numbers of PDF files was pretty ugly.  That was completely our fault. Our needs were extremely specialized since we had different "libraries" and only wanted searches within the specific library, never outside it.  In almost everywhere else, pointing at a directory structure with PDF files and having a recursive search for all files from X and below would have made much more sense.  I apologize to the world for that in those years. It was my fault.  I wrote the library management code - not for Adobe, so they didn't have to copy our method, but I still felt guilty years later.

These days and for the last 20 yrs, I avoid PDF whenever possible and stick with more flexible formats which can trivially be converted to any number of other useful formats, but still allow slightly technical people to use grep for searches.

---

### Post by TheFu on 2022-06-18
DVDs that aren't commercially created last about 10 yrs. With extra parity files (par2) added, even with a few bits are dropped, it is possible to fix minor issues and restore the files involved.  Back before HDDs were relatively cheap, I was using DVDs for long term, offline, storage, but with 10% par2 files.  When I wanted to retrieve selected files, I'd look in the catalog (ls -Rl) for the file, get a cross-ref to the DVD (I numbered them all) and would pull all the files off the disc.  Then I'd validate the files had been restored error free thanks to par2 files.  As quickly as 5 yrs later, the discs started showing errors.

Here's an article about the restore process after some corruption: [https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2)

mDisc is supposed to be 50+ yrs of stable storage. I've been tempted, but the media costs are significant.  I decided to stay with HDDs and have backups which get pulled forward when more storage is needed.  I did standardize on 2TB drives around 2007, but moved to 4TB around 2015 and the last drives I've bought were 8TB, still split into 4TB volumes so existing storage could be mixed and matched.  The 8TB drives are not primary storage. They are for backups.

I'm expecting 16TB drives to become cost effective in the next 2-3 yrs, so I'll probably switch out all current storage to those in that timeframe, mainly to free up some SATA and eSATA ports.

---

