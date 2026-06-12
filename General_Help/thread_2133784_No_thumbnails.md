---
title: "No thumbnails"
date: 2013-04-09
forum: General Help
---

### Post by ac98521 on 2013-04-09
Hi guys, I've just reinstalled my ubuntu 12.04 and now, there are no thumbnails displayed for my videos. Why is that?

---

### Post by slickymaster on 2013-04-09
Do you have **libxine1-ffmpeg** installed? That may be needed for some thumbnails.
Try:
```
sudo apt-get install libxine1-ffmpeg
```
Then force nautilus to generate new thumbnails:
```
rm -r $HOME/.thumbnails/fail
rm -r $HOME/.thumbnails/normal
killall -9 nautilus
```

---

### Post by ac98521 on 2013-04-09
it didn't work :(

---

### Post by slickymaster on 2013-04-09
Maybe you need to install more codecs (depending upon the kind of videos you have).
Run this to see if works:
```
sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly totem
sudo apt-get install ubuntu-restricted-extras
sudo rm -r $HOME/.thumbnails/fail
sudo rm -r $HOME/.thumbnails/normal
```

---

### Post by ac98521 on 2013-04-09
I did [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install gstreamer0.10-plugins-bad gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly totem

but not

[/FONT][/COLOR]
sudo apt-get install ubuntu-restricted-extrassudo rm -r $HOME/.thumbnails/failsudo rm -r $HOME/.thumbnails/normalSince I don't remember having them before and my OS displayed thumbnails :) So... any other ideas my man? :(

---

### Post by slickymaster on 2013-04-09
> **ac98521 said:**
> So... any other ideas my man? :(

I'm sorry, but to be honest, no.

You could see [this]("http://fixed-it.blogspot.pt/2009/08/nautilus-ubuntu-missing-thumbnails.html"), try if somehow you can get a clue to solve it.

---

### Post by ac98521 on 2013-04-09
i di[FONT=Georgia, serif][COLOR=#333333]*d "*[/COLOR][/FONT][COLOR=#333333][FONT=Georgia][I]nautilus &"

[/I][/FONT][/COLOR]here's what I got

Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/A%20Tale%20of%20Mari%20and%203%20Puppies.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/bongbong.flv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Brave.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Cars%202%20%7B2011%7D.avi' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Citizen%20Kane.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Conan%20the%20Barbarian.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Constantine.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Dead%20Silence.avi' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Drive%20%20%7B2011%7D.avi' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Eurotrip.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Fight%20Club.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Hachiko.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/He-Man%20Last%20Stand.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Ju%20On.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/KAMEN%20RIDER%20DECADE.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/MaskedRider.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.

---

### Post by slickymaster on 2013-04-09
> **ac98521 said:**
> i di[FONT=Georgia][COLOR=#333333]*d "*[/COLOR][/FONT][COLOR=#333333][FONT=Georgia][I]nautilus &"

[/I][/FONT][/COLOR]here's what I got

Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/A%20Tale%20of%20Mari%20and%203%20Puppies.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/bongbong.flv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Brave.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Cars%202%20%7B2011%7D.avi' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Citizen%20Kane.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Conan%20the%20Barbarian.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Constantine.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Dead%20Silence.avi' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Drive%20%20%7B2011%7D.avi' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Eurotrip.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Fight%20Club.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Hachiko.mkv' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/He-Man%20Last%20Stand.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/Ju%20On.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/KAMEN%20RIDER%20DECADE.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/MaskedRider.mp4' isn't thumbnailable
Reason: Media contains no supported video streams.

Y_ou should had start your original post saying that the videos were in a windows directory_. Like me, I'm guessing that everybody else got convinced that they were on your Ubuntu system.

Do you have permissions on **[COLOR=#000000]///media/9808C6C208C69F1E/Documents%20and%20Settings/Brian/Videos/[/COLOR]**[COLOR=#000000]?[/COLOR]
Do you have samba package installed on your 12.04?

---

### Post by ac98521 on 2013-04-09
I don't have a samba package. And I don't know how to find out my permission on the path :(

---

### Post by slickymaster on 2013-04-09
> **ac98521 said:**
> I don't have a samba package.
[Samba File Server]("https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html")

> **ac98521 said:**
> And I don't know how to find out my permission on the path :(
As that path refers to a windows folder, you have to access it in windows, then right-click the file or folder, click Properties, and then click the Security tab.

---

### Post by ac98521 on 2013-04-09
Wait! I got them both now! Still the same. I think the thumnails problem only applies to the video file types :(

Here is what I tried. 

I tried to copy 1 video 1 file from my windows system and still. No thumnail for the copied file. Usually when I transfer a file to another system, ubuntu makes a thumnail for it.

Then I tried to record a video. Guess what? there is a good thumbnail :o

---

### Post by ac98521 on 2013-04-09
please delete this reply as it will be double post and I dont know how to delete this post

---

### Post by slickymaster on 2013-04-09
> **ac98521 said:**
> Wait! I got them both now! ...
To be honest I don't understand what you now have. Do you mean that you already had Samba package installed?

> **ac98521 said:**
> Still the same. I think the thumnails problem only applies to the video file types :(

Here is what I tried. 

I tried to copy 1 video 1 file from my windows system and still. No thumnail for the copied file. Usually when I transfer a file to another system, ubuntu makes a thumnail for it.

Then I tried to record a video. Guess what? there is a good thumbnail :o

Keep in mind that by default Nautilus won't create thumbnails for files larger than 10MB.

You could try to install [ffmpegthumbnailer]("https://code.google.com/p/ffmpegthumbnailer/")

---

### Post by ac98521 on 2013-04-09
> **slickymaster said:**
> 
To be honest I don't understand what you now have. Do you mean that you already had Samba package installed?



Keep in mind that by default Nautilus won't create thumbnails for files larger than 10MB.

You could try to install [ffmpegthumbnailer]("https://code.google.com/p/ffmpegthumbnailer/")
Yes I have samba and permission

libxine1-ffmpeg?? I have it

If nautilus wont create thumbnails larger than 10 MB, how come I had thumbnails for videos 2gb before I reinstalled ubuntu 12.04? I also have a video 2mb and it didn't have a thumnail

---

### Post by slickymaster on 2013-04-09
> **ac98521 said:**
> libxine1-ffmpeg?? I have it

No, I'm not speaking of a single library.
[ffmpegthumbnailer]("https://code.google.com/p/ffmpegthumbnailer/") is a video thumbnailer used to create thumbnails for video files. The thumbnailer uses ffmpeg to decode frames from the video files, so supported videoformats depend on the configuration flags of ffmpeg. It was designed to be as fast and lightweight as possible. The only dependencies are ffmpeg, libpng and libjpeg.

> **ac98521 said:**
> If nautilus wont create thumbnails larger than 10 MB, how come I had thumbnails for videos 2gb before I reinstalled ubuntu 12.04? I also have a video 2mb and it didn't have a thumnail
I said that by default Nautilus won't create thumbnails for files larger than 10MB, but that's a customizable feature of Nautilus. To change it, open Nautilus and navigate to **Edit -> Preferences -> Preview**&#8203;.

---

### Post by ac98521 on 2013-04-10
[FONT=Verdana]> **slickymaster said:**
> No, I'm not speaking of a single library.[/FONT]
[ffmpegthumbnailer]("https://code.google.com/p/ffmpegthumbnailer/")[FONT=Verdana] is a video thumbnailer used to create thumbnails for video files. The thumbnailer uses ffmpeg to decode frames from the video files, so supported videoformats depend on the configuration flags of ffmpeg. It was designed to be as fast and lightweight as possible. The only dependencies are ffmpeg, libpng and libjpeg.[/FONT]
[FONT=Verdana][/FONT]

[FONT=Verdana]still didn't work, preferences and ffmpeg failed. Do you think it was because I lack a plug in or something?[/FONT]

[FONT=Verdana]EDIT[/FONT]
[FONT=Verdana] i found the answer[/FONT]
[http://askubuntu.com/questions/2608/nautilus-video-thumbnails-without-totem](http://askubuntu.com/questions/2608/nautilus-video-thumbnails-without-totem)

I know I sucked so much that you ran out of patience and time for helping man. Anyway thank you a lot :) If you were a woman I would've kissed you right now hahaha thank you so much

---

### Post by slickymaster on 2013-04-10
> **ac98521 said:**
> [FONT=Verdana]still didn't work, preferences and ffmpeg failed. Do you think it was because I lack a plug in or something?[/FONT]

[FONT=Verdana]EDIT[/FONT]
[FONT=Verdana] i found the answer[/FONT]
[http://askubuntu.com/questions/2608/nautilus-video-thumbnails-without-totem](http://askubuntu.com/questions/2608/nautilus-video-thumbnails-without-totem)


Glad you got it working. Sometimes, with linux, it's just like that, trial and error.
> **ac98521 said:**
> 
I know I sucked so much that you ran out of patience and time for helping man. Anyway thank you a lot :) If you were a woman I would've kissed you right now hahaha thank you so much

Not only you didn't suck as I didn't ran out of patience. Thing was a deadline on a project which I had to fulfilled.

Anyway, now you can finally mark this thread as solved.

---

