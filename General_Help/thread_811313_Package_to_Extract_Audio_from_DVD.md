---
title: "Package to Extract Audio from DVD?"
date: 2008-05-29
forum: General Help
---

### Post by ramjet_1953 on 2008-05-29
Does anyone know if there is a Linux package that can extract the audio tracks from a DVD?

I have a couple of concert DVD's with song tracks on them that I would like to extract.

I know that you can use the command line for menplayer to extract chapters, but you can only extract one at a time to get individual tracks, otherwise you just get one continuous wav file.

I have had success with running CAS's Windows program DVD Audio Extractor under WINE with good success.
It gives the option to extract and encode on the fly in ogg, MP3, wav, FLAC or CD image and Cue Sheet.

This is exactly what I am after, but would prefer a native Linux application.

Regards,
Roger :cool:

---

### Post by andrew.46 on 2008-05-29
Hi,

Not sure if I will be repeating what you already know:

> **ramjet_1953 said:**
> I know that you can use the command line for menplayer to extract chapters, but you can only extract one at a time to get individual tracks, otherwise you just get one continuous wav file.

MPlayer will extract *complete* audio tracks from a DVD and yes this is traditionally done to wav format. Usually the tracks can be seen:

```
$ mplayer dvd:// -identify -frames 0 | grep "audio stream"
```

and then extracted, in this example aid 128:

```
$ mplayer -aid 128 dvd:// -vc null -vo null -ao pcm:fast:waveheader:file=song_track.wav 
```

and then converted:

```
$ oggenc -q 6 song_track.wav -o song_track.ogg
```

Is this what you mean or do I have the wrong end of the stick and you have already tried and discarded this method :-).

             Andrew

---

### Post by ramjet_1953 on 2008-05-29
Hi, Andrew!

Thanks for the reply.
Yes, I know how to do it with the mplayer command line, but it is rather laborious when you have about 60 separate song files to extract and encode.

That's why I mentioned the Windows program DVD Audio Extractor as it separates all of the tracks, and encodes them automatically as a batch. The only additional thing that you need to do is to add the individual song title tags.

It looks like I will have to persist with WINE.

Thanks again.

Regards,
Roger :cool:

---

