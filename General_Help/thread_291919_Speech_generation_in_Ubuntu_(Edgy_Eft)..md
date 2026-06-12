---
title: "Speech generation in Ubuntu (Edgy Eft)."
date: 2006-11-03
forum: General Help
---

### Post by moma on 2006-11-03
For your information.

Hello,

I have testet two very useful synthetic speech generators for Ubuntu.

**FESTIVAL**:
The [Festival...]("http://www.cstr.ed.ac.uk/projects/festival/download.html") speech generator is included in Edgy Eft by default ([AFAIK]("http://catb.org/%7Eesr/jargon/html/A/AFAIK.html")). Besides American and British English it can also speak Spanish.

In Ubuntu 7.10, I had to install Festival + one of the voice (language) packages. I chose festvox-don voice.
Note: Festvox-don package is in the restricted repository. You must enable that repository in the Software Sources dialog from Administration menu.

$ [COLOR="SeaGreen"]sudo aptitude install festival festvox-don[/COLOR]

List all Festival related packages
$ [COLOR="SeaGreen"]apt-cache search festival [/COLOR]

The usage of Festival is easy.

$ [COLOR="Green"]echo "Hello mrs Simpson. How are you?" | festival --tts[/COLOR]

I found a fancy talking-clock script on Ulteo.com's website.
See: [http://www.ulteo.com/main/forums/viewtopic.php?t=257](http://www.ulteo.com/main/forums/viewtopic.php?t=257) 
All credits to the author "ernie". Let's assume the script is GPL. Save the script to a "clock.sh" file, and test it with this command:

$ [COLOR="Green"]while [ 1 ]; do sh clock.sh; sleep $((60*5)); done &[/COLOR]

It sleeps 5 minutes between the time signals.
It uses the Festival speech engine which you can replace with Espeak if you wish.
---------------------------------------------------------------------------

**ESPEAK:**
Espeak is another good speech generator.
See: [http://espeak.sourceforge.net](http://espeak.sourceforge.net)

[COLOR="Red"]EDIT 20.okt.2007:[/COLOR]eSpeak is now in included in Ubuntu 7.10. Start the Synaptic and get it if it's not already installed.
$ [COLOR="SeaGreen"]apt-cache search espeak [/COLOR]
$ [COLOR="SeaGreen"]sudo aptitude install espeak[/COLOR]

Test it
$ [COLOR="Green"]espeak << END
How are you mrs Simpson.
Would you like to have a cup of tea.
Whaat?
I said it's TEA TIME.
END[/COLOR]

Study what options it provides.
$ [COLOR="Green"]espeak --help[/COLOR]

Notice that the **/usr/share/espeak-data/voices/** directory (or $HOME/espeak-data/  if you installed from source)  has several voice formats and languages.
$ [COLOR="Green"]ls -l /usr/share/espeak-data/voices[/COLOR]
(many sub directories)

You can also use this command to list the supported languages, dialects and voices.
$ [COLOR="Green"]espeak --voices[/COLOR]
---------------------------

Speak Finnish (Suomi's language)
$ [COLOR="Green"]espeak -v fi "Hyvvää päivää kansalaiinen. Mikä on sinun nimi?"[/COLOR]

Adjust the pitch of voice
$ [COLOR="Green"]espeak -p 7 -v en "How are you mrs Simpson?"[/COLOR]
$ [COLOR="Green"]espeak -p 200 -v en "How are you mrs Simpson?"[/COLOR]

Scary voice!
$ [COLOR="Green"]espeak -p 10 -s 100 -v en "How are you mrs Simpson?"[/COLOR]

Save the output to a .wav file
$ [COLOR="Green"]espeak -p 10 -s 100 -v en-rp -w voicemessage.wav "How are you mrs Simpson?"[/COLOR]

Convert it to .ogg file (avoid M$ wav formats)
$ [COLOR="Green"]ffmpeg -i voicemessage.wav voicemessage.ogg[/COLOR]

Play it in xmms or totem etc
$ [COLOR="Green"]totem voicemessage.ogg[/COLOR]
-------------------------------

**Now, let's imitate [HAL 9000...]("http://www-128.ibm.com/developerworks/autonomic/library/ac-hal9000.html?ca=dgr-lnxw02aHALWithAutoComp")**

Make Ubuntu _talk_ some manual pages for you. Let's make it talk
$ [COLOR="Green"]man ls[/COLOR]

The following is a long long line.  It will only talk the paragraphs NAME, DESCRIPTION and "SEE ALSO" of the "ls" manual page. So let's speak out !

$ [COLOR="Green"]zcat /usr/share/man/man1/ls.1.gz | nroff -man | col -b | sed -e '/./{H;$!d;}' -e 'x;/NAME/b' -e '/DESCRIPTION/b' -e '/SEE ALSO/b' -e d  |  espeak -p 30 -s 120 -l 10 -v en+11[/COLOR]

The -v en+11 argument sets espeak to produce english female voice. -p 30 makes the voice slightly darker.
The variants are  +1 +2 +3 +4 +5  for male voices and  +11 +12 +13 +14  which simulate female voices by using higher pitches.
---------

How about the manual page for "nslookup" tool. 

Where's the manual page?
$ [COLOR="Green"]locate "nslookup.?.gz"[/COLOR]
/usr/share/man/man1/nslookup.1.gz

Produce the voice of "man nslookup".
$ [COLOR="Green"]zcat /usr/share/man/man1/nslookup.1.gz | nroff -man | col -b | sed -e '/./{H;$!d;}' -e 'x;/NAME/b' -e '/DESCRIPTION/b' -e '/SEE ALSO/b' -e d  |  espeak -p 30 -s 120 -l 10 -v en+3[/COLOR]

Of course you can pipe it to "festival --tts" instead of "espeak"
---------------------

Espeak has also a GUI tool for editing of phonemes of your language and dialect.
Check [espeakedit-1.29](http://sourceforge.net/project/showfiles.php?group_id=159649)

[COLOR="Red"]Your help is needed to improve the pronunciation of your native language ![/COLOR]
See: [http://espeak.sourceforge.net](http://espeak.sourceforge.net)

You can also incorporate (link) espeak to your applications. 
So GO ON and develope a [fuzzy-logic..]("http://en.wikipedia.org/wiki/Fuzzy_logic"). intelligent agent that lives in the skydomes of a [Compiz...]("http://www.youtube.com/watch?v=pTRsLW0eet0") boosted desktop.  [COLOR="Red"]Talking, self reasoning and co-operative [<AI...>]("http://www.futuredesktop.org/hpc_linux.html#AI") agents must be the NEXT LEVEL of Ubuntu's development.[/COLOR] !
-----------------------

Study also: 
[Natural Language Toolkit.... ]("http://nltk.sourceforge.net/index.php/Main_Page")
and 
[http://www.speechio.org](http://www.speechio.org)

[http://tombuntu.com/index.php/2008/04/11/the-espeak-speech-synthesizer/](http://tombuntu.com/index.php/2008/04/11/the-espeak-speech-synthesizer/)

Julius speech recognition engine
[http://mugshot.org/visit?post=pPdbT6RW1zhZWJ](http://mugshot.org/visit?post=pPdbT6RW1zhZWJ)
[http://sourceforge.net/users/speechtotext/](http://sourceforge.net/users/speechtotext/)
---------------------------------------------------------------------


**ESpeak the old old way:**
ESpeak was not included in Feisty (Ubuntu 7.04) so we had to install it manually.

Download the latest Linux version of espeak from 
[http://sourceforge.net/project/showfiles.php?group_id=159649](http://sourceforge.net/project/showfiles.php?group_id=159649)
Pick the espeak-1.29-linux.zip package.

[COLOR="Red"]EDIT:[/COLOR] The latest development version is available from [here...]("http://espeak.sourceforge.net/test/latest.html")  (recommended version)

Unzip the zip file and move or copy the "espeak-data" directory to /usr/share/ or to your $HOME folder.

$ cd espeak-1.29.11
$ cp -fr espeak-data/ $HOME

Test it. (you should be in the .../espeak-1.29.11 directory)

$ [COLOR="Green"]./speak << END
How are you mrs Simpson.
Would you like to have a cup of tea.
Whaat?
I said it's TEA TIME.
END[/COLOR]

--- the end ---

---

### Post by ahgogo on 2007-01-05
Hi thank you for posting your test results on text-to-speech in Linux. I'm just wondering if there is something equivalent to those with a graphical user interface? Thanks in advance.

---

### Post by kolinab on 2007-01-05
Hey, that's Dr. Sbaitso! Anyone remember him? It was the early text to speech voice on my old Sound Blaster card. "Hello, my name is Dr. Sbaitso, I am here to help you . . ."

Seriously though, that's a useful feature to know about. I used to use it infrequently for proofreading papers (it's surprisingly effective) and I'm going to remember to use it again. Hopefully there's an easy way to plug in a large string of text, or select a paragraph and have it read.

---

### Post by mikeym on 2007-02-27
I was wondering if any of you experienced Ubuntu users had any means of implementing these text to speech programs, say in the way the Mac works with a shortcut to read any highlighted text? 

I had a go with Festival but I couldn't even work out how to change the selected voice. 

It is possible to set a script to run when a shortcut is pressed but I don't know where to pick-up the information on what is selected.

---

### Post by Marsolin on 2007-02-27
[KSayIt]("http://linuxappfinder.com/package/ksayit") and [Gnopernicus]("http://linuxappfinder.com/package/gnopernicus") are two graphical options.

---

### Post by Hendrixski on 2007-02-27
Sweet, this is very cool stuff.  I'll check it out after work.  Thanks for posting!

---

### Post by mikeym on 2007-02-27
This is aparently the command for KDE and Festival

```

dcop klipper klipper getClipboardContents | fmt | festival --tts

```

I don't have KDE though - so I'm still wondering how to do this in XFce (my WM or GNome)

---

### Post by Samhain13 on 2008-01-29
Thanks OP. :)

---

