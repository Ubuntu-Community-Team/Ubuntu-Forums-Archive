---
title: "Flash plug-in not working in Chromium"
date: 2016-10-04
forum: General Help
---

### Post by rdh61 on 2016-10-04
Hi,

I am unable to understand how to resolve this issue. I want to watch the video on this page: [http://indexing.vbatech.com/tutorial-PDF.htm](http://indexing.vbatech.com/tutorial-PDF.htm)

What I see is a grey panel with a symbol of a piece of a jigsaw puzzle in the middle of it, and the message. "This plug-in is not supported."

I have adobe-flashplugin installed. I can watch other videos on Chromium and I can watch this video on Firefox. What could the problem be?

Many thanks.

P.S. Chromium v[COLOR=#303942][FONT=Ubuntu]ersion 52.0.2743.116 B, running on Ubuntu 16.04.[/FONT][/COLOR]

---

### Post by howefield on 2016-10-04
The adobe-flashplugin should give you Flash Version: 23.0.0.162 in Chromium and also Flash 11.2 r202 in Firefox, the linked video seems to work with Flash 11.2 r202. Do you have Firefox installed ?

---

### Post by rdh61 on 2016-10-04
> **howefield said:**
> The adobe-flashplugin should give you Flash Version: 23.0.0.162 in Chromium and also Flash 11.2 r202 in Firefox, the linked video seems to work with Flash 11.2 r202. Do you have Firefox installed ?

Yes, I do, but generally I prefer Chromium as I find it faster, so I would like it to have full functionality if possible.

---

### Post by howefield on 2016-10-04
Out of interest does the video play if you enter the address to it in the address bar ?

```
http://indexing.vbatech.com/videos/intro%20demo.mp4
```

If you are allowed to download the video and view offline, that's also another option.

---

### Post by dragonfly41 on 2016-10-04
I see the same report in my Chromium Web Browser.

That movie seems to expect Apple Qt plugin.

Does this explain ... [https://discussions.apple.com/thread/6526781?tstart=0](https://discussions.apple.com/thread/6526781?tstart=0)

---

### Post by rdh61 on 2016-10-04
> **howefield said:**
> Out of interest does the video play if you enter the address to it in the address bar ?```
http://indexing.vbatech.com/videos/intro%20demo.mp4
```Yes, that works. Thanks for the tip.

---

### Post by howefield on 2016-10-04
You're welcome, feel free to mark the thread as solved :)

---

### Post by rdh61 on 2016-10-04
> **dragonfly41 said:**
> I see the same report in my Chromium Web Browser.That movie seems to expect Apple Qt plugin.Does this explain ... [https://discussions.apple.com/thread/6526781?tstart=0](https://discussions.apple.com/thread/6526781?tstart=0)I guess it might. If so, does this suggest the provider of this video needs to update it with something Chrome/Chromium will support?

---

### Post by rdh61 on 2016-10-04
> **howefield said:**
> Out of interest does the video play if you enter the address to it in the address bar ?```
http://indexing.vbatech.com/videos/intro%20demo.mp4
```BTW, how did you derive that URL?

---

### Post by howefield on 2016-10-04
> **rdh61 said:**
> BTW, how did you derive that URL?

Right click on the "flash video" and select Inspect Element.. you'll see the relevant html source on the right hand side of the browser window.

---

### Post by rdh61 on 2016-10-05
> **howefield said:**
> Right click on the "flash video" and select Inspect Element.. you'll see the relevant html source on the right hand side of the browser window.

Apologies if I'm being dumb, but I cannot see that URL in the "Inspect Element" window (see screenshot). I presume that is because my plug-in is not loading. In that case, my problem remains: without the loaded plug-in I can neither watch the video directly, not find the video URL to watch in another tab or download. I guess the only option is to resort to Firefox. But I do ask, if Firefox can play it, why can't Chromium?




[ATTACH=CONFIG]271504[/ATTACH]

---

### Post by howefield on 2016-10-05
I can see it in your attached screenshot, it is the .mov file - right click on it and select "*Copy link address*" as per my screenshot. Once copied you can put it into the address bar and play, or use wget to download and watch in movie player, vlc ect.

---

### Post by rdh61 on 2016-10-05
> **howefield said:**
> Once copied you can put it into the address bar and play, or use wget to download and watch in movie player, vlc ect.

Thank you again. I have done what you suggested. When I paste the URL into the address bar, nothing happens in the browser. However, a window pops up prompting me to save the video to my computer. Then I can watch it in my preferred media player, for which I am grateful! 

However, I cannot mark this thread solved: my practical problem is solved by a work around, but it still seems there is a problem regarding Chromium's functionality.

---

### Post by howefield on 2016-10-05
> **rdh61 said:**
> ... I guess the only option is to resort to Firefox. But I do ask, if Firefox can play it, why can't Chromium?

I missed this part of your post. As mentioned earlier in the thread adobe-flashplugin which you have installed, should give you 2 versions of Flash Player, one which Firefox can use (NPAPI: 11.2.202.635) which can play quicktime movies, and also a version (PPAPI: 23.0.0.162) that Chromium/Chrome/Opera ect, can use but that would seem cannot play quicktime movies.

Firefox can be made to use the newer google developed PPAPI flash player but Chromium can't be made to use the older adobe developed NPAPI player.

That isn't a good explanation but might help answer as to why Firefox will play the file and Chromium won't.

> **rdh61 said:**
> Thank you again. I have done what you suggested. When I paste the URL into the address bar, nothing happens in the browser. However, a window pops up prompting me to save the video to my computer. Then I can watch it in my preferred media player, for which I am grateful!

Can't quite remember how I got the URL that I posted earlier in the thread which will play in the browser window.

---

### Post by howefield on 2016-10-05
> **rdh61 said:**
> ... I guess the only option is to resort to Firefox. But I do ask, if Firefox can play it, why can't Chromium?

I missed this part of your post. As mentioned earlier in the thread adobe-flashplugin which you have installed, should give you 2 versions of Flash Player, one which Firefox can use (NPAPI: 11.2.202.635) which can play quicktime movies, and also a version (PPAPI: 23.0.0.162) that Chromium/Chrome/Opera ect, can use but that would seem cannot play quicktime movies.

Firefox can be made to use the newer google developed PPAPI flash player but Chromium can't be made to use the older adobe developed NPAPI player.

That isn't a good explanation but might help answer as to why Firefox will play the file and Chromium won't.

> **rdh61 said:**
> Thank you again. I have done what you suggested. When I paste the URL into the address bar, nothing happens in the browser. However, a window pops up prompting me to save the video to my computer. Then I can watch it in my preferred media player, for which I am grateful!

Can't quite remember how I got the URL that I posted earlier in the thread which will play in the browser window.

---

### Post by rdh61 on 2016-10-05
> **howefield said:**
> I missed this part of your post. As mentioned earlier in the thread adobe-flashplugin which you have installed, should give you 2 versions of Flash Player, one which Firefox can use (NPAPI: 11.2.202.635) which can play quicktime movies, and also a version (PPAPI: 23.0.0.162) that Chromium/Chrome/Opera ect, can use but that would seem cannot play quicktime movies.

Firefox can be made to use the newer google developed PPAPI flash player but Chromium can't be made to use the older adobe developed NPAPI player.

That isn't a good explanation but might help answer as to why Firefox will play the file and Chromium won't.

Good enough for me! I'll mark solved (as solved can be).

---

