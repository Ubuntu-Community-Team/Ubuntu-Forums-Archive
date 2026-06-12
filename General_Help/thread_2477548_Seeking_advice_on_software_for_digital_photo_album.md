---
title: "Seeking advice on software for digital photo album"
date: 2022-07-29
forum: General Help
---

### Post by satimis on 2022-07-29
Please advise the best software for digital photo album for Linux?

Scribus is on Ubuntu repo

Picasa is no more for Linux

Thanks in advance.

Regards

---

### Post by TheFu on 2022-07-29
"Best" is highly subjective.  You should list features, prioritize those features, then begin looking at the 50 options.  Your list and my list are different, I'm certain.

Here's my list:
* Honors directory structure layout for yyyy/mm/event/
* Doesn't use php, java, or node; I want a webapp.
* Displays EXIF data - not all of it - but things like date, GPS coordinates, comments, location fields, along with camera and shot info.
* Creates external links based on the EXIF data
* Search by filename, exif data, date.
* Stores the original photos read-only. Cannot touch, modify, delete those.
* Creates thumbnails and a few web-display resolutions as needed.
* Branding can be removed.  The photos are the star, not the software.
* Easy to create quick, specific subject, galleries.
* Accessible from any client, though I.E. or whatever MSFT uses as a browser does NOT need to work.
* All data is NOT stored outside the directory layout or text files or EXIF.  Don't want a proprietary DBMS with lots of added metadata that can never be pulled out when the software becomes unsupported in 10 yrs (or 1 yr).
* Theme control, but simple.  Control through a template.
* Privacy. No outside company needs to know anything about our photos or the metadata.  

There are things I wish my gallery had, but it doesn't. These are
* add audio notes for each photo
* Easy rotation for specific users only.
* Easy Red-eye removal.
* Slideshow with normal controls for directories, image match patterns, and delay time.  Optional playback of audio notes or random music from a playlist.

I've been using/maintaining a perl-cgi gallery created by FuzzyMonkey a very long time ago.  I've customized the EXIF handling, search, and theme a bit. I think the original creator abandoned the webapp, but it is still working great.  Just looked and the original website seems to be gone.

[https://jpegclub.org/losslessapps.html](https://jpegclub.org/losslessapps.html) has a list of apps using lossless jpg translation which could be a place to start.

Of course, if you want a monstrous thick desktop application, then I cannot help.  All of those seem to use proprietary DBs and lock the metadata away, never to be available outside that program again.  Long ago, I used a program like that and when it was time to migrate, I became unhappy. All the work around putting metadata into the collection was effectively lost, so I decided to put up with a less capable gallery tool, but have complete control over the metadata.  If the meta data isn't added into the EXIF by the tool, then I don't want it. It is a waste of my time.

---

### Post by dragonfly41 on 2022-07-29
Can I suggest an app I have started to use fr general document production, now that GitHub has given notice to "sunset" Atom editor (which you can also use in parallel wioth Zettlr as I do..

Zettlr.com is a Markdown editor.

There is an option to export Markdown files as Reveal.js slideshows.

Now from the list of features offered by @TheFu above you can 
(a) embed running commentaries or background music in reveal.js slides.
(b) add wait times

It takes some time to understand Markdown features but Zettlr with Pandoc and reveal.js is a useful combination.

You can import photos into individual slides or sections using simply

@import "photo.jpg" 

Individual photos will be placed in

<slide>
@import "photo.jpg"
</slide>

You can embed <div></div) with grid of multiple photos.

[P.S.] I have recently decided to use Tresorit.com as zero knowledge data silo.

---

### Post by sudodus on 2022-07-29
Please describe what kind of photo album you want:

- local or available via the internet
- simple or advanced: list what features you want

How many pictures are there now, and how many do you expect to manage?

---

### Post by satimis on 2022-07-30
Hi all,

Thanks for your advice.

Detail of the digital photo album expected;
1.  It is not open to public nor posted on Internet.  I only give the album to friends as souvenir.
2.  The album can be read on my friends' computers with general software.
3.  2/3 photos per page with written description of each photo.
4.  About 50~80 photos per album
5.  Simple oral narration will be added at the front page introducing the album.  If too complicate I'll add written description instead.

Thanks

Regards

---

### Post by TheFu on 2022-07-30
For that need, I'd forget a photo album and use a presentation tool - whatever LibreOffice has.

---

### Post by sudodus on 2022-07-30
> **TheFu said:**
> For that need, I'd forget a photo album and use a presentation tool - whatever LibreOffice has.
+1;

I would create a presentation with a format suitable to show on a computer screen (16x9 width to height proportion) using LibreOffice Impress, and let it export the result as a **pdf** file, because that format is very portable between different operating systems.

---

### Post by dragonfly41 on 2022-07-30
> Post #1 - Scribus is on Ubuntu repo

That is another fine tool to create a PDF photo album as you specify.

---

### Post by ActionParsnip on 2022-07-30
Something like Tumblr

---

### Post by satimis on 2022-07-30
> **ActionParsnip said:**
> Something like Tumblr
Please explain in more detail?

Whether you meant using the share services similar to Tumblr, YouTube and Flickr?  I don't expect posting my photos to Internet.

On searching I found following thread;
7 Best Linux Photo Management Software
[https://itsfoss.com/linux-photo-management-software/](https://itsfoss.com/linux-photo-management-software/)

Would they be a route for me to follow?

Thanks

Regards.

---

### Post by satimis on 2022-07-30
> **TheFu said:**
> For that need, I'd forget a photo album and use a presentation tool - whatever LibreOffice has.
You're right.  The steps are very simple and straightforwards.  Just copy&paste the photos on LibreOffice and add description.  Then export the file as a PDF file.

In the past, I just on Terminal combine all photos as a PDF file.  But I'm looking for a solution with more features.

Regards

---

### Post by ActionParsnip on 2022-07-30
> **satimis said:**
> Please explain in more detail?

Whether you meant using the share services similar to Tumblr, YouTube and Flickr?  I don't expect posting my photos to Internet.

On searching I found following thread;
7 Best Linux Photo Management Software
[https://itsfoss.com/linux-photo-management-software/](https://itsfoss.com/linux-photo-management-software/)

Would they be a route for me to follow?

Thanks

Regards.

Yeah I thought you wanted an album system you can view your images. Tumblr etc are great for this but if you want to keep the data on the LAN then it's not a good solution.

---

### Post by Dennis N on 2022-07-30
To present photos you could create one or more webpages using HTML with links to the image files and then add descriptive text. It would be viewable in any web browser. Easy to make changes too. I think you would get a nicer result than using LibreOffice. You can distribute the whole thing in a .zip file

This solution meets all the conditions you set in post #5.

Web pages do not have to be on the internet. You can store the entire project on your computer for personal use.

---

### Post by satimis on 2022-07-30
In my personal opinion, the best digital photo album is a slideshow in mp4 format.  I can add many features on the slideshow, such as oral and written narrations (in different languages and dialect), background music, subtitles in many forms such as burning, fading, rotating etc.  In the past I have created many slideshows.  Besides I can re-edit the slideshow in any time.

But the only inconvenience is their file sizes.  I can't send them to friends as email attachment.  I must upload them to Dropbox or similar websites and inform my friends to download them.  But not all of my friends are knowledgeable on computer science.  Some of them didn't know how to download the slideshows nor to play them on their computers.

[B][COLOR="#FF0000"]Edit
====[/COLOR][/B]
Just found;
How to Reduce Video Size With FFmpeg
[https://linuxhint.com/how-reduce-video-size-with-ffmpeg/](https://linuxhint.com/how-reduce-video-size-with-ffmpeg/)

Does it work?

Can it be easily extracted by a person without advanced knowledge on computer science ?

---

### Post by TheFu on 2022-07-30
> **Dennis N said:**
> To present photos you could create one or more webpages using HTML with links to the image files and then add descriptive text. It would be viewable in any web browser. Easy to make changes too. I think you would get a nicer result than using LibreOffice. You can distribute the whole thing in a .zip file

This solution meets all the conditions you set in post #5.

Web pages do not have to be on the internet. You can store the entire project on your computer for personal use.

I love using static HTML for sharing data!  Beware that many of the new browsers will not open local HTML pages by default in the name being more secure.  Used to be, we'd be able to use file:// URLs or just double-click on the HTML index for any project, but that stopped around 2016.  We have to specifically tell Chromium that opening local files is intended, for example.  
```
 $ chromium-browser --allow-file-access-from-files ~/Presentations/My_new_Presentation.html &
```
I use chromium when I need full javascript. It is just easier, though firefox is my default browser. Both are run constrained under firejail. The level of constraints depends ... untrusted websites don't get to access any files on the local disk and never get to write to disk.  Trusted sites, there are about 5, get to run just limited to /tmp/ and ~/Downloads/.  I hate ~/Downloads/ but have been beaten into submission since it is the default for so many programs.  Anyway, the people you send the full HTML setup to likely will not be so concerned with security (they aren't used to being attacked, daily).

I'm not a fan of anything from Adobe. [https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools](https://blog.jdpfu.com/2010/06/30/why-are-you-still-using-adobe-tools)

---

### Post by dragonfly41 on 2022-07-30
Just print an ebook. Pandoc helps here.

---

### Post by satimis on 2022-07-30
> **dragonfly41 said:**
> Just print an ebook. Pandoc helps here.
Could you please explain in more detail?

Thanks

Regards

---

### Post by dragonfly41 on 2022-07-30
I referred in much earlier post to leveraging Markdown (Zettlr.com et al).
Markdown editors in turn leverage Pandoc.
[https://pandoc.org/](https://pandoc.org/)
Notice also the link to reveal.js in Pandoc.
[https://revealjs.com/](https://revealjs.com/)
[P.S.] such presentations need not be on the web, they can be bundled into a zipped folder with password.

But also you can use Pandoc at command level to create a eBook which you can &#8220;publish&#8221; to your chosen audience.
this explains how ...
[https://pandoc.org/epub.html](https://pandoc.org/epub.html)
...
But in closing I point to yet another very simple editor.
cherrytree
which I use daily.
It is Hobson's choice.

---

### Post by TheFu on 2022-07-30
> **satimis said:**
> Could you please explain in more detail?

Thanks

Regards

pandoc is a document transformer.  We create documents in the allowed input formats (must be 20 of those) run it through pandoc and it generates output formats - must be 30+ of those.  Simple.

I use textile as my preferred "input" and want "S5" as my output:
```
$ pandoc -s -T "$TITLE" --toc --standalone --slide-level=3 -f textile   -t s5 $ROOT.md -o $ROOT.html
```

Or text as output:
```
$ pandoc -s -T "$TITLE" --standalone --slide-level=3 -f textile  -t plain $ROOT.md -o $ROOT.txt
```

I pass in the title and filename into the script.  Nothing can replace the manpage for pandoc. It holds so much information.  It can create PDF files, but there are some specific helper tools required for that to work. I've never bothered, plus going from a very open format (any markdown) to something so very restrictive is just wrong.

Pandoc can output Reveal.js, though I suspect the CSS and JS need to be in specific locations for that to work.  S5 is similar and definitely has a few files that need to be in specific places relative to the generated HTML file to be useful.

Generating an epub output would be pretty easy too.  epub is basically ZIPped html, but as a single file.  But I don't know if audio is part of that standard or not.  OTOH, it is 1 file so all the images and html wouldn't be known to anyone but the creator.  The downside is that the viewers would need an epub viewer - there are lots of those, most are free, but it is another program to insist that people have.  fbreader is popular.

epub is a much larger format than the markdown or text files:
```
$ du Shell-Review.*
152K    Shell-Review.epub
12K     Shell-Review.html
8.0K    Shell-Review.md
8.0K    Shell-Review.txt
60K     total-for-image-files.jpg

```
So, we took 8k + 60k and made it into 152k as epub.  Not too efficient, but for a convenience of 1 file, with an open standard, not too bad.  There are many more wasteful things, that is certain. Looking at the resulting epub file, seems that about 10 pages from the .md file weren't included. I don't have time to figure out the issue now, but it is likely due to my non-standard textile.

---

