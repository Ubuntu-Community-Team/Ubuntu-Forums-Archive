---
title: "Detecting Drive"
date: 2006-10-16
forum: General Help
---

### Post by Kulluminatii on 2006-10-16
Most of the questions on my previous post, 'Getting WINE to Install' have been answered, but a new problem has arisen. I have sucessfully installed both Wine and the game I wanted, Emperor: Rise of the Middle Kingdom. Now the problem is on running it. This is what I type in.

```
wine /home/vinny/.wine/Emperor.exe
```
It does work, but a error pops up which says "No disc in drive", when their was the game disc in it. So I pop out the disc, put it back in, and it gives me the same error.

Any way to solve this problem?

---

### Post by foxmulder881 on 2006-10-16
You normally have the mount the disc first and then launch .exe.

---

### Post by Kulluminatii on 2006-10-16
Say what now? Yes im a noob.....

---

### Post by foxmulder881 on 2006-10-16
I don't use WINE myself so I can't really step you through it. But as far as I know you have to mount the game disc first so that it recognizes that it's even in the drive. You would have had to mount it when you installed it wouldn't you?

---

### Post by Kulluminatii on 2006-10-16
Err...sure? I can tell you that the game and wine were installed successfully. I used 'winecfg' and made sure that the D: drive was pointed to cdrom0. What do you mean by mount the game disc?

---

### Post by foxmulder881 on 2006-10-16
When you make sure that WINE is pointing to the correct CD-ROM, that's called mounting.

---

### Post by Kulluminatii on 2006-10-16
Oh, okay. Well im pretty sure...well not 100% sure...that WINE is pointing to cdrom0.

---

### Post by Kulluminatii on 2006-10-16
Any way to make sure that WINE is pointing to cdrom0?

---

### Post by foxmulder881 on 2006-10-16
It should tell you in the WINE config screen.

---

### Post by Kulluminatii on 2006-10-16
ok thanks, im sure it is, cant understand why it gives me that error though.

---

### Post by 3rdalbum on 2006-10-16
I had the same problem with another game. The only advice I was given was:

1. Try the subscription version of Cedega, which has support for some copy protection schemes.
2. Find a crack or a cracked version of the game that doesn't require a CD.

---

### Post by Kulluminatii on 2006-10-16
1. Dont you pay monthly for that?

2. Find a cracked version...well..it will be kinda legal for me since I own the originial disc but 1). The pc that runs Ubuntu does not have any internet connection to it, I transferred files through cd's and 2). I have dial up on my pc, kinda would be slow and long to download a 300+MB game.

Hoping to find other options...but im losing hope=\

---

### Post by Cene on 2006-10-16
You should try to find the crack for the game. Often cracks are just a size of few mb's and they just replace the original .exe or some other file.

---

### Post by Kulluminatii on 2006-10-16
Oh where oh where can those little cracks be?;)

---

### Post by Kulluminatii on 2006-10-16
Well after downloading the crack and replacing the originial Emperor.exe and Emperoredit.exe files with the one given nothing really happened.

I type in 'wine /home/vinny/.wine/Emperor.exe' and basically all I hear is some sound, then nothing. It doesnt even give me the 'no disc is inserted in the drive' error, it just does..nothing.

Anything I am doing wrong?

---

### Post by foxmulder881 on 2006-10-16
This is the exact reason I gave up trying to play games through WINE. I found it simply wasn't worth the efforts.

---

### Post by Cene on 2006-10-16
Does it print anything in terminal where you run it?

I just checked the WineHQ's AppDB and if [this](http://appdb.winehq.org/appview.php?iVersionId=3989&iTestingId=4095) is the game you meant.. Well, see for yourself. Platinum rating, nothing said about the need for crack, so are you really sure the cd is mounted correctly? :D

---

### Post by foxmulder881 on 2006-10-16
> **Cene said:**
> So are you really sure the cd is mounted correctly? :D

That's what I've suspected all along!! :-k

---

### Post by Kulluminatii on 2006-10-16
Well before I start doing this](*,) 


Lets see, im kinda sure the cd is mounted correctly..then again...I dont know what the hell you are talking about...so, maybe thats the problem?:D 

One thing that I have noticed though is that their are two versions of the crack, one is 1.01.1 or something like that and the other is 1.0. I downloaded the first one, I think the second one MIGHT work.

Now looking at that page that you linked Cene...I feel like ](*,), so now a new question, how do you mount the cd drive correctly? I just typed 'winecfg' and the box that popped up, I went to drivers, and pointed :D to 'cdrom0', their is also the :C and :E, but when I point :C to cdrom0, I get errors when I run winecfg again.

So basically, how do I make sure I mounted it correctly, because Im still not sure what you guys are talking:mrgreen: 

Well, I'll download the other crack, and wait for your guys response..AND think for once:-k

---

### Post by foxmulder881 on 2006-10-16
A crack isn't the solution.

---

### Post by Kulluminatii on 2006-10-16
Ok, so the only problem I need to solve is mounting the cd correctly?

So..how would I go about doing that?

---

### Post by Kulluminatii on 2006-10-16
Well, I typed in 'winecfg' and when the box popped up, I selected the Drives tab, and clicked on autodetect. I just now noticed that when I do this, it gives this error in the terminal.

err:winecfg:load_drives GettoWineInformation() for 'D:\' failed, setting serial to 0

I do not know what the following error means, but what I am guessing is that the D: drive is not the one I should point to cdrom0.

---

### Post by foxmulder881 on 2006-10-16
Do you have another optical drive you can try it in?

---

### Post by Kulluminatii on 2006-10-16
Optical drive? Thats the drives listed on 'winecfg' right? Wow i feel stupid, anyways, here they are.

C: ../drive_c

D: /media/cdrom0

E: /

H: /home/vinny

Now that I think of it, would E: be the right drive?

---

### Post by foxmulder881 on 2006-10-16
> **Kulluminatii said:**
> Optical drive? Thats the drives listed on 'winecfg' right? Wow i feel stupid, anyways, here they are.

C: ../drive_c

D: /media/cdrom0

E: /

H: /home/vinny

Now that I think of it, would E: be the right drive?

Optical drive is a CD/DVD drive. On your system I suspect that C: and H: are your hard drives. And D: and E: are your optical drives. If you have 2 optical drives, try the other one. eg. E: drive.

---

### Post by Kulluminatii on 2006-10-16
Ok, thanks, I have a feeling this might work...and I learned something!

---

### Post by Kulluminatii on 2006-10-16
Well, I tried it, the same thing happened as with :D. I tried the regular files first, and it gave me the message 'no disc in drive', then I tried with the crack files, nothing happened.

Maybe I do need the 1.0 crack files?

---

### Post by Kulluminatii on 2006-10-17
Should I go ahead and burn the 1.0 crack file and see if it works or is their something I am doing wrong?

---

### Post by Kulluminatii on 2006-10-17
Ok now I am totally lost. I burned the 1.0 crack...did the SAME EXACT thin as the other one. I dont know what I am doing to mount the cd wrongly...then again...I don't know exactly how to mount anything..but I've already tried for 4 days, why not try some more.

---

### Post by foxmulder881 on 2006-10-17
Perhaps it simply doesn't want to work. Not all games work with WINE.

---

### Post by Kulluminatii on 2006-10-17
That would suck to find out after all this, but it showed it worked  on the WineHQ's AppDB, their MUST be something I am doing wrong.

---

### Post by cssutto on 2006-10-17
If I use file browser to go to a file that I want to open with wine, right click on it and it asked what to use to open and I select wine, is that not an acceptable way to run wine?

CSSJR

---

### Post by Kulluminatii on 2006-10-17
Hmm....im so hopeless right now, but that just might work, thanks for the tip.

---

### Post by Kulluminatii on 2006-10-17
> **cssutto said:**
> If I use file browser to go to a file that I want to open with wine, right click on it and it asked what to use to open and I select wine, is that not an acceptable way to run wine?

CSSJR

Well when I right clicked on "Emperor.exe", I did not see wine on the list of programs I had, I am sure though that WINE is installed.](*,)

---

### Post by al_sharpe on 2006-10-18
Hello Kulluminatii:

I was just wondering if you cannot see the cdrom drive how you installed
the game in wine.
In Ubuntu the cdrom drive should be auto detected just as in windows
when you insert the disc, and an icon appears on the desktop.
wine /media/cdrom0/setup.exe (will install program)

then in terminal cd (DOS speak for Change Directory) to directory where emperor.exe is and 
type wine emperor
Should work!

Hope this helps
Al

---

### Post by foxmulder881 on 2006-10-18
> **Kulluminatii said:**
> I did not see wine on the list of programs I had, I am sure though that WINE is installed.](*,)

Sounds like you haven't installed WINE correctly. Or you've uninstalled somehow.

---

### Post by Kulluminatii on 2006-10-18
To answer al_sharpe, when I put in the game disc, a cd icon does pop up and I can open it and everything.

Thanks for the tip though al, I will be sure to try it out.

Now to what foxmulder881 stated. Im not sure how I couldve messed up installing it, the .wine directory is where it was supposed to be.

---

### Post by foxmulder881 on 2006-10-19
You've got me stumped Kulluminatii. Have you Googled the game to make sure others have got it working on WINE? As I mentioned, not all games will work using WINE and Linux.

---

### Post by Kulluminatii on 2006-10-19
> **foxmulder881 said:**
> You've got me stumped Kulluminatii. Have you Googled the game to make sure others have got it working on WINE? As I mentioned, not all games will work using WINE and Linux.

Well, at least I got something accomplished:p 

Anyways, I just noticed that the version of WINE the people at WineHQ used to test Emperor was a older version than the one I have, maybe..just maybe, the older one might work?

Sound possible?

---

### Post by foxmulder881 on 2006-10-19
> **Kulluminatii said:**
> Sound possible?

It might work. If you can be bothered, give it a shot.

---

### Post by Kulluminatii on 2006-10-19
Sure why not, not like I have many other options left.

---

