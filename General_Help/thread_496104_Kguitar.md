---
title: "Kguitar"
date: 2007-07-08
forum: General Help
---

### Post by zanazzi on 2007-07-08
i downloaded s few tabs from ultimate-guitar.com and they loaded in kguitar but they play with no sound :(

Im guessing that there is no sound files loaded for the instuments, can anyone tell me how to get the correct files please

---

### Post by AlexThomson_NZ on 2007-07-08
I assume KGuitar is the linux version of Guitar Pro?  In that case it should just use MIDI to output sound, so I am sure your .gp4 files are fine, but the KGuitar app/Sound system needs tweeking

---

### Post by AlexThomson_NZ on 2007-07-08
BTW- Did you know the MPAA is trying to shut down these sites, as apparently guitar tab are copyright violations!!!! ridiculous!

Dm F A# F (sue me!)  </rant> ;)

---

### Post by hikaricore on 2007-07-08
I think you mean RIAA.

But yea they are @#$% RIAA and because of other rediculous issues @%^$ the MPAA right up their silly bums.

---

### Post by AlexThomson_NZ on 2007-07-08
Actually I can't remember the acronym, but it is not the RIAA (or the MPAA- Motion Picture) this time- it's the Music Publishers Assoc..- no doubt with close ties to the RIAA/MPAA though...

---

### Post by zanazzi on 2007-07-09
> **AlexThomson_NZ said:**
> I assume KGuitar is the linux version of Guitar Pro?  In that case it should just use MIDI to output sound, so I am sure your .gp4 files are fine, but the KGuitar app/Sound system needs tweeking

the files r fine i downloaded the same tab and it played in guitar pro so the problem is definatly with kguitar.

i assumed there would be some plug in for hte sound files.

So how do i 'tweak' kguitar.

btw yes i could just go use guitar-pro but its in windows and, well, i'd rather keep my time in that pile ca#p to a min :D

off topic, do these big corps really think that they can win these battles, yes short term they might succeed in closing a few sites down or forcing them to charge a nominal joining fee, but some-one might like to give them an economics lesson about people power, and lets be honest the power of the net is far greater than any of these businesses, Linux has shown that, that if enough people with the same goal work together then even the largest of all companies, microsoft, cant stop it.

---

### Post by Topfs on 2007-07-09
Well from what I have gathered Ubuntu isn't shipped with a midi sound server, as windows does. And so you need a wavetable and there is one for free called timidity and It works with Songwrite on ubuntu and my machine.

I haven't tried kguitar since edgy but it were buggy back then :), could have been my machine to..

Well, for instructions to install timidity : 
[How to install timidity++]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MIDI_sound_server_.28Timidity.2B.2B.29")

---

### Post by zanazzi on 2007-07-09
ok i opened the execute file in terminal to have a peek and found the following in it;

```
&#65533;&#65533;&#65533;&#65533;U&#65533;&#65533;^B&#65533;&#65533;^A&#65533;^B&#65533;&#65533;u^P;^U&#65533;&^E^Ht^H&#65533;^T$&#65533;?&#65533;&#65533;&#65533;&#65533;e&#65533;[^_]&#65533;;^U&#65533;&^E^Ht&#65533;&#65533;^T$&#65533;'&#65533;&#65533;&#65533;&#46477;]&#1814;&#470;D$^D&#65533;^Q^E^H&#65533;^\$&#34189;r&#54669;&#65533;&#65533;&#65533;&#50573;^D&#470;D$^L^A^@^@^@&#470;D$^H^D'^E^H&#65533;\$^D&#65533;<$&#34189;&#65533;&#38285;&#65533;$
allowed us to make changes to tabdefs.tex^@^@^@A stringed instrument tabulature editor (with MIDI support via TSE3)^@^@^@^@^@^@^@^@^@^@^@^@T^$
*.kg|^@ (*.kg)
*.tab|^@ (*.tab)
*.mid|^@ (*.mid)
*.gp4|^@ (*.gp4)
*.gp3|^@ (*.gp3)
*.xml|^@ (*.xml)
*|^@Could not find KGuitar KPart! Check your installation!^@^@*.kg *.gp4 *.gp3 *.mid *.tab *.xml|^@saveURL(const KURL&)^@slotToggleMainTB()^@$
^E^HY
^E^HJ

```

any ideas anyone?!?!?

---

### Post by zanazzi on 2007-07-09
> **Topfs said:**
> Well from what I have gathered Ubuntu isn't shipped with a midi sound server, as windows does. And so you need a wavetable and there is one for free called timidity and It works with Songwrite on ubuntu and my machine.

I haven't tried kguitar since edgy but it were buggy back then :), could have been my machine to..

Well, for instructions to install timidity : 
[How to install timidity++]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_MIDI_sound_server_.28Timidity.2B.2B.29")

so does this play .4gp files?

---

### Post by Topfs on 2007-07-09
> **zanazzi said:**
> so does this play .4gp files?

Nono, all it does is play Midi, but kguitar uses midi so kguitar transformes gp4 -> midi.

But from your previous post it seems you haven't installed kguitar entierly correct, how did you do? sudo apt-get install kguitar?

---

### Post by zanazzi on 2007-07-09
yeah i just teh apt-get command

---

### Post by Topfs on 2007-07-09
Well that SHOULD be enough :)

Well try the timidity. If you can start kguitar but don't get sound and if you can open guitar pro files but don't get sound i'd think it is because you don't have timidity

---

### Post by zanazzi on 2007-07-09
ok that didn't work, and it might have screwed something else :S

i lost my internet but gaim still worked !!!!!!!!!

Now im not blaming timidity but. .... i removed it and now everything is ok.

---

### Post by Topfs on 2007-07-09
Auch, seems like a wierd thing to happen but glad you got it back online again :D

Well, it could be a difference between KDE and Gnome seeing you are a Kubuntu User, but then I have no clue.. Sorry, hoped to be a better help :)

---

### Post by bingobingo on 2007-10-23
I am also having problems with the sound on KGuitar. I tried DGuitar with the same files and it plays fine. So did anyone find a solution to it yet?

---

