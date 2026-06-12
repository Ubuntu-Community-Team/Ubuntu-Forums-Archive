---
title: "video playback - green bar"
date: 2006-11-19
forum: General Help
---

### Post by trstn on 2006-11-19
Hi all, made the switch to ubuntu from xp a few weeks back, getting there with linux but i seem to be having some codec problems.

Basically when playing some videos in vlc, mplayer, xine etc i get a horizontal green bar accross the very top of the video. Size varies but seems to be the same proportion of the screen (about 1 7th).

It only seems to affect xvid avi's - the problems not there with the same video's under XP.

Any ideas?

---

### Post by studentism on 2006-11-21
Just out of curiosity, are you running either compiz or beryl?

Either way, try (from the main VLC window)

Settings > Preferences > Video > Output Modules (check the Advanced options in the bottom right hand corner) > Change "Video Output Module: Default" to "Video Output Module: X11 Video Output"

Seem to recall that's what worked for me, let me know your results.

---

### Post by trstn on 2006-11-24
What do you know; that's solved it, thanks studentism.

Regards compiz/beryl, I am running beryl, in full screen i get a glitchly playback unless i switch the window manager back to Metacity. If i do that i get seemless playback.

The green bar thing was becomming annoying, you've given me one less reason to boot into xp :)

Now if only i could get bin/cue files working with vlc.

---

### Post by afarrakh on 2006-11-27
I had the same problem with Edgy/Beryl/XGL on my VLC.

Green band at top with some videos. following ur instructions i changed the output to X11 in VLC preferences that solved the problem. No more green bars.

But the video quality is lower as compared with default output vs X11.

When i shift to metacity, the X11 output doesnt work at all. video is too jerky to play. Does it mean that X11 only works on beryl?

I hope theres a better way to handle this.

...

---

### Post by xopher on 2006-11-27
> **trstn said:**
> 
Now if only i could get bin/cue files working with vlc.

If you cant figure out how, you could always convert the bin/cue file to an iso -- with eg. bchunk

Maybe not a final solution -- but at least a workaround. Hope it helps

---

### Post by trstn on 2006-11-29
Yeah i've been looking at something like that. Just dropping into xp for the time being as vlc will play them natively there.

I think I'm on it, making progress anyway and I'm learning more ubuntu/linux stuff as i go along which is always helpful.

---

### Post by raul_ on 2006-12-30
How can i change that in xine or totem? i've looked in all the options but i can't seem to find it :-k

---

### Post by raul_ on 2007-01-06
Settings->Video

Changing driver from "auto" to "xshm" did the trick

---

### Post by Tweepy on 2007-01-15
Hello, every Ubuntu users, I still have the same problem, even with the hint in VLC.
It's append regardless to the player, but only with xvid format
here the output:
[IMG]http://www.tachypic.com/image/3818.jpeg[/IMG]
And the color red is shifted down, a little unpleasant :)
Thx in advance.
OOOpsss, I'm running with:
beryl/xgl
ATI X600 mobile with proprietary drivers
Ubuntu 6.10 up to date
Codecs installed from Automatix2

---

### Post by Poene on 2007-09-28
Thanks, This thread helped me as well.

---

### Post by sr20ve on 2007-12-20
> **raul_ said:**
> Settings->Video

Changing driver from "auto" to "xshm" did the trick


Thanks, that did it for me.

---

### Post by MaindotC on 2008-03-16
> **studentism said:**
> Just out of curiosity, are you running either compiz or beryl?

Either way, try (from the main VLC window)

Settings > Preferences > Video > Output Modules (check the Advanced options in the bottom right hand corner) > Change "Video Output Module: Default" to "Video Output Module: X11 Video Output"

Seem to recall that's what worked for me, let me know your results.

Dude you're da man!  If you search my posts you'll see VLC caused me to reinstall twice today, and now I'm not sure it was even my setup - I think it was the type of video I was playing :(  Why can I not give you thanks??  Don't see the icon...

Now can you fix totem so everyone's skin isn't blue :-p  There was a blog about it a while ago title "I'm feeling blue" or "I'm so blue" something like that - explained how to fix it but now I can't find it.

---

### Post by eeefresh on 2008-03-26
This worked for me, too.  Thanks!

Now can anyone tell me why I get this message when I try to open an avi file?
```

The filename "The Italian Job.AVI" indicates that this file is of type "avi document". The contents of the file indicate that the file is of type "AVI video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "AVI video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
```

I have VLC set up as my default media player, but it just gives me this error.  But when I right-click and say open with VLC, they play fine.  Any ideas?

---

### Post by harold4 on 2008-05-05
> **studentism said:**
> Just out of curiosity, are you running either compiz or beryl?

Either way, try (from the main VLC window)

Settings > Preferences > Video > Output Modules (check the Advanced options in the bottom right hand corner) > Change "Video Output Module: Default" to "Video Output Module: X11 Video Output"

Seem to recall that's what worked for me, let me know your results.

Thank you.  That bar was driving me up a wall.

---

### Post by antofthy on 2008-07-01
> **eeefresh said:**
> This worked for me, too.  Thanks!

Now can anyone tell me why I get this message when I try to open an avi file?
```

The filename "The Italian Job.AVI" indicates that this file is of type "avi document". The contents of the file indicate that the file is of type "AVI video". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "AVI video", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file. 
```


I have been battling this problem for years, on and off. but no one seemed to have an answer.   However I have now finally found the solution in a 'fedora' forum.

The problem is that you personal 'mime' settings do not match the system mime settings.  I have no idea what cases this but it screws up my thumbnails and double-left clicking of AVI documents.  The solution is simple.
```
rm ~/.local/share/mime/globs
```
Now logoff and log back in.  Suddenly AVI's and even AVI thumbnailing is working properly!!!  :D

If this does not work you can also try running
```
update-mime-database /usr/share/mime
```
as the root user.   I myself did not need this.

PS: AVI thumbnailing in Fedora requires the "totem-xine" package from the livna repository.  No idea about this in Ubuntu.

---

### Post by Muffinabus on 2008-07-09
> **harold4 said:**
> Thank you.  That bar was driving me up a wall.

Fixed it for me too (:

Good thread.

---

