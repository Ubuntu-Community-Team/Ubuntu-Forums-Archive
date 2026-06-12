---
title: "Is there a program like &quot;Shortkeys Lite&quot; for Linux?"
date: 2006-09-02
forum: General Help
---

### Post by solarwind on 2006-09-02
Hi everyone,

Is there a program like "Shortkeys Lite" for Linux?

Thanks in advance!

---

### Post by Ramaddan on 2006-09-02
Hi,

What does shortkeys lite do?

Is this what you mean?
[http://keytouch.sourceforge.net/]("http://keytouch.sourceforge.net/")

---

### Post by solarwind on 2006-09-02
> **Ramaddan said:**
> Hi,

What does shortkeys lite do?

Is this what you mean?
[http://keytouch.sourceforge.net/]("http://keytouch.sourceforge.net/")


shortkeys lite is a free windows program that is a text replacement tool.

for example, if i told it that everytime i typed "ubuntu", it would replace that exact text with, lets say, "Linux for human biengs", if i configured it that way, so i wouldn't keep having to type in long phrases, i could configure it to replace text with the proper hotkey. 

Thanks a lot for the reply, but keyTouch seems to be for special keyboards. I don't think that the its what i'm looking for. But thanks for the reply, keyTouch may be nice for my laptop!!

Any other ideas guys?

Thanks in advance!

---

### Post by solarwind on 2006-09-03
Hmm.. I searched around, but I found nothing. Maybe I don't know what to look for. 

Can someone please help?

---

### Post by Ramaddan on 2006-09-03
Hi,

I actually also searched around for you, but I couldn't find anything.

I am actually going to try to run it or a similar program using wine,
which I doubt will work, but I will try anyway.

Sorry that I couldn't help more, but this would be a nice project for
someone to do for Linux, since there does not seem to be any similar
program for Linux out there.

---

### Post by solarwind on 2006-09-04
I'll try making one if I can find out a way to "write" to the keyboard device.

By the way, where is the keyboard device? I see /dev/input/mouse, but where is the keyboard device. Is there even one?

---

### Post by Ramaddan on 2006-09-04
If I remember right (but don't quote me on this), it's /dev/input/event0 or 1

Anyone else here to confirm this?

---

### Post by solarwind on 2006-09-04
Even if /dev/input/event0 or 1 is the keyboard device, how would I "write" to the device so that I can simulate a keypress?

---

### Post by Ramaddan on 2006-09-04
It's kind of sad that no one has replied to this post yet but us two.

I'm not that good at programming, so I will not know at the top of my head,
but I think that the following links might be useful:

[http://www.velocityreviews.com/forums/t279108-how-to-simulate-keyboarddevtty0-.html]("http://www.velocityreviews.com/forums/t279108-how-to-simulate-keyboarddevtty0-.html")

[http://www.linux.org/docs/usenetlinux.html]("http://www.linux.org/docs/usenetlinux.html")

From the above we notice that there is:
comp.os.linux.development.apps and comp.os.linux.development.system

And I think you need in this case: comp.os.linux.development.system

Here is an example site:
[http://groups.google.fr/group/comp.os.linux.development.system/search?group=comp.os.linux.development.system&q=keyboard&qt_g=1&searchnow=Search+this+group]("http://groups.google.fr/group/comp.os.linux.development.system/search?group=comp.os.linux.development.system&q=keyboard&qt_g=1&searchnow=Search+this+group")

Hope the above helps you to get started.

Wish I could help you more, but this is very new to me.

---

### Post by peabody on 2006-09-04
Within text editors such as vi and emacs, this is known as abbreviations.

From within Emacs:

Type out the word or sentence you want.  Drag the mouse and highlight the phrase.  C-u 0 C-x a g.  Type the abbreviation.  Then turn on abbrev-mode by M-x abbrev-mode or expand manually via C-x a e.

From within vim:

:iab <abbreviation> <expansion>

Then type the abbreviation in insert mode.

I do not know of a program that performs such an operation system wide.

---

### Post by solarwind on 2006-09-05
Hmm.. I need a system wide one. One that can even macro in java applets on the web.

---

### Post by solarwind on 2006-09-06
Can somone PLEASE help?

---

### Post by solarwind on 2006-09-09
Hmm.... Still looking. I really need this. I bet other people need a program like this too. I would really appreciate it if anyone could help.

Thanks in advance!

---

### Post by Rengor on 2007-03-08
I've been desperately looking for this as well. I have about 150 text strings I use for support purposes in various applications so it's not feasible for me to copy&paste them from a text file.

This functionality is the only thing keeping me from doing work from Ubuntu which I otherwise much prefer, but they ShortKeys for Windows is too important for me (huge time saver).

I could possibly live with assigning a bunch of hotkeys. But I haven't been able to quite find that functionality either.

If anyone has any ideas please do tell!

---

### Post by peabody on 2007-03-08
Well, since this has been talked about so much, I'm interested in figuring out how to write it.  I'm a computer science college student right now.  My language of choice is Python, but I can do C and C++ as well (I'm just not a seasoned expert in those languages).

My concern is how technically feasible this is for Desktop Linux.  For a program like this to work it would need system-wide access to the keyboard and it would need to be able to replace text already typed into an application

The first point I'm pretty sure is possible and may even be easy to implement (although a forseeable problem is that the program might require root authentication).  The second point is the one I'm worried about.  There are multiple GUI toolkits in GNU/Linux.  I'm not an expert on the event APIs for each of them.  I also don't know if there's a way to send events consistently to all the different toolkits.  If there were, then this could work...once a known sequence had been written, all one would have to do is send the proper number of backspace events and then send the replacement string as a sequence of keystroke events.

Ironically, I'd probably be better suited to write this in Windows ;).  I once wrote a  keylogger in Windows, about three years back.  Doing that on Windows involved installing a system wide dll hook as part of the program.  I remember I researched the Win32 API for days to figure that out.  Too bad none of that work comes in handy here.

[Edit]
heh, I just came across this post again...looks like I finally got around to writing that program: [http://peabody.weeman.org/autokey.html](http://peabody.weeman.org/autokey.html).

---

### Post by Rengor on 2007-03-08
I would be most happy to test it with you if you'd be willing to take it on. I've been searching around for a while and found quite a few people interested in this functionality.

---

### Post by peabody on 2007-03-08
I'd love to try...however, I'm a week away from finals.  I can't start now, however I can try tackling it over my break which will be after the 20th.

Also, for this project to even get off the ground, I'm going to need liturature on the two things I mentioned.  1) How to interface to system wide keyborad events in X, and 2) how to send events to the various different gui apps in Linux.

I have zero experience and knoweledge about these things.  Also, I could really use information on whether Python could access these things.  If so, development will go a lot faster.

---

### Post by 3chris on 2007-09-23
I'm look for a program like shortkeys for linux too. I find a program called Snippits 0.3 , it seems like a text replacement program . But I can't execute the program . 

[http://www.kde-apps.org/content/show.php/Snippits?content=52197](http://www.kde-apps.org/content/show.php/Snippits?content=52197)

Reply to Delkster:
 the author of  "Snippits 0.3" wrote this stuff:
==Installation==
To install, copy the keyout and snippit scripts to a directory in your PATH. *
Make sure they are executable.**  Copy the provided snippits to the snippit
directory, which by default is $HOME/.snippits

snippit depends on erb, embedded ruby, to be installed.  Consult your
distribution documentation on how to install erb.
keyout depends on xte from the xautomation suite.  Consult your distribution
documentation on how to install xte.

*****************************************
Here is what i did:
Distribution I use: ubuntu 7.04 , gnome
1. I can install embedded ruby 1.0.5-1  by Synaptic Package Manager provided by ubuntu
2. I can install xautomation 0.96-5 , by Synaptic Package Manager too
   **but i can't find xte in the Synaptic Package Manager  

Here is the problem i face:
*question 1:What does it mean my PATH?  where should I put the keyout and sippit file?  (line 1)
**question2 : how do I make sure they are executable? I double click the files , and they did not run. (line 2)


Can anyone help me execute the program?

---

### Post by Delkster on 2007-09-23
> **3chris said:**
> I'm look for a program like shortkeys for linux too. I find a program called Snippits 0.3 , it seems like a text replacement program . But I can't execute the program .

How are you trying to execute it?

---

### Post by peabody on 2008-01-27
I got snippits working, for ubuntu, install this stuff:

```
sudo apt-get install ruby ruby1.8-dev rdoc rubygems libruby-extras xautomation xsel
sudo gem install raspell
sudo gem install snippits
```

You then have to add /var/lib/gems/1.8/bin to your path.  Add the following to your **~/.profile** (not .bashrc) file and log in and out again:

```
export PATH="/var/lib/gems/1.8/bin:$PATH"
```

Documentation for the software can be read now in your browser from:
file:///var/lib/gems/1.8/doc/snippits-0.5.1-/rdoc/index.html

Now you can use the ks program to type out text.  For example, you could use xbindkeys, KHotKeys, or the edit the gconf custom commands in GNOME so that you could assign the shell command ks snippit_file_goes_here to a key sequence.

I have also made an attempt at a text expansion program.  Mine actually tries to monitor input from a /dev/input file.  It requires the python-xlib package be installed, I have thread about here:

[http://ubuntuforums.org/showthread.php?t=679612](http://ubuntuforums.org/showthread.php?t=679612)

And my youtube page has some demonstrations:
[http://www.youtube.com/user/peabodyman](http://www.youtube.com/user/peabodyman)

---

### Post by solarwind on 2008-01-27
> **peabody said:**
> I got snippits working, for ubuntu, install this stuff:

```
sudo apt-get install ruby ruby1.8-dev rdoc rubygems libruby-extras xautomation
sudo gem install raspell
sudo gem install snippits
```

You then have to add /var/lib/gems/1.8/bin to your path.  Add the following to your ~/.bashrc file and log in and out again:

```
export PATH="/var/lib/gems/1.8/bin:$PATH
```

Documentation for the software can be read now in your browser from:
file:///var/lib/gems/1.8/doc/snippits-0.5.1-/rdoc/index.html

Now you can use the ks program to type out text.  For example, you could use xbindkeys, KHotKeys, or the edit the gconf custom commands in GNOME so that you could assign the shell command ks snippit_file_goes_here to a key sequence.

I have also made an attempt at a text expansion program.  Mine actually tries to monitor input from a /dev/input file.  It requires the python-xlib package be installed, I have thread about here:

[http://ubuntuforums.org/showthread.php?t=679612](http://ubuntuforums.org/showthread.php?t=679612)

And my youtube page has some demonstrations:
[http://www.youtube.com/user/peabodyman](http://www.youtube.com/user/peabodyman)

Thanks a lot for this! I'll also be making a program that'll easily do what I was looking for.

---

### Post by peabody on 2008-01-27
Yikes!  Just an update...you should be adding that /var/lib/gems/1.8/bin path statement to the **~/.profile**, NOT the ~/.bashrc.  Then login and out again.  That should make it so the desktop environment has the 'ks' command in your path.

[Edit]

Yet one other thing.  you need the xsel package installed to use the {paste} command.

[Edit]

Yet one more thing, I forgot the ending " on the PATH statement in the post above.  I've fixed it.

[Edit]

Yet again, that should have been ~/.profile

---

