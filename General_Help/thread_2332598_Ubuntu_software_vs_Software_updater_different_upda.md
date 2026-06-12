---
title: "Ubuntu software vs Software updater different updates"
date: 2016-08-02
forum: General Help
---

### Post by iqdesigner on 2016-08-02
Hi,

I use Ubuntu 16.04 LTS. I get a pink popup that important updates are available but clicking it nothing happens.
For some time Software Updater provide to me a list of updates and I install them successfully (I always run Software Updater manually)
During last days Software Updater it says me that no updates are available. However if I open Ubuntu Software I get two updates in the Updates tab.

Why the one shows me updates and the other not? What is the difference? Is the Software Updater broken?

Thanks

---

### Post by deadflowr on 2016-08-02
Software Updater /update-manager i has a built-in function called [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").
Ubuntu software's update system does not.

This, of course also leads to a small annoyance, as the Ubuntu Software program has a notification setting that Ubuntu has decided to have launch at start-up.
So when you run the software updater, randomly if any updates are available, the notify-bubble in the top right corner of the screen will tell you, even if the software updater you just ran shows no updates.
A quick tip for this, if you prefer to just use the software updater for updates, is to open the program Startup Applications and uncheck the gnome software entry.
That'll stop those particular notifications. 
For what it's worth

---

### Post by howefield on 2016-08-02
> **deadflowr said:**
> ..A quick tip for this, if you prefer to just use the software updater for updates, is to open the program Startup Applications and uncheck the gnome software entry.

Thanks for that deadflowr, never noticed that sneaking into Startup Applications :)

---

### Post by deadflowr on 2016-08-02
> **howefield said:**
> Thanks for that deadflowr, never noticed that sneaking into Startup Applications :)

Yeah, if you run development versions of Ubuntu you might never notice the difference since dev releases should have the phased updates turned off.
So in those cases all updates should match.

But for regular stable releases it is a bit disconcerting to see a notice about updates available only to run the updater and see no updates.

And personally, I don't need any notifications for updates as I always run updates as soon as I login.
And machines that are always on have [unattended-upgrades]("https://help.ubuntu.com/community/AutomaticSecurityUpdates") configured.

And also, a big +1 to users to sign-up to the [Ubuntu Security Notices]("http://www.ubuntu.com/usn/") announcement mailing list or rss or atom feeds, for what it's worth.
(Slightly off-topic, but totally worth it, imo)

---

### Post by iqdesigner on 2016-08-02
> **deadflowr said:**
> Software Updater /update-manager i has a built-in function called [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").
Ubuntu software's update system does not.

This, of course also leads to a small annoyance, as the Ubuntu Software program has a notification setting that Ubuntu has decided to have launch at start-up.
So when you run the software updater, randomly if any updates are available, the notify-bubble in the top right corner of the screen will tell you, even if the software updater you just ran shows no updates.
A quick tip for this, if you prefer to just use the software updater for updates, is to open the program Startup Applications and uncheck the gnome software entry.
That'll stop those particular notifications. 
For what it's worth


Hi deadflowr,

So from what I understand installing the two updates I get from Ubuntu Software is not a good practice, as they might have problems as they are not take part on Phased-Updates (might introduce failures in existing apps). So propably Ubuntu is wrong to provide such updates from a main tool. Also if everything goes right, the updates from Ubuntu Software will pass to Update Manager so I expect to see the same updates already have in Ubuntu Software in Update Manager sooner or later. However, It is 5 days now I do net get updates from Update Manager.

Thanks

---

