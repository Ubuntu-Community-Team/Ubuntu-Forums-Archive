---
title: "How to add FLAC encoding to K3B"
date: 2019-07-01
forum: General Help
---

### Post by Ralph L on 2019-07-01
Although I set the operating system field for this thread to Kubuntu (so Kubuntu users would look at it), I am really running Xubuntu 18.04 with K3B installed on it.  I am trying to rip some CDs, get the "cover" data added (to each song, I think), and convert the .wav files to FLAC files.  While K3B has a decoder for FLAC, I couldn't find an encoder for FLAC.  Obviously I need to have a FLAC encoder if I am to convert the .wav files to FLAC. Otherwise K3B seems to do just what I want done.  I found some web sites that discussed adding a FLAC encoder to K3B, but they were for suse, were somewhat old, and I could not make the suggestions work.

Anybody know how to add a FLAC encoder to K3B, and while we are at it, an ACC encoder as well in case I go the Apple direction?????

---

### Post by CatKiller on 2019-07-01
Apparently (I don't have an optical drive to test it properly)

```
sudo apt install flac
```

is the main step.

If K3b doesn't automatically pick that up, which reports on the forums here suggest it should, and my limited test did, then you can go to the plugins part of the settings and configure the "K3b External Audio Encoder" to use flac.

I have no idea about AAC.

---

### Post by oldfred on 2019-07-01
I have used Sound Juicer to rip my CDs.
In preferences are under output format are Ogg Vorbis & Flac among others.

I then have used Sound converter to convert my flac files to MP3 for my MP3 player. I have not done this for a while, but it seemed that using Sound Convert to extract & copy mp3 to player was faster than just the copy (once extracted) to mp3.

---

### Post by SeijiSensei on 2019-07-02
Yes, you need to install flac as CatKiller says to have it appear in the K3b helper list.

I know ffmpeg supports AAC. "ffmpeg -codecs | grep AAC" returns

```

DEA.L. aac     AAC (Advanced Audio Coding) (decoders: aac aac_fixed )

```
The D and E at the beginning of the line indicate support for decoding and encoding. A means its an audio codec, and L stands for "lossy."

---

### Post by Ralph L on 2019-07-02
CatKiller, oldfred:  Thank you for the responses.  I really appreciate it.  CatKiller you were right on; I needed to install flac, which I did with Synaptic.  Once I did that and went to k3b>Settings>Configure K3b>Plugins>K3b External Audio Encoder and clicked the Configure Box (the empty box on the right side), there was Flac listed as one of the encoders.  When I selected Tools>Rip Audio CD and then clicked the Start Ripping button, went to the Filetype box (in the new window that came up) and selected Flac, I ripped the CD to Flack files on my USB disk.  I had installed a bunch of stuff on my system before I installed flac, so I don't know that flac was the only thing that was needed by K3b.
My only concern now is that Flac files aren't really much of a compression from .wav files--.flac files were about 2/3 the size of the .wav files.  So I guess I will look at some lossy compression formats.  From what I have been reading ACC (apple) is one of the best.
Oldfred I thank you for the suggestions of Sound Juicer and Sound Converter.  I may end up using those if K3b presents me more problems.  

So if anybody knows how to to rip CDs to ACC format, please let me know....

---

### Post by SeijiSensei on 2019-07-02
You can't expect the files to be a lot smaller when using a "fully-lossless" encoder.

A**A**C is a proprietary codec.  The only open-source implementation I know of is in ffmpeg.

---

### Post by Ralph L on 2019-07-05
I installed Clementine as CatKiller suggested.  It DOES rip CDs to mp4 (aac).  However, I can't make it include any metadata. No album identification, no song names, no cover art.  When I play the Clementine ripped songs, with Clementine it won't find any of this stuff over the Internet.  Other aac rips that I did years ago include this stuff.  Probably I don't know how to use Clementine and the only documentation I can find is the Clementine wiki, and that's pretty limited.  CDs ripped by K3b to flac (and I think other formats) include the meta data and other information, like song lyrics, is found over the Internet.  But I can't get K3b to rip to aac.  I found some web sites from around 2007 that said the faac encoder had bugs and mentioned a patch.  But they also said that libfaac contained newer versions on the AAC encoder.  I installed faac, libfaac0, and libfaac-dev, but K3b still would not rip to AAC.  I guess it must not use faac or libfaac.  I didn't see either in K3b dependencies in synaptic.

Does anybody know how to set up Clementine to rip CDSs to include the metadata I listed above?????????

---

### Post by CatKiller on 2019-07-05
> **Ralph L said:**
> Does anybody know how to set up Clementine to rip CDSs to include the metadata I listed above?

Clementine not filling the tags with the metadata that it gets from Musicbrainz was [a bug that got fixed](https://github.com/clementine-player/Clementine/issues/6045). There haven't been any releases of Clementine since the fix was put in. Actually, there don't seem to have been any actual releases since 2016, although the codebase is still being updated.

If I were you, I would rip to FLAC - since it's lossless - and only transcode to something else when you find that you need to. That way your archived audio is of the highest quality and the destructive decisions in the future will be based on your actual requirements. Android's been able to play FLAC files for years and you can get 1 TB SD cards now. I think the time for storage of lossy audio formats is coming to an end.

---

### Post by Ralph L on 2019-07-09
Catkiller:  I was able to install Clementine from the latest source as described in [https://github.com/clementine-player/Clementine](https://github.com/clementine-player/Clementine) and [https://github.com/clementine-player...ng-from-Source](https://github.com/clementine-player...ng-from-Source) . This installed Clementine Version 1.3.1-610-ga0e478534, which fixed the no metadata problem.  Also, I think I will take your advice and rip everything into flac, then transcode it into acc mp4 if I need to.  I tried the transcode function in the compiled Clementine and it seemed to work fine bringing across most of the metadata, but not the album cover.  However, I was able to associate the album cover to the album using Cover Manager to fetch missing covers, then right-clicking on the album cover, doing Save cover to disk, and saving to the album folder. It save a .jpg of the cover into the album folder and somehow Clementine picked this up when playing the album.  This site contains further info on compilation: [https://ubuntuforums.org/showthread.php?t=2422498&p=13871796#post13871796](https://ubuntuforums.org/showthread.php?t=2422498&p=13871796#post13871796) .
Thank you again for your help.

---

### Post by Ralph L on 2019-07-18
After using Clementine for a while to rip my CD library I discovered that Clementine is very slow compared to K3B.  I decided to rip everything into flac so I can do the ripping with either Clementine or K3B.  Since K3B takes only half the time to rip a CD as Clementine, I am going to use that until I need AAC.  Also K3B automatically creates a folder ripped songs.  I have to do those things manually with Clementine (Maybe I don't know how to use Clementine correctly).  One problem with K3B:  I am writing to an ntfs file system (nobody else reads linux file formats), and K3B sometimes puts a ":" in the folder title.  This is a no-no for ntsf and Windows, so I am going to have to do some folder title editing.

I also tried Sound Juicer as Old Fred suggested.  However, like Clementine, I found Sound Juicer to take about twice the time to rip a CD as K3b took.  However, Sound Juicer will rip to AAC (m4a), and that is a real plus, since I could not get K3b to rip to AAC.

---

### Post by CatKiller on 2019-07-18
Most ripping programs have an option to exclude special characters from filenames because of Windows' crippled filesystems. I can't remember specifically that K3b does by default but, if it doesn't, and you can't find a plugin to do so, there are code snippets all over the Internet for doing the substitutions yourself when you copy the files to the NTFS partition. It's a solved problem.

---

