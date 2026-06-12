---
title: "Why no MACRO programs? I need one bad like autohotkey"
date: 2006-08-08
forum: General Help
---

### Post by videodrome on 2006-08-08
Why are there no macro programs under Linux?

Imagine that you have a text file with your address in it:

```
myaddress.txt
1234 xfce street
ubuntu, ohio
44223
```

And I want to press a key combination like ALT+A to paste this text *wherever the cursor is*, be it at a shell, in Thunderbird, or wherever. 

Why isn't this possible? Isn't there some way to send a text file to the buffer and then dump it at the prompt? You've got programs like Macro Magic, Autohotkey, ect that do this under Windows, as well as doing much more as well.

Also. there are prorams under Windows that insert typing for you so if you type a certain thing, like "address" it will type your address for you.

These things are a necessity for me, as I type a lot of the same things over and over and over again.

Thanks

---

### Post by videodrome on 2006-08-19
40 views and no responses. No one has any thoughts?

---

### Post by orb9220 on 2006-08-19
[http://keytouch.sourceforge.net/about.html](http://keytouch.sourceforge.net/about.html)

---

### Post by Arisna on 2006-08-19
If you're up for trying out KDE (kubuntu-desktop), you can also get a lot of powerful keyboard-driven functionality using the dcop system.

---

### Post by videodrome on 2006-08-21
Keytouch is NOT at all what I am talking about. That's for enabling special keys on a laptop. I've used it before to contol an Inspiron's volume button.

---

### Post by peabody on 2006-08-21
Yes it's too bad I don't know of a program off hand that has this functionality.  However lots of text editors have this functionality, such as Emacs (what I use) or vi.  If you need this kind of functionality desktop-wide though, I'm not sure how to implement it.  I'll try googling.

---

### Post by Lunar_Lamp on 2006-08-21
I don't understand how this differs from copy and paste.  I'm sorry - I'm sure I'm being a bit slow about it...

---

### Post by peabody on 2006-08-21
> **Lunar_Lamp said:**
> I don't understand how this differs from copy and paste.  I'm sorry - I'm sure I'm being a bit slow about it...

Copy paste is only as good as the clipboard.  Without a clipboard manager you only have one thing on the clipboard at a time.  With a clipboard manager you can store several things at once and refer to them later, but it's usually tied to what you've copied and pasted.  I believe this user in question is looking for something that allows him/her to assign text or actions to a keyborad shorcut that can then be used in any application (firefox, gedit, gaim, xchat, etc.).

---

### Post by germanblando on 2006-08-21
I'm a user of macro programs too. One of the firs thins I did when I began in Linux was looking for this kind of programs. I didn't find a lot of them, but certainly there is something.
Take a look to these links:

[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)
[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)

The two programs above can be used in conjunction to achieve functionality as similar as Autohotkey.

Regards

---

### Post by Zolox on 2006-08-27
Has anyone found an easier solution yet?

---

### Post by videodrome on 2006-09-24
Apparently not. Right now all that I can do is to use a Thunderbird extension that allows you to use macros. It's called Quicktext. Of course the macros only work within Thunderbird. If they were system-wide I'd be set.

---

### Post by ikester8 on 2007-01-05
I've been playing with xmacro and I'm beginning to like it. I have an entry-level tutorial on my blog. Please see [http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html](http://ikester.blogspot.com/2007/01/im-huge-fan-of-autohotkey.html).

Ike

---

### Post by Bel-O-Kan on 2007-01-12
I'm at your side for this request videodrome !
I've spent 2 days googling to find a macro tool (gnome) to implement basic tasks in gnome-terminal like :

ssh -l user host
stty erase ^?
select * from ...
export DISPLAY=...

And I'm still close to nowhere.

---

### Post by Epperly on 2007-01-20
Nobody's found one yet? Stinky...

---

### Post by balloons on 2007-02-07
You mean like this?

---

### Post by Epperly on 2007-05-03
> **guitara said:**
> You mean like this?
nice, where can I download gmacro? :)

---

### Post by balloons on 2007-05-03
Well I never released it since interest seemed to wane... I still have the source, but it's not complete as of yet. It can only play and record. The internal editing of a macro needs to be added (you can edit in an external editor, so I guess it's a mute point). I moved on to other projects. It was my attempt to learn python and glade. I was planning on rewriting it in C, since I know the language better, but I found interacting with the xserver was a pain, with no easy to use language bindings so I stopped.

---

### Post by z-vap on 2008-01-10
I know this thread is ancient, but I need to address why I think there are soo few programs like autohotkey or autoit.  

Basically Autohotkey & AutoIt are text based programming tools, that function as high level batchfiles.  What sets them apart from other macro utilities is their ability to understand Micro$oft API's and Window properties.  

I use these tools extensively on Windows.  I use them to do repetitive tasks.  I also use them as low level VB/C/C++/C# programs.  They basically extended the life of my windows boxes.  

They do what Linux probably already can do. 

What I mean by that is: alot of what can be done with AutoHotkey in windows can be done with Linux already, at least with scripting.  AutoHotkey's scripting is a hodgepodge of various programming languages, Bash shell scripts are pretty high level also.  Where Linux fails in regards to AutoHotkey is understanding the window they are reacting to.  The very fact that there is no "standard" windowing shell for Linux is the greatest downfall for not having a tool like AutoHotkey around.  IF someone were to port AutoHotkey to a linux environment, they'd have to understand all the different window environments around.  

The fact that the majority of what needs done in the window of a Gnome/KDE/xfce/etc generally already can be done in the terminal of the linux system.  

You can try the tools I listed below.  Or try to use the available tools that are already available for Linux.  (ie bash, etc).  The path to your "solution" may lead in a different direction with Linux, but the end result can be the same!! :)

---

xbindkeys

[http://ldtp.freedesktop.org/wiki/](http://ldtp.freedesktop.org/wiki/)

[http://xmacro.sourceforge.net/](http://xmacro.sourceforge.net/)

[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html)

---

### Post by peabody on 2008-02-18
just wanted to let people know that my autokey program has become pretty usable.  It still may not work for everybody, but most people are starting to report success with it.  You can download it here:

[http://autokey.sf.net/](http://autokey.sf.net/)

It only implements the hotstring functionality, but I imagine most people will still find that pretty useful.

---

### Post by jasonmeansfriend on 2008-03-03
how about snippets?

---

### Post by andrewkk on 2008-05-27
Thanks for the insight. I think you're right that most functionality gained from AutoHotkey in Windows is already more efficiently available through various commandline interfaces in Linux. It takes some rethinking if you're used to the AutoHotkey approach of automation, but it's definitely worth it in the end.

The largest remaining "missing" functionality in Linux I think is AutoHotkey's common use as a text-replacement utility. I haven't done any research to see what's currently out there to serve this purpose (though Autokey does look promising), but it definitely looks like a niche that would best be fulfilled by a specialized snippets utility and not a general purpose GUI scripting program.

---

