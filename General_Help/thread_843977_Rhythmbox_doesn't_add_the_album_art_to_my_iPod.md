---
title: "Rhythmbox doesn't add the album art to my iPod"
date: 2008-06-29
forum: General Help
---

### Post by Faethin on 2008-06-29
Greetings

I'm a complete newbie to Ubuntu and its common apps (I just recently made the leap from Windows to Linux). 

I just got Rhythmbox in place of iTunes, since I've been told there's no really great way of running iTunes from Ubuntu. Rhythmbox so far has behaved perfectly except for one detail: When I click and drag music from my library into my iPod the music is added to the device without its cover art, that is, the iPod doesn't display it, even though when play a song in Rhythmbox from the iPod the cover art is perfectly visible.

Help, please? I'd be very grateful.

---

### Post by LMP900 on 2008-06-29
Unfortunately, Rhythmbox doesn't use the cover art embedded into the file. It fetches it from an online source and stores it in: ~/.gnome2/rhythmbox/covers/

You'll have to embed the album art yourself using iTunes (if you still have access to a Windows or OS X computer) or an application like EasyTAG in order to view the album art on your iPod.

**[Edit]** After some searching, I ran across these:

[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/7342](https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/7342)
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/117583](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/117583)

---

### Post by Faethin on 2008-06-29
Thank you for your reply.

I downloaded EasyTag and was able to embed the album art and edit other tags. However, when I add the album to my library in Rhythmbox and then onto my iPod, the album art is still missing. I think it has to do with the way Rhythmbox adds the tracks to the device, whether they have embedded cover art or not. Could this be it?

---

### Post by LMP900 on 2008-06-30
This might be too obvious, but do you have album art enabled on the iPod? The only other thing I can suggest is trying another media player such as Banshee to transfer your files into your iPod.

Good luck!

---

### Post by Faethin on 2008-07-01
Thank you for your help!

I followed through one of the links you provided, which led me to this:

[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/117583](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/117583)

This patch fixed the issue for me. I'd like to spread the word, but I haven't got a clue on where to start.

Anyway, thanks again for you time.

---

### Post by srf21c on 2008-09-25
Here are the steps to apply the patch.

download the patch at the bottom of [this web page]("http://bugzilla.gnome.org/show_bug.cgi?id=529873#c5").  The link is called "proposed patch"

or you can right click and save the direct link [here]("http://bugzilla.gnome.org/attachment.cgi?id=109946") 

save the patch file as: art-metadata.patch in your homedir

Please be mindful that the patch installation instructions at the first link have an error.  They tell you to run the patch command one directory level too high.   Below is a corrected sequence.

```
sudo cp art-metadata.patch /usr/lib/rhythmbox/plugins/
cd /usr/lib/rhythmbox/plugins/ ; sudo patch -p0 < art-metadata.patch 

```

---

### Post by Xizorbg on 2008-09-26
Hey All-

Applied the patch - no go.  Even did a reboot.  Anyone know?

Thanks,
X

---

### Post by crinno on 2008-09-26
Same here. Patch applied, removed everything from iPod and reinstalled.
Still no cover art.:mad:

---

### Post by Judge P on 2008-09-28
I've got an ipod 30g video, rhythmbox 0.11.5, format set to mp3. 

I ran the patch, and now the album art is displayed fine.
I know this doesn't help 'crinno' or 'Xizorbg' but the patch is worth a go, it seems to work for some of us.

(Thanks to 'Faethin' for posting the thread)

Thanks

Robert

---

