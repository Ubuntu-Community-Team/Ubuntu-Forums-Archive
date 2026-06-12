---
title: "Amarok+iPod problems"
date: 2006-10-14
forum: General Help
---

### Post by alecjw on 2006-10-14
[SobStoryWhichDoesNotNeedToBeRead]
I like to keep my audio files on my computer in the OGG format, but my iPod can't play OGGs, so for a long while I kept all of my files in MP3 and AAC, which gives you terrible audio quality through speakers and therefore is only good with earphones. Then I found out that Amarok can store my fiels in OGG and convert them to MP3 as I transferred them to my iPod.
[/SobStoryWhichDoesNotNeedToBeRead]

I now have my songs in OGG, but when I transfer them, it does not convert them. I found out that I needed to change some settings. I couldn't cahnge these settings (see the attached screenshot), because the checkbox was greyed out. 

Any ideas as to how I can fix this?

---

### Post by alecjw on 2006-10-14
Bump?

---

### Post by alecjw on 2006-10-14
Hello?

---

### Post by PriceChild on 2006-10-14
I would also like to know how to fix this...

I think it has to do with Amarok not being compiled with the correct options...

---

### Post by alecjw on 2006-10-15
Anyone?:(
I've also heard that we have to recompile it with some sort of iPod module, but I don't know how.

---

### Post by Bigbluecat on 2006-10-15
This may not be the way you want to do it but you could try Rock box on your ipod:

[http://www.rockbox.org/](http://www.rockbox.org/)

This would replace you Apple fimrware with Rockbox and allow your ipod to play Ogg format files.

I have not used this myself to "buyer beware".

If it is not to your liking you can always replace re-install the apple firmware with the ipod udater.

---

### Post by alecjw on 2006-10-15
> **Bigbluecat said:**
> This may not be the way you want to do it but you could try Rock box on your ipod:

[http://www.rockbox.org/](http://www.rockbox.org/)

This would replace you Apple fimrware with Rockbox and allow your ipod to play Ogg format files.

I have not used this myself to "buyer beware".

If it is not to your liking you can always replace re-install the apple firmware with the ipod udater.

I've tried rockbox before, but it just crashes the iPod, but i'll try it again - I've got noting to lose.

---

### Post by alecjw on 2006-10-15
I've installed the rockbox bootloader and put the rockbox files on the drive,but it boots the iPod firmware. Any ideas?

---

### Post by stevu on 2006-10-29
AFAIK you have to press some key sequence at boot to activate rockbox. I'm gonna try next week and let you know.

---

### Post by PriceChild on 2006-10-29
Ok i've got further on this one...

You need to go into amarok, and manage plugins.

Add one named something like "transKode"

also a ```
sudo apt-get install lame
```Then you should be able to use the greyed out checkboxes to get it to transcode if needed.

When i transfer music though atm it still freezes... at least it realises it needs to transcode though.

---

### Post by alecjw on 2006-10-31
> **PriceChild said:**
> Ok i've got further on this one...

You need to go into amarok, and manage plugins.

Add one named something like "transKode"

also a ```
sudo apt-get install lame
```Then you should be able to use the greyed out checkboxes to get it to transcode if needed.

When i transfer music though atm it still freezes... at least it realises it needs to transcode though.

I managed to work this out a few weeks ago. It's becuase you need to install vorbistools so that you can decode ogg (not included by default...)

Go into the transKode settings manager and tell it to guess where the programs are. When you try to transfer songs, it doesn't freeze - it's converting them although the status bar stays at 0%. It usually transcodes very slowly, about 4X speed so it will take quite a while. I hope this helps.

---

### Post by PriceChild on 2006-10-31
> **alecjw said:**
> I managed to work this out a few weeks ago. It's becuase you need to install vorbistools so that you can decode ogg (not included by default...)

Go into the transKode settings manager and tell it to guess where the programs are. When you try to transfer songs, it doesn't freeze - it's converting them although the status bar stays at 0%. It usually transcodes very slowly, about 4X speed so it will take quite a while. I hope this helps.Thanks for that... I just wasn't patient enough then :)

Pricey

---

### Post by mlissner on 2007-02-27
Yeah, I second that about it being VERY slow, but it does seem to work.

As for vorbistools, it's not in the usual repos. Not sure how to feel about that considering that it works...or seems to anyway.

---

### Post by djbon2112 on 2008-03-22
> **PriceChild said:**
> You need to go into amarok, and manage plugins.

Can someone please tell me where this menu is? I'm using Amarok 1.4.8 and I can't find ANYTHING about plugins anywhere in it. I've installed lame and TransKode and the option is for me is still grayed out (like the OP).

Ubuntu 7.10 Gutsy.

---

### Post by adrimaxi on 2008-04-28
> **djbon2112 said:**
> Can someone please tell me where this menu is? I'm using Amarok 1.4.8 and I can't find ANYTHING about plugins anywhere in it. I've installed lame and TransKode and the option is for me is still grayed out (like the OP).

Did you get any clue ?

---

### Post by djbon2112 on 2008-04-30
> **adrimaxi said:**
> Did you get any clue ?

No I just gave up. But if anyone knows, please speak up!

---

### Post by colinrgodsey on 2008-07-22
im also kinda stuck with this problem

---

