---
title: "Good audio application wanted"
date: 2006-08-23
forum: General Help
---

### Post by muz1 on 2006-08-23
Hey.
I wanted to pick people brains out there and present a situation hoping someone knows a possible solution.

I have a heap of long audio files that are in excess of half an hour each. I want to be able to cut them down to chapters that I can set manually as the chapter lengths would vary. Then to be able to click a button and save them all in one hit with track numbers. You can do it in Sound Forge but that is for windows and  I can't afford it.

Does anyone know a package for Ubuntu 6.06 that can do this? I have looked at audacity which looks pretty good but it didn't seem to support the chapter mode.

Thanks in advance.
Cheers
muz

---

### Post by cleentrax on 2006-08-23
I don't know of any Linux program that can do this, though there may be some command-line tool. 

I still do all of my audio production in Windows. Most of the Linux audio apps are either buggy or lacking in features.

---

### Post by TLE on 2006-08-23
Ok I searched around and I'm pretty sure I can help you but I need a little more info,
What format are the files in, if mp3 do you want to keep the id3 tag
excactly what kind of naming convention do you want to use ?

---

### Post by jonzep on 2006-08-23
how about breaking up the files into seperate mp3s with audacity and then putting them all in a matroska container using something like mkvmerge? not sure if that's exactly what you want but it would allow you to have the "chapter" effect.

---

### Post by muz1 on 2006-08-28
> **TLE said:**
> Ok I searched around and I'm pretty sure I can help you but I need a little more info,
What format are the files in, if mp3 do you want to keep the id3 tag
excactly what kind of naming convention do you want to use ?

Hey there TLE. 
I really appreciate your help.
Firstly, the program is not for me. I am currently trying to bring a friend to Ubuntu who has reservations. I know that if I could show him something like the audio tool, he would jump in. As far as I know, ID3 tags and that sort of thing are not important. Basically he burns to mp3 but hewants to be able to cut up the really long tracks into shorter ones to skip through tracks as you would on a cd. I believe that the initial tracks would be mp3 or something like that but I know that linux has heaps of audio conversion tools so I cannot see that as being a problem.

Hopefully that gives you some more insight and once again, thanks for your help. Hope I can return the favour someday.
Cheers
muz

---

### Post by muz1 on 2006-08-28
> **jonzep said:**
> how about breaking up the files into seperate mp3s with audacity and then putting them all in a matroska container using something like mkvmerge? not sure if that's exactly what you want but it would allow you to have the "chapter" effect.

Hey Jonzep.
I guess that I want to try and avoid having to cut up all the tracks individually. As in set the markers and then save and its saves all the tracks at the same time.

If you know of anything, that would be awesome.
Cheers
muz

---

### Post by IYY on 2006-08-28
I googled, and came up with this: [http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)

It seems to have a GUI version, and a command line version as well. So if the GUI doesn't have the exact automation you want, you can very easily make a shell script to do it (if you need help, this site is a good place to ask, or you can just ask me).

---

### Post by TLE on 2006-08-28
> **muz1 said:**
> I believe that the initial tracks would be mp3 or something like that but I know that linux has heaps of audio conversion tools so I cannot see that as being a problem.

I didn't think so either. But as it turnes out since mp3 is a proprietary format it actually isn't as well supported as the rest. But there are alternatives both for mp3 and for all the rest. 

Assuming for the time being that it is mp3. I found 2 different kinds of tools worth mentioning.

One of them is a program which has GUI and allows for multiple cut-points, save them all at once and userchoise naming conventions. BUT it is a beta, and is not in repositories. I tried it out and.. well it works but you can tell that it's not all done yet.

The second one is a commandline tool. It's basically just a command where you feed it the input filename, output filename and the cut-in and cut out. Fast and reliable. Now of course if you think he would be frightened away by the commandline, it is perhaps not the best idea. But it can VERY easily be made into and "easy to use" script, and I would be more then happy to write it. So if we did that he would be required to open the script file and enter cut points manually and then execute it with the input filename ad input.

Personally I would really recommemend the second option, as I feel that if you want to show of the abilities of Ubuntu I would rahter show something unfamiliar than something which has not yet been finished.

Let me know what you think. Regards TLE

---

### Post by TLE on 2006-08-28
> **IYY said:**
> I googled, and came up with this: [http://mp3splt.sourceforge.net/mp3splt_page/home.php](http://mp3splt.sourceforge.net/mp3splt_page/home.php)

mp3splt is the GUI option I was talking about. Nice digging IVY

---

### Post by muz1 on 2006-08-29
Hey TLE.
Thanks again for your extremely helpful research and suggestions. The mp3 split program is perfect and it will do exactly what is needed.
I really appreciate your help.
Thanks once again.
Propz.
muz

---

### Post by TLE on 2006-08-29
> **muz1 said:**
> Hey TLE.
Thanks again for your extremely helpful research and suggestions. The mp3 split program is perfect and it will do exactly what is needed.
I really appreciate your help.
Thanks once again.
Propz.
muz

Your very welcome, I'll split the honor with IVY.

---

