---
title: "[SOLVED] ies4linux in Hardy"
date: 2008-05-31
forum: General Help
---

### Post by sparkguitar05 on 2008-05-31
Anyone know how to get ies4linux to work in Hardy?

---

### Post by aysiu on 2008-05-31
> **sparkguitar05 said:**
> Anyone know how to get ies4linux to work in Hardy?
Yes. Follow these instructions:
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by sparkguitar05 on 2008-05-31
Worked great.  Thanks!

---

### Post by huffy318 on 2008-06-16
I installed as instructed, and a couple times when I ran IE, I got an error something like

thunk32 connect failure or Thunk Connect 32 Failure!

I did a search, and some places indicate that comes from the DERDERO.A WORM.

Other than the websites ies4linux sets IE to startup with, all I connected to is my Linksys WVC54GCA camera, which I just got and requires ActiveX to set one of the settings.

Any idea what happened?  Is ies4linux or the windows install files themselves compromised?

I'll couldn't find a way to post on the ies4linux site (the link to login/create a login only took me to a place to login, not create one).

---

### Post by Ontolog on 2008-07-01
I was having download problems and I found a partial solution here:

[http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html](http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html)

Partial because while it did download some more files using this method, I still couldn't get at all the files. I wound up downloading most of them manually with Firefox. Note that you can only download one file at a time. If you try to pull in more than one at a time you will get rejected by MS's download site.

Now that I get IE6 up and running I am having another problem. Typing in the address bar is extremely super slow. However typing in text fields is no problem.

---

### Post by zhuohua on 2008-10-11
Hi, i still get this following errors. What should i do.. please help me.. thanx alot
btw, i am on kubuntu hardy (wine 1.0)


IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).

No user interface available. Use command-line ies4linux or install pygtk. Details: [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI)

IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com).


Usage: ./ies4linux [OPTIONS]

This script downloads and automagically installs multiple versions of
Microsoft Internet Explorer on Wine.

Without any option, IEs4Linux will:
- install IE6
- install Adobe Flash 9
- create icons on Desktop and Menu
- use folder: /home/zhuohua/.ies4linux

You can configure other things:

--install-ie55         Install IE5.5 in BASEDIR/ie55/
--install-ie5          Install IE5 in BASEDIR/ie5/

--install-corefonts    Install MS Core Fonts (corefonts.sf.net)

--no-flash             Don't install Adobe Flash Player 9
--no-ie6               Don't install IE 6

--no-desktop-icon      Don't create an icon in Desktop
--no-menu-icon         Don't insert icon on Menu

--full-help            Display all possible options

---

### Post by figo2476 on 2008-10-29
> **Ontolog said:**
> I was having download problems and I found a partial solution here:

[http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html](http://tehpost.blogspot.com/2008/06/ie4linux-download-problem-during.html)

Partial because while it did download some more files using this method, I still couldn't get at all the files. I wound up downloading most of them manually with Firefox. Note that you can only download one file at a time. If you try to pull in more than one at a time you will get rejected by MS's download site.

Now that I get IE6 up and running I am having another problem. Typing in the address bar is extremely super slow. However typing in text fields is no problem.

I am wondering is the download links in the script (ies4linux - install.sh) still working. I tried the widget options "-c -t 10 -T 10", but many files are not downloaded.

---

### Post by vandorjw on 2008-11-06
Gtk:ERROR:/build/buildd/gtk+2.0-2.14.4/gtk/gtktextview.c:3425:gtk_text_view_validate_onscreen: assertion failed: (text_view->onscreen_validated)
ui/pygtk/python-gtk.sh: line 6:  7749 Aborted                 python "$IES4LINUX"/ui/pygtk/ies4linux-gtk.py


Before the Install process, it complained about my version of wine.
(Saying it was too old)

It wanted Version 0.9, but I have version 1.01.

This method doesn't work flawlessly in Ubuntu 8.10 :(
-------------------------------------------------------
I was trying to install while running compiz-fusion. I wonder if it makes a difference if I turn that off.

---

### Post by Doncr on 2008-12-29
Doesn't work for me. I get a Kommander errors, so I forced it to use gtk, and get more errors, so tried --no-gui.

But the real problem is it cannot download the files. The server does not respond. dig shows it it there, but running wget manually gets no response. I guess they must be running IIS :-|

Oh well - back to VirtualBox :-(

---

