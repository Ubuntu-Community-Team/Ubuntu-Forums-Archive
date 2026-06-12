---
title: "Waiter, bring me more WINE"
date: 2007-06-07
forum: General Help
---

### Post by the lemming on 2007-06-07
Could somebody please tell me how to use Wine with ubuntu?

Cheers

---

### Post by steeleyuk on 2007-06-07
At the terminal type:

wine /path/to/program

For example, if ABC.EXE is in my home directory I would type:

wine /home/andrew/ABC.EXE

Edit: you should also be able to type wine --help to view a list of associated commands (I don't have Wine installed at the moment so this may not be true)

---

### Post by Martje_001 on 2007-06-07
Install it (follow the instructions on winehq.com) and just right-click on a file and choose 'Wine Windows Emulator'.

---

### Post by AZzKikR on 2007-06-07
> **Martje_001 said:**
> Install it (follow the instructions on winehq.com) and just right-click on a file and choose 'Wine Windows Emulator'.

What's wrong with
```
sudo apt-get install wine
```
?

---

### Post by Nythain on 2007-06-07
the version in the ubuntu repos isnt updated as much as the official winehq repos, if at all even... while it runs stable and fine, it wont get updated for a loooooooooong time... like its probably sitting at 32 or 33 while they are already up to like 38 now

---

### Post by the lemming on 2007-06-07
> **Nythain said:**
>  like its probably sitting at 32 or 33 while they are already up to like 38 now



Does this mean that I have a copy of wine with ubuntu?

I have a couple more questions.

I've read that I can create a short-cut for the desktop to get an application to work.  Could somebody please explain how I can do this?

My next question is, do I need to have the windows application placed within the ubuntu filing system or can I hunt around in my Windows XP partition for it?

Cheers

---

### Post by FuturePilot on 2007-06-07
> **Nythain said:**
> the version in the ubuntu repos isnt updated as much as the official winehq repos, if at all even... while it runs stable and fine, it wont get updated for a loooooooooong time... like its probably sitting at 32 or 33 while they are already up to like 38 now

That's why you add the official Wine repo.

---

### Post by the lemming on 2007-06-13
I've just installed wine by following the instructions from the WINE HQ web site.  From there I followed the instructions in the magazine Linux Format July edition to install a simple windows application called Notepad.

I managed to install the program by following the notepad.exe.

Now here is the hard part, for me, I can't find where Wine or Notepad are hidden within my filing structure.  I was told to look in my Home folder and my Root folder.  Unfortunately all I can find is a couple of icons in the home folder and nothing in Root.

Am I missing something because of my inexperience?

---

### Post by wjhildreth on 2007-06-13
I have very little experience with WINE but the files WINE uses by default are in your home folder and hidden. You need to turn on hidden folders with CTRL-H I think. But all the emulated folder system is found under that folder. Should be something like:

/home/<username>/.wine/

HTH,

Joe

---

### Post by Citizin on 2007-06-13
When I had wine, I just installed WINE, set it up, then double clicked on windows executables, seemed to work for me, but if you want a easier/better approach, try Crossover.

---

### Post by Amazona aestiva on 2007-06-13
Hi I'm new here, but I installed Wine,and it is WORKING now.

So, see this: [http://ubuntuforums.org/showthread.php?t=149585](http://ubuntuforums.org/showthread.php?t=149585)

I hope This will help!;)

---

