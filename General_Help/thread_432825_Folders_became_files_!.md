---
title: "Folders became files !?"
date: 2007-05-04
forum: General Help
---

### Post by JJNova on 2007-05-04
Hello,

I started up Amarok in order to "jam some tunes' while surfing the internetz. I just clicked on some random song that I figured got imported when I moved all the files from my old drive. Amarok couldn't play it, so I immediately assumed that I decided to delete the file somewhere in the past, since it was probably downloaded by the roommate I used to have when that previous hard drive was in use. Clicking through Amaroks options, I instruct the program to rescan my collection, so that all dead links are removed.

Amarok fails at this also. So I decide to look and see what is going on, and Lo and Behold something I have not seen before. My folders.... have been turned into files. In order to help anyone visualize this, I have attached this image.

[IMG]http://img.photobucket.com/albums/v623/jjnova/folder.png[/IMG]


The files Music and Video, are supposed to be folders. In fact, they are supposed to be gigantic folders. Checking the properties of each of the files is futile, as all categories are returned as 'Unknown'. Although the drive is named "windows/media" it is not an NTSF filesystem. It is now an EXT3, but when I changed it over I retained the same name structure to avoid confusion.

The only problem shooting I have done aside from searching the forum and using google is to restart gnome, which didn't solve the problem. Any suggestions are greatly appreciated. 

Thanks for your time.

---

### Post by dannyboy79 on 2007-05-04
> **JJNova said:**
> Hello,

I started up Amarok in order to "jam some tunes' while surfing the internetz. I just clicked on some random song that I figured got imported when I moved all the files from my old drive. Amarok couldn't play it, so I immediately assumed that I decided to delete the file somewhere in the past, since it was probably downloaded by the roommate I used to have when that previous hard drive was in use. Clicking through Amaroks options, I instruct the program to rescan my collection, so that all dead links are removed.

Amarok fails at this also. So I decide to look and see what is going on, and Lo and Behold something I have not seen before. My folders.... have been turned into files. In order to help anyone visualize this, I have attached this image.

[IMG]http://img.photobucket.com/albums/v623/jjnova/folder.png[/IMG]


The files Music and Video, are supposed to be folders. In fact, they are supposed to be gigantic folders. Checking the properties of each of the files is futile, as all categories are returned as 'Unknown'. Although the drive is named "windows/media" it is not an NTSF filesystem. It is now an EXT3, but when I changed it over I retained the same name structure to avoid confusion.

The only problem shooting I have done aside from searching the forum and using google is to restart gnome, which didn't solve the problem. Any suggestions are greatly appreciated. 

Thanks for your time.

the picture you attached isn't there so I can't see what you're seeing. this is what I suggest. boot into a live cd, mount the hard drive where you THINK the music folder's are that contain all your music. are they folder's now? perform a search from a terminal using this command

sudo find /whereeveryoumountedtheharddrive -name *.mp3

that's of course only if it's all mp3's, if you have ogg music than use that. let me know what's up. also, maybe you could host the picture on imageshack.org, that's where I put my pictures cause I don't know how you tried to attach the picture. good luck

---

### Post by JJNova on 2007-05-04
> **dannyboy79 said:**
> the picture you attached isn't there so I can't see what you're seeing. this is what I suggest. boot into a live cd, mount the hard drive where you THINK the music folder's are that contain all your music. are they folder's now? perform a search from a terminal using this command

sudo find /whereeveryoumountedtheharddrive -name *.mp3

that's of course only if it's all mp3's, if you have ogg music than use that. let me know what's up. also, maybe you could host the picture on imageshack.org, that's where I put my pictures cause I don't know how you tried to attach the picture. good luck

The image is here - [http://img.photobucket.com/albums/v623/jjnova/folder.png](http://img.photobucket.com/albums/v623/jjnova/folder.png)

Alas, I think the hard drive is going out. After rebooting, the hard drive no longer mounts. :( 
This is the first time I have had a hard drive die out on me silently though, all other instances (only 3) have consisted of a bad arm, which I could hear 'scraping' the disc.

---

