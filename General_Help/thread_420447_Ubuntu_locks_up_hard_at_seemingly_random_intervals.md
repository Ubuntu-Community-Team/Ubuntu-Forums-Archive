---
title: "Ubuntu locks up hard at seemingly random intervals"
date: 2007-04-23
forum: General Help
---

### Post by marsh24601 on 2007-04-23
(I posted this in the Apple Intel forum first, because I was dumb and didn't see the whole "Apple" thing.  Sooo, trying again...)

Okay; I've been trying to make a go with Ubuntu as my primary system since Dapper Drake.  I just upgraded to Feisty, and I've still encountered my issue, so I'm desperate.  I'm actually... ASKING FOR HELP!

For reasons I can't determine, Ubuntu will lock up hard every so often.  When it does this, it does the following:

* The screen (usually) goes kablooey.  Most often, it will exhibit a checkerboard pattern of interference... it's approximately 80 "squares" by 80 "squares."  You can still see the screen in half the squares, but in the other alternate squares it's all distorted.
    -- Occasionally the screen will lock up in other weird patterns (for example, distortion along the right-hand side), and I believe at least once or twice it has done so with nothing otherwise wrong with the screen.

* The sound will usually turn into this awful screeching noise, sounding like a staticy squeaky tire.  This screeching happens even if I'm not playing any sound files.
    -- Occasionally the sound will loop whatever is playing most recently, if it locks up while playing a sound file.  In this case, it loops about a second or two, forever.</ul>

* The system is otherwise totally locked; no keyboard or mouse commands do anything, and I need to press the reset key.


Unfortunately, there doesn't seem to be any rhyme or reason for how it happens.

Most often, the biggest offender seems to be WINE.  If I'm working with Microsoft Office, it will occasionally lock up.  In particular, using the scroll wheel in the mouse is very "hit or miss."

However, it happens for other reasons.  For example, if I use the scroll wheel in gedit, it's locked up there.  It's happened when I'm burning a DVD and otherwise not doing anything else.  (This is rare.)

It also happens if I'm not doing <i>anything.</i>  For example, I have a directory that contains a lot of PDFs.  If it trolls that directory (presumably to load thumbnails), then it has locked up there, even if I'm away from the computer and happen to have kept that directory open.

I have removed the video card (a Radeon 700) and reverted to on-board video; I'm not certain, but I believe the screen looked differently when it locked up there.  The box was originally a Gateway 550GR (Intel 915G chipset, I810 video chipset), but all that pretty much remains of the original is the motherboard.  The only other item of note is an Audigy soundcard; everything else is an on-board component.

It doesn't happen consistently, but it does happen often if I'm doing something it doesn't like to do.  Ordinarily it locks up between once a day to once a week, depending on what I'm doing, but if I'm doing something it doesn't like, it can crash almost all the time.  For example, if I were to load up the offending PDF directory, it would probably crash; and one document in Office it <i>really</i> didn't like, achieving a near-100% crash rate.

I don't think it's a heat issue because it happens even when it's not under load (although it seems to happen more often if the system is straining).  In addition, I never had any problems with lockups when I was using XP, and I was running it under XP in an incredibly warm apartment.

Anyway, if anyone could give any help, I'd be eternally grateful.  This one problem is all that keeps me from being totally in love with Ubuntu.

Thanks in advance!

---

