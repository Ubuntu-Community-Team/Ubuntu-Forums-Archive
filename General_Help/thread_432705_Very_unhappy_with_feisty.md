---
title: "Very unhappy with feisty"
date: 2007-05-04
forum: General Help
---

### Post by mainalisuyog on 2007-05-04
Well, i've been using ubuntu since 2004, and have been quite content with this wonderful OS. However, Feisty has greatly disappointed me. I'm almost on the verge of switching the distro, but i'm trying to hang on hoping things will get better with bugfixes and updates. Here is a list of few things that make Fiesty an unpleasant experience for me:

- When I try to run some wmv, ogg and avi files, the system freezes leaving me with no option but a hard reboot. Why can't it just crash totem and leave the system alone instead of freezing the whole GUI? No mouse, no keyboard, nothing! No way out but reboot. And I thought linux was stable!

- when i put in a cd, everything's fine. an icon gets placed on desktop and it mounts properly. But when i puit in a DVD, it doesn't automount. Totem, vlc etc can all see the disk and play the movie, but there is no icon on desktop, no icon inside "computer", and /media/cdrom is empty. I've read through the forums and it has gone unanswered.

- when i unmount a removable usb drive, it gives an error "can not eject media" or something like that.

- I plug in my nokia mobile and it mounts fine. i can browse the file and all, but when i try to copy the files to/from the mobile, it just hangs. So far, haven't found a solution in the forums. All i can do is to run windows in vmware and transfer files through windows.

- and yes, my biggest grievance is that i can never seem to find answers to my problems in the forums. everybody suggests something and in the end, the problem remains the same and the problem remains unsolved, and i mess up my system trying out different solutions. 

Please forgive my bitterness, but i've been telling all my friends what a great OS ubuntu is, and Feisty is ruining it for me. Hours and hours of reading and research to make simple things work, i'm disappointed. :-(

---

### Post by yopnono on 2007-05-04
Did you do an upgrade or did you do an clean install.
Try clena install if you upgraded, also try to create a new user profile and login to that and try.

---

### Post by 50words on 2007-05-04
I share your frustration with the support, but remember, this is free software, as is the support, such as it is. It seems like most threads with "real" questions just sink down without an answer. The easy answers get addressed quickly.

That's a little frustrating, since I always search before posting, and am almost never rewarded with any constructive help. At the same time, I try to remember that if I really want support, I can always pay for it.

---

### Post by m.musashi on 2007-05-04
Feisty for me is clearly the best one yet. I have next to zero problems. I did do, and always do, a clean install rather than an upgrde. It's fast and I have a clean system again. I keep /home on it's own partiton so other than some apps I need to apt-get, eveything is as it was - just new and better.

That said, if you are having issues then we need to solve them. Unfortunately I have not seen or experienced anything like what you are. If you did an upgrade, you might want to consider a fresh install. If you already did that, I would suggest picking the one problem that you are most anxious to fix and post a thread about it. It does sound like some of your issues may be related so fixing one thing might fix others.

Given your comment about having tried lots of things and only messing it up more, I would highly encourage a fresh nstall. Unlike windows, reinstalling Ubuntu is a painless 20 minute process (at least for many people).

---

### Post by BobLand on 2007-05-04
I had similar problems.  On the "How To..." I found this code and ran it.  It allowed me to run all of my windows video files, those being wmv and avi.

sudo aptitude install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs

Hope this helps,
bobland

---

### Post by pebo on 2007-05-04
Ref ejecting USB disk: [this]("http://ubuntuforums.org/showthread.php?t=418688") thread sorted it out for me

---

### Post by m.musashi on 2007-05-04
Well, if it's just an issue with codecs and such, check out [medibuntu](http://medibuntu.sos-sts.com/repository.php)

---

### Post by Turellius on 2007-05-04
> - when i unmount a removable usb drive, it gives an error "can not eject media" or something like that.
This can be solved by```
 sudo umount */path/device*
```
If you need more help here's a related [thread]("http://ubuntuforums.org/showthread.php?t=401591")

---

### Post by poppers1957 on 2007-05-07
> **m.musashi said:**
> 

That said, if you are having issues then we need to solve them. Unfortunately I have not seen or experienced anything like what you are. If you did an upgrade, you might want to consider a fresh install. If you already did that, I would suggest picking the one problem that you are most anxious to fix and post a thread about it. .

How do I post?  I am very new here and can't find where to post new.  Looked in FAQ and other places, but no help.  PLEASE HELP ME.:confused:

---

### Post by rich.bradshaw on 2007-05-07
> **poppers1957 said:**
> How do I post?  I am very new here and can't find where to post new.  Looked in FAQ and other places, but no help.  PLEASE HELP ME.:confused:

LOL!

It's at top of forum list, not in threads, but in the main list on the left...

---

### Post by orb9220 on 2007-05-07
> Well, i've been using ubuntu since 2004, and have been quite content with this wonderful OS. However, Feisty has greatly disappointed me. I'm almost on the verge of switching the distro,

Well 3 years of Bliss for free and Feisty just released and I have not given them time to fix the bugs . So I'll just dump them.

Does not matter that during that whole time from 2004 I have a total of 42 posts and I have given next to nothing in return in helping new user's make the transition.

> - and yes, my biggest grievance is that i can never seem to find answers to my problems in the forums. everybody suggests something and in the end, the problem remains the same and the problem remains unsolved

I would think after 3 years with linux you would have taught yourself how to fix most things yourself.

> Please forgive my bitterness, but i've been telling all my friends what a great OS ubuntu is, and Feisty is ruining it for me.

Again how easily you forget all the great times with other releases of ubuntu to let it be overshadowed by a new release that hasn't even been out a month yet.

> Hours and hours of reading and research to make simple things work, i'm disappointed.


And if you would have spent some little time of those 2-3 years learning the OS you would not have been spending hours and hours.

I am sorry but I think your Perception of each and every release must BE! closer to perfection and bug free as a bit naive.

And I hold some bitterness toward your ungrateful attitude towards the hard work of Developers,and Users.and forum members that make it a wonderful OS. Yes wonderful does not mean bug-free for everyone. 

And yes there is still much to be done but come on are you saying that you are now so quick to dump ubuntu because of Feisty not working for you.

You still have edgy,dapper to fall back to and why not have a little patience and wait for feisty to fix things.

---

