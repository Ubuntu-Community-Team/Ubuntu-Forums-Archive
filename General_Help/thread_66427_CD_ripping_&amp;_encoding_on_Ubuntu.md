---
title: "CD ripping &amp; encoding on Ubuntu"
date: 2005-09-17
forum: General Help
---

### Post by miniml on 2005-09-17
Hello all, just installed Ubuntu yesterday and it's great, I'm amazed! :)

Now, I come from Windows world mostly, so I'm used to excellent CD ripping and encoding tools. But here, I can't find good solution for my needs.

I want to rip, encode, tag and apply replaygain in one solution/program/script. I would prefer latest musepack as the encoder. I added all Ubuntu's repositories and Rarewares repository. I found Crip, but it only rips to Ogg Vorbis or FLAC, and Ogg Vorbis is 1.0.1 version! wich is from 2003 me thinks. I can't find latest vorbis. I think that Musepack is latest but crip doesn't support it (or mp3, only vorbis and flac).

So, in short I want this:

Rip to Musepack (with tag and album replaygain) *
Have mpd as pseudo music server
Play it with gmpc or ncmpc

* Well, It could be mp3 or vorbis too.

So, I'm all open for suggestions. I tried grip and abcde.

What do you use for ripping, encoding etc... On Win, I used EAC and foobar2000. Thanks in advance...

---

### Post by jmrush on 2005-09-17
Try Sound juicer and consider you'll need lame encoder package to rip to mp3.
Luck

---

### Post by fordfan753 on 2005-09-18
[QUOTE=][/QUOTE]
 I always use abcde (a better cd encoder) it's a good program, I don't know if it can do all that you want, but it is a great command line ripper/encoder.

---

### Post by MetalMusicAddict on 2005-09-18
I use Audiograbber through WINE.  I get an error every once in a while but all the rips have turned fine. I belive you can get EAC to work also. Ive been lookin for the same solutions but havnt found any that are perfect for me. Grip looks promising.

I used [THIS](http://www.mrbass.org/linux/ubuntu/dvdshrink/) great guide for DVD Decrypter then just installed Audiograbber. Try the guide then install EAC.

When it mentions enabling DMA I used this command **sudo hdparm -d1 /dev/cdrom**. But you have to make sure **/dev/cdrom** is correct for you. I have a DVD drive but **/dev/cdrom** is how its specified.

;)

---

### Post by miniml on 2005-09-18
No, it must be native and fast, console app is a plus.

I will use Crip, but I only need vorbis-tools 1.1.1, can anyone help me?

---

### Post by paxmark on 2005-10-02
On abcde - I fiugred out to use -t to get the track labeled.

But I keep getting abr instead of vbr.  I cannot get --vbr-new to work.

any hints

---

### Post by xmixahlx on 2005-10-11
i posted a howto for musepack+grip at hydrogenaudio.org (old post)
[http://www.hydrogenaudio.org/forums/index.php?showtopic=1927&st=80&p=120640&#entry120640](http://www.hydrogenaudio.org/forums/index.php?showtopic=1927&st=80&p=120640&#entry120640)

you can get replaygain using RareWares/Debian (musepack-replaygain)

also, k3b (for gui) does a great job at ripping.


later

---

