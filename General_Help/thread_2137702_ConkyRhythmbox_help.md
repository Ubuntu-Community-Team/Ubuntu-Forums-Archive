---
title: "ConkyRhythmbox help"
date: 2013-04-21
forum: General Help
---

### Post by neilnoise on 2013-04-21
I'm trying to get Conky to display the now playing information from Rhythmbox, using the conkyRhythmbox script, but every field just outputs "unknown".

This is what I have in my conky config file:

```
Title:${execp conkyRhythmbox --datatype=TI}Artist:${execp conkyRhythmbox --datatype=AR}
Album:${execp conkyRhythmbox --datatype=AL}
```

I'm probably missing something really simple, but I can't think what!

Anyone able to help please?

---

### Post by Cheesemill on 2013-04-21
What version of Rhythmbox are you using?

Due to changes in Rhythmbox the script doesn't work with the latest versions.

---

### Post by neilnoise on 2013-04-21
It's version 2.97

---

### Post by Cheesemill on 2013-04-21
Thought so.

The conkyRhythmbox script won't work with that version.
The last version it worked with was 2.9.0 I believe.

---

### Post by kostkon on 2013-04-21
Is there a conky script that displays track info using MPRIS? You could use that.

---

### Post by VinDSL on 2013-04-21
> **kostkon said:**
> Is there a conky script that displays track info using MPRIS? You could use that.
Here's what I came up with (with scrolling)...

SOURCE:  [http://ubuntuforums.org/showthread.php?t=1771033&page=86&p=12600562&viewfull=1#post12600562](http://ubuntuforums.org/showthread.php?t=1771033&page=86&p=12600562&viewfull=1#post12600562)

```
##################################
##  RHYTHMBOX 2 (Experimental)  ##
##################################
${if_running rhythmbox}
${voffset -13}${font DroidSans:bold:size=8}${color4}RHYTHMBOX${offset 8}${color6}${voffset -2}${hr 1}${font}
${voffset 2}${font DroidSans:size=8.25}${color3}${if_match "${execpi 2 expr length "`qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""`"}" >= "48"}${alignr 15}${scroll 38 4* ${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}}${font}${else}${alignc}${execi 2 qdbus org.mpris.MediaPlayer2.rhythmbox /\org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Metadata | grep title | cut -c 14-""}${font}${endif}${endif}
```

All I wanted is the "Title", but this code (above) shows the MPRIS entry point for Rhythmbox , so you can extrapolate from there.  ;)

---

### Post by neilnoise on 2013-04-22
Thanks! That's just about working perfectly!

---

### Post by Cheesemill on 2013-04-22
Another option is to use the rhythmbox-client program that's part of Rhythmbox to extract the required data...
```
man rhythmbox-client
```
```
${if_running rhythmbox}${lua conky_draw_bg}${execpi 20 ~/.conky/getAlbumArt.sh}${image ~/.conky/albumart -s 75x75}${voffset 6}${goto 96}${font Ubuntu:size=10}${execp rhythmbox-client --no-start --no-present --print-playing-format=%tt}${font}
${voffset 6}${goto 96}${execp rhythmbox-client --no-start --no-present --print-playing-format=%ta}
${goto 96}${execp rhythmbox-client --no-start --no-present --print-playing-format=%at}
${voffset 6}${goto 96}${execp rhythmbox-client --no-start --no-present  --print-playing-format=%te} / ${execpi 3 rhythmbox-client --no-start --no-present  --print-playing-format=%td}${alignr}${execpi 3 rhythmbox-client --no-start --no-present  --print-playing-format=%ay}${endif}
```

[[IMG]http://ompldr.org/taTZscw[/IMG]]("http://ompldr.org/vaTZscw")

---

### Post by neilnoise on 2013-04-22
I came across that, but apparently it's not supported anymore. The only trace of it I could find is the man page!

---

### Post by Cheesemill on 2013-04-22
> **neilnoise said:**
> I came across that, but apparently it's not supported anymore. The only trace of it I could find is the man page!

That's strange. I use this conky on both my 12.10 and 13.04 installations and the rhythmbox-client command is working fine.

---

### Post by VinDSL on 2013-04-22
> **Cheesemill said:**
> That's strange. I use this conky on both my 12.10 and 13.04 installations and the rhythmbox-client command is working fine.
I used rhythmbox-client for years.

When it worked... it worked.  LoL!  :D

They did away with it for a while... then, they brought it back.

Recently, with Gnome-Shell 3.8.1, it started hard-locking Conky.

That's why I came up with the MPRIS code.  ;)

Maybe I'll try rhythmbox-client again, later, or not...

---

