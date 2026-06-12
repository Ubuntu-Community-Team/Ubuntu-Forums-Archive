---
title: "Windows &quot;spread&quot; not working"
date: 2013-02-05
forum: General Help
---

### Post by Myoldmopar on 2013-02-05
I am having a small issue and was wondering if someone could confirm before I post a bug.

Generally if you have two or more windows of a single app open, and you click on the app when one already has focus, it will spread each instance over the screen, allowing you to select a single instance.

It seems that anytime I have two windows of an app open, and one of them is marked with "Always on Top", this doesn't work.  It will never spread (I know I've heard spread before but I'm not sure it's the right word for this action.).  

Is it just my configuration somehow?  I noticed it with google-chrome, but then tested it with nautilus and it's the same thing.

Thanks!!

---

### Post by howefield on 2013-02-05
Works fine here, but it would probably help if you indicated which version of Ubuntu you are having a problem with.

---

### Post by Myoldmopar on 2013-02-05
Thanks, Ubuntu 12.10 64-bit.  Plain old Unity.  I am using the x-swat nvidia x driver, though I think that should be irrelevant to Unity.

I confirmed with other applications that once I mark a single window as always-on-top, I can no longer invoke the spread of the windows.  As soon as I uncheck always-on-top, it spreads fine.

---

### Post by howefield on 2013-02-05
Not an issue on 12.10 (64 bit with nvidia) for me.

---

### Post by Myoldmopar on 2013-02-05
Thanks for the replies...I did some more testing.  To isolate issues, I did this demo on a virtual machine with nearly default 12.10 installation.

Steps:
1. Open two nautilus windows.  Mark one as always-on-top.  Click on the nautilus Unity launcher, and it spreads fine.
2. Then I opened firefox.  It opens in front of one nautilus and behind the 'always-on-top' nautilus window.  Once I click on the nautilus launcher again it no longer spreads.  

It seems, for me anyway, on two 'separate' 12.10 installations, that the problem is narrowed down such that if an app has multiple windows, one of which is 'always-on-top', and others are hidden, it won't spread.

Any confirmations?  Thanks again!

---

### Post by howefield on 2013-02-05
> **Myoldmopar said:**
> Then I opened firefox.  It opens in front of one nautilus and behind the 'always-on-top' nautilus window.  Once I click on the nautilus launcher again it no longer spreads.

This behaviour, (which is different to your original post) I can confirm.

Can't explain it though.

---

### Post by Myoldmopar on 2013-02-05
Thanks for the reply.  

I think the behavior which I originally posted (spread is not working when a window is 'always-on-top') is still pretty close to the current understanding, but now complicated because it is only present when a window is in between them on the drawing stack order.

I think I have enough info to build up a reasonable bug report, especially since I can replicate it on a fresh install on a vbox.

If you or any one else has anything related, I'd appreciate the info.  I'll post a link to the launchpad bug here to close up this thread.

---

### Post by Myoldmopar on 2013-02-05
Thanks again, I have opened a bug report on launchpad, so I'll just track everything over there.  For cross-referencing purposes, here is the bug report link:

[https://bugs.launchpad.net/unity/+bug/1116376]("https://bugs.launchpad.net/unity/+bug/1116376")

---

### Post by varunendra on 2013-02-05
> **Myoldmopar said:**
> Steps:
1. Open two nautilus windows.  Mark one as always-on-top.  Click on the nautilus Unity launcher, and it spreads fine.
2. Then I opened firefox.  It opens in front of one nautilus and behind the 'always-on-top' nautilus window.  Once I click on the nautilus launcher again it no longer spreads.
I can confirm this behaviour in a live session of 12.10 32-bit on Virtualbox. I can also confirm that it does not exist on my 12.04 64-bit host.

---

