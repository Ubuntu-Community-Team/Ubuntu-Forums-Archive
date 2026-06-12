---
title: "Problems accessing Facebook with friend-app / online accounts"
date: 2015-03-29
forum: General Help
---

### Post by lunalui on 2015-03-29
Hello,
for some reason my friends-app can no longer post to facebook. I've tried removing and adding again my facebook account using online-accounts but the result is that now I don't even see the facebook timeline. Also, each time I have to authenticate my facebook account two windows pop up, one of which --web authentication for facebook-- is totally blank and cannot be closed (see the picture attached). Any ideas where the problem comes from and how it can be fixed? with many thanks in advance for your replies.

PS I'm using ubuntu 14.04 with gnome desktop

---

### Post by lunalui on 2015-03-29
actually it seems to work again now, after the n-th reboot something must have fallen into place. Sorry for the inconvenience...

---

### Post by lunalui on 2015-05-19
Well, the problem's back and this time removing the account, adding it back, and rebooting my laptop hasn't solved the problem. So I'm reopening this thread, hoping that someone has an idea of what's going on and how this can be fixed! Thanks for your replies.

---

### Post by Mr.Dunham on 2015-06-06
> **lunalui said:**
> Hello,
for some reason my friends-app can no longer post to facebook. I've tried removing and adding again my facebook account using online-accounts but the result is that now I don't even see the facebook timeline. Also, each time I have to authenticate my facebook account two windows pop up, one of which --web authentication for facebook-- is totally blank and cannot be closed (see the picture attached). Any ideas where the problem comes from and how it can be fixed? with many thanks in advance for your replies.

PS I'm using ubuntu 14.04 with gnome desktop

Regarding authentication to Facebook, same thing happened to me when I was on Flashback-session (you know, the old Gnome-fallback; although in my case, the pop-up window was *black*, not blank), and I found out that under Unity interface, it works fine. I had to log-out from Flashback, log-in to Unity and authenticate from there and worked fine. Then you log out and log back in to yuor usual desktop and it'll be authenticated, you'll see it under Online Accounts as if everything is OK; at least authentication succeeded.

The other problem still remains: I cannot see the Facebook timeline and I cannot post to Facebook; posts to Twitter work fine and the timeline too. I'll keep googling around.

I'm on 14.04 too and the Trusty version of friends-app shows up as "supported" on Launchpad, although last update was more than a year ago. The Vivid version shows up as "stable" and the Wily version shows as "Active development" and has been updated recently.

I am by no means an expert in Ubuntu, neither a coder nor anything like that, but my quick guess is that I'll see if I can try a Friends-app force-update to the Vivid version. I'm on a hurry right now but I'll come back to this later today.

---

### Post by lunalui on 2015-06-06
Thanks a lot for your reply. In my case, regardless of the pop-up problem, I do authenticate to facebook, but then nothing happens. If you find out a way to force upgrading friends to one of the newer versions, I'd be more than happy if you let me know: a similar trick used to allow me to have sound on a laptop that was too recent for the ubuntu distribution I had at that time, so this may be a winning strategy. Unfortunately I don't have the technical knowledge to understand how this is done myself.
Anyway, thanks again!

---

### Post by Mr.Dunham on 2015-06-13
Sorry, tried everything I know (which isn't much) but it didn't work.

Removed Ubuntu from inside my Facebook settings page (under "Applications"), then removed Facebook from my Online Accounts and completely removed and purged friends-app, to install it again and validate FB account again, but still didn't work.

Force-update doesn't work for me from inside Synaptic, it's grayed out.

Removed and purged again and tried the Vivid version of friends-app from here (it will warn you that you should install the older version but you can ignore it)
[http://packages.ubuntu.com/vivid/i386/friends-app/download](http://packages.ubuntu.com/vivid/i386/friends-app/download)
and it opens, but I don't see anything; the app window remains transparent on my desktop.

So I remove and purge this Vivid version and reinstall the Trusty one, Facebook still doesn't show up... but my Instagram feed does now! which previously didn't :o
Also, posting from Friends-app only works for Twitter, not for Facebook, at least in my case.

I give up. This doesn't work well, the Unity webapps for Facebook and Twitter won't show any notifications on me, Empathy doesn't work anymore on Facebook... so much social integration embedded on the system that doesn't work is useless. The only option I know of is to try separate stand-alone clients for Facebook and Twitter, I'll see which ones I can find.

---

### Post by lunalui on 2015-06-13
Thanks a lot for your message and all your tests. I tried to upgrade to the Vivid version, and get the same problem you have. You're probably right in saying that it's not worth trying any further, even if the situation is pretty irritating: ubuntu never really put much effort into social integration, clearly.
Cheers

---

### Post by lunalui on 2015-06-13
I just wanted to add that I tested Yoono this evening: I encounter the same problems with Facebook, that is, just like friends-app, Yoono is unable to retreive notifications from Facebook and post status updates. I wonder whether the problem is related to some modification in the way Facebook works.

---

### Post by sandyd on 2015-06-13
> **Mr.Dunham said:**
> Sorry, tried everything I know (which isn't much) but it didn't work.

Removed Ubuntu from inside my Facebook settings page (under "Applications"), then removed Facebook from my Online Accounts and completely removed and purged friends-app, to install it again and validate FB account again, but still didn't work.

Force-update doesn't work for me from inside Synaptic, it's grayed out.

Removed and purged again and tried the Vivid version of friends-app from here (it will warn you that you should install the older version but you can ignore it)
[http://packages.ubuntu.com/vivid/i386/friends-app/download](http://packages.ubuntu.com/vivid/i386/friends-app/download)
and it opens, but I don't see anything; the app window remains transparent on my desktop.

So I remove and purge this Vivid version and reinstall the Trusty one, Facebook still doesn't show up... but my Instagram feed does now! which previously didn't :o
Also, posting from Friends-app only works for Twitter, not for Facebook, at least in my case.

I give up. This doesn't work well, the Unity webapps for Facebook and Twitter won't show any notifications on me, Empathy doesn't work anymore on Facebook... so much social integration embedded on the system that doesn't work is useless. The only option I know of is to try separate stand-alone clients for Facebook and Twitter, I'll see which ones I can find.
Side note: Empathy (or other XMPP-based apps that work with facebook) has stopped working due to another (possibly) related [depreciation of the Chat API]("https://developers.facebook.com/docs/chat")

---

### Post by Mr.Dunham on 2015-06-27
> **lunalui said:**
> I just wanted to add that I tested Yoono this evening: I encounter the same problems with Facebook, that is, just like friends-app, Yoono is unable to retreive notifications from Facebook and post status updates. I wonder whether the problem is related to some modification in the way Facebook works.
I found out about Yoono yesterday, and I came here to let you know, I see you've already tested it. The Facebook issue (basically, not working anymore with *anything* it used to work) is mostly sure because of what **sandyd** posted, which I quote below.


> **sandyd said:**
> Side note: Empathy (or other XMPP-based apps that work with facebook) has stopped working due to another (possibly) related [depreciation of the Chat API]("https://developers.facebook.com/docs/chat")
Thank you for letting us know. It is appreciated.

---

### Post by lunalui on 2015-06-28
Yep, I that's right. I think the status of the thread should be marked as unsolvable :( It's not the first time something like this happens either. I think the previous time this happened (with gwibber), they managed to find a way to bypass the constraints imposed by facebook, but this time it looks hopeless...

---

