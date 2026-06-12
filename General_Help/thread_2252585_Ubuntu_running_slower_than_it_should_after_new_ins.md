---
title: "Ubuntu running slower than it should after new install."
date: 2014-11-12
forum: General Help
---

### Post by Wil_Brown on 2014-11-12
Hello all, I am a new Ubuntu user that used to run Windows 8. I recently decided that I wanted to get away from windows and began looking into a linux-based OS. After doing a fair amount of research, I decided that Ubuntu would be the best fit for me. One of the main reasons I chose Ubuntu was that everything that I read and saw in videos mentioned that it would almost always make your machine run better. This has not been the case for me. I notice my boot time is significantly longer than it was with windows and programs take longer to open than they should. opening multiple programs makes this even worse. I love everything else about the OS. I have a decent laptop. It's an ASUS with an i5 and 8GB of RAM. Everything I have read makes me believe my computer should have no problem with Ubuntu. Please keep suggestions to a elementary level; I am very new to this. Thanks in advance!

---

### Post by QIII on 2014-11-13
Hello!

A subjective feeling that something is slow is not as good as an objective measure.  Can you give us some sense of the actual measured time it takes things to open so that we can compare that with our experiences?

With regard to startup, that is an unabashed "magic trick".  A Windows 8 machine never really shuts down.  The "Fast Start" thing is a gimmick to make you think things are speedy.  The mobo manufacturers have agreed to Microsoft's Fast Start slight of hand, which really just hibernates Windows and then skips a lot of the POST processes on waking.  It appears that Windows is starting quickly, but it is just really waking from hibernation.  A great little bit of smoke and mirrors -- and, to be honest a pretty neat idea.

---

### Post by Bucky Ball on 2014-11-13
Welcome. Yes, those specs are more than adequate. Is there something running in the background that is launched at boot? I'm using xfce4 rather than Unity, so for me Settings>Session and Startup. Session and Startup is what you're looking for. Then the 'Applications Autostart' tab. Switch off what you don't need. There could be a bunch of stuff autostarting there.

Ninja-ed by QIII: and as they say, Windows 8 hibernates, it doesn't shut down so it launches virtually immediately when you open the lid (or hit the power button).

---

### Post by mastablasta on 2014-11-13
to get some better measurements on full boot up you can to use boot chart or similar boot measuring time tool.

---

### Post by buzzingrobot on 2014-11-13
You can get much the same effect of Win8's "Fast Start" by suspending your machine, rather than shutting it down.

---

### Post by HermanAB on 2014-11-13
Howdy,

Run 'top' or 'htop' and 'ntop' to see what is going on, then stop the processes that are not needed.

---

### Post by Bucky Ball on 2014-11-13
> **buzzingrobot said:**
> You can get much the same effect of Win8's "Fast Start" by suspending your machine, rather than shutting it down.

This is true. I virtually never switch my laptop off (probably once a week, if that), just close lid. ;)

---

### Post by Wil_Brown on 2014-11-13
Wow, thanks for all the responses. I can almost deal with the slower boot times since I was aware of the quick start thing was just a windows trick. However, it's the actual functionality of the laptop when I'm using it that bothers me most. Sometimes it takes 15-20 seconds to open a program. It gets worse when I am running multiple programs at once and that's something I've not seen anyone complain about while using Ubuntu. Everything I have seen mentions how well the OS does when you are using multiple programs. Thanks again for all the reponses.

---

### Post by QIII on 2014-11-14
Something odd is going on if things take that long.

Please run 

```
top
``` from the terminal or install htop and run

```
htop
```

Get it running for a bit, then press Ctrl + C to stop the updates.

Highlight the text and press Ctrl + Shift + C to copy it.

Then post back the results here so we can take a look.

Remember to put the output between code tags.

To use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

