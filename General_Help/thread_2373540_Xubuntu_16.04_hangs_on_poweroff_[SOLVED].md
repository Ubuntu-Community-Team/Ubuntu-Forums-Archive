---
title: "Xubuntu 16.04 hangs on poweroff [SOLVED]"
date: 2017-10-07
forum: General Help
---

### Post by shersk on 2017-10-07
I have a fully up to date Xubuntu 16.04 which hangs on poweroff, after killing all the processes. The last message was about stopping KVM virtualization. After I saw that I turned off virtualization in the BIOS, booted, and then rmmod'ed the kvm module. But this did not solve the problem. It still hung at poweroff, only without the KVM related message. The last message says that now it's powering off the computer. 

How can I diagnose and solve this problem?

EDIT: A probable culprit is that I disabled nouveau driver and installed the proprietary NVIDIA graphics driver recently but reverted to nouveau. There might have been an update of either nouveau or nvidia, I don't know. Could it somehow be related to the 'hanging on shutdown' problem?

Another possible culprit is the BIOS driver, I would assume. But I would really like to approach this 'by the book', so what's the right way to diagnose the problem?

---

### Post by mc4man on 2017-10-07
> **shersk said:**
> 

EDIT: Sorry, but the headline is wrong. It's Xubuntu 16.04. I wanted to delete this message and post a new one with correct headline, but how can I delete it? Again: This is about Xubuntu 16.04!


Edit your 1st. post using the Go Advanced option. Then change the Title: to whatever you want

---

### Post by shersk on 2017-10-07
Thank you. 

Do you have any idea how to diagnose the poweroff problem? If you do a search on ubuntuforums, you will see that there have been a lot of reports of problems with the shutdown / poweroff hook in Ubuntu and hardly anyone has any clear sense of how to fix it, also going back to previous releases. Seems like a pretty important thing to fix in Ubuntu.

---

### Post by mörgæs on 2017-10-09
> **shersk said:**
> ...also going back to previous releases.

Maybe better to test if the problem is fixed in one of the new releases.

---

### Post by shersk on 2017-10-09
Yes, what it shows is that the same kind of problem was ignored in the past, so it's about time to address this issue in 16.04.

---

### Post by mörgæs on 2017-10-09
Don't expect non-security bug fixes to appear in 16.04. Bug fixing and other kinds of development takes place in the development release, hence the name. A non-security bug fix might in rare instances be backported to old releases but the main rule is that old software is left as it is.

The problem could be fixed in 16.10, 17.04 or 17.10 without you knowing it. Testing 17.10 is worth the while.

---

### Post by shersk on 2017-10-10
I had some problems in the past upgrading so I try to stick to the LTS versions, but your message made me want to try upgrading. 

Update as to my problem: I believe it is related to an HDMI screen I have been using lately, as the computer was able to shutdown normally when I disconnected the HDMI cable.

UPDATE: I upgraded to 17.04, and now it works. Thank you for the spot-on comment!

UPDATE2: By the way, 17.10? It hasn't been released yet, has it? How do I test it?

UPDATE3: I found it. [Announcement]("https://wiki.ubuntu.com/ArtfulAardvark/Beta1/ReleaseAnnouncement") and specifically for Xubuntu, the [Beta-2 image]("http://cdimage.ubuntu.com/xubuntu/releases/artful/beta-2/").

---

### Post by mörgæs on 2017-10-11
Good that you got it working. Now your turn to show people the potential in the short term releases :-)

I don't upgrade, always a fresh install. 

Please use Thread Tools for marking the thread solved.

---

### Post by shersk on 2017-10-11
> **mörgæs said:**
> [COLOR=#000000]I don't upgrade, always a fresh install. [/COLOR]

If you are absolutely certain that other directory trees than home don't contain anything that you need, you can do that. In my experience, most users don't have such good habits (myself included).

> **mörgæs said:**
> please use thread tools for marking the thread solved.

ok.

---

