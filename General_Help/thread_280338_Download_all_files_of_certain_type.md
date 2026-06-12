---
title: "Download all files of certain type"
date: 2006-10-19
forum: General Help
---

### Post by Blyzzard on 2006-10-19
Hey everyone,

I collect online comics and download them to disk. I used to use a number of programs that could downlaod a list of files all at once... 

usually something like
[http://www.domain.com/comic/img001.jpg](http://www.domain.com/comic/img001.jpg)
[http://www.domain.com/comic/img002.jpg](http://www.domain.com/comic/img002.jpg)
[http://www.domain.com/comic/img003.jpg](http://www.domain.com/comic/img003.jpg)
etc...

i could probably do that with d4x or wget...

The problem is that the latest comic i want to downlaod uses many file formats... jpg/gif/png/bmp... and they're all in random order, So i'd need somesort of program that i can put the domain and directory, and maybe even first part of file name like:

[http://www.domain.com/comic/img*](http://www.domain.com/comic/img*)

and then set it to downlaod all files with that start like that.

is there anythnig i could use to do that?

And yes, i am lazy, i could go and do it manually, but there could be hundreds of images.

Oh - I've only been using ubuntu (or any non windows system for that matter) for about a month now, so please be gentle :-)

---

### Post by apjone on 2006-10-19
1) Do you have the websites permission
2) Have you tried FlashGot firefox extension?
man curl
man wget

---

### Post by Blyzzard on 2006-10-19
> **apjone said:**
> 1) Do you have the websites permission
2) Have you tried FlashGot firefox extension?
man curl
man wget

Anyone can download the images - you don't need a password to access the site and i only want them for personal use, i'm not going to upload them to some other website and claim ownership of them.

and no i haven't tried flashgot, i was under the impresison that that extension downlaoded all available links of a certain type. I suppose i COULD go and create a spreadsheet with all the possible links.. i.e.

[http://www.domain.com/comic/img001.**jpg**](http://www.domain.com/comic/img001.**jpg**)
[http://www.domain.com/comic/img001.**png**](http://www.domain.com/comic/img001.**png**)
[http://www.domain.com/comic/img001.**bmp**](http://www.domain.com/comic/img001.**bmp**)
[http://www.domain.com/comic/img001.**gif**](http://www.domain.com/comic/img001.**gif**)
[http://www.domain.com/comic/img002.**jpg**](http://www.domain.com/comic/img002.**jpg**)
[http://www.domain.com/comic/img002.**png**](http://www.domain.com/comic/img002.**png**)
[http://www.domain.com/comic/img002.**bmp**](http://www.domain.com/comic/img002.**bmp**)
[http://www.domain.com/comic/img002.**gif**](http://www.domain.com/comic/img002.**gif**)
[http://www.domain.com/comic/img003.**jpg**](http://www.domain.com/comic/img003.**jpg**)
[http://www.domain.com/comic/img003.**png**](http://www.domain.com/comic/img003.**png**)
[http://www.domain.com/comic/img003.**bmp**](http://www.domain.com/comic/img003.**bmp**)
[http://www.domain.com/comic/img003.**gif**](http://www.domain.com/comic/img003.**gif**)

and then creat an html from that, access it with firefox and then tell it to downlaod all... that's one hell of a mission though. 

I will do that (thanks for the thought) if there isn't some sort of application that can do it for me automatically...

---

### Post by DarkN00b on 2006-10-19
Looks like you need the Downthemall Firefox extension.
[https://addons.mozilla.org/firefox/201/]("https://addons.mozilla.org/firefox/201/")

Its great for downloading many things, but especially pictures.

---

