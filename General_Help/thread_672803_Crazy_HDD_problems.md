---
title: "Crazy HDD problems"
date: 2008-01-20
forum: General Help
---

### Post by Astral Abraxas on 2008-01-20
I was originally dual booted as:

Ubuntu Feisty Fawn (32-bit)
Windows XP Home (64-bit)
Also a third partition for storing things (I forget it's format)

Anyways, I did some weird partitioning stuff with the ubuntu boot disc and then got it back installed and dual booted again. Things seemed fine...

I went to do a full format to windows or at least format my windows partition and now it won't boot ANY windows XP i use.

Type of errors over many different discs:

- pci.sys errors.
- no hard discs found

Now I got a new Windows XP home edition from a friend, and when I try to boot off it, I just get a black screen immediately and it does nothing. I left it for a few hours came back, still nothing but a black screen.

I'm right now fully formatted as Ubuntu Gutsy (64-bit I think)

I tried using wine to to start up xp discs setup.exe, and it does start up, but when I click on install windows xp it tries to go to full screen and crashes x.x.

Perhaps I should get some hard drive disc diagnostic utilities?

EDIT:

Important note, I was told by a friend that I could possibly have a boot sectorvirus?

"Boot sector viruses can also infect the MBR. The first PC virus in the wild was Brain, a boot sector virus that exhibited stealth techniques to avoid detection. Brain also changed the volume label of the disk drive."

That sounds very similar to how my windows was acting before I decided to pop in my windows xp disc to reformat it.

But now I can't even get my windows xp disc far enough to fixmbr.

---

### Post by der_joachim on 2008-01-20
If your friend was right, your problems may not be that big. You can easily restore your MBR by using a Ubuntu (or any other *buntu) desktop CD. Although it is quite old, I recommand reading [this HOWTO]("http://ubuntuforums.org/showthread.php?t=24113"). Use the method in the second post and make sure you know which partition is where.

---

