---
title: "supported video files (other than ogg)"
date: 2008-06-18
forum: General Help
---

### Post by miningold on 2008-06-18
i am new to ubuntu and i dont have it installed yet but i am getting my files prepared and i want to know which video files are automatically supported by ubuntu, other than ogg and if you demand that i switch to ogg give a good program that will convert mp4 files to ogg. i currently have prism video converter (along with switch sound converter) which can convert between .avi .wmv .asf .mpg .3gp .mp4 .mov and .flv

i am hoping one of those file types is supported, otherwise i need another program(for windows) that will convert .mp4 to .ogg theora

Thanks

---

### Post by sdennie on 2008-06-18
I think nearly every format is supported.  The first time you try to open a particular type of media file it will tell you that you need to install codecs to read it and then give you the option to install those codecs.

---

### Post by tech0007 on 2008-06-18
There's a plethora of formats supported by Ubuntu. check this link: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by cariboo on 2008-06-18
I would suggest you install the ubuntu-restricted-extras. This will install all the codecs you need including flash and java. The only thing it won't install are the files to play DVDs. To install the programs needed to play dvds go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and follow the instructions, then open System-Adminsitration-->Synaptic and search for libdvdcss2 and libdvdread3 install those two files and you will be ready to watch dvds too.

Jim

---

### Post by miningold on 2008-06-18
thanks, but i still want to get my video files into ogg if i can, i just cant seem to find a windows app that doesnt cost any money and converts mp4 to ogg theora

---

### Post by manfer on 2008-06-18
I have tried now VideoLan (VLC Media Player) and it worked. It is a player, an streaming player and server, an encoder too and multiplatform.

In the test a made (mp4 to ogg with vlc), it doubled the file size. Changing the encoders maybe this could be improved or maybe not. I think mp4 is a good video compression format (good quality with small file size).

A good free encoder in windows is virtual dub but i don't know if it can read mp4 format and make an ogg encoding.

---

### Post by manfer on 2008-06-18
Reading better I saw you look for theora-ogg. Well I installed the necessary library on ubuntu and VLC stills do the job with that codec.

Looking on theora download page you have a link to some encoders on many different systems. For windows you can try MediaCoder or SUPER (Simplified Universal Player Encoder & Renderer) from eRightSoft.

---

