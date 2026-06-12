---
title: "Copy &amp; paste commands to Terminal - 1 line at a time?"
date: 2008-06-28
forum: General Help
---

### Post by Ozdemon on 2008-06-28
If I am copying and pasting commands into Terminal, e.g.

> sudo apt-get install alsa-oss compizconfig-settings-manager faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar

can I copy and paste the lot at once, or do I have to do it 1 line at a time?

Also, how can you tell when one command finishes and another starts?  In the above example, is each line a separate command?

Tks for helping.  :confused:

---

### Post by geraldm on 2008-06-29
multiple lines can be pasted with one command.
Normally you would paste into a terminal program, such as another editor, and it would handle the text.  Some editors may not paste correctly when the settings you are using require automatic indentation.  You will know because it does not come out as expected.
A line extends to the 0x0a character.
It is too difficult to tell on an individual line when the text is not pasted into the same system as the origin of the line.  Text and .html editors may add punctuation for formatting that were not in the original clipboard paste.

Gerald

---

### Post by drs305 on 2008-06-29
If you are using a mouse, go right to the next post... ;-)

In ubuntu, when copying and pasting to or from the terminal, you have to also use the SHIFT key in combination with CTRL-C and CTRL-V, so it becomes CTRL-SHIFT-C to copy and CTRL-SHIFT-V to paste - at least for me. Use the more standard (for windows) CTRL-C and CTRL-V when not in terminal.

---

### Post by forger on 2008-06-29
select your text, right-mouse button > copy, go to terminal, right-mouse button > paste :)

---

### Post by nick_h on 2008-06-29
There is also a more Linux way to copy and paste.

Select the text you want to copy in the terminal.  Then in the application you want to paste into click the middle mouse button.

---

### Post by Elfy on 2008-06-29
> Also, how can you tell when one command finishes and another starts? In the above example, is each line a separate command?

Your example is one command - for root to use apt-get to install all the packages which follow 'install'

Also another way to copy, which I frequently curse when I have to use a windows machine, is to double click the line to copy - then in the new application, terminal etc., use the middle button if you have - really simple and quick.

If you go back to your original post and edit it - where you have quote and /quote inside square brackets - change the quote to code at the beginning and end and you will find that the command is probably one line.


```
sudo apt-get install alsa-oss compizconfig-settings-manager faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar
```

---

### Post by Ozdemon on 2008-06-29
First, let me say thanks to everyone who replied.  I recently discovered the select and middle click way of posting into terminal after (well, I'm too embarassed to say how long) a time of manually typing each command.

That said, my 2 questions are:

(1) Suppose I see these commands:

sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin

sudo apt-get install gnome-mplayer gecko-mediaplayer 

They appear to be 2 distinct commands.  Can I copy both - at the same time - and post both -at the same time - into terminal and hit enter once, or do I have to copy and paste each command, and hit enter separately for each command?

(2) In the example given in my first post - taken from [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

sudo apt-get install alsa-oss compizconfig-settings-manager faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-gcjwebplugin liblame0 non-free-codecs openjdk-6-jre unrar

I believe this is one command, although it is spread over multiple lines.  How can I tell by looking at it that it is one command and not several?

Thanks again.

P.S. GeraldM.  Sorry but I do not understand what "A line extends to the 0x0a character" means.

---

### Post by drs305 on 2008-06-29
1. You would have to do each separately, or you could combine them with a "&&" inbetween. In the first example, the command/switch is "sudo apt-get remove" and it will act on every entry after that with a space. If you combined the lines, when it got to the second "sudo apt-get install" it would try to remove "sudo", then remove "apt-get", then remove ... And in fact, these items *could* be uninstalled.

2. It's all one command. It would be hard to know at first looking at it, but there is only one command, followed by options. You can have more than one command but it should be joined with "&&" before the second command if it is on the same (extended) line.  

Actually you *could* see words that might be commands, in other circumstances, in this entry (e.g. if you saw gimp in the list) but in this case they are the apps and packages that "sudo apt-get install" is going to act on.

---

### Post by Elfy on 2008-06-29
> P.S. GeraldM. Sorry but I do not understand what "A line extends to the 0x0a character" means.I don't either :)

1 - if you wanted to run these at the same time you could

> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin [COLOR="Red"]&&[/COLOR]sudo apt-get install gnome-mplayer gecko-mediaplayer

but it would do each seperately - the easiest way would be to add the second set of packages to the first

> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin [COLOR="#ff0000"]gnome-mplayer gecko-mediaplayer[/COLOR]

2 - at the beginning of the command it gives

> sudo apt-get install
sudo - gives it root rights
apt-get - is what you are running
install - is the option you are using
you could also want to use more options

Everything after that is what you want to install.

Does that help - I've only been here a year so my explanations can sometimes be a bit simplistic, you could make them more complicated :)

---

### Post by brian_p on 2008-06-29
> **Ozdemon said:**
> They appear to be 2 distinct commands.  Can I copy both - at the same time - and post both -at the same time - into terminal and hit enter once, . . . . .  ?

Yes. Including a newline at the end means not having to hit enter.

> I believe this is one command, although it is spread over multiple lines.  How can I tell by looking at it that it is one command and not several?

You have to read and interpret it. That means being familiar with commands.

---

### Post by Ozdemon on 2008-06-30
Okay, got it now.  Thanks muchly for all the help.

):P

---

### Post by steveneddy on 2008-06-30
> **nick_h said:**
> There is also a more Linux way to copy and paste.

Select the text you want to copy in the terminal.  Then in the application you want to paste into click the middle mouse button.

+1 - my favorite

---

