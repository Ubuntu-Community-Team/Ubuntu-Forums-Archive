---
title: "DVI Monitor help."
date: 2007-02-15
forum: General Help
---

### Post by Roasted on 2007-02-15
I just got a new monitor. ViewSonic 22 inch 5ms flat panel. It's recommended resolution is 1680x1050. In VGA mode, I can get to 1600x1200 (1680x1050 isn't available). But in DVI mode, the highest I can go is 1280x1024.


Why?

---

### Post by Roasted on 2007-02-15
Also, question about text clarity. I was just reading an email which was line after line after line of text, and I realized some lines were slightly blurry while others were completely clear. As I sloooowly scrolled down, I noticed the the lines that were once blurry became more clear, and as I scrolled down more, they'd get blurry, then clear, blurry, clear, etc. It seemed like there were horizontal sections on the monitor where text isn't as sharp. Now this is the first LCD I've ever owned, so I'm unsure of why this would be.

I tried changing the settings on the monitor, and I noticed it even had a "text" setting, but even then it doesn't do anything. Just curious as to why I noticed this.

And if you folks who have LCD monitors could maybe do a little test and see. I only really noticed it on my yahoomail, checking an email.

---

### Post by dcstar on 2007-02-15
> **Roasted said:**
> Also, question about text clarity. I was just reading an email which was line after line after line of text, and I realized some lines were slightly blurry while others were completely clear. As I sloooowly scrolled down, I noticed the the lines that were once blurry became more clear, and as I scrolled down more, they'd get blurry, then clear, blurry, clear, etc. It seemed like there were horizontal sections on the monitor where text isn't as sharp. Now this is the first LCD I've ever owned, so I'm unsure of why this would be.

I tried changing the settings on the monitor, and I noticed it even had a "text" setting, but even then it doesn't do anything. Just curious as to why I noticed this.

And if you folks who have LCD monitors could maybe do a little test and see. I only really noticed it on my yahoomail, checking an email.

You should always run your LCD at its maximum "Native" resolution, and then modify your font sizes (if you have to).

Do not forget to use your monitor's "Auto adjust" feature if you do change resolutions/refresh rates - sometimes a monitor won't automatically do this.

---

### Post by dcstar on 2007-02-15
> **Roasted said:**
> I just got a new monitor. ViewSonic 22 inch 5ms flat panel. It's recommended resolution is 1680x1050. In VGA mode, I can get to 1600x1200 (1680x1050 isn't available). But in DVI mode, the highest I can go is 1280x1024.


Why?

With the new monitor plugged in, in a terminal:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Roasted on 2007-02-15
Okay, question. I ran that command in terminal, but when I eventually come to the screen which asks about the resolutions and whatnot, do I suggest all resolutions I want to include in the list? Or JUST the one I want to run? Cause I selected a few, figuring they'd just be added to the list, and they weren't. :(

edit - Just went through and selected JUST the resolution recommended for this monitor (1680x1050) and it didn't show up in the list then when I went to change my resolution.

---

### Post by Roasted on 2007-02-15
Here, check out this picture.

I hope it turns out the same for you guys as I saw it on my screen, but if you look closely, my profile, my photos, my notes, my events, my mobile, my privacy, are all slightly blurred. If you notice, it's every other line. My friends, my shares, my groups, my messages, and my account are not blurred.

Why?

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-8.png[/IMG]


EDIT - DAMNIT. Once I posted this picture, I scrolled up ONE notch, and I noticed that everything I said was blurry, was indeed clear. I scrolled down one notch, and it was reversed. Dangit.

I know it sounds like I'm being picky, but I'm just urked by this. Maybe I should go to Circuit City and see what it looks like in person on their display model.

---

### Post by dcstar on 2007-02-15
> **Roasted said:**
> Here, check out this picture.

I hope it turns out the same for you guys as I saw it on my screen, but if you look closely, my profile, my photos, my notes, my events, my mobile, my privacy, are all slightly blurred. If you notice, it's every other line. My friends, my shares, my groups, my messages, and my account are not blurred.

Why?

[IMG]http://i2.photobucket.com/albums/y36/Roasted/Screenshot-8.png[/IMG]


EDIT - DAMNIT. Once I posted this picture, I scrolled up ONE notch, and I noticed that everything I said was blurry, was indeed clear. I scrolled down one notch, and it was reversed. Dangit.

I know it sounds like I'm being picky, but I'm just urked by this. Maybe I should go to Circuit City and see what it looks like in person on their display model.

Go into System-Preferences-Fonts, set the DPI to your screen's DPI (check the manual) and then select the LCD Anti-aliasing choice (and go the the next screen to "fine tune" even more).

---

### Post by Roasted on 2007-02-15
I'm not really seeing how the DPI will help. I just changed it to higher and lower and either way I still see the blurry lines. Plus I have no idea what it's SUPPOSED to be set to. But it was set to 96 when I checked it.

---

### Post by Roasted on 2007-02-16
And for the record, I know youtube had crappy quality videos anyway as far as their picture goes, but on this monitor, they don't seem as clear as they were with my 8 year old CRT. Granted this thing has a huuuuuuge screen and it's very nice but I'm just kind of urked that besides those qualities, UNLESS I'm watching something that's high definition, it seems to be crappier. 

BTW - I only have it hooked up with the DVI cable. Maybe I should use the vga one instead?? :confused:

---

### Post by dcstar on 2007-02-16
> **Roasted said:**
> I'm not really seeing how the DPI will help. I just changed it to higher and lower and either way I still see the blurry lines. Plus I have no idea what it's SUPPOSED to be set to. But it was set to 96 when I checked it.

96 is a "guesstimate" value that a lot of monitors used to use, changing it to your monitor's actual setting gives the font rendering a better chance of matching up what it is trying to do with your actual hardware.

---

### Post by Roasted on 2007-02-16
Gah. Turns out it's due to the resolution. Like I said above, I can't get to the recommended resolution for this monitor, which is 1680x1050. I went to windows and set it to that and read the same email that I first noticed the fuzzy text on. Crystal clear. 100% clear. I set it to 1280x1024 and sure enough it had a slight blurr. It's definitely the resolution. Like I said, the blur isn't bad, but my eyes are better than 20/20 and I was sitting insanely close at the time and I was like, uh, what? 

Anyway, new problem. Booting back into linux set my resolution to 1024 768. I can't set it to anything else now that's higher. What in the world happened? Also, it's INSANELY SLOWWWWWWWWWWWWWWWWWWWWWWWW to scroll up/down on web pages. Drives me INSANE!

---

### Post by Roasted on 2007-02-17
Okay. Let me just rephrase the question.

I bought a new monitor.

It's native resolution is 1680x1050.

In Ubuntu Edgy 6.10, 1680x1050 is not a selectable option for me.

How can I make it a selectable option?

Thanks!

---

### Post by Roasted on 2007-02-17
Strange. I rebooted, and they magically popped up. That's weird because I rebooted a few times to get into Windows to play Counterstrike and when I came back in Linux nothing changed.

But I guess I must of done SOMETHING that helped. But anyway, I'm at native resolution of 1680x1050. Great. Looks good.

Question is, what else do I have to set? Wasn't there some veritcal or horizontal axis or something I had to set??



EDIT - In fact, this is bugging me. I don't know what I did to fix this. Now, think about this guys. I get a new 22 inch monitor, and the highest resolution I can set is 1024x768. WHAT could I of done to fix it to make ALL of these other options, including the native resolution of 1680x1050 show up in the list of available options? What could I of done to essentially fix this?

Also - Is it BAD for a monitor if you don't run it at native resolution? Or is it just strongly recommended to get the peak performance out of it?

---

### Post by der_joachim on 2007-02-17
You have omitted one piece of information: what kind of VGA card do you have? I had similar issues with my shiny new 20" Samsung monitor and my MSI Geforce5600, and I found some posts on the net with the same problems. Windows is OK though. I cannot use my DVI either, but that seems to be a video card related problem. My fonts are slightly blurry, as if antialiasing barely keeps up. 

I will be buying a more modern video card soon (I play the occasional game), so I can live with these issues for now.

---

### Post by Roasted on 2007-02-17
I have a GeForce 6600 256mb. The DVI works fine on Windows and Linux. Everything is peechy now. Font is sharp and very clear on both operating systems. No issues. Nadda.

The only gripe I have is I have no idea how I fixed this. Also, my cousin suggested to me I install nvidia-xconfig. I did, but doing do uninstalled nvidia-glx. I just went along with it anyway. But, tell me, what did this change do??


And, second question. This question is to help me figure out what I did wrong.

Before when I got this monitor, I didn't have the native resolution as an option to choose for the new monitor. So I used "sudo dpkg-reconfigure xserver-xorg" and went through some menus to figure it out. Somehow, I guess I got it working.

Question is this. Since nvidia-glx is uninstalled, in the future, can I use "sudo dpkg-reconfigure xserver-xorg" to obtain other resolutions? Or should I use nvidia-xconfig? 

Does my question make sense?

---

### Post by Derspankster on 2007-03-30
I have a 19" Acer LCD and a EVGA Geforce 6200 video card with 256MB of ram. I have NEVER been satisfied with the quality of text using Ubuntu. I have installed the true type fonts and configured them. They are not even close to the clarity under Windows XP. Another interesting note. **I bought a DVI cable for this computer an find that the display is much worse using the DVI than it is using the analog cable. **  I've never seen that with a Windows machine. 

I actually really like Ubuntu but the absolute WORST part of the OS is the way text is rendered. I might add that this is not machine specific, I dual boot my laptop to Ubuntu and text rendering is inferior on that computer as well.

---

### Post by Roasted on 2007-03-30
I really forgot where I left off but, in short, everything is fixed, and this screen is sharp as hell.

I have no problems with seeing text on here at all. This to windows seems fine to me. *shrug* The only text reading problem I have is because of my theme, the colors are a little weird. But on regular theme, it's fine to me. *shrug*

---

