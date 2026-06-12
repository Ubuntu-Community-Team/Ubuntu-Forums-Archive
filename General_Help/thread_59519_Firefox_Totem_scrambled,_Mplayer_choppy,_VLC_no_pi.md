---
title: "Firefox: Totem scrambled, Mplayer choppy, VLC no picture, Xover flaky..."
date: 2005-08-24
forum: General Help
---

### Post by elempoimen on 2005-08-24
...there's just no video love for me in Hoary. :(

Here's the situation:

I have the latest w32codecs installed.

I have the latest Mplayer and Mplayer-mozilla installed (yes, 2.85 as per the howto).

I have a Thinkpad T23, which doesn't have stellar graphics but can certainly sustain video in a browser.

Here's what happens when I use various browser plugins (disabling the others) for playing multimedia:

Totem:
[INDENT]I have a strange problem where the video in Totem is scrambled part of the time anyway, even when playing a DVD.  If I resize the window just right, then it's OK.  But there's no way to resize a browser window--so I have good audio, and it looks like it would work if I could just get the video unscrambled.  It's almost like it breaks up into diagonal bars...wierd.  Sites that use WMA don't detect this one.[/INDENT]

Mplayer:
[INDENT]It works.  But the sound tends to be choppy...but not consistently.  Even within the same video, sometimes it breaks up, sometimes not.  Very annoying.  Sites that use WMA detect this plugin without problem.[/INDENT]

VLC:
[INDENT]I get a black box that says "(no picture)."  It's been said that VLC doesn't stream, and that a user should wait--but after a minute with no activity on the broadband connection, it's probably safe to say that there's a problem.  Again, sites that use WMA don't detect this one.[/INDENT]

Crossover Plugins:
[list]
[*]Quicktime: When using the OSS driver, it works but there is no sound.  When using the ALSA driver, it works, but sound is really choppy.  I tried the troubleshooting ideas on the Codeweavers web site, but to no avail.  Killing ESD doesn't seem to make a difference.
[*]WMA: The plugin loads, shows the Windows Media logo, but no love.  Nothing happens.  It just sits there.
[/list] 

It's also worth mentioning that I made the modifications in order to use ESD and ALSA simultaneously.  This has not seemed to make much of a difference--although Mplayer seems to break up less now when I switch to using the OSS driver in the Multimedia Systems Selector in GNOME...but it *does* still break up.  I've also tried all of the video options in the Multimedia Systems Selector--still nothing.

My preference is to get the picture straightened out in Totem, and get it working with sites like CNN that autodetect WMA.  If not, I'd be happy if I could at least get Mplayer working without sound problems.

Or Crossover...

Thanks in advance for any help you can offer.

---

### Post by frodon on 2005-08-24
I have always got problems with firefox and embedded videos,  and when I installed mozilla (to see if the problem was firefox) I was really surprised to see that all the plugins worked perfectly. Give a try to mozilla web brother and install mplayer plugin (in synaptic) ....  it could solve all your problems quickly.

---

### Post by elempoimen on 2005-08-24
Nope.  Mplayer is still choppy in Mozilla.  (It was installed as a dependency when I installed Mplayer.)  Not sure what the deal is, but it's annoying.  I didn't take the time to test the others--especially since the one I really want (Totem) is problematic outside of Firefox as well.

---

### Post by RadixLecti on 2005-11-25
Try this:

Start an embedded movie. Rightclick on the movie -> cofigure. 
In the Audio output, choose oss.

---

### Post by elempoimen on 2005-11-27
It's a solution...but not the best.

I'm using the newest mplayer now...and things seem better.

Thanks!

---

### Post by frodon on 2005-11-28
I recently tried the media player connectivity extension of firefox and all work really well with it.
You can find it using the tab extension of your firefox window.

---

