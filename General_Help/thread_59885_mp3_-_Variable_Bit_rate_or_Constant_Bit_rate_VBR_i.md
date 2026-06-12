---
title: "mp3 - Variable Bit rate or Constant Bit rate? VBR in Sound juicer?"
date: 2005-08-25
forum: General Help
---

### Post by byen on 2005-08-25
hey fellas,
About to convert my 100 cd collection into mp3 for backup. I was wondering if you guys have any real time preference between a CBR and a VBR mp3 format? I googled it but found mixed results.... The bottom line being that VBR is better but on all formats except mp3..is this true?

Im using GRIP  right now...which is burning it into VBR mp3 by default..is there anyway I can make this happen in Sound Juicer? 

Any help/sugg would be greatly appretiated.

---

### Post by masteryoda on 2005-08-25
VBR does give you some good results and if you have a good sound system.... you will notice the difference, But I personally don't go for them... because,
1) Not all players support it... especially the old ones.
2) They tend to have larger size.
3) If you are not concerned with size but want quality... go for higher bit rate in CBR than for VBR.

---

### Post by byen on 2005-08-25
lol....nice avatar.....

- Well... ive ripped an mp3 into both a VBR and a CBR and ive really not seen huge diff. between the two...i have a kick ass panasonic pro-headset and it is one of the best...and frankly....its pretty much the same....(except for a point where there were many instruments playing at the same time...then....VBR seemed to catch up..atleast i think it did)..but bottom line i see no diff... Are ogg's any better,...ive read great reviews about VBR oggs..but havnt got a chance yet....what do you guys think?? 

other serious Q i have is with Sound Juicer...can i do a VBR mp3 on it....i seem to be only gettin CBR files.
thanks.

---

### Post by woedend on 2005-08-25
[QUOTE=byen]lol....nice avatar.....

- Well... ive ripped an mp3 into both a VBR and a CBR and ive really not seen huge diff. between the two...i have a kick ass panasonic pro-headset and it is one of the best...and frankly....its pretty much the same....(except for a point where there were many instruments playing at the same time...then....VBR seemed to catch up..atleast i think it did)..but bottom line i see no diff... Are ogg's any better,...ive read great reviews about VBR oggs..but havnt got a chance yet....what do you guys think?? 

other serious Q i have is with Sound Juicer...can i do a VBR mp3 on it....i seem to be only gettin CBR files.
thanks.[/QUOTE]
 i haven't played around with Ogg in a couple years, but back then it wasn't as good as MP3 in the higher bitrates, but did well where it was designed for, the super low bitrates.  VBR should always be smaller...that is the point in it.  If you have unlimited space...I'd just rip 320 kbps CBR.   If space is a factor, I'd set it high of 256 low of 128 VBR.  If space is very limited, high 128 low 96...but 96 is where you begin to hear huge dropoffs in quality.

---

### Post by byen on 2005-08-25
> VBR should always be smaller...that is the point in it. If you have unlimited space...I'd just rip 320 kbps CBR. If space is a factor, I'd set it high of 256 low of 128 VBR. If space is very limited, high 128 low 96...but 96 is where you begin to hear huge dropoffs in quality.

so... 320CBR is better than a 320/256 VBR ? i see some sense in this....considering the space.. as ive seen that a 320CBR takes a lot less space than a 320 VBR....hmmm Frankly with the copyright crap starting off with mp3s I really wanted to switch to ogg but my brother has an Xp (games) and an Ipod...so gotta stick with mp3...

---

### Post by woedend on 2005-08-25
im not sure WHY a 320 vbr file would be larger than a 320 Cbr.  maybe we use different encoders or your vbr quality rating is too high and its encoding at a higher bitrate.  320 kbps is 320 kbps...in theory they would and should be the same size..  The ones i've always used(lame based) would use vbr to get a high value and a low value.  When the sound needed a higher bitrate, it would use the highest.  when it needed lower(simple sounds, pauses) it would use the low bit rate.  In songs with a lot of pauses or simple drum beats(intro to ironman?) there would be no reason to have 320 kbps.

---

### Post by byen on 2005-08-25
so the general suggestion is to go for a higher bit rate CBR than to a Higher bit rate VBR?..i want quality.... have a good headphone and a good system....final suggs?

---

### Post by woedend on 2005-08-25
[QUOTE=byen]so the general suggestion is to go for a higher bit rate CBR than to a Higher bit rate VBR?..i want quality.... have a good headphone and a good system....final suggs?[/QUOTE]
 best quality run a CBR at 320... vbr is for spacesaving/quality mix.  think of the cbr as a fire breathing v8 engine that runs on all 8 at all times, and vbr as that chevy 4-6-8 crap  that runs 8 cylinders at take off, 6 during accell, and 4 while cruiising.  Saves gas, but not going to be running optimally at all times.  In theory you shouldn't see a difference but if youre anal about it run 320 cbr

---

### Post by byen on 2005-08-25
lol...nice comparision....LOL.... got the point mate..thanks! CBR it is!

---

### Post by bionnaki on 2005-08-26
LAME alt preset standard is what you want.

--alt-preset standard %s %d would be the commandline.

except no substitute - lame is the encoder you want. and aps is
an excellent rip for mp3 (lame is VBR which, in my opinion, is better than CBR).

---

### Post by doclivingston on 2005-08-26
A VBR mp3 which has average bitrate X shouldn't be worse/larger than a CBR mp3 with bitrate X - unless a) your encoder is crap (you should be using LAME), or b) you're using setting that make it do that.


When you set minimum or maximum bitrates you're artificially constraining the VBR encoder, which will make files larger or worse quality - it's much better to set the average bitrate to what you want (for gstreamer-lame use vbr-mean-bitrate=160 or whatever).

There is virtually no reason to ever use a minimum bitrate, unless you are streaming VBR mp3s over the net, and the software requires a minimum bitrate. The two reasons I can think of for using a maximum bitrate are:
 * You are streaming them over the net, and want a fixed cap on how much bandwidth it uses.
 * You have a portable mp3 player, which can't go above a certain rate.

If you are just encoding for use on a computer, you shouldn't need a maximum bitrate - just set the average, and let the encoder do it's job.


Ogg vorbis encoding works similarly, but you don't even set the average bitrate directly (you can, but it makes decreases quality/increases filesize). When encoding you give it a "quality" parameter (from -1 to 10) which determines how much quality loss you are willing to deal with - and hence approximately the bitrate.
 * Quality 0 is good for voice, although you'd be much better to use a voice specific codec such as speex
 * Quality 3 is slightly worse quality than a 128kbs CBR mp3, with a nominal bitrate of about 96kbs
 * Quality 4 is approximately the same quality as a 160kbs CBR mp3, and a nominal bitrate of 128kbs
 * Quality 5 is the default and has a average bitrate of about 150kbs, with quality similar to a 200kbs CBR mp3.
 * Qualities 6-10 are better, but have increasing file sizes (obviously).


If you want the best quality use FLAC, it's a lossless codec (so you don't lose *any* quality), but it's files are around 600-800kbs.

---

### Post by joker on 2005-08-31
Lame can be run CBR, VBR, or ABR, take a look at the man page for it to see all the options, it can be configured to create your MP3 any way you like it.  Except no substitute!

VBR is a trade off between file size and quality.  If you don't like the file size of a 320CBR file, you can use VBR to reduce the size significantly without sacrificing as much sound quality as using a lower bit rate CBR setting.  For example, the into and trailing silence will be encoded at 64 kbps while a busy part of the song is encoded at 320 kbps, the end result will average 225 kbps but be of higher quality than a 225 kbps CBR file.  It only uses the higher bit rate when necessary.

I personally use --preset-extreme with lame, which is 192 kbps VBR IIRC, my files usually average between 200 and 250 kbps, it depends on the music.  I compared these to the origional CD on my stereo and can not tell the difference , so I figure they are good enough for me.  my setup is slightly above average, but nothing spectacular.  I suggest you do a similar comparison to see what you like.  In tha audio world its always good to get advice but in the end you have to trust your own ears.

---

### Post by duan on 2005-08-31
depends on what kind of music you listen to. 
If it is mostly rock 'n roll CBR is good(i.e. music with a fairly regular and constant mix of a broad spread of instruments and plenty of human voice). mp3 was designed around what most people hear and like.
music with lots of variations with some solo and isolated instruments going to the foreground might dissapoint you or waste space for simpler bits with cbr and I've always found vbr better for this, with things like bagpipes vbr shoots up and you get a nicer reproduction. weird.
If you're heavy into jazz maybe mp3 is sacriledge to start with.

---

