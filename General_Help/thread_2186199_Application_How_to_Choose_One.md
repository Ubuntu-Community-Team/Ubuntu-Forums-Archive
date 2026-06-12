---
title: "Application How to Choose One?"
date: 2013-11-06
forum: General Help
---

### Post by tomsubt on 2013-11-06
Hi:   I want to download and install VLC  from here>>   [http://www.videolan.org/](http://www.videolan.org/)

But when I try to, a Launch Application screen comes up and I have no idea how to do this, please see attachment and if anyone would be kind enough to explain how to do this I would be  great-full?  Thank You

---

### Post by Bucky Ball on 2013-11-06
Try here:

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

I got there by clicking 'Other Systems' underneath the download button on the link you provided. When I click the download button there I get 'The address wasn't understood'.

Something wrong with the VLC in the repositories or you just want 2.1?

The screenshot you've attached seems to indicate that the file that is downloaded is probably an .exe file or something Ubuntu doesn't know what to do with, so it is asking you how it can open it (what application do I use to open .exe). Of course, there isn't one. 

Also, just a note from that site on installing VLC:

> Graphical way

Open Synaptic application (click on System -> Administration -> Synaptic Package Manager).
Search for vlc and install it. You may also want to install browser-plugin-vlc.
If you are interested in streaming or transcoding, you should additionnally install libavcodec-extra-53.

---

### Post by howefield on 2013-11-06
Click on choose and navigate to file system > usr > bin > software-center.

---

### Post by Bucky Ball on 2013-11-06
> **howefield said:**
> Click on choose and navigate to file system > usr > bin > software-center.

+1. Worth a shot. Good thinking. That will soon tell if it a suitable installer for Ubuntu.

---

### Post by tomsubt on 2013-11-06
> **Bucky Ball said:**
> +1. Worth a shot. Good thinking. That will soon tell if it a suitable installer for Ubuntu.

Thank You Bucky Ball and Howefield,  I did as instructed and I believe VLV was installed my dvd's play pretty good but when I play a you tube video (dean martin roasts) the viewing screen looks all out of whack, please see the attachment to see and if you guys can tell me how I can get to to play back correctly like the dvd's do, Thanks

/home/tomsubt/Pictures/you tube video bad

---

### Post by Bucky Ball on 2013-11-06
That attachment didn't work. Try:

Edit Post>Go Advanced>paperclip icon>upload pic.

You are trying to play the Youtube stream in VLC? 

Copy the vid address>open VLC>Click Media>choose Open Network Stream, and paste the vid address in there.

Is it still out of whack?

---

### Post by tomsubt on 2013-11-06
Bucky Ball      Please copy and paste the attachment link to your address bar and hit go, I just tried it and it works if it don't work for you I will try as you instructed  Let me know OK?

---

### Post by Bucky Ball on 2013-11-06
> **tomsubt said:**
> Bucky Ball      Please copy and paste the attachment link to your address bar and hit go, I just tried it and it works if it don't work for you I will try as you instructed  Let me know OK?

It won't work for me as it is a path to a file on your hard drive:

/home/tomsubt/Pictures/you tube video bad 

I don't have the location '/home/tomsubt/Pictures/you tube video bad' on my hard drive, which is why it works for you. You do. I will receive a 'File not found' error, naturally. ;)

---

### Post by tomsubt on 2013-11-06
Ok  my mistake I thought It was like photobucket.com  I will try your instructions and get back to you, Thanks

---

### Post by tomsubt on 2013-11-06
Bucky Ball  you said>>>  You are trying to play the Youtube stream in VLC?

Copy the vid address>open VLC>Click Media>choose Open Network Stream, and paste the vid address in there.

Is it still out of whack?

No it worked pretty good from VLC but when I go to you tube its all out of whack, is there anyway to fix this, I look at you tube alot?  Thanks

ps: when I try to upload the picture I keep getting Error Invalid File. 

Let me try again and get back to you

---

### Post by tomsubt on 2013-11-06
I went to the adobe global storage settings and tried to disable hardware acceleration and  the picture was so distorted there too,  I could not see to uncheck it. I don't know if that would have worked or not to clear the picture on you tube
Maybe there is a setting or install I need on ubuntu what do you think? Thanks

---

### Post by Bucky Ball on 2013-11-06
Try installing ubuntu-restricted-extras.

---

### Post by tomsubt on 2013-11-07
Ok, I will try ubuntu-restricted-extras  have to go out for a few hours but will get back to you, Thanks

---

### Post by tomsubt on 2013-11-07
OK, I installed ubuntu restricted extras but did not help, so I installed "mtpaint" and sent the picture in the attachment. If you don't see the image let me know, if you do this green picture is the distorted picture I get when viewing dean martin roasts. Any idea's on what is wrong here and how to get a clear picture when viewing? Thanks

---

### Post by Bucky Ball on 2013-11-07
There is a default app already there to take screenshots, but no, no idea about the problem there.

---

### Post by tomsubt on 2013-11-07
OK, Thanks Bucky Ball and all you guys for the replies, guess i have to hope someone see's the attachment and can tell me why the you tube video's play like that!!

---

### Post by VMC on 2013-11-07
tomsubt, I don't know what Dean Martin roast you were watching, but I tried a John Wayne Dean Martin roast and it worked but just stopped. Then I tried another unrelated youtube and it work perfectly. Just copy and paste into network stream.

---

### Post by tomsubt on 2013-11-08
VMC:  Please explain what is meant by >>.paste into network stream. Do you mean paste it to the address bar? Thanks

---

### Post by vasa1 on 2013-11-08
> **tomsubt said:**
> OK, I installed ubuntu restricted extras but did not help, so I installed "mtpaint" and sent the picture in the attachment. If you don't see the image let me know, if you do this green picture is the distorted picture I get when viewing dean martin roasts. Any idea's on what is wrong here and how to get a clear picture when viewing? Thanks
See if this helps: [http://askubuntu.com/q/335124/25656](http://askubuntu.com/q/335124/25656)

---

### Post by Bucky Ball on 2013-11-08
> **tomsubt said:**
> VMC:  Please explain what is meant by >>.paste into network stream. Do you mean paste it to the address bar? Thanks

It is already in the address bar in Firefox. You want to copy it from there>open VLC>click File>Play Network Stream>Paste in the vid youtube address you just copied, as has been explained previously.

---

### Post by tomsubt on 2013-11-08
It does not play on vlc but my dvd did. also I went to link Vasa 1  sent and I looked into verify adobe and it verified that I had the latest, but video was green in there too.
I then went to update drivers and it tried to update but a message came back saying

"No Propriety drivers are in use on this system", how can I correct this and do you think this is the reason for poor video?

---

### Post by VMC on 2013-11-08
I don't recall what Linux OS your using and also what hardware. That shouldn't matter much, but it may reveal something.

Also, thanks for bringing this topic to light. I've used VLC for years without ever using the network stream, although there are youtube video's that I use each month. I use to use the youtube downloader. Not anymore! VLC works the best.

---

### Post by tomsubt on 2013-11-08
Yes, I am using 12.04, and don't have anything hooked up to it yet.

I see that others have the green distorted screen when viewing you tube too, but no-one seems
to know what could be causing it. I thought in my case it was the driver needed to be updated
but as I mentioned it stated "No Propriety drivers are in use on this system" would this somehow cause the green video? How to get drivers on ubuntu? Thanks

---

### Post by tomsubt on 2013-11-08
If anyone on this forum finds the answer to the green distorted viewing on you tube, please come back and reply here and I will try any idea you have.
Meanwhile I just put this URL from you tube where it would not show up correctly, into the VLC media player and it works great Here is the link from you tube>>>

[http://www.youtube.com/watch?v=pIeL7lQu3Po](http://www.youtube.com/watch?v=pIeL7lQu3Po)

I will have to use VLC directly from now on if I want to view you tube video in the future and I don't mind it, but can some one tell me if i have to keep going to the Dash to start VLC or is there a short cut I can install somewhere? Thanks

Oh,oh  I just realized the VLC player only plays for about 3 minutes then goes back to the start screen. I played the same you tube video twice and it keeps stopping at 3 minutes
anyone know what is causing this problem now?  I'm starting to think I died and went to hell and no one is telling me, heeeeelp"lol'

Now its not playing at all, I just need to know how to Uninstall VLC and reinstall it, this might help, thanks

---

### Post by VMC on 2013-11-08
> **tomsubt said:**
> ...
I will have to use VLC directly from now on if I want to view you tube video in the future and I don't mind it, but can some one tell me if i have to keep going to the Dash to start VLC or is there a short cut I can install somewhere? Thanks

...

**[UnityLaunchers]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")**

---

### Post by tomsubt on 2013-11-10
Thanks for the unity launcher link,  but it a little complicated for me to follow right now, so I will look into it later and just use dash.

---

