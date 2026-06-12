---
title: "mp3 re-encode"
date: 2006-07-02
forum: General Help
---

### Post by OrganicPanda on 2006-07-02
hey peoples,

i am looking for a program or script or something that will batch re-encode my existing mp3's as they are all different bitrates and i would like to convert them down to 128kbs so i can save space and throw more on my zen, anybody know of / use something capible of this?

cheers,
panda

---

### Post by marcozs on 2006-07-02
Hello,

try GNORMALIZE ... you can find it at [http://www.gnomefiles.org/app.php?soft_id=736](http://www.gnomefiles.org/app.php?soft_id=736) but I haven't managed to find a deb for ubuntu yet...

---

### Post by Soarer on 2006-07-02
Gnormalize works well. You can download the rpm package & then use alien to make it a deb package, then install. Worked for me & I'm no expert.

---

### Post by OrganicPanda on 2006-07-06
ok chers guys, using alien that installed fine ...pitty it doesn't work atall lol.
trying to re-encode a directory of mp3's i get:

```

/files/mp3s/Albums/00000/1.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/2.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/3.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/4.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/5.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/6.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/7.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/1.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.

/files/mp3s/Albums/00000/1.mp3: Can't call method "title" on an undefined value at /usr/bin/gnormalize line 9724.
Use of uninitialized value in abs at /usr/bin/gnormalize line 6920.
*** unhandled exception in callback:
***   Can't open /home/panda/Desktop/temp_encode/1.mp3: No such file or directory, stopped at /usr/bin/gnormalize line 10005.
***  ignoring at /usr/bin/gnormalize line 13838.
panda@panda-desktop:~/Desktop$   

```

so i guess that program is determined not to work, any other solutions?

---

### Post by 3rdalbum on 2006-07-06
From memory, I think Lame can re-encode MP3s at different bitrates. It's in repositories - just check the Lame man page for usage.

---

### Post by jamesford on 2006-07-06
try this lame script:
for x in [ `ls -1 *.mp3` ]; do nice lame -a -b 64 --resample 44.1 $x m64-${x}; done

this will convert everyjting in the fiolder the command was issued into 64 kbps mono. just change the 64 into 128 or whatever. i dont recall if mono is the -a or -b thing but u will probably find out if u do 'man lame', im too lazy to do it myself ;)
you can probably leave out --resample 44.1

---

### Post by JoWilly on 2006-07-06
You will find gnormalize for dapper in this repo :
[URL="http://asher256-repository.tuxfamily.org"]
http://asher256-repository.tuxfamily.org[/URL]

---

### Post by Soarer on 2006-07-06
It looks like gnormalize has some dependencies missing for what you want to do. If you hit the 'show' button about 1/2 way down on the left, it opens a window for terminal-type output at the bottom of the app. Anything missing (mine can't find madplay or faac for example) are displayed, but it won't fall over as it can't know what sort of conversion you want until you tell it. So I can't play mp3s with gnormalize, as I don't have madplay, but I don't try to so it doesn't matter. It will do CD to flac though, and ape to flac & flac to ogg as all those are installed.

---

### Post by OrganicPanda on 2006-07-09
excellent cheers man i guess i was missing a whole bunch of things, namely:

```

gnormalize 0.49 

Can´t find "mac" in executable path. The output can´t be "ape" format.
Can´t find "flac" in executable path. The output can´t be "flac" format.
Can´t find "faac" in executable path. The output can´t be "mp4" format.
Can´t find "metaflac" in executable path. 
Can´t find "normalize" in executable path. The wav files can´t be normalized.
Can´t find "faad" in executable path. The input can´t be "mp4" format.

 None cddb info, install the perl module "CDDB_get".
 No mp3 info, install the perl module "MP3::Info".

```

this is the thing i find difficult about linux applications, the names listed above .... i cant find anywhere, apt-get doesn't find them and the words themselves are far too generic to search the web, any help please?

---

### Post by jnev on 2006-07-09
you do realize that reencoding your music will give you severe quality loss right?

---

### Post by Soarer on 2006-07-09
If you do a search in Synaptic (System>Administration>Synaptic Package Manager) in Name & Description for each of those you should find them.

For example "normalize" is actually "normalize-audio" I believe.
"faac" is a package in Synaptic (Multiverse)
"flac" is a package 
"metaflac" is in "flac"

etc.

Not sure about the perl scripts, you may need to look a bit further for those.

---

### Post by OrganicPanda on 2006-07-09
cheers soarer i guess using the gui isn't all bad

@jnev: i beleive it will only reduce the quality of the music to the quality i choose (freq. and kbps), i see no point in my 320kbps audio files taking up so much space when, to me, 128kbps sounds pretty much the same ... well thats how it is for mp3's in my opinion although i might convert them to .ogg for a change, i've heard good things

---

