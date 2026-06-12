---
title: "Solution for keeping thousands of old photos"
date: 2024-02-29
forum: General Help
---

### Post by satimis on 2024-02-29
Hi all,

I have thousands of old photos captured world-wide in the past.  Some of them are digital photos and some of of them are hardcopy photos. I have no problem converting the hardcopy photos to digital on smart phone.  But how to store the old photos is really my headache?

Currently I create digital slideshows on them and upload the slideshows to YouTube for sharing.  But there will be hundreads of digital slideshows to be created.

Now I'm searching for a better solution.  Could you please shed me some light?  Thanks

Regards

---

### Post by dragonfly41 on 2024-02-29
There will be multiple workflows suggested.
This is based on my own recent research into different tools in a toolchain.
I assume that you prefer to keep your photos collection(s) private on your desktop rather than in the cloud.
The keywords you use are 

thousands of old photos,
smart phone, 
digital slideshows,
sharing
YouTube
hundreds of digital slideshows to be created.


There are many paths you can take.  This is just one ideas dump.

[LIST=1]
[*]Operate on a desktop rather than smart phone (I don't use a smart phone).
[*]Explore Zettlr markdown editor which allows images to be embedded into Markdown documents and even audio clips. Note that two directions can be navigated (up/down fragments, and right/left slides).
[*]From Zettlr export your documents as slideshows in reveal.js (built into Zettlr > export).
[*]Use yaml front matter at top of each markdown document to hold variables for inclusion in exported document.
[*]Rather than YouTube (which I avoid) consider registering your own google domain. Then use Hugo templating (also Markdown based) to create and upload private shows (with passwords).
[*]Alternatively consider holding your slideshows in a zerotrust data vault such as tresorit.com and post private links to recipients' to download your custom slideshows.
[*]Consider automation tools if this is a production line. I use basic tools such as actiona which incidentaly has OpenCV functions built in (e.g. searching for match of images).
[*]Consider adding desktop tools such as Shotwell into your workflow.
[/LIST]
If you want to enter into photo effects that is extra time play.
[https://es.wolframalpha.com/examples/pro-features/image-input](https://es.wolframalpha.com/examples/pro-features/image-input)

---

### Post by satimis on 2024-02-29
> **dragonfly41 said:**
> There will be multiple workflows suggested.
This is based on my own recent research into different tools in a toolchain.
I assume that you prefer to keep your photos collection(s) private on your desktop rather than in the cloud.
The keywords you use are 

thousands of old photos,
smart phone, 
digital slideshows,
sharing
YouTube
hundreds of digital slideshows to be created.


There are many paths you can take.  This is just one ideas dump.

[LIST=1]
[*]Operate on a desktop rather than smart phone (I don't use a smart phone).
[*]Explore Zettlr markdown editor which allows images to be embedded into Markdown documents and even audio clips. Note that two directions can be navigated (up/down fragments, and right/left slides).
[*]From Zettlr export your documents as slideshows in reveal.js (built into Zettlr > export).
[*]Use yaml front matter at top of each markdown document to hold variables for inclusion in exported document.
[*]Rather than YouTube (which I avoid) consider registering your own google domain. Then use Hugo templating (also Markdown based) to create and upload private shows (with passwords).
[*]Alternatively consider holding your slideshows in a zerotrust data vault such as tresorit.com and post private links to recipients' to download your custom slideshows.
[*]Consider automation tools if this is a production line. I use basic tools such as actiona which incidentaly has OpenCV functions built in (e.g. searching for match of images).
[*]Consider adding desktop tools such as Shotwell into your workflow.
[/LIST]
If you want to enter into photo effects that is extra time play.
[https://es.wolframalpha.com/examples/pro-features/image-input](https://es.wolframalpha.com/examples/pro-features/image-input)
Hi@dragonfly41,

Lot of thanks for your detailed advice.

Currently I'm running OpenShot to create photo slideshows, exporting them as .mp4 video.  If I want to share them to friends I just upload that particular slideshow to YouTube.  I can create features and add narration as well as background music to the slideshows.  The complete workflow has been working for me for sometimes without problem.

I need to retain the photos on my computer not uploading them to Cloud.   Besides I won't use smart phone to do the job.

Now I'm searching for a new way, if any.

Regards

---

### Post by TheFu on 2024-02-29
[https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) is what I've been doing for a long time. Early on, I tried to use specific programs and when those programs disappeared or became otherwise useless to me, I lost all the metadata I'd been adding.

I have a slide and negative scanner to digitize most photos, except those from when I was kid with 110 camera. Those are better scanned at 1200 dpi on the flatbed scanner.  I was able to scan the slides from my father's photos taken in the 1950s in some interesting parts of the world.

For sharing, I find there are different audiences.  Family is only interested in family photos. They don't care about 300 photos from my latest hiking trip somewhere remote.  Of course, the people on that trip, might be interested in the "best" from that trip, usually great scenery with one of them in the photo.  Family doesn't care about trip acquaintances.

I self-host a gallery website which can be used to search by filename or metadata or location - I add GPS coordinates, along with country, province, city/area, subject information to the EXIF when that's easy.  For the last 15 yrs, I've been adding all metadata to the EXIF of the files.

My gallery software is a customized version of **My Photo Gallery** from around 1997 written in perl.  Over the years, I've looked at others, but they haven't impressed me.  My Photo Gallery keeps the original photos and all resized/thumbnails/metadata in separate directories.  I've always had an "untouched original" mandate for any gallery software.  

After I installed NextCloud, I added a photo manager for it and pointed it at a read-only mount with my 30K photos.  It took a few days to index everything.  I wasn't impressed.  For software to be so very bad at searching files is an embarrassment.  There are some really fantastic photo addons for NextCloud, but they all seem to choke on the amount of photos I have.  I do like how NextCloud Maps will pull GPS data and place photos on the world map it has.  Combined with GpxPod addon for GPX track files, it is nice to see where and when I was in the world.  Of course, I only use GPX tracks when I'm traveling, never at home.  GpxMotion and Memories are good NextCloud addons too.  The NextCloud-Maps addon can't seem to handle all the photos, but what it does handle is nice - at least locally.

The big issue with NextCloud is that my original photos are large and not optimized for web viewing.  Waiting 45 seconds for each photo to load is just too long.

For slide shows, I'll just hardlink the original files into a slideshow directory and use **feh** or **geeqie** to display them.

As my younger family members get older, I could create "this is your life" slideshows just for them.  I generally add the people in a photo to the filename, so using **find** would make it easy to create hardlinks and a person specific slideshow.  Hummmmm.

---

### Post by dragonfly41 on 2024-02-29
If you are commited to your workflow with YouTube, as I understand you are exploring local methods for holding and delivering your mp4 objects which runs on desktop.
Recently I started experimenting with eXistDB. You can store mp4 objects in that database. You will need to understand how to build collections and use say WebDav to upload to eXistDB. I have Krusader file manager installed and objects in any panel (such as ~/Photos) can be easily uploaded using Tools > New Network Connection > protocol WebDav. But this is just one line of thought. You can of course try different desktop servers (another example MongoDB) but eXistDB has good reviews.
The next task you alluded to is automating hundreds of slideshows and whenever there is an automation or batch requirement I try Actiona as an orchestrator (client) to oversee and manage multiple processes. I still think that you should experiment with Hugo/Zettlr/Markdown/Reveal.js. I am not a fan of YouTube with its ads and other distractions.
Finally if you want to put your photos into time capsules for future generations of family consider adding to WaybackMachine.

---

### Post by TheFu on 2024-02-29
If you insist on using video for photos, set the FPS to 1 fps or less. No need to have 25fps eating space for a photo. The audio quality isn't tied to the video frame rate.

Seems there should be a way to add an image to an audio file. I've seen this with audiobooks many times. I haven't looked up how to do it. Probably in a tag editor, like EasyTag.

---

### Post by dragonfly41 on 2024-02-29
> 
[COLOR=#000000]Seems there should be a way to add an image to an audio file. [/COLOR][COLOR=#000000]
Reveal.js as suggested earlier.
[/COLOR]https://github.com/tgogos/reveal.js_photo_slideshow

Added links

[https://revealjs.com/backgrounds/](https://revealjs.com/backgrounds/)
[https://revealjs.com/speaker-view/](https://revealjs.com/speaker-view/)
[https://www.linkedin.com/learning/reveal-js-online-presentations](https://www.linkedin.com/learning/reveal-js-online-presentations)

---

### Post by TheFu on 2024-02-29
Javascript is a complete NO-GO for me as a part of a gallery.  Too many issues, poor security, flaws.

---

### Post by satimis on 2024-02-29
> **TheFu said:**
> [https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival) is what I've been doing for a long time. Early on, I tried to use specific programs and when those programs disappeared or became otherwise useless to me, I lost all the metadata I'd been adding.

I have a slide and negative scanner to digitize most photos, except those from when I was kid with 110 camera. Those are better scanned at 1200 dpi on the flatbed scanner.  I was able to scan the slides from my father's photos taken in the 1950s in some interesting parts of the world.....
......  
Hi,@TheFu
Lot of thanks for your advice and your time spent to help me.  Hererinbelow are my reply:-

1)
I can't browse your link;
Finally it popup:```

This site can’t be reachedblog.jdpfu.com took too long to respond.
Try:.....

```

2)
For family photos I have a private website.  Visitors can only login with password to browse this website.  But who will maintain this private website in long term?

3)
I won't put my old photos to Cloud

Actually my current method, converting the digital photos to slideshows, aleady is a good solution.  But there are still hundreds of .mp4 files created.  If converting 1,000 digital photos to a big slideshow, I don't think the visitor will have interest to browse it, a big file.

Following links are 2 examples of my slideshows created;

1)
Counties in northern California, USA - Part 3
[https://www.youtube.com/watch?v=DWx6LF3eCCg](https://www.youtube.com/watch?v=DWx6LF3eCCg)
language: English, Chinese (2 dialects)
text: English, Chinese

2)
Dusseldorf, Germany - Part 1
[https://www.youtube.com/watch?v=oSUkOjZgrJg](https://www.youtube.com/watch?v=oSUkOjZgrJg)
language: German, English, Chinese (2 dialects)
text: German, English, Chinese

But I'm still searching "would there is a better way" ?

Regards

---

### Post by satimis on 2024-03-01
> **dragonfly41 said:**
> If you are commited to your workflow with YouTube, as I understand you are exploring local methods for holding and delivering your mp4 objects which runs on desktop.
Recently I started experimenting with eXistDB. You can store mp4 objects in that database. You will need to understand how to build collections and use say WebDav to upload to eXistDB. I have Krusader file manager installed and objects in any panel (such as ~/Photos) can be easily uploaded using Tools > New Network Connection > protocol WebDav. But this is just one line of thought. You can of course try different desktop servers (another example MongoDB) but eXistDB has good reviews.
The next task you alluded to is automating hundreds of slideshows and whenever there is an automation or batch requirement I try Actiona as an orchestrator (client) to oversee and manage multiple processes. I still think that you should experiment with Hugo/Zettlr/Markdown/Reveal.js. I am not a fan of YouTube with its ads and other distractions.
Finally if you want to put your photos into time capsules for future generations of family consider adding to WaybackMachine.
Hi@dragonfly41

Whether you meant;

Vitamins for your Applications
[https://exist-db.org/exist/apps/homepage/index.html](https://exist-db.org/exist/apps/homepage/index.html)

Regards

---

### Post by dragonfly41 on 2024-03-01
From satimis
> [COLOR=#000000]Whether you meant;[/COLOR]

[COLOR=#000000]Vitamins for your Applications[/COLOR]
[https://exist-db.org/exist/apps/homepage/index.html](https://exist-db.org/exist/apps/homepage/index.html)

Indeed, yes.

From TheFu
> [COLOR=#000000]Javascript is a complete NO-GO for me as a part of a gallery. Too many issues, poor security, flaws.

[/COLOR]Point well taken and registered.  Snakes and ladders. I am rethinking how to build a secure frontend (sans javascript) based on Java. HaXe is one useful tool. I have switched from Jetty to Tomcat.

---

### Post by satimis on 2024-03-01
> **dragonfly41 said:**
> From satimis


Indeed, yes.
eXist-db is completely new to me.

Just found;
First Steps with eXist-db 2.0
[https://www.youtube.com/watch?v=xvMau2aHRDo](https://www.youtube.com/watch?v=xvMau2aHRDo)

Although it is quite old.  Can it help me to start?

I also found;
eXist-db documentation
[https://exist-db.org/exist/apps/doc/documentation](https://exist-db.org/exist/apps/doc/documentation)

What I'm interested to know is the use of this application?

Regards

---

### Post by dragonfly41 on 2024-03-01
> [COLOR=#000000]What I'm interested to know is the use of this application?[/COLOR]

Unlike other databases such as SQL etc. eXistDB is a NoSQL database.
Unstructured content can be archived as collections.  If you refer back to earlier notes I posted in this thread you can upload (either eXistDB in your desktop or eXistDB on a remote server instance) collections.  Sample applications can be installed.  Such as Shakespeare works.
The broad idea is to provide a repository of your thousands of photos (or other object such as commentary).  What I did to install locally was:
Create a desktop folder such as ~/eXistDB
Download an install exist-installer-6.2.0.jar
Start the *.jar file and thereafter better to follow documentation.

I mentioned earlier one game plan I personally use to leverage Krusader to use WebDav but there are multiple ways by command line / Python to drive eXistDB, leveraging xQuery.

sudo apt install krusader

I am looking to install eXistDB on local and remote servers for various experiments.

In short it answers your opening quest for a photos repository (local and remote). Delivery to a user client app (on mobile or desktop) in the next experiment but I do not sport a bells and whistle smart phone. It will be a desktop client. Secure - sans javascript as per theFu concerns. But smart phones UI can be emulated on desktop dev for test purposes.

---

### Post by TheFu on 2024-03-01
> **satimis said:**
>  
1)
I can't browse your link;
Finally it popup:```

This site can’t be reached blog.jdpfu.com took too long to respond.
Try:.....

```


Well, it might be offline for 3 minutes a day around midnight (local time)
OR
you may happen to be on a subnet that has attacked some of my servers, so it is blocked from all access.  You can try the wayback machine. The linked article was created years ago, so a copy or 50 would be there.  When google provided their google-cache, that would have been the easier way.
 
> **satimis said:**
>  
Following links are 2 examples of my slideshows created;

1)
Counties in northern California, USA - Part 3
[https://www.youtube.com/watch?v=DWx6LF3eCCg](https://www.youtube.com/watch?v=DWx6LF3eCCg)
language: English, Chinese (2 dialects)
text: English, Chinese

But I'm still searching "would there is a better way" ?


I started watching that youtube link, but it is confusing to me. **Fort Bragg** is in NC and was renamed to Fort Liberty last year. [https://www.armytimes.com/news/your-army/2023/06/01/fort-bragg-to-become-fort-liberty-heres-what-you-need-to-know/](https://www.armytimes.com/news/your-army/2023/06/01/fort-bragg-to-become-fort-liberty-heres-what-you-need-to-know/)  Ask anyone related to the US military anywhere in the world and they will know about the NC Army base.  It is huge.  

Searching just for "Fort Bragg", without any state, points to the NC location.  It is odd that a "Fort" would have been named the same in two places controlled by the US.  Cities are commonly named the same around the US ... there must be 15 "San Jose" cities here and there's a Paris, Tx but having 2 military cities based on old Fort names does seem odd to me.  Adding clarification could be useful to prevent confusion.

Many of the photos weren't up long enough for my tastes.Even 2 seconds longer for each, after the slide-in effects would have been helpful.

Another idea - have you considered using multiple audio tracks to keep the English and Mandarin separate?  Does youtube support that?  [https://support.google.com/youtube/answer/13338784?hl=en](https://support.google.com/youtube/answer/13338784?hl=en)  Just a thought.

I'd probably use captions/subtitles for the text, so the images get more screen time, but I can see why doing it as you have makes sense too.

Seeing what you've done, that does give me lots of ideas for some of my trips.  Thanks for sharing.

---

### Post by ActionParsnip on 2024-03-01
Can the hard copies with a scanner to the file type of your choosing. You can then back them up to a USB drive (Ideally two for safety).

---

### Post by satimis on 2024-03-02
> **ActionParsnip said:**
> Can the hard copies with a scanner to the file type of your choosing. You can then back them up to a USB drive (Ideally two for safety).
Thanks.

I have no storage problem.  I store all photos on a 4TB hard drive on 2 computers,  the hard drives solely for storage without OS installed.  So in case if one of them broken down I still have the 2nd hard drive.  Additionally I retain another copies of all photos on an external USB SSD.

What I need is an easy way finding the photos ?  How to classfy their storage of thousands of photos

Regards

---

### Post by TheFu on 2024-03-02
>  How to classfy their storage of thousands of photos

That depends entirely on how you want to find them.  There are multiple types of queries, so you'll need to pick the most common and make the others possible, if not easy.

For me, the date and event/location matter the most, so my directory structure is laid out with those things.
WaybackMachine link, if the already provided link doesn't work for you. [https://web.archive.org/web/20210502055015/https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival](https://web.archive.org/web/20210502055015/https://blog.jdpfu.com/2011/01/05/tips-for-digital-photo-organiz-storage-and-archival)

Of course, I want some information about the photo subject, so that's in the filename. for example, 
gallery/2017/1126-Torres_del_Paine-Overview/425-Guanaco-baby-best.jpg 

Inside the EXIF data for that photo, 
```
$ photo-data gallery/2017/1126-Torres_del_Paine-Overview/425-Guanaco-baby-best.jpg 
================
File Name                       : 425-Guanaco-baby-best.jpg
Date/Time Original              : 2017:11:26 16:41:34
Time Zone City                  : (not set)
City                            : Torres del Paine
Sub-location                    : Condor Views
Country-Primary Location Name   : Chile
GPS Position                    : 50 deg 56' 52.45" S, 72 deg 42' 43.28" W

```

photo-data is a tiny script I wrote that filters out all the EXIF I don't need, leaving just the parts that matter.  It is just **egrep** and **sed** of **exiftool** output.  EXIF allows comments, which can hold lists of descriptive terms for a photo, if you need those.  Professional photographers need about 20 other things - day/night/dusk/dawn, sun/clouds, rain, snow, moon, animals, plants/flowers, water (lake/ocean/stream/river/colors), buildings, if any, construction type, .... think if you were selling stock photos and had 1M photos with different subjects. Say the client wants to convey modern, rural, living. How would you need to search to find all the photos you have that would fit those terms?  Perhaps a Ranch house, with solar panels, a Tesla vehicle in the barn charging, surrounded by fields or animals.

Fortunately, my needs are easier. See the attachment of the example photo that goes with the exif data.  My gallery webapp creates a google-maps link if the photo has GPS information inside it to the exact location.  That's fun.  The NextCloud maps/gallery addons can do something like that. Some will show thumbnails on a world map and allow zooming in.  Seeing hundreds of photos all around a region of the world can be fun, but seeing the photos in order they were taken tells a different story and help retain the experiences.

---

### Post by satimis on 2024-03-02
> **TheFu said:**
> Well, it might be offline for 3 minutes a day around midnight (local time)
OR
you may happen to be on a subnet that has attacked some of my servers, so it is blocked from all access.  You can try the wayback machine. The linked article was created years ago, so a copy or 50 would be there.  When google provided their google-cache, that would have been the easier way.

I would try another time
 
> 
I started watching that youtube link, but it is confusing to me. **Fort Bragg** is in NC and was renamed to Fort Liberty last year. [https://www.armytimes.com/news/your-army/2023/06/01/fort-bragg-to-become-fort-liberty-heres-what-you-need-to-know/](https://www.armytimes.com/news/your-army/2023/06/01/fort-bragg-to-become-fort-liberty-heres-what-you-need-to-know/)  Ask anyone related to the US military anywhere in the world and they will know about the NC Army base.  It is huge.  

Searching just for "Fort Bragg", without any state, points to the NC location.  It is odd that a "Fort" would have been named the same in two places controlled by the US.  Cities are commonly named the same around the US ... there must be 15 "San Jose" cities here and there's a Paris, Tx but having 2 military cities based on old Fort names does seem odd to me.  Adding clarification could be useful to prevent confusion.

Fort Bragg, California
[https://en.wikipedia.org/wiki/Fort_Bragg,_California](https://en.wikipedia.org/wiki/Fort_Bragg,_California)

I have been there several times.

> 
Another idea - have you considered using multiple audio tracks to keep the English and Mandarin separate?  Does youtube support that?  [https://support.google.com/youtube/answer/13338784?hl=en](https://support.google.com/youtube/answer/13338784?hl=en)  Just a thought.

Whether you meant language selection?  It would be a little bid complicate?  I need 2 identical sites.

> 
I'd probably use captions/subtitles for the text, so the images get more screen time, but I can see why doing it as you have makes sense too.
It is easy.  OpenShot has feature controlling image screen time.  Adding text on photos is also easy, even running text.  It depends on my time injected.

> 
Seeing what you've done, that does give me lots of ideas for some of my trips.  Thanks for sharing.
I have been doing it sometimes and up to now have more than 100 YouTube links created.  It is still increasing that is my headache.  I'm now searching hard for a better solution, if any?  I have thousands of photos captured in Northern, Western and Southern Europe countries.

Following YouTube link was finished about an hour ago

Kuala Lumpur, Malaysia
[https://www.youtube.com/watch?v=el310VbhbV0](https://www.youtube.com/watch?v=el310VbhbV0)
Include:-
KL Ritz Carlto Hotel
Pavilion Kuala Lumpur
Petronas Twin Towers
Tugu Negara, Kuala Lumpur
Istana Negara, Kuala Lumpur

Background Music
Swedish Rhapsody

Regards

---

### Post by dragonfly41 on 2024-03-02
[COLOR=#000000]>  .. now have more than 100 YouTube links created. It is still increasing that is my headache

[/COLOR]Perhaps what you are looking for is simply using [Zotero]("https://www.zotero.org/download/") which can hold all your YouTube links plus notes in a private or public collection.  Zotero installs into your Brave browser(as connector) and Zotero runs in your desktop. Then there are several extensions to explore. It is quite powerful. in particular Python can index your creations to add to Zotero. Your building of Zotero collection(s) can be automated.

Meanwhile my eXistDB experiments continue. I will publish these experiments when I'm finished.

---

### Post by TheFu on 2024-03-02
```
find gallery/ -type f |wc -l
32076

```

I have only 32K photos.

Closest I've been to Kuala Lumpur is Singapore and Thailand.  Always wanted to get there.  
```
11-Singapore-Thailand/
&#9500;&#9472;&#9472; 1121-ATL
&#9500;&#9472;&#9472; 1122-NRT
&#9500;&#9472;&#9472; 1123-SIN_Buddha_Tooth_Fattys
&#9500;&#9472;&#9472; 1124-Wheel_Waterfront
&#9500;&#9472;&#9472; 1125-Waterfront_Orchard_Rd
&#9500;&#9472;&#9472; 1126-Botanical_Gardens
&#9500;&#9472;&#9472; 1127-SIN_to_BKK
&#9500;&#9472;&#9472; 1128-Walk_Eat-Me
&#9500;&#9472;&#9472; 1129-Shopping
&#9500;&#9472;&#9472; 1130-Ayutthaya
&#9500;&#9472;&#9472; 1201-Chatuchak
&#9500;&#9472;&#9472; 1202-Palace
&#9492;&#9472;&#9472; 1203-Flights
```

The world is huge. Can't see all of it. I made a mind-map for the places I wanted to prioritize and where I'd already been when I was traveling multiple months of the year. I need to find that mind-map.  Found it. Travel-Places_to_visit_and_do.mm Used Freemind.  Last time it was touched was 2021, which makes since. Haven't traveled overseas since pre-COVID.

There's a snap package (aaaaarg) [https://snapcraft.io/freemind](https://snapcraft.io/freemind) .  I'm trying not to pollute my Mint desktop with any snaps and always avoid Java stuff. An AppImage would be ideal for this.  Snaps don't work on most of my systems, since my HOME directory isn't in the hard-coded place Canonical snaps require and I'm not going to move it for them after over 20 yrs of using NFS HOME mounts. Much too convenient.

---

### Post by dragonfly41 on 2024-03-02
[D3.js]("https://d3js.org/") should cover such requirements. Mapping media object, travel nodes, metadata .. 

[URL="https://www.toptal.com/javascript/a-map-to-perfection-using-d3-js-to-make-beautiful-web-maps"]One example. 
[/URL]
And here is a random walk based on your earlier examples ..

With some caution in kicking off another thought vector, your list of vectors takes us into the domains of context vectors and vector databases.

I first met early developers (product written in lisp) around 2000 in U.S. visit.
Today, explore Milvus. Vector database.
[https://github.com/milvus-io/milvus](https://github.com/milvus-io/milvus)
[https://github.com/towhee-io/examples/blob/main/image/text_image_search/1_build_text_image_search_engine.ipynb](https://github.com/towhee-io/examples/blob/main/image/text_image_search/1_build_text_image_search_engine.ipynb)
[https://milvus.io/milvus-demos/](https://milvus.io/milvus-demos/)
[https://github.com/tropy/tropy](https://github.com/tropy/tropy)
[https://phdprogress.com/organising-and-annotating-research-photos-with-tropy/](https://phdprogress.com/organising-and-annotating-research-photos-with-tropy/)
[https://tropy.org/](https://tropy.org/)
[https://www.dpreview.com/opinion/0718588880/one-thing-files](https://www.dpreview.com/opinion/0718588880/one-thing-files)
[https://www.dpreview.com/tag/one-thing-series](https://www.dpreview.com/tag/one-thing-series)
[https://forums.zotero.org/discussion/22126/photo-or-image-library-item](https://forums.zotero.org/discussion/22126/photo-or-image-library-item)

Zotero artwork
[https://libguides.libraries.wsu.edu/c.php?g=768677&p=5514196](https://libguides.libraries.wsu.edu/c.php?g=768677&p=5514196)

P.S. I should add to this curated list that I have Internet Archive installed as desktop app and I have just launched that, search "travel" and here is a bunch of YouTube clips .. [h=1]Mirrortube: Mirrored YouTube Videos[/h]

---

### Post by satimis on 2024-03-02
> **dragonfly41 said:**
> [COLOR=#000000]

[/COLOR]Perhaps what you are looking for is simply using [Zotero]("https://www.zotero.org/download/") which can hold all your YouTube links plus notes in a private or public collection.  Zotero installs into your Brave browser(as connector) and Zotero runs in your desktop. Then there are several extensions to explore. It is quite powerful. in particular Python can index your creations to add to Zotero. Your building of Zotero collection(s) can be automated.
Yes, my immediate need  is to organize all YouTube links created.  I'm now holding all links on a text file.

Where can I find document or video relating to the use of Zotero?  All found by me on searches are its instalation.  Thanks

> 
Meanwhile my eXistDB experiments continue. I will publish these experiments when I'm finished.
Thanks

Regards

---

### Post by satimis on 2024-03-03
> **TheFu said:**
> 

- snip -

The world is huge. Can't see all of it. I made a mind-map for the places I wanted to prioritize and where I'd already been when I was traveling multiple months of the year. I need to find that mind-map.  Found it. Travel-Places_to_visit_and_do.mm Used Freemind.  Last time it was touched was 2021, which makes since. Haven't traveled overseas since pre-COVID.

- snip - 
The World is huge.  It is correct.  I don't expect creating ONE video covering all my old photos captured in the past.

If I can't find a better solution.  I would stick on my present solution creating photo slideshows.  It is not simple nor straight-forwards.

Applications applied to create one slideshow video;
OpenShot/ShortCut
Inkscape
Libre Office
Libre Draw
Text to speech app
Text Editor to create tranparent and funny texts
GIMP
etc.

It will take 1 or 2 days to finish creating ONE slideshow video, depending on its quality which I need to achieve.  I'm still improving my technique daily.

My early photo slideshow video was very simple.  You can refer to my old slideshow below;

1992 carnival festival (Nottingham UK)
[https://www.youtube.com/watch?v=1B4TN9xgsJo](https://www.youtube.com/watch?v=1B4TN9xgsJo)

without text description nor oral narration

Regards

---

### Post by TheFu on 2024-03-03
When I need a simply lookup table of data, that is decoupled from the files, I use vimwiki.

I don't use it for photos, but I do use it for movies and watched TV shows. These are for those things I never want to bother with again - hence it is called "never_again".  Every once in a while, I'd find myself watching a movie I'd already seen and never wanted to bother with again. There are a bunch of bad movies out there ... or those that get released under multiple titles trying to find an audience.
My text DB, holds multiple tags and is similar to YAML, but my scripts to search it are just **egrep** commands.  For my needs, just the title, alternate titles and release year would probably be enough.  I usually add something to let me remember why I bothered before, so I don't do it again. Here's an example, 
```
- title: Back_Roads
  year: 2018
  actors: [ Jennifer Morrison ]
  description: Tubi version; A young man cares for his younger sisters after their mother is imprisoned for murdering their abusive father. When he strikes up an affair with a married woman, long-dormant family secrets bubble to the surface.
  tags: 
```

With the **egrep** script, I can query based on any of those things and others from Recoll searches which know about the video metadata too.  The only time I see things again now is if I actually want to see them.  I tried using the media center software to handle this, but it doesn't.  The indentation means it is part of the previous "title" record, so I really can add as many varied lines/tags as I'd like, as long as there isn't anything in the first column.  Grepping files is fast until they become huge. 100K lines is nothing.  Right now, it has about 12K lines, so I have lots of room.

There are lots of ways to store extra information about things.  Text processing is built into Unix. There are 50 text processing commands already on every Unix system, so why not master those and be able to create your own DB?

I also have a text list of music playlists.  ```
M3U_FILE="$HOME/bin/m3u_files.dat"
```  The script that I use to play those playlists quickly can also update the list of playlists.
```
if [ "$SEARCH" == "-u" ] ; then  
   /usr/bin/find $MUSIC -type f -iname \*m3u 2>/dev/null | tee "$M3U_FILE"
   echo "INFO: Done updating "$M3U_FILE" "
   exit 0;
fi
```
Very simple.  That .dat file is just a list of files from a specific directory tree that end in m3u (i.e. a playlist).  I like scripts that can self-update their data, especially when it is so easy.  1 line from that .dat file:
```
/d/D7/Music/New_Age/George_Winston/Autumn/vorbis-q6/George_Winston-Autumn-vorbis-q6.m3u
```
So, I'm likely to search on "Autumn" or "Winston" when I'd like it played:

```
$ m-search Autumn
0: /d/D7/Music/Music-Best/New_Age/George_Winston/Autumn/vorbis-q6/George_Winston-Autumn-vorbis-q6.m3u
1: /d/D7/Music/New_Age/George_Winston/Autumn/flac/George_Winston-Autumn-flac.m3u
2: /d/D7/Music/New_Age/George_Winston/Autumn/vorbis-q6/George_Winston-Autumn-vorbis-q6.m3u
a: play all
Select number: 2
```

Now I'll be able to listen to a great album this morning.  The "Music-Best/" directory system ends up on my phone for travel. Can't hold everything. I rip from CD to lossless flac. Never want to do that again.  q6 vorbis is excellent quality. Most importantly, I cannot tell the difference between q6 and flac music.

Anyways, there are lots of options that keep your photo metadata completely under your control and easy to find things.
My photo gallery software can store comments about the photo. That's where I put extra tags.  These comments are stored per-photo, but in a separate file, in a separate directory area.   So, if my original photos are in gallery/{YYYY}/, then the extra stuff like thumbnails, and resized photos are kept in photodata/{YYYY}/
photodata/2017/1130-Zodiac_Cruise/**comments**/048_Nieces_n_Uncle-Glacier.jpg.txt
My webapp searches include the image names and the contents of all txt comment files. There are also "descriptions/" files, but those are created in the webapp administration GUI, which is a pain to use.  I treat the description and comment files exactly the same.

photodata/2017/1130-Zodiac_Cruise/ contains:
```
$ ls
1024/  640/  800/  comments/  descriptions/  log.txt  thumbnails/
```
You can guess what each does.  Photos get scaled automatically - either by first view or through a weekly batch script.  I only pre-generation 1024-size images.  These are good enough for screen viewing on any devices I have and are 10x smaller than the originals.
```
7.7M    photodata/2017/1130-Zodiac_Cruise/1024/
692M    gallery/2017/1130-Zodiac_Cruise/
```
Size matters.

---

### Post by dragonfly41 on 2024-03-03
> [COLOR=#000000]Where can I find document or video relating to the use of Zotero? All found by me on searches are its instalation.[/COLOR][COLOR=#000000]
I will leave the installation instructions to read from Zotero site.

Regarding your question the best reference point is the Zotero forum.

I searched "YouTube citations in Zotero" .. and there are [discussions in Zotero forum]("https://forums.zotero.org/discussion/76017/citations-for-youtube-videos").
[/COLOR]
[And here is another explanation]("https://libguides.cmich.edu/c.php?g=104307&p=676121").

[COLOR=#000000]On the other points about analysing large datasets of metadata text there is yet another tool which might help although certainly the tools discussed in earlier posts are very powerful - recoll and egrep. Another app (GUI) is SearchMonkey.

[/COLOR]The suggested tool to investigate is AntConc part of a powerful toolset. It comes from a professor in linguistics based in Japan. 

Introducing AntConc
[https://www.laurenceanthony.net/software/antconc/](https://www.laurenceanthony.net/software/antconc/)

This allows pure text files to be analysed as corpora.
A helicopter view of all words in a created corpus (of metadata for the entire cluster of presentations) can be analysed.

Another part of the Swiss army knife of tools.

[Tutorial]("https://www.youtube.com/playlist?list=PLiRIDpYmiC0Ta0-Hdvc1D7hG6dmiS_TZj").

I have just downloaded AntConc 3 series into my latest Ubuntu 22.04 desktop. i have used this in earlier desktops.
But if you find other tools work then regard this as another experiment in metadata wrangling.
AntConc introduces the field of corpus linguistics and can apply to your [English and Mandarin corpora]("https://groups.google.com/g/antconc/c/UrjMWq8jbmY?pli=1").

---

### Post by dragonfly41 on 2024-03-03
I will just add in this slot (due to double posting) that once you have a library of Zotero citations you can quote them in separate documents (LibreOffice for example) or email messages. That is the purpose of citations.

---

### Post by satimis on 2024-03-07
Hi all,

I think I should target at creating an attractive website for embedding the YouTube links of all my photo slideshows.

In the past I have created following 5 webistes for presenting my photos captured worldwide:-

phgallery1.reynoldstocks.com
phgallery2.reynoldstocks.com
phgallery3.reynoldstocks.com
phgallery4.reynoldstocks.com
phgallery5.reynoldstocks.com

but not very successful.  I just leave them running on Internet without much effort injected to update and upgrade the websites.

Now I found the way creating photo slideshows on my old photos.  Up-to-now it is a wonderful solution to me for publishing my old photos.  **[COLOR="#FF0000"]I think I should inject my time and effort creating a private website to embed all the YouTube links of the photo slideshows.[/COLOR]**

How to create an attractive private website I'm still searching information on Internet?  There are many suggestions on Internet.  Which of them shall I follow?

Today, I just finished building following photo slideshow and upload it to YouTube.

**[COLOR="#FF0000"][COLOR="#FF0000"]Stockholm "Capital of Sweden"[/COLOR][/COLOR]**
[https://www.youtube.com/watch?v=RTYiAfYGiFQ](https://www.youtube.com/watch?v=RTYiAfYGiFQ)

with short text title on each photo.
2 text languages: English and Chinese
3 oral speeches: English and Chinese (Cantonese and Mandarin dialects)

Background music:
Serenade composed by Shubert
Piano version

The wonder of photo slideshow is able adding video on the master video.  Following link is an example:-

**[COLOR="#FF0000"]Civitella del Tronto (Italian)[/COLOR]**

I Borghi più belli d'Italia (Italian)
The most beautiful village of Italy

**[COLOR="#FF0000"]YouTube link[/COLOR]**
[https://www.youtube.com/watch?v=XRpy_de8P4Y](https://www.youtube.com/watch?v=XRpy_de8P4Y)

3 languages ==&#12299; Italian, English, Chinese
4 oral speeches ==&#12299;Italian, English, Chinese (Cantonese and Mandarin dialects)

Background music:
Torna A Surriento (Italian)
Come Back To Sorrento

Regards

---

### Post by TheFu on 2024-03-07
Be careful what you share.  I got a stalker that way.  Also, web indexing will happen and next thing you know, your photos are being used in commercial work without your permission.  A trivial password will stop most web-crawlers.   If you want people to find everything using common web-search tools, but not get great resolutions (perhaps limit them to x320 resolutions), then you can setup the full resolution (or web-optimized 1024 sized versions) behind a password area, but have low-quality, smaller, versions in the main site for the web-crawlers.

Be careful using copyrighted music.  The fines can be huge if you don't have permission.  You'll need to store all music permission information (which might be a web-page image) somewhere.  Watch out for music licenses that don't say "perpetual".  You probably know these things.

Lots of websites have pointers to youtube videos.  None have jumped out at me.  For example, [https://www.irongeek.com/](https://www.irongeek.com/) has links to IT Security Conference videos.  He's been doing it for over 15 yrs.  I first met Adrian in 2008 at a conference.  He starts with an event list of videos and links again to a single-page on his website for a specific video [https://www.irongeek.com/i.php?page=videos/oisf2023/oisf-03-these-artifacts-arent-fiction-matt-scheurer-tuan-phan](https://www.irongeek.com/i.php?page=videos/oisf2023/oisf-03-these-artifacts-arent-fiction-matt-scheurer-tuan-phan)  where he adds the abstract/summary.

The trick is to let people find you and the information, but not make it too busy.  Nobody wants to see a 4x4 grid of images when they only want to see 1-2 specific images. Guess it matters greatly on the audience and their reason for watching.  All the jokes about being invited over to someone's home to see vacation photos definitely apply.

Also decide if you want to allow ping-backs or comments from the public.  On my nearly dead blog, some of the best stuff is in the comments for a few articles.  Everyone has a slightly different viewpoint, if not completely different. ;)

---

### Post by dragonfly41 on 2024-03-07
My suggestion is to design your delivery to be *dynamic*. That is reflecting the interests and traffic of visitors. I for one am not interested in a multi language mix of commentaries. I might not require commentary. I might prefer large fonts. I might not want to use YouTube and so on. So capture up front your viewers' preferences (with their permission to save them as most privacy aware sites do today) then fire up a custom show for each viewer. Personalisation. So you might read viewer's preferences then automatically (based on viewer preferences) fire up a viewing session only for the period of viewing. If there are no views in play there are no servers to pay for. Heroku is good for firing up dynos. Platform as a Service. PaaS. don't follow in the ruts of YouTube. Be different. If you want to push your content to say registered viewers consider a zerotrust data vault to direct links to registered viewers.

---

### Post by satimis on 2024-03-08
My only target is retaining my old photos, able easily found by me and shared of my past travels to friends.  **[COLOR="#FF0000"]I'm not interested attracting other users on Internet.[/COLOR]**

I don't think hackers are interested on the video of my old photos.  There are many of similar photos on Internet.  Nether they have much to do on my video upload to YouTube.

Regarding the background music on my video, they are classics and the composers alread died long time ago.

I have friends worldwide.  They are Chinese, British, American, Canadian, French, German, Italian, Swede etc. therefore I need video in multi-languages, giving them a respect if I can speak their languages.  The photos were captured in their countries.

**[COLOR="#FF0000"]Following video is another example:[/COLOR]**
[https://www.youtube.com/watch?v=oSUkOjZgrJg](https://www.youtube.com/watch?v=oSUkOjZgrJg)

[B][COLOR="#FF0000"][COLOR="#FF0000"]Dusseldorf, Germany - Part 1
Düsseldorf, Deutschland &#8211; Teil 1  (German)[/COLOR][/COLOR][/B]
include:
Königsallee and Erkrath
enthalten (German)
Königsallee und Erkrath (German)

---

### Post by dragonfly41 on 2024-03-08
Suggestion. Take a leap of faith and install hidden gem [CherryTree]("https://www.giuspen.net/cherrytree/#downl") onto your desktop.
Play around with it. Read Online Manual. Tweak Preferences.
Then time permitting I can later write a thread on how to apply it to support your example workflow of managing multiple vectors (geography, languages, accessibility, interests, ...).

I am developing a similar workflow myself to use CherryTree (inter alia) as part of a toolchain to create a customised library of presentations.

As a starter for one, consider how you can map your global population of targetted recipients into the hierarchical node structure.  Consider how you can add images and text and code into each node.  Consider that you can export the hierarchical structure to conventional HTML structure for future massaging.
And so on.  CherryTree can be your private working desktop repository of assets but in a vector database style.

---

### Post by TheFu on 2024-03-08
A Guy in my LUG uses **CherryTree** for his personal wiki.
I use **vimwiki** for my personal wiki.

There are lots of options for this sort of need.  I looked at about 10 before finally deciding. For me, the choice was more about using text for other processing needs.  I'm odd.  Everyone has slightly different priorities.  CherryTree might be exactly what you want!

---

