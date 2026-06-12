---
title: "[SOLVED] Can I execute a sound when I execute my web browser?"
date: 2008-06-19
forum: General Help
---

### Post by MasterJ37 on 2008-06-19
I'm just wondering if it's possible to execute a sound or audio file when I execute my web browser. I opened the icon to Opera on my desktop as a text file in hopes of seeing how it works. I partially understand it. I've seen the line towards the bottom that says: Exec=opera %u
I then created a line bellow that said Exec=firefox %u
When I executed the file both browsers loaded up. I was wondering if I could tell it to execute a sound file at the same time, instead of something like firefox. I have tried adding this: Exec=/home/jimmy/Desktop/get_v.mp3
get_v.mp3 is the file. It didn't play.

---

### Post by Warm.Beer on 2008-06-19
Try installing SoX:
```
sudo apt-get install sox
```

Then you should be able to change your line to:
```
Exec=play /home/jimmy/Desktop/get_v.mp3
```

Cheers

---

### Post by MasterJ37 on 2008-06-20
I guess when I did this:

Exec:Opera u%
Exec:Firefox u%

it opened Firefox (it always opens the second one), and it had a second window tab open on my main panel that said test (name of my desktop configuration file), and it had the Opera sign, so I thought it was opening opera, so I closed the window. I thought it opened both, but I now realize if only opened firefox, and I can't execute two things in the same desktop configuration file. it only executes the second one. Thanks for your help, though. when I had it like this:

Exec:Opera %u
Exec:play /home/jimmy/Desktop/get_v.mp3

it played my mp3, so that was cool. I guess what I was trying to do just isn't possible.

Edit: Smiley face is an accident. it's supposed to be : p, but without the space. when I type : p without the space, it  just happens to look like a smiley face

---

### Post by werries on 2008-06-20
if im right in what you're doing, Exec:, executes a command.
so in order to get this to work it should be something like
```
Exec:Opera %u && play /home/jimmy/Desktop/get_v.mp3
```
Hopefully this works out for you!

---

### Post by MasterJ37 on 2008-06-20
Thanks for trying, but it seems that for every space after the command (&& play /home/jimmy/Desktop/get_v.mp3) followed by text it would open each one up in a different tab as if they were web sites.

---

### Post by Forlong on 2008-06-22
Just write yourself a little script.

E.g.
```
#!/bin/bash

aplay -q /usr/share/sounds/question.wav

firefox
```
works fine here.

If you have any further questions, just ask. :)

---

### Post by MasterJ37 on 2008-06-22
I'm new to programming, and script, it's something I'd like to start learning more about, so all I did is I copied that code into text editor, and saved it. when I executed it, it opened firefox without playing the sound, and the code is what appeared in the window. I put it in the terminal, and it worked, but is there a way for me to execute it from an icon on my desktop?

---

### Post by Forlong on 2008-06-22
Do you get a sound when running this in a terminal:
```
aplay /usr/share/sounds/question.wav
```

---

### Post by MasterJ37 on 2008-06-22
Yes. when I run the whole thing in the terminal, firefox would come up after the sound is played. I'm just wondering if I could do that by running an icon off my desktop, just by clicking it. I don't want to go to the terminal everytime I want to do this. when I saved it in text editor, it saved it as a script file, and when I click it, it runs with firefox. Is there a program I can select to run it that will do the same as me placing the code in the terminal? I chose "Open with Terminal", but that didn't do it. and, when I ran it from terminal, after firefox opens, I closed the terminal. is there a way for me to execute it without the terminal window being open?

---

### Post by Forlong on 2008-06-23
Ah, sorry, I misunderstood you.

OK, all you have to do is drag & drop the Firefox launcher from the Applications menu to the panel.
Then you right-click on it and choose Properties. There you can change the execute command -- just click on the button next to it and choose the script you just saved.

Make sure it's executable, though (you can do that in Nautilus' context menu of the script).

Hope that wasn't too confusing. :)

---

### Post by MasterJ37 on 2008-06-24
Thank You! I almost didn't get it to work, until I re-read the line "Make sure it's executable, though (you can do that in Nautilus' context menu of the script).", It confused me for a sec, then I remembered that when I viewed the properties, I came across: "Allow Executing file as program" underneath permissions. now  it works! only one thing I don't like, is that it executes opera after the sound file is done being played, and I'd like it to execute at the same time. that's bearable though, because I need to edit the sound file to make it shorter.
P.S. sorry if I was being complicated or confusing. I'm usually smarter than this on the computer, I'm just quite new to linux. I've been raised on Windows.

---

### Post by Forlong on 2008-06-24
> **MasterJ37 said:**
> only one thing I don't like, is that it executes opera after the sound file is done being played, and I'd like it to execute at the same time.
Try this:
```
#!/bin/bash

opera &

aplay -q /usr/share/sounds/question.wav
```
The & causes Opera to load in the background, so (a)play doesn't wait until it's fully loaded.

---

### Post by MasterJ37 on 2008-06-24
Perfect! Just what I wanted.

---

