---
title: "Terminal beep to WAV file?"
date: 2006-11-15
forum: General Help
---

### Post by Peepsalot on 2006-11-15
I find the terminal beep from the PC speaker to be incredibly annoying.  The beep is oten too loud(no volume control is available that I know of), and I feel the beep itself is just a harsh sound.  I know there are ways to disable it completely, but I think it does serve some purpose and would be good to keep around in one form or another.

So I think the ideal solution would be if it could play a sound through a *real* sound card.  We are living in the 21st century, and IMO PC speakers are unecessary legacy hardware at this point.  Every time I hear it I feel like I'm back in the 80's.  There must be some way that beeps can be sent to a process that just plays a wav or mp3 instead of this cheapo system beep.

Personally I think a sort of soft swish sound would do the job much better than a harsh beep, but of course if something like this is possible, people could use whatever sound they feel.

If there is absolutely no way this is possible, then perhaps someone can explain how to configure the visible bell, becuase I can't get that working either.

---

### Post by organica on 2006-11-15
Its in your Sound Preferences under the System Beep tab.

---

### Post by sam81 on 2006-11-16
absolutely agree with your point, the beep is nasty, and better system sounds should be configured by the default installation

---

### Post by Peepsalot on 2006-11-16
> **organica said:**
> Its in your Sound Preferences under the System Beep tab.
You mean just for configuring a visual bell?

I don't see anything there about using WAVs

---

### Post by organica on 2006-11-21
There's a deb package that unlocks the "Hidden Preferences" in GNOME.  [http://hideseek.sourceforge.net/]("http://hideseek.sourceforge.net/")

You can have WAV files associated with the terminal beep.  The option is there but I haven't tried it.

---

### Post by ciscosurfer on 2006-11-21
There aren't any .deb packages there, only source.

Can someone build a deb and upload it here?

I can't get the source to build correctly.

---

### Post by mannheim on 2006-11-21
I haven't tried this, but you could try:

Open gconf-editor, and navigate to

/desktop/gnome/peripherals/keyboard

Then under "bell_custom_file", try entering the name of .wav file.

---

### Post by organica on 2006-11-21
> **ciscosurfer said:**
> There aren't any .deb packages there, only source.

Can someone build a deb and upload it here?

I can't get the source to build correctly.

The deb package is here:

[http://www.getdeb.net/]("http://www.getdeb.net/")

It's on the homepage.

---

### Post by Peepsalot on 2006-11-21
> **mannheim said:**
> I haven't tried this, but you could try:

Open gconf-editor, and navigate to

/desktop/gnome/peripherals/keyboard

Then under "bell_custom_file", try entering the name of .wav file.
It looks like you also need to set bell_mode to custom, according to the documentation.

However, I am trying this method, and it doesn't seem to be working.

---

### Post by Peepsalot on 2006-11-21
> **organica said:**
> The deb package is here:

[http://www.getdeb.net/]("http://www.getdeb.net/")

It's on the homepage.
Hmm, I also just tried installing this deb, and I can see the settings that I already changed in gconf-editor, but still can't get it to work.  I wonder if the file has to be a specific format, or rate, etc.

---

### Post by ciscosurfer on 2006-11-21
> **organica said:**
> The deb package is here:

[http://www.getdeb.net/](http://www.getdeb.net/)

It's on the homepage.Cool site.  Didn't know it existed!  Looks like they have some cool apps.

---

### Post by organica on 2006-11-21
Yeah, got some godd stuff off it.  Hope they build up more debs.

---

### Post by basic0 on 2008-05-05
> **Peepsalot said:**
> Hmm, I also just tried installing this deb, and I can see the settings that I already changed in gconf-editor, but still can't get it to work.  I wonder if the file has to be a specific format, or rate, etc.

I can't get this to work either. I have bell_mode set to "custom" and bell_custom_file set to "/home/matt/converts.wav" (Luke Skywalker: "But I wanted to go to Tashi Station to pick up some power converters!") but it doesn't do anything. Now I have no system bell at all. Are we doing something wrong, or is it broken?

---

