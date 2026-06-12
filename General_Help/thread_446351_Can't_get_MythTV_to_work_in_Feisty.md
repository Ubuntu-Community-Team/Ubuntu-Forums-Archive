---
title: "Can't get MythTV to work in Feisty"
date: 2007-05-16
forum: General Help
---

### Post by 64mgb on 2007-05-16
My MythTV box got messed up so I finally decided to rebuild it.  So I did a fresh install of Feisty, then installed MythTV.  Now, when I try to watch live TV, it just goes blank for about 30 seconds, then comes back to the MythTV menu.  If I start it from a terminal, this is the message I get:

2007-05-16 20:23:16.215 New DB connection, total: 2
2007-05-16 20:23:16.216 Connected to database 'mythconverg' at host: 192.168.1.199
2007-05-16 20:23:16.245 Connecting to backend server: 192.168.1.199:6543 (try 1 of 5)
2007-05-16 20:23:16.246 Using protocol version 31
2007-05-16 20:23:16.289 TV: Attempting to change from None to WatchingLiveTV
2007-05-16 20:23:16.289 Using protocol version 31
2007-05-16 20:23:16.550 DPMS Deactivated 
2007-05-16 20:23:56.542 TV Error: StartRecorder() -- timed out waiting for recorder to start
2007-05-16 20:23:56.542 TV Error: LiveTV not successfully started
2007-05-16 20:23:56.555 TV: Deleting TV Chain in destructor
2007-05-16 20:23:56.557 DPMS Reactivated.

I can do this:

cat /dev/video0 > test.mpg

and it will capture video that I can watch with VLC.  My dmesg output for ivtv looks normal (I think). 

Any ideas what is wrong?  It does the same thing when running mythfrontend from a different computer.

Thanks,
Rich

---

### Post by newlinux on 2007-05-16
I need a bit more information to see if I can help you. What type of tv Tuner are you using (brand, model). How did you set it up in mythtv (DVB, V4L, MPEG-2 hardware encoder, etc.).  Is it a hauppage of some type (PVR-150, 250, etc.)?

Any clues in your backend log? (/var/log/mythtv/mythbackend.log)

---

### Post by 64mgb on 2007-05-16
> **newlinux said:**
> I need a bit more information to see if I can help you. What type of tv Tuner are you using (brand, model). How did you set it up in mythtv (DVB, V4L, MPEG-2 hardware encoder, etc.).  Is it a hauppage of some type (PVR-150, 250, etc.)?

Any clues in your backend log? (/var/log/mythtv/mythbackend.log)

Man...what an idiot I am!  Your questions triggered the answer.  It's a Hauppauge PVR-150 and I had it set up as a V4L Analog card, rather than as an MPEG-2 hardware encoder.  DOH!

Sorry to waste your time, but I appreciate your help!

Thanks,
Rich

---

### Post by newlinux on 2007-05-16
I've done that before. No worries. It was actually my first guess, but I didnt't want to assume. :)

---

