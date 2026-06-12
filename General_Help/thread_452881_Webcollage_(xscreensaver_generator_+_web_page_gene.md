---
title: "Webcollage (xscreensaver generator + web page generator)"
date: 2007-05-23
forum: General Help
---

### Post by seamuso on 2007-05-23
This has plagued me for a while now (predates my ubuntu install by quite some time). Xscreensaver includes a script called webcollage which generates a couple of things .. the first is a screensaver page of images that are randomly grabbed from several sources. The second ability is that you can run the script as a standalone and generate an image map filled with random images ( [http://www.jwz.org/webcollage/](http://www.jwz.org/webcollage/) .. may have nudity which is where I'm heading with this).

The first time I had it running, my wife slapped me .. OK, not really, but she got pretty pissed ... something about women spread eagle on my screen, etc .. and we have kids in the house .. was unintentional, btw.

So, I dug into the script and discovered how to weight the searches so that only google was being searched
```
my @search_methods = (  0, "altavista",    \&pick_from_alta_vista_random_link,
                        0, "livejournal",  \&pick_from_livejournal_images,
                        0, "yahoorand",    \&pick_from_yahoo_random_link,
                        33, "googlephotos", \&pick_from_google_image_photos,
                        34, "googleimgs",   \&pick_from_google_images,
                        33, "googlenums",   \&pick_from_google_image_numbers,
                        0, "flickr_recent", \&pick_from_flickr_recent,
                        0, "flickr_random", \&pick_from_flickr_random,

```

 and on top of that, I found the setting to  use the full safe search option at google

```


my $google_images_url =     "http://images.google.com/images" .
                            "?site=images" .  # photos
                            "&btnG=Search" .  # graphics
                            "&safe=on" .     # no screening
                            "&imgsafe=on" .
                            "&q=";

```

all was well .. I had my randomly generating screensaver based on a custom dictionary list + I was generating a page ( [http://info.bluefrogcs.com](http://info.bluefrogcs.com) )that was auto-uploaded to my website every 30 minutes or so (also based on the dictionary list) that were about 99% clean of the inappropriate images.

It was about that same time that google did their adsense changes and suddenly I was no longer able to pull in any images. I just ran webcollage again in my feisty install and same thing, I can't get any images from google .. google is also the only option that has a safe search option.

Has anyone else used the webcollage and gotten it working with google (recently)?

---

### Post by rockhoppr on 2007-06-04
I found out about this screensaver at a very inopportune time! I REALLY wish someone at Gnome would get a clue and allow easy screensaver management. 

Anyway, I ultimately just removed this screensaver but this info was very helpful. Thanks for posting it.

---

### Post by seamuso on 2007-06-04
I think google has pegged the way webcollage searches and blocks all search queries.  It's too bad really though, was a fun way to generate a random page or screensaver and when you have a family, it also (unfortunately) becomes unsafe for the home.

---

### Post by airtonix on 2007-11-27
Fspot has a screensaver function that lets you use your photo collection as a slideshow screensaver...  not as unique as the collage format, but at least you can control the quality and content of the pictures

---

