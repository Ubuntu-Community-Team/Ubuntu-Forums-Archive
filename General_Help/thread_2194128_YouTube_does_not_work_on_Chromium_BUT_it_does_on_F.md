---
title: "YouTube does not work on Chromium BUT it does on Firefox!"
date: 2013-12-16
forum: General Help
---

### Post by amjjawad on 2013-12-16
Hi,

```
Xubuntu 12.04.3 - 3.2.0-57-generic x86_64 GNU/Linux
```

I am using two browsers:

Chromium:
```
Version 31.0.1650.63 Ubuntu 12.04 (31.0.1650.63-0ubuntu0.12.04.1~20131204.1)

```

Firefox: 
```
26.0
```

I am having hard time with Chromium when it comes to YouTube.

[ATTACH=CONFIG]248654[/ATTACH] 

However, the very same video on YouTube, on the very same system on the very same machine works like a charm on Firefox!

Odd enough, some videos work on Chromium but the majority that I click on don't work unless I use Firefox.

Any idea what is wrong?

Yes, 
```
xubuntu-restricted-extras
```
is installed :)

Thank you in advance!

---

### Post by grier-devon on 2013-12-16
Did some searching and could not find anything, the only two things I could suggest is uninstall the restricted extras and then install them again. The other option would be to install the Pepper Plugin from Chrome into Chromium. I know that is proprietary but so is the Adobe Flash plugin and pepper will always give you the latest Flash player which is nice. Just....
```
sudo add-apt-repository ppa:skunk/pepper-flash
sudo apt-get update
sudo apt-get install pepflashplugin-installer
```
```
sudo apt-get install gksu #it`s not installed by default in Ubuntu 13.04
gksu gksu gedit /etc/chromium-browser/default
```
```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```

EDIT: Did you also look to make sure it is enabled under plugins?

---

### Post by amjjawad on 2013-12-16
Okay, I just did a test right now and I found out something very odd and strange:

First of all, all videos on Facebook, I can watch these normally on Chromium without any problem. And I mean 'Videos' NOT youtube links.

As for youtube links on Facebook, inside facebook, I can watch normally but if I click on the youtube link and a new tab for youtube will be opened I will not be able to watch anything:

[ATTACH=CONFIG]248656[/ATTACH]

Refresh will not fix the issue. Clearing the cache did not fix the issue too.

Guess what? which is really odd:
If I click on different video (any) and go back to the previous one that didn't work on the first place, it will work!

I just can't explain what is going on? I mean, I have no idea why is that?

With Firefox, I don't have this problem, never had it.

---

### Post by finny388 on 2013-12-16
I have the exact same problem
Started a few weeks ago

On youtube, every so often, maybe every 8th video, won't play (this video is currently unavailable). Copy and paste url to firefox and it always works.
I'm also on 12.04 (voyager, xubuntu)

I just tried clicking on any other video, then hit the back button and voila, the video that wouldn't play now plays

very frustrating

---

### Post by amjjawad on 2013-12-17
> **finny388 said:**
> I have the exact same problem
Started a few weeks ago

On youtube, every so often, maybe every 8th video, won't play (this video is currently unavailable). Copy and paste url to firefox and it always works.
I'm also on 12.04 (voyager, xubuntu)

I just tried clicking on any other video, then hit the back button and voila, the video that wouldn't play now plays

very frustrating

Don't get me wrong but it feels better when someone has the very same problem :)

Hope we could find a solution for this :)

---

### Post by monkeybrain20122 on 2013-12-17
Have you checked this?
[http://askubuntu.com/questions/234871/youtube-says-this-video-is-currently-unavailable](http://askubuntu.com/questions/234871/youtube-says-this-video-is-currently-unavailable)

---

### Post by amjjawad on 2013-12-17
> **monkeybrain20122 said:**
> Have you checked this?
[http://askubuntu.com/questions/234871/youtube-says-this-video-is-currently-unavailable](http://askubuntu.com/questions/234871/youtube-says-this-video-is-currently-unavailable)

Hi,

Thank you for posting :)

I just installed:
```
apt-get install chromium-codecs-ffmpeg-extra
```

```
The following packages will be REMOVED:
  chromium-codecs-ffmpeg
The following NEW packages will be installed:
  chromium-codecs-ffmpeg-extra
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.


```

```
dpkg: chromium-codecs-ffmpeg: dependency problems, but removing anyway as you requested:
 chromium-browser depends on chromium-codecs-ffmpeg (>= 0.6) | chromium-codecs-ffmpeg-extra (>= 0.6); however:
  Package chromium-codecs-ffmpeg is to be removed.
  Package chromium-codecs-ffmpeg-extra is not installed.
(Reading database ... 166759 files and directories currently installed.)
Removing chromium-codecs-ffmpeg ...
Selecting previously unselected package chromium-codecs-ffmpeg-extra.
(Reading database ... 166756 files and directories currently installed.)
Unpacking chromium-codecs-ffmpeg-extra (from .../chromium-codecs-ffmpeg-extra_31.0.1650.63-0ubuntu0.12.04.1~20131204.1_amd64.deb) ...
Setting up chromium-codecs-ffmpeg-extra (31.0.1650.63-0ubuntu0.12.04.1~20131204.1) ...


```

Videos now on YouTube works for the first 3 seconds ONLY then BLACK Screen!!

---

### Post by amjjawad on 2013-12-17
I did 're-install':

```
chromium-browser
```

and

```
xubuntu-restricted-extras
```

I will check/test Chromium with YouTube and see whether that will make any difference or not!

---

### Post by monkeybrain20122 on 2013-12-17
This may shed some light?

[http://code.google.com/p/chromium/issues/detail?id=250139](http://code.google.com/p/chromium/issues/detail?id=250139)

Sorry you got black screen from the AskUbuntu link. I don't use Chromium.

---

### Post by amjjawad on 2013-12-17
> **monkeybrain20122 said:**
> This may shed some light?

[http://code.google.com/p/chromium/issues/detail?id=250139](http://code.google.com/p/chromium/issues/detail?id=250139)

Sorry you got black screen from the AskUbuntu link. I don't use Chromium.

Hi,

Thank you again, I have added my comment and I am not sure if reporting this as a bug using 'ubuntu-bug' will help? It might be hard to re-produce that for some!

---

### Post by amjjawad on 2013-12-17
> **amjjawad said:**
> I did 're-install':

```
chromium-browser
```

and

```
xubuntu-restricted-extras
```

I will check/test Chromium with YouTube and see whether that will make any difference or not!

That did NOT change anything. Still 'Black Screen' and of course, there is a sound!

I think I will report this as a bug, much better :)

---

### Post by amjjawad on 2013-12-17
[**Bug**]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1261733") has been reported!

If this affect you too, please click on: > This bug affects 1 person. Does this bug affect you? 


Thank you!

---

### Post by monkeybrain20122 on 2013-12-17
In the meantime, if it only affects Youtube there is an easy work around if you can install the Chrome addon tampermonkey,  use Viewtube [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011).  (In Firefox install the script with the greasemonkey addon)  It works much much better than flash on supported sites (Youtube, Vimeo, Dailymotion.. all the common ones) so even though I have no flash issue I still use it. 

Gecko-mediaplayer may not work on Chromium (it never works on Chrome except magically in Ubuntu13.10), in that case use Totem as the backend. Depending on the site and the video you may have to choose the output format from Viewtube's options (e.g Vimeo only works with "vlc" on Chrome, but pretty much anything works on Firefox, guess Chromium is like Chrome)

---

### Post by finny388 on 2013-12-17
Thanks for posting the bug. I have concurred making you and 1 other.

Have you mentioned that coming back to the video gets it to work? (I don't see a description of the bug outside of the title)

By no means a fix, that seems to be consistent for me. (click on another video, then hit back button)

---

### Post by amjjawad on 2013-12-18
> **monkeybrain20122 said:**
> In the meantime, if it only affects Youtube there is an easy work around if you can install the Chrome addon tampermonkey,  use Viewtube [http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011).  (In Firefox install the script with the greasemonkey addon)  It works much much better than flash on supported sites (Youtube, Vimeo, Dailymotion.. all the common ones) so even though I have no flash issue I still use it. 

Gecko-mediaplayer may not work on Chromium (it never works on Chrome except magically in Ubuntu13.10), in that case use Totem as the backend. Depending on the site and the video you may have to choose the output format from Viewtube's options (e.g Vimeo only works with "vlc" on Chrome, but pretty much anything works on Firefox, guess Chromium is like Chrome)

It does only affect YouTube on Chromium only :)

I am kind of old-school type of user. I am keeping everything as simple as possible. One package, gives me all what I need so I don't really add anything to my browser except the spelling checker (English Dictionary) :)

My easiest work around is to use Firefox ;)
But this bug need to be fixed, that is why I reported it.

Thanks for posting!

---

### Post by amjjawad on 2013-12-18
> **finny388 said:**
> Thanks for posting the bug. I have concurred making you and 1 other.

Thank you :)

Chad has marked it as incomplete so I hope he will change that to confirmed - I left him a note.


>  Have you mentioned that coming back to the video gets it to work? (I don't see a description of the bug outside of the title)

Check the very first line on the description ;)
I included the link of this thread.

> By no means a fix, that seems to be consistent for me. (click on another video, then hit back button)
Well, for now, going to another video is not helping either :/
Going to the other video will give me black screen right away!!

---

### Post by finny388 on 2013-12-22
so far clicking another video and going back as worked every time.

playlist are f'ed up too though. They play for 2-5 secs then automatically forward to the next one, then 2-5 sec...

---

### Post by amjjawad on 2013-12-23
> **finny388 said:**
> so far clicking another video and going back as worked every time.

playlist are f'ed up too though. They play for 2-5 secs then automatically forward to the next one, then 2-5 sec...

Hi,

I appreciate if you could post that on the [Bug Comment]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1261733") and please, make sure to click on "Affect me too" and everyone else who can see this bug or re-produce it, needs to do the same :) the developers need to know it is happening with more than one user.

Thank you!

---

### Post by finny388 on 2013-12-26
I posted a comment

I have already declared that it affects me. So far still OP and 1 more.

---

### Post by amjjawad on 2013-12-26
> **finny388 said:**
> I posted a comment

I have already declared that it affects me. So far still OP and 1 more.

Hi,

Many thanks :)

I hope Chad will work on that soon. Since he changed the bug into 'incomplete', he didn't get back to us so let's wait for him few more days :)

---

### Post by amjjawad on 2014-02-06
I am still suffering from this, by the way!

---

### Post by finny388 on 2014-02-16
I've 'upgraded' to pepper flash in chromium

this issue still happens (occasionally) and so far clicking on another video then hitting back button fixes it every time.

still, it's bloody annoying

---

### Post by amjjawad on 2014-02-17
> **finny388 said:**
> I've 'upgraded' to pepper flash in chromium

this issue still happens (occasionally) and so far clicking on another video then hitting back button fixes it every time.

still, it's bloody annoying

Hi,

Have you posted that on the bug report?

Thank you!

---

### Post by finny388 on 2014-02-17
yes

---

### Post by amjjawad on 2014-02-18
> **finny388 said:**
> yes

Thank you :)

I posted a note for Chad, hope he will read it soon :)

---

### Post by amjjawad on 2014-03-08
Hi,

Seems the issue is 'less' happening right now - can anyone confirm that?
It is not 100% solved as far as I can tell but now, another issue is happening - not sure if it related.

1- I open a youtube video
2- go to another website or click 'back'
3- go back to the same video and it is blurry 

[ATTACH=CONFIG]250958[/ATTACH]

I don't know if it is clear or not.

So, it the screen is not black, it is blurry.

Nothing much is happening on the bug report :(

---

### Post by CaptainMark on 2014-03-09
As a workaround it's worth joining the YouTube HTML 5 beta, I've been using it for a while without issues and any way to get rid of flash is worth a look IMO.

[https://www.youtube.com/html5?](https://www.youtube.com/html5?)

---

### Post by amjjawad on 2014-04-24
Hi,

Has anyone upgraded to 14.04 LTS with the same issue happening? I'm still on Xubuntu 12.04 LTS and haven't yet upgraded (most likely will not as long as Xubuntu 12.04 LTS is working very well) and the issue is still happening and there is no action on the [reported bug]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1261733") :(

The only news I read the other day was:
[https://lists.ubuntu.com/archives/ubuntu-desktop/2014-April/004487.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2014-April/004487.html)

---

