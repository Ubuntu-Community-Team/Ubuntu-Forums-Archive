---
title: "Chrome 34 Won't Play Yahoo Videos"
date: 2014-08-01
forum: General Help
---

### Post by Smallwheels on 2014-08-01
Chrome 34 won't play video on Yahoo: [https://screen.yahoo.com/snl/red-flag-000000452.html](https://screen.yahoo.com/snl/red-flag-000000452.html)


A couple of months ago I was so frustrated with Firefox not being able to play Flash videos on Yahoo that I switched to Chrome. Chrome could play the videos that Firefox wouldn't because Chrome comes with Pepperflash, which is a plug-in that keeps up with Flash releases. My favorite browser is Firefox because it has some features that Chrome doesn't have and some comparable features take extra steps to access on Chrome. I spent a lot of time setting up Chrome with all of my bookmarks and arranging them in the bookmarks bar. 


A couple of weeks ago some videos that played on Chrome before stopped playing and did play on Firefox. So for some time I've been switching between them trying to get videos to play. Doing that is annoying. 

In Chrome the page [https://screen.yahoo.com/snl/red-flag-000000452.html](https://screen.yahoo.com/snl/red-flag-000000452.html) will open. The place where the video should play is black. If I move the cursor over it I get a pop-up message that says "click here to see flash content". So clicking just gets rid of the little message and nothing happens. 

What is going on now? 

Just to save time I have the restricted extras package. 


Is anybody else experiencing this? All suggestions are welcome.

---

### Post by monkeybrain20122 on 2014-08-02
Works here. But the latest Chrome is 36, you are two versions behind, not sure if that is the reason.

Restricted extras should have nothing to do with it, as you said Chrome uses its own flash.

---

### Post by Smallwheels on 2014-08-02
I'm still on 12.04 LTS. Maybe that is why I still have 34. Chrome doesn't give me any options to update it. It is done automatically.

---

### Post by monkeybrain20122 on 2014-08-02
Are you sure it is Chrome and not Chromium? Google should update it whether it is 12.04 or 14.04.

---

### Post by vasa1 on 2014-08-02
> **monkeybrain20122 said:**
> Are you sure it is Chrome and not Chromium? ...
That most probably explains the old version.

---

### Post by kostkon on 2014-08-02
I'm on 12.04 and it plays just fine in Firefox with the old 11.2 Flash.

Anyway, make sure that you don't have any plugins blocking your Flash content.

If you are indeed using Chromium, then try reinstalling the pepper flash package:
```
sudo apt-get install pepperflashplugin-nonfree --reinstall
```

and / or

updating it:
```
sudo update-pepperflashplugin-nonfree –install
```

Btw, if you want to get the latest pepper flash (from Chrome unstable that is), then, do:
```
sudo update-pepperflashplugin-nonfree –install –unstable –unverified
```

Hope that helps.

---

### Post by monkeybrain20122 on 2014-08-04
> **kostkon said:**
> I'm on 12.04 and it plays just fine in Firefox with the old 11.2 Flash.



That is odd, Firefox never works here even with hal installed.

---

### Post by Smallwheels on 2014-08-16
I went to the settings and learned I'm using Chromium. I did turn off all plug-ins and extensions and the same thing happened. 

With some updates something changes that just doesn't go right. Now Firefox plays some videos and Chromium doesn't. On Yahoo after a video plays on the page full of video links, none of the other videos will load or play. The way to get around that is to right click on a video and select open in a new window. Then that video will play. This is just annoying. 

If only I could download programs or an OS and have it work well once set up. Then I could just leave it alone until it didn't function properly. Then I would try updating things. I came across a video about PC BSD. It is another free OS. It is quite a bit different from GNU/Linux under the hood but just about the same on top. It has a feature similar to the System Restore in the Windoz OS that allows users to undo any updates that caused problems. THAT is a VERY attractive feature for me. If I could undo updates that messed things up I would go back to Ubuntu 13.04. I loved that one. It was totally bug free on my system. Ubuntu 13.10 was a nightmare. I'm glad to have left it. 

I've got a new bug that is annoying me. It is totally unrelated to the web browsers. Thumbnail images for videos and photos no longer display a picture. They just show the placeholder from the respective programs. The thumbnails from older uploads and downloads continue to show images. This is a big deal for me because I sell things on ebay and need to edit lots of images. I'm going to reload the OS or try another one or two very soon. Maybe in the updated latest and greatest versions of whichever one I select, the Chromium bug, Firefox bug, and thumbnail bug will be gone. 

Is Ubuntu 14.04 LTS running smoothly for most people by now? Is it safe to switch from 12.04 LTS to this one without too many problems?

---

### Post by Smallwheels on 2014-08-17
I forgot to mention that I did a pepper flash update and nothing has changed in Chromium. There is just a black box where a video and the controls should be.

---

