---
title: "Does Flash Player Use GStreamer?"
date: 2013-05-18
forum: General Help
---

### Post by Iggy64 on 2013-05-18
Although Pandora (internet radio) switched their web page to HTML5 a couple of years ago, the actual audio is reportedly still played through Adobe Flash Player.  Typically, the player is provided as a plugin in your web browser.  If I understand it correctly, Pandora downloads a temp file to your disk, then plays it using Flash.

As I am still relatively new to Linux, I am trying to figure out how Adobe Flash outputs the music to ALSA.  Specifically, I wonder if it is routed through GStreamer, or if it can be configured to run through GStreamer.  I'd like to know this because, if it can go through GStreamer, I could use GStreamer plugins (such as an equalizer) to tailor the sound.

If the answer is not obvious, is there a way I can monitor what processes are running, and would that show me whether GStreamer is doing something?  (In my old Windows days, I would use Process Explorer.)

Many thanks for any insights.

---

### Post by Hekabe on 2013-05-18
you could try to use lsof to find out what processes are using your sound card. It'd be something like this:
```
lsof /dev/dsp
```

---

### Post by Iggy64 on 2013-05-19
Thanks for the idea regarding the lsof command.  

I opened Firefox and cued Pandora.

Then 

> lsof | grep flash

quickly showed that the flash plugin was open.

Then 

> lsof | grep gst

showed that no GStreamer plugins were open.

So Pandora is running through Adobe Flash, but not through GStreamer.  Therefore, looks like no way to sneak an equalizer in.

By the way, just to be sure, I closed Firefox and opened Clementine.

Now, I could see no Flash plugin open, but I could see lots of GStreamer plugins.  So, as advertised, Clementine is playing through GStreamer.

Thanks for your helpful suggestion.

---

### Post by Frogs Hair on 2013-05-19
I have been using Pithos, which is a free Pandora client in the software center since last December . The program doesn't allow like or dislike, but I have three different stations and a quick mix station which combines them. There is no advertising with continuous play. If you are not interested in the social aspects of Pandora it is a nice application.

---

### Post by Iggy64 on 2013-06-15
Thanks for the Pithos idea, Frogs Hair.  (Sorry about not responding sooner.  I got tied up in some other issues and neglected to track this post.)

Actually, I have been considering trying Pithos, after taking a VERY brief look at Pianobar.  As soon as I get past a couple of other Linux learning issues (mainly, how to quit screwing up permissions), I hope to come back to this and try Pithos.

Thanks very much for the reminder.  I'm going to give it a shot.  My Pandora stations are all very well tuned in, so no big need for thumbs up and thumbs down.

---

### Post by HiImTye on 2013-06-15
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
flash uses ALSA directly, but you can make your .asoundrc redirect it to pulse if you like

---

