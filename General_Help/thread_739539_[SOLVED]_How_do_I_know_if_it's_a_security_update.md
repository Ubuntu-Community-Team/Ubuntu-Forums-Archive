---
title: "[SOLVED] How do I know if it's a security update?"
date: 2008-03-29
forum: General Help
---

### Post by Levander on 2008-03-29
I installed a new Gutsy system about a week ago.  I want to make sure that security updates are in fact being auto-installed like I selected them to be in "Software Sources"..

Every time I log in, it says there are 124 updates available.  Now, I would assume that this is just the number of non-security updates available since the CD I installed from was pressed.  But, at the top of the Update Manager window, it says, "Important Security Updates", like that's a section header or something.  Then, the 124 available updates are listed.  I don't see anything down in that list that marks updates as in some other "Non-security updates" section.  So, I'm assuming those 124 updates are security updates?

Also, they didn't ever set it up so that you could auto-install all updates, not just security updates did they?

Non-security updates are just like bug fixes?

---

### Post by ibuclaw on 2008-03-29
Packages that come from **[http://security.ubuntu.com](http://security.ubuntu.com)** are generally security updates.

But in most cases, all updates should be considered as security updates.
Since, in a worst case scenario. A known hole or backdoor in a program can cause serious problems if the fix isn't downloaded and/or installed with immediate effect.

Though this is unlikely. It is usually best to keep topped up on everything from the official ubuntu repository, just incase ;)

If you feel any safer doing so.
You can open up Software Sources, and set security updates to download and install automatically.
[[IMG]http://img297.imageshack.us/img297/6983/screenshotsoftwaresourcom7.th.png[/IMG]](http://img297.imageshack.us/my.php?image=screenshotsoftwaresourcom7.png)

Regards
Iain

---

### Post by Bubba64 on 2008-03-29
Did you access software resources through administrative or synaptic. I have noticed that any change requires a reload which synaptic doesn't do automatically. I don't know if this is an answer but the first thing that comes to mind.

---

### Post by Levander on 2008-03-29
tinivole - I'm not sure you completely understood what I'm asking about.  I've already selected security updates to be auto-installed.  

And, I'm pretty sure there are at least some updates that come out that are not considered security updates.  Not that I've gone into Ubuntu internals and checked, just that I've seen chatter around.

Bubba64 - I got into it via the Administrative menu and chose to auto-install security updates via the "Software Sources" dialog.  I'm thinking there are 124 updates available due to that little notification thing in the upper right, and looking at the "Update Manager" dialog that pops up when I click on it.  

I first selected to auto-install security updates a week ago, and my computer has been rebooted a couple of times since then.  So, anything that needed to be reloaded since I selected that option has been reloaded.

---

### Post by ugm6hr on 2008-03-29
Is there a reason you haven't accepted the 124 updates?

The auto-install security updates should work after that.

Definitions of security updates are given in the Software Sources control.

---

### Post by ibuclaw on 2008-03-29
The repositories are updated daily, sometimes once every 12 hours (due to people all over the world maintaining the ubuntu packages.) Security updates come round frequently.

But alas, if it's not downloading them, then the package isn't from the security.ubuntu.com repository.

Here is a quote from my /etc/apt/apt.conf.d/50unattended-upgrades file:
```

// Automaticall upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "Ubuntu hardy-security";
//      "Ubuntu hardy-updates";
};

```
As we see, Only "hardy-security" is the only one that is "not" hashed out.

But that does not mean to say that updates from other repositories aren't "security updates".

Perhaps you're being a bit paranoid with the whole "stable vs bleeding edge" mumbo.

I have kept myself update to date daily on ubuntu ever since I started, even when I switched to alpha1. And I have never experienced any major problems.
Ubuntu is a stable brick. As long as you keep to the official repositories from within Ubuntu, nothing much can go wrong!

---

### Post by Levander on 2008-03-29
ugm6hr - Originally I didn't accept them just because I figured they'd be installed automatically. I haven't accepted them yet now because I wanted to look into it and see what I could figure out.  This is something I've been wondering about for awhile.

tinivole - Yeah, I'm thinking they are just non-security updates, like in the original post.  But, the purpose (and title) of this thread is how to find out if it's a secuirty update?  Maybe that is the usual way, just if it's not auto-installed when you have auto-installed updates turned on, well then it's not a security update?

Maybe that's what the Ubuntu developers had in mind.  But, it sounds a pretty lazy way to implement it that way to me.  Especially since there's an indicator on the Update Manager dialog that makes it look like all the updates that are available to me really are security updates.  This was described in the original post, but you see where it says, "Important security updates" in the sceenshot?  I am using Gutsy, not Hardy like yourself.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=64285&stc=1&d=1206843672[/IMG]

---

### Post by Levander on 2008-03-30
If you guy ahead and install these initial non-security updates, the "Important security updates" message goes away and it becomes "Recommended updates" like it's supposed to be (for non-security updates).  

I uncommented that "hardy-updates" line in /etc/apt/apt.conf.d/50unattended-upgrades that tinivole posted (well, mine read "gutsy-updates", and now non-security updates are being auto installed.  

A way to figure out if an update is a security update or not is to run 'apt-cache policy <package name>'.  E.g.:

```

levander@louis:~$ apt-cache policy cupsys
cupsys:
  Installed: 1.3.2-1ubuntu7
  Candidate: 1.3.2-1ubuntu7.5
  Version table:
     1.3.2-1ubuntu7.5 0
        500 http://us.archive.ubuntu.com gutsy-updates/main Packages
     1.3.2-1ubuntu7.3 0
        500 http://security.ubuntu.com gutsy-security/main Packages
 *** 1.3.2-1ubuntu7 0
        500 http://us.archive.ubuntu.com gutsy/main Packages
        100 /var/lib/dpkg/status

```

Since the ***'d update is not coming from security.ubuntu.com, it's not a security update.

I posted a bug report about the "Important security update" message on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/209169](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/209169)

---

