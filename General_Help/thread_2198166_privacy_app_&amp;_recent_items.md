---
title: "privacy app &amp; recent items"
date: 2014-01-07
forum: General Help
---

### Post by choochoousmc on 2014-01-07
I want to completely disable the recent items tracking.
When I click on my Hard drive icon, at top is home and RECENT (among others).
I have told privacy, not to record anything.
And I have told it to delete history.
So why is the history not being deleted?
Why is my recent activity still being recorded?
How can we force Ubuntu NOT to record any activity?

---

### Post by choochoousmc on 2014-01-08
Well I guess either nobody has an answer, or if they do don't want to provide it,
or there is no way and even then nobody wants to say so.
So much for help at this site.
But that is something Ubuntu needs to include. A way to stop all recent activity tracking.
I have installed two different privacy apps that claim to disable the recent tracking.
They DON"T and they need to be removed from the software center.

---

### Post by steeldriver on 2014-01-08
What version of Ubuntu are you running? For 13.10 I was able to remove the 'Recent' item from the nautilus file manager using command line

```
gsettings set org.gnome.desktop.privacy remember-recent-files false
```

---

### Post by 3rdalbum on 2014-01-08
Please be aware that we are volunteers and the answer might lie with somebody who wont be on again for hours or days. Bumping your thread after a day is fine, just please don't complain about the free support.

The Privacy panel controls the Unity dash and the Zeitgeist service, which are the more complained-about and misunderstood services. It doesn't control the file manager's own little list, which very few people complain about.

I believe Dconf Editor exposes the file manager (Nautilus)'s option for how many recent items to remember. If you can find this key in Dconf Editor and set it to zero, you disable the Recent Items.

I've not done this because I don't think anyone has ever asked me how to stop the Recent Items before. I don't see how much risk it can pose to the ordinary user, but if I haven't given you the solution I hope I've at least pointed you to the right area.

You can't stop all logging entirely. Not in any operating system. Like any bureacracy, an operating system needs to keep records in order to run at all. If you are worried about this, you could use whole-disk encryption to prevent anyone being able to access logs when your system has been shut down.

---

### Post by choochoousmc on 2014-01-09
> **steeldriver said:**
> What version of Ubuntu are you running? For 13.10 I was able to remove the 'Recent' item from the nautilus file manager using command line

```
gsettings set org.gnome.desktop.privacy remember-recent-files false
```

---------------------

------------------------------------------------------]
Thanks for the suggestion. I will give it a try.
I'm still running 13.04. I'm very cautious about up grading. I don't just jump on the upgrade when it comes out.
I wait 4 or 5 months to see what problems others have had.
With all the NSA spying and such, With Linux supposedly being more secure etc.
Ubuntu really needs to be easily modified to turn off all tracking and recent files.
Yes I know caching them helps for quicker finds next time. But I don't need that benefit.
I rather my computer NOT track every thing I do.

---

### Post by choochoousmc on 2014-01-09
> **3rdalbum said:**
> Please be aware that we are volunteers and the answer might lie with somebody who wont be on again for hours or days. Bumping your thread after a day is fine, just please don't complain about the free support.

The Privacy panel controls the Unity dash and the Zeitgeist service, which are the more complained-about and misunderstood services. It doesn't control the file manager's own little list, which very few people complain about.

I believe Dconf Editor exposes the file manager (Nautilus)'s option for how many recent items to remember. If you can find this key in Dconf Editor and set it to zero, you disable the Recent Items.

I've not done this because I don't think anyone has ever asked me how to stop the Recent Items before. I don't see how much risk it can pose to the ordinary user, but if I haven't given you the solution I hope I've at least pointed you to the right area.

You can't stop all logging entirely. Not in any operating system. Like any bureacracy, an operating system needs to keep records in order to run at all. If you are worried about this, you could use whole-disk encryption to prevent anyone being able to access logs when your system has been shut down.
---
I understand what you are saying about volunteers and such. but it is aggravating after a couple days and absolutely no response, but yet over a 100 views.
But then when you take a somewhat negative approach you get some kind of an answer quickly. Go figure.
Don't need whole disk encryption. I could do it with truecrypt and such.
But every time I open a file (picture, text, data, etc) it is right there for anybody to see in the recent used folder.
I don't need it or want it. It even pops up in the dash, when I open it.  So if anybody did access my system (even remotely) the data could or would be exposed.
What gets me is the privacy app says it deletes recent files. either there are two or more recent files areas or it isn't wiping. So that is confusing when you have record set to off and you deleted history, but yet click recent lists and there they are.
Anyway thanks for your suggestion. I will see if I can find the key you mentioned.

---

