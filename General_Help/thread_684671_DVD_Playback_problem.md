---
title: "DVD Playback problem"
date: 2008-02-01
forum: General Help
---

### Post by Lloydus on 2008-02-01
Hi Everyone,

I am fairly new to Ubuntu and have been unable to get DVD playback on my Ubuntu 7.10 notebook.

I have followed a number of tutorials and always end up with the same error in totem!

"The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I am sure I have installed libdvdcss whilst following other tutorials, if anyone could advise me how to check what I am missing I would really appreciate it!

Thanks

Lloydus

---

### Post by jolx on 2008-02-01
[http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html]("http://geekybits.blogspot.com/2007/10/playing-encrypted-dvds-in-ubuntu-710.html")
This worked for me

---

### Post by Lloydus on 2008-02-01
Hi Jolx,

Thanks for the link.

I followed the tutorial, but unfortunately totem is still giving me the same error. 

I have saved the responses I got from the two commands whilst in the terminal, maybe they will help to identify what is wrong. 

Thanks for your help.

Lloydus

---

### Post by mc4man on 2008-02-01
maybe you should try vlc player. It's much easier to troubleshoot. There are only 3 things it needs to play back dvd's - libdvdcss2, libdvdread3, libdvdnav4. With those in place if you don't get playback you can look at other issues. (regions, title of dvd, model of dvd drive, ect.)

---

### Post by Lloydus on 2008-02-02
Hi Mc4Man,

Thanks for your response,

I have checked and I appear to have libdvdnav4 installed, heres the code from the terminal.

lloyd@lloyd-laptop:~$ sudo apt-get install liba52-0.7.4 libdvdcss2 libdvdnav4 libdvdread3

Reading package lists... Done

Building dependency tree       

Reading state information... Done

liba52-0.7.4 is already the newest version.

liba52-0.7.4 set to manual installed.

libdvdcss2 is already the newest version.

libdvdnav4 is already the newest version.

libdvdnav4 set to manual installed.

libdvdread3 is already the newest version.

0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

lloyd@lloyd-laptop:~$ 


Unfortunately still no luck on the DVD front. Nothing appears to have changed, each of the programs give me the same errors they usually do.

I am using a number of palyers including vlc player, hopefully I will eventually get it working!

thanks

Lloydus

---

### Post by SpiderGorilla on 2008-02-02
Are you on an i386 or AMD64 system?

---

### Post by Lloydus on 2008-02-02
my notebook is AMD and has a AMD 64 X2 sticker on it.

I hope this helps

Lloydus

---

### Post by SpiderGorilla on 2008-02-02
Okay then. AMD64 installations for anything is more difficult than other systems. I'm checking into a theory I have. I think this may get you set up, but I'm going to need a few hours to test it.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

That last bit there I may have followed.

*EDIT*

Okay. I'm not 100% certain on this, because I did this a few days ago, but I'm pretty sure I went into Synaptic Package Manager (System > Administration > Synaptic Package Manager) and did a search for restricted and added the package:

ubuntu-restricted-extras

*tiny edit* Also, I'm pretty sure I ran the bit about:

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_amd64.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_amd64.deb

What that is is basically a set of files that allows you to playback non-free formats such as MP3 and such. I also made sure I went to Medibuntu and I ran the portion about Adding the Repositories before downloading:

[http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/non-free-codecs_1.1_amd64.deb](http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/non-free-codecs_1.1_amd64.deb)

And installing that. I know that was the very very last thing I did there. I also have all the libdvd stuff that you've already got. Since the .DEB file is linked to fron the Medibuntu page I linked to, that may work for you. And there are many other black, dark, bleak things I may have done. I'm not entirely positive. I may also have installed something from MPlayer's site. I really wish I was more help, but I had a ton of issues with this myself and when it finally worked, I tried not to question it.

---

### Post by Lloydus on 2008-02-02
Hi Spider,

Thanks for the link.

Should I try out some of that code for amd64 in the terminal? or do want to try out your theory first?

Just so you know I have an amd64 system, but I am running the 32 bit ubuntu OS. I dont know weather that will make any difference - but i thought you should know! 

Thanks

Lloydus

---

### Post by SpiderGorilla on 2008-02-02
Hmm. Actually that makes a ton of difference, really. You should be able to do this with the 32bit codecs instead. Mine is a pure AMD64 system. Uhm, just install the ubuntu-restricted-extras and then try that. If it doesn't work, follow the 32-bit codec installation on the Medibuntu page I linked you. DVD playback on 32bit is supposed to be easier than the dark things you have to do to get it to run on AMD64.

*EDIT* For clarity, the 32-bit instructions are the i386 instructions. I can't guarantee that'll work for you, though. I haven't tried it on a 32-bit system yet. Y'know, I'm supposed to go get my Mom's laptop working and it's i386. Want to wait a minute while I try it out on that first?

---

### Post by Lloydus on 2008-02-02
Hiya,

Ok im glad i mentioned it.

I have allready got the restricted extras installed from when I first got my laptop at xmas.

Thanks for helping out with all this - I would be happy to wait for you to try your mums laptop out first.

I have been trying to get this working on and off since xmas - so whats a little longer going to matter!!

Thanks

---

### Post by SpiderGorilla on 2008-02-02
Okay, I got it working with VLC media player only. But that's the best. It's really janky, but that's probably because the laptop I'm using isn't the best for this sort of thing.

Here's what I did:

1st - I made sure I had the ubuntu-restricted-extras -- From getting MP3s to play, this was already present. Totem had downloaded this itself earlier.

2nd - I ran the following:

wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

Yeah, i already had that libdvdcss stuff, but I figured "why not?"

3rd - I ran this:

wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb

4th and finally, i ran this:

[http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/non-free-codecs_1.1_i386.deb](http://packages.medibuntu.org/pool/non-free/n/non-free-codecs/non-free-codecs_1.1_i386.deb)

It seemed to work right after that. But it ONLY worked right in VLC. MPlayer attempted it, but was really really bad off and gave me a fatal error. Totem (aka Movie Player) just kept giving me the same dredge about unsupported codecs.

I'm sorry I can't get it to expand the links. If you follow into the Medibuntu page and scroll down to the following parts in order:

Playing Encrypted DVDs // With Individual Packages
Playing Non-Native Formats // With Individual Packages

You'll get the links you need to copy.

---

### Post by Lloydus on 2008-02-02
Thanks for all this.

I cant get it to work at the moment, but perhaps with a litlle tweaking I will get their in the end.

I will let you know how i get on.

Regards

Lloydus

---

### Post by SpiderGorilla on 2008-02-02
Wish I could be more help. As I said, it's a dark thing to get DVDs to run on Ubuntu right now. You could try the Medibuntu thing from the top down and see if that works.

---

### Post by mc4man on 2008-02-02
you have everything you need installed to playback a _dvd_ with vlc. try putting a disk in and then opening vlc from the terminal. When the interface pops up choose to play from disc and if it doesn't work post the output from the terminal

---

### Post by ubuntu-freak on 2008-02-02
Just incase this helps you or whoever, try part 1 & 3 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Nathan

---

