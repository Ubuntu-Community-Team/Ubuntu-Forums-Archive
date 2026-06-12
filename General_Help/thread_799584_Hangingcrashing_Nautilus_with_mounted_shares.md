---
title: "Hanging/crashing Nautilus with mounted shares"
date: 2008-05-19
forum: General Help
---

### Post by psypher on 2008-05-19
Hey everyone,

I have a pretty seriously annoying issue since upgrading to Hardy. This is a showstopper for me personally and I'm pretty sure it would be for anyone else.

I mount cifs shares with fstab on boot. the shares are hosted on a Ubuntu gutsy samba server which worked perfectly when my desktop was still running gutsy.

Since the upgrade nautilus crashes almost EVERY time when you either view a video or even browse through pictures using gthumb.

what happens is once start the video within a few mins or seconds nautilus will grey out and hang. And when you kill nautilus the whole machine will hang for 2 mins and nautilus will re-launch and open my home folder. then i can continue until I view another movie or picture from the share.

As you can imagine this is just not cool. What is going on? Where should I start looking for clues? Which logs will show me the error output? I have looked everywhere but not sure if the error is with nautilus or samba client or cifs client. I also have a feeling it could be gvfs as I see quite a few bugs and complaints about it and it is the biggest thing that has changed since gutsy 

Has anyone else experienced this issue and know if there is already a bug report for it and possibly a workaround? It seems quite important if this is a general error.

Any help would be much appreaciated.

Thanks

---

### Post by psypher on 2008-05-24
Bump, this is a pretty serious bug and brand new to hardy!!!

Should I log this on launchpad? Has it already been logged, any help PLEASE!

---

### Post by psypher on 2008-05-29
bump!

---

### Post by psypher on 2008-07-08
this is ridiculous, Hardy is TERRIBLE!!??! Constant nautilus crashing, slow USB copying, you drag and drop a file between nautilus windows and the entire desktop crashes, copying files over the net has the "microsoft minutes" effect, thats if nautilus does not crash, everything seems like it's lagging. I'm either going to Opensuse or back to Gutsy. I would NOT call hardy LTS! Dapper was uber stable, this is NOT stable! I'm very dissapointed and would not recommend hardy to anyone trying out ubuntu/linux for the 1st time. Whats going on?? I know I'm not the only one experiencing these issues but no end in sight?

---

### Post by nanog on 2008-07-16
I am having the same problem in 64 bit hardy. I cannot get a stable nautilus mount on a remote server. It is a new bug although gvfs has always been incredibly buggy for me on every box I use or administer.

---

### Post by nanog on 2008-07-17
There is a bug filed now..please subscribe to:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/236050](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/236050)

---

