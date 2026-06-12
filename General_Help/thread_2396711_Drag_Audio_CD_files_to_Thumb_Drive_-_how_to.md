---
title: "Drag Audio CD files to Thumb Drive - how to"
date: 2018-07-19
forum: General Help
---

### Post by mark bower on 2018-07-19
Using Ubuntu 16.04 with Classic Gnome Desktop

How can I drag all the displayed audio CD .wav files to a jump drive?  I can copy them individually to the jump drive, but the shift lt-click selection method and ctrl-A method to select all files does not work.

Thanks
mark

---

### Post by Holger_Gehrke on 2018-07-19
Three ideas:

[LIST=1]
[*]Does ctrl-click to selectively mark multiple files work ? (more work than shift-click or ctrl-a, but still better than dragging the files one by one)
[*]Try a different file manager. I'm using XUbuntu and don't have that problem in Thunar.
[*]Get a real cd-ripper program. Not only do these programs use all kinds of tricks to ensure that the cd is read correctly (audio CDs have very little protection against misreading them ...) they can also convert the tracks on the fly to some format that takes less space (flac for lossless or one of the lossy formats if you can't hear much of a difference and care more about saved space than the approval of audiophiles), look up metadata like artist, album title, track title(s)  ...
[/LIST]

Holger

---

### Post by mark bower on 2018-07-19
Nope.  Ctrl-click to selectively mark multiple files one after another still will only allow selecting one file at a time.  My file manager is of course, Nautilus.  

I guess I'll continue with the "impediment", however, your suggestion of converting the .wav to a more compressed format is a good idea.  I notice that an audio file downloaded from the internet might be about 8 times smaller or there abouts than the file taken from my CDs.  Also, based on the relatively large number of CDs I have, I may cave in and go to ripping in a batch process to a more compressed format per your suggestion.  Anyhow, no surprise, I plan to get all audio CDs onto HD as I have with our DVDs.

Additional:  After posting above, I installed Thunar from the cmd line and it worked like a charm, v. simple.  It didn't seem to show in synaptic thus went to cmd line and executed from cmd line.

Thanks
mark

---

### Post by Yellow Pasque on 2018-07-19
Yeah, if you're going to bother with physically putting the CD into your computer, you might as well rip.

---

### Post by mark bower on 2018-07-19
Actually, after reading on line re .wav .mp3 .flac, I should probably just go with mp3 and use something like Handbrake for conversion.  I have severe hearing loss.  However, I tired a sample .flac download and to my surprise its plays just fine on my PC with no additional needed software issues.  Flac might be nice as there are statements that it compresses to about 60% of .wav, if I have it right.

---

### Post by Holger_Gehrke on 2018-07-20
If you're suffering from hearing loss, you should be very careful using mp3 compression or any lossy audio format.These formats all use psycho-acoustic modelling to hide the errors produced by lossy encoding and those models assume normal hearing. In a double blind test done several years ago by the German magazine c't the only person consistently able to tell high quality mp3 from CD-audio was somebody suffering from a somewhat frequency selective hearing loss. He couldn't hear the frequencies playing more loudly well enough to hide the softly playing frequencies with errors. 

Holger

---

### Post by Yellow Pasque on 2018-07-20
What format is "best" depends on how much space you have for your music collection, what devices/OS's you're going to use to, how picky you are about audio quality, etc.

If you have the space for FLAC, it's a good choice, especially if you're just going to use Linux and/or Windows 10. (macOS supports FLAC to some degree, but not in iTunes for some reason.) If you want to use FLAC on a mobile device, you can always transcode without needlessly losing audio quality. This is what I do for my old mp3 player to save space.

If you want more compression, it's a little murkier. For medium or higher bitrates (128k-320k), I think most people would struggle to hear a difference between AAC vs. mp3 vs. vorbis.
If you're an Apple/ipod/itunes fan, it's AAC if you want to make life easy.
If you want max compatibility, mp3 is a good choice, especially now that the patents have expired.
I personally prefer ogg/vorbis because I find the tagging system less quirky than mp3's ID3 tags

For low bitrates (< 128k)or streaming, I guess most people use HE-AAC or opus nowadays.

> Actually, after reading on line re .wav .mp3 .flac, I should probably just go with mp3 and use something like Handbrake for conversion.

I personally like abcde or Audex for ripping.  A good overview of mp3/lame options here: [https://trac.ffmpeg.org/wiki/Encode/MP3](https://trac.ffmpeg.org/wiki/Encode/MP3)
I would use -V 2 or even -V 1 unless I was really squeezed for space.

---

### Post by mark bower on 2018-07-20
@ Holger_Gehrke

Very interesting.  It is a good thing the bulk of music sound is in the relatively lower frequencies.  However, I realize I miss a lot, but I do love music.  You might be surprised that I have no hearing above 2500Hz.  This of course means I have great trouble with intercepting speech.  What my hearing aids do is to grab the frequencies between 2500Hz and 4,000Hz, compress them a bit, then shift them down into my hearing range as an "overlay", maybe in range 1500Hz to 4,000Hz.  I am amazed how I hear sounds, like coffee maker beep, or Lipo battery charger beeps when my hearing aids are in; nothing when my hearing aids are out!  And the letter "S" gets severely distorted in both speech and music via the hearing aids.

But, again I love music, and to an extent, I am not cognizant of all that I am missing.
Thanks
mark

@ Temüjin
Since .flac seems to present no problems on equip I currently have, I believe my first compression trials will be with .flac.  I was delighted(although I realize very poor sound quality) that I could plug a SanDisk with a .flac file into my Sony DVD player, and play the .flac through the TV.  I had first played the .flac on my PC.  I am not a high end user; I only use the "old school" flip phone, so not have to be concerned with compression for newer devices.  I anticipate buying a stereo receiver that has usb input.  Although I am not going to purchase a stereo receiver with a usb port in the immediate future, I believe I will go to the local store and verify that what is being sold will accept .flac.  If not, then might have to keep .mp3 on the rear burner.
Thanks
mark

---

### Post by mark bower on 2018-07-24
o.k.
Intermittently there still is some sort of problem displaying the CD .wav files, but with some"playing around" I get to them.

More importantly, I am pleased to be compressing/converting the files to about 57% of original .wav size to .flac format.  I am using ultra simple Sound Converter to do this.  I didn't know what compression level to use, so chose "Better" given the options below?
Less (faster)
Default
Better(slower)

Thanks again for the suggestion to convert .wav to .flac.

mark

---

### Post by ajgreeny on 2018-07-24
One problem with simply copying the audio files on a CD in the file manager is that they are un-named as Track 1.wav etc etc.

If you use a ripper (I also like abcde) it gives all tracks their real name, album title, and performer, and tags them properly if you use the correct config file; a much better way to do this in my experience.

---

### Post by mark bower on 2018-07-24
@ajgreeny
I have just learned, as I understand it, that audio CDs do not mount like a data CD.  That still does not explain why sporadically the files will display and I can just copy them as .wav files.  And you are absolutely correct, all that is seen is numbered .wav files.  However, as consistently suggested here and other posts I read, it makes good sense to rip the audio CD to the desired format.

Now I am on my way.  I hit on Asunder which is available from the Ubuntu Software Center.  Very simple to use as a ripper/converter - feeling a bit guilty, almost too easy to use.  The app easily detects the audio CD and displays file names. In preferences I chose to export as .flac with intermediate compression.  And this is the method (ripping vs starting out with copying) that all commentators have tried to softly shoe me into doing.
Tx all
mark

---

### Post by Yellow Pasque on 2018-07-24
> I didn't know what compression level to use, so chose "Better" given the options below?
Less (faster)
Default
Better(slower)

The 'flac' encoder has 9 compression levels, so I'm not sure what numbers those settings correspond to in Sound Converter (or what Asunder gives you options for). Normally, I would say, "Use the slowest you can tolerate." However, with flac, the very highest compression levels can add significant time to the rip with little or no gain in compression. I think most people would do well with default/medium settings when ripping to FLAC.

---

### Post by HermanAB on 2018-07-25
Even easier, is to simply dump all your CDs in the recycling bin and use Streamtuner (which includes streamripper) and rediscover listening to the 'radio' again.

---

### Post by mark bower on 2018-07-25
Asunder uses a slider to obtain compression levels 0 to 8, or 9 levels as you say.  So I looked at differences in file sizes versus compression level.  For extremes and mid-point compression I get .flac file size as percentage of .wav file as follows:  0 = 70%, 4= 62%, 8 = 60%.  So as you have pointed out, the compression is not linear, ie, less relative compression takes place with higher compression level selection.  Unexplained, the time for ripping/converting/compressing 2 files with Asunder remained the same regardless of level of compression selected.  This process was done with no error checking - oops.

So under the "Advanced" Tab, I unchecked the "Faster ripping(no error correction) option so that error checking would be effected.  The process time for 26 .wav files at an average of 23.38MB per file takes about 10 minutes to convert to .flac files at maximum compression.  Works for me.

---

