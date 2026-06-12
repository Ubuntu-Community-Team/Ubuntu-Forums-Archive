---
title: "How do I mount a ISO to play a game?"
date: 2007-05-21
forum: General Help
---

### Post by EvenStevens on 2007-05-21
I've got Worms Armageddon working in Ubuntu with my game disc (using Wine), but I'd like to be able to rip an ISO of the CD and use that instead.
I've taken an ISO from the CD and mounted it in the normal way with the sudo mount command...but when I try to start the game it says "please insert game CD".

---

### Post by blazercist on 2007-05-21
dude do "winecfg" in console and look under one of the tabs there should be an option to map drives... simply map to the mounted iso.

---

### Post by EvenStevens on 2007-05-21
Well it's mapped to like...4 drives right now including the ISO.

Still, without the Cd in the tray it doesn't work. :|

---

### Post by Nehvrook on 2007-05-21
I've managed to mount game .iso's so that it believed the CD was in, but I used some custom mount scripts. Maybe using the method in this thread will help you
[http://ubuntuforums.org/showthread.php?t=87369&highlight=mount+script](http://ubuntuforums.org/showthread.php?t=87369&highlight=mount+script)

---

### Post by ghell on 2007-05-21
I have not tried this in Ubuntu but can't you just do the regular mount -r -t iso9660 worms.iso /media/wormscd (sudo it if needed) ?

---

### Post by EvenStevens on 2007-05-21
Thanks for the replies guys but none of it seems to be working.
It still complains about needing the CD :-(

---

### Post by Nehvrook on 2007-05-21
When you mount the image is it showing up in /media/ ?

Oh and this might be a long shot, but back on Windows I used a program called Deamon Tools to mount images for this purpous. Maybe you could get that running under wine and see if that works?

Sorry I can't offer more helpful advice

EDIT: Just a thought, how are you trying to launch the game? Are you using a terminal command or going to the directory and clicking the .exe? If so what is the path to the .exe you're clicking?

---

### Post by EvenStevens on 2007-05-21
Yeah, the drive is showing up in media and under my "places" list.

I too use Daemon tools with Windows but no dice on Linux.

I launch it by typing the command into the console.

---

### Post by Nehvrook on 2007-05-21
What command exactly do you type please?

---

### Post by EvenStevens on 2007-05-21
wine wa.exe

(wa.exe being my worms executable)

I sometimes use wine wa.exe /NOINTRO to be different :P

---

### Post by Nehvrook on 2007-05-21
Confusing me a little here. You just type "wine wa.exe" rather than "wine </path/to/exe/>wa.exe"?

I'm just thinking if you're using the .exe in your install folder (For example /home/<user>/Worms/wa.exe) you should try running the .exe on the CD (or at least your image of the CD which should be mounted just like a CD)(So it would be "/media/<CDname>/wa.exe") and that might help you.

If this still doesn't help try using the command
"cd <path/to/exe>"
and then just
"wa.exe"

---

### Post by EvenStevens on 2007-05-22
Yes, I do type wine blah blah wa.exe essentially but that's irrelevant I feel.

And there is no .exe on the CD.
It's merely a way of gaining autheticity for you to run the game.

---

### Post by Nehvrook on 2007-05-22
It's not irrelevant, I need to know which .exe you were running.

Did you try what I suggested? I find it very hard to believe there isn't a wa.exe or setup.exe on the CD, either of them should at least bring up a launcher for the game.

---

### Post by EvenStevens on 2007-05-22
There is a setup but it launches the actual setup, not the game itself.

---

### Post by EvenStevens on 2007-05-23
Bumping this.

---

### Post by juan_suave on 2007-10-23
I've had the same problems with the WA cd being needed to play. I think what happens is the game check the serial number for the CD drive, which is specific for the worms cd.  If you look in the 'Drives' tab in winecfg and click advanced, look at the bottom when you have the real cd drive selected, you'll see the number.  I've tried to assign that serial to my mounted iso file, but it won't take.  Maybe a NOCD crack will help you (oops, I didn't just say that).

MY question, if you don't mind me hijacking the thread, is why did my upgrade to Gutsy break ******* WORMS!!  I was so happy when I found my old worms cd, but only a few weeks later I decided to upgrade.  I think the problem is with ddraw.dll (same problem wine has had before with worms, diablo, etc).  For some reason wine won't use the hacked ddraw.dll file, or something else is wrong.  Does anyone have a fix for this yet?

To summarize:  Worms Armageddon, Ubuntu Gutsy, wine 0.9.47, hacked ddraw.dll.. how can I put these things together and destroy small pink worms with awesome weapons?  I promise 5$ and an eCookie to whoever can help me.  :D

---

### Post by UK-Wobbie on 2007-10-23
> **EvenStevens said:**
> I've got Worms Armageddon working in Ubuntu with my game disc (using Wine), but I'd like to be able to rip an ISO of the CD and use that instead.
I've taken an ISO from the CD and mounted it in the normal way with the sudo mount command...but when I try to start the game it says "please insert game CD".

Why not have a go using AcetoneISO2 that can mount data CDs and DVDs!
[http://www.acetoneteam.org/central.html](http://www.acetoneteam.org/central.html)

---

### Post by silentrhythm on 2007-10-23
sounds like this is what you were looking for...

sudo mkdir /media/cdimage
sudo mount -o loop myfile.iso /media/cdimage

from the ubuntu community documentation, at
[https://help.ubuntu.com/community/MountIso?highlight=%28mount%29](https://help.ubuntu.com/community/MountIso?highlight=%28mount%29)

---

### Post by juan_suave on 2007-10-24
acetone doesn't work.  one nocd patch i found didn't work.  oh well.

---

### Post by Haak on 2007-10-25
Is there any chance of getting acetone for GNome in some next ubuntu release? How can I ask for that? 

I read the instructions and might be able to get this working (mounting with mount works for now). But this in a package with GUI would be cool.

---

### Post by Jose Catre-Vandis on 2007-10-27
Simple facts are, unless you make a perfect 1:1 copy of the original CD, the executable is not going to like it. Look for some alternate No-CDs (if you really do have the original game)
and test your 1:1 iso and no-cd patches out on plain windows (no Daemon Tools). if that works then it should work through Wine.

---

