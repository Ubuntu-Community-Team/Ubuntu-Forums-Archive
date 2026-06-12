---
title: "gomastage instead of Sonicstage"
date: 2008-02-15
forum: General Help
---

### Post by maniheer on 2008-02-15
Hi,
I've got Ubuntu and found a song I like which I want to put on my NW-A1000 Sony MP3 Player but Sonicstage doesn't work on Linux. So I looked for alternatives and found NW-E00X which transfered songs to my MP3 in atrac but had to connect to Sonicstage to recognize the track, which kills the point. :(
Then I found gomastage which should work on Linux and my MP3 player, heres the source [http://code.google.com/p/gomastage/source/browse](http://code.google.com/p/gomastage/source/browse) but I don't know what to do with it.:confused:

Can somebody give me step by step instructions or give an alternative.

As you have probably guessed, I am new to Linux.

Thanks

---

### Post by petedct on 2008-02-22
There's a Howto over at Google. Give that a try.

[http://code.google.com/p/gomastage/wiki/Howto]("http://code.google.com/p/gomastage/wiki/Howto")

---

### Post by statto1977 on 2008-02-25
I've tried to go about installing this via the instructions, and I thought I had all the libraries they mentioned, but when I typed 'make' in terminal I got all these errors.

gcc -g -DSPLASH_ENABLED `taglib-config --cflags` `xml2-config --cflags` `pkg-config --cflags gtk+-2.0` -c -o log/log.o log/log.c
/bin/sh: taglib-config: not found
/bin/sh: xml2-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
log/log.c:1:19: error: stdio.h: No such file or directory
log/log.c:3:18: error: time.h: No such file or directory
log/log.c:4:25: error: glib/gstdio.h: No such file or directory
In file included from log/log.c:6:
log/log.h:4:18: error: glib.h: No such file or directory
In file included from log/log.c:6:
log/log.h:8: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;init_log&#8217;
log/log.h:9: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
log/log.h:10: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;close_log&#8217;
log/log.c:8: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
log/log.c:20: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;init_log&#8217;
log/log.c:70: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
log/log.c:106: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;close_log&#8217;
make: *** [log/log.o] Error 1

It's all a bit daunting as I've only been using the OS for a week, so I'm completely new to this. Are there any specific libraries I should be looking to add, and can I do it through synaptic?

---

### Post by petedct on 2008-02-25
Sorry I can't help further.

---

### Post by orasetaina on 2008-06-13
any luck with this?....if so give me a private mssage! im trying to do this as well!!!

---

### Post by orasetaina on 2008-06-16
Anyone manage to find a solution to this?

---

### Post by statto1977 on 2008-06-18
> **orasetaina said:**
> Anyone manage to find a solution to this?

There is an alternative that's much easier to get working called Symphonic. I've only used it with the NW-E003 so far (I got given one today) but according to Wikipedia it's compatible with the NW-A series of walkmans: [http://sourceforge.net/projects/symphonic/](http://sourceforge.net/projects/symphonic/)

You need to have Java installed.

Guide:

Extract the downloaded file to the root directory of the player.
Delete your OMGAUDIO folder, then create another one with the same name.
Right click on the jar file you extracted to the root directory, and select 'Open with Java'.
Change the device path to the location of your player (probably /media/disk).
Change the local music path to the directory your music is in.
Apply the changes.

You should now be able to use Symphonic to select tracks from your hard drive and import them to the player or export from the player to the computer. The program takes up less than 1MB of space, and because it's on your player and it runs under Java it means that you can use your player with any PC running Linux or Windows as long as they have Java.

Hope this helps.

---

### Post by orasetaina on 2008-06-19
Is there any sort of wrapper that will play mp4 aac and omg files on the players as well?
Maybe a plugin for the above said programs!

---

### Post by orasetaina on 2008-06-19
"Change the device path to the location of your player (probably /media/disk).
Change the local music path to the directory your music is in.
Apply the changes."

where do i enter this?

Does the .jar file need to be in where all the music will be stored?

---

### Post by statto1977 on 2008-06-19
> **orasetaina said:**
> "Change the device path to the location of your player (probably /media/disk).
Change the local music path to the directory your music is in.
Apply the changes."

where do i enter this?

Does the .jar file need to be in where all the music will be stored?

Open the .jar file with Java
Click 'Options'
Click 'Configuration'
Click 'Paths'

Then you can change the device path and local music path.

The .jar file is best kept in the root directory. The only thing you use it for is importing and exporting tracks.

Hope that solves your issues.

---

### Post by orasetaina on 2008-06-20
Open the .jar file with Java
Click 'Options'
Click 'Configuration'
Click 'Paths'


I believe none of these options are available to me in this app!

---

### Post by statto1977 on 2008-06-20
Have you definitely downloaded the right file? The one I downloaded was JSymphonic version 0.2.1alpha

---

