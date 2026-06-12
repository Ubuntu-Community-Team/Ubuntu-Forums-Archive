---
title: "Video player problem"
date: 2014-02-22
forum: General Help
---

### Post by dwjeanes2 on 2014-02-22
Hi folks. I need some help. When I play a video, after a few minutes the video gets choppy and eventually just stops. I have tried closing all other programs, and the problem still occurs with only the video player active. I began experiencing this after the upgrade to 13.10 ver.

What I have done:

because I had browser and irc both open while playing the vids, I first archived all irc logs and cleared cache and cookies in the browser.

Then, I tried without irc.

Then, i tried without browser or irc.

Even after a fresh boot, with no other programs having been started, the video player still fails after 5-15 minutes of video.

Can someone suggest an approach to fixing this issue?

Thanks in advance!

---

### Post by Yellow Pasque on 2014-02-22
Have you checked free command to make sure it's not a memory leak?
```
free -m
```

What GPU and driver are you using?

Have you tried making a log with vlc or starting whatever video player you're using in the terminal?

---

### Post by dwjeanes2 on 2014-02-22
I tried to start konsole to check free memory... not found,sigh.

I am using a dell latitude d620 with standard hardware (it's a laptop)

I don't know how to use vlc (don't even know what it is)

and, no, I haven't tried to start a default video player in a terminal, because I can't get konsole to run.

---

### Post by andrew.46 on 2014-02-22
> **dwjeanes2 said:**
> I don't know how to use vlc (don't even know what it is)

vlc is a reasonably self-contained media player that would be a great starting point to diagnosing what sort of problem you have. You can install it from the Software Centre or from Synaptic (if you have Synaptic installed). If you can find a terminal window (you will definitely have at least one terminal emulator installed) you can install it with:

```

sudo apt-get install vlc

```

and then try your videos again...

---

### Post by dwjeanes2 on 2014-02-22
ok, installed VLC and all seems good. 

played a video with no problems so far. 

I'll update this if anything goes sour.

Thanks!

---

