---
title: "Unable to watch youtube"
date: 2016-11-20
forum: General Help
---

### Post by srodocker on 2016-11-20
Hello,

So my desktop recently crashed and so im using my toughbook all the time now.  Well since i've built it up awhile ago its always be unable to watch youtube as it restarts everytime.  Doesnt matter if the video is embedded or not.  I searched on here for a solution for the problem but only one I saw was to switch operating systems to oprea.  I currently use chrome as thats what on my phones and tabelets.

Any help would be greatly appreciated. Im very new with linux so bare with me.  My system is a cf30 with a 1tb HD and maxed out ram.  Is there a way to check like on windows where you can check you system performance.  

Thanks
Scott

---

### Post by QIII on 2016-11-20
Hello!

Do you really man "switch operating systems" or change browsers?

---

### Post by srodocker on 2016-11-21
Yes change browserrs lol.  Between kids and wife interupting took awhile to type out the original post and made some mistakes heh

---

### Post by irongolem0982 on 2016-11-22
So just to clarify it is running Ubuntu right? What version? and also to clarify does the computer restart or just the youtube video?

open terminal (control + alt + T) and type:
```
google-chrome --disable-gpu
```
then go to youtube and see how it behaves. (this disables GPU from chrome and is NOT a fix, as videos will play horribly)

How are the graphics drivers?
under menu/Additional Drivers is there any proprietary drivers for the GPU?

In chrome go to:
chrome://GPU/

under "Graphics Feature Status" what do you see?

Try disabling extensions: (go into terminal again with contorl+alt+t)
```
google-chrome --disable-extensions
```
then going to youtube and testing the problem

Hardware:
menu/System Monitor or in terminal the "top -d 1" command
does the CPU spike just before it happens? if so what process?
does the ram max out just before it happens?
any weird hardware behavior?

Try firefox? - I don't recommend Opera but it might also be a solution

If worst comes to worst you could install vlc (sudo apt-get install vlc) and then Open>Network Stream> then paste the youtube url as done here: [https://www.youtube.com/watch?v=3kGvqgiNeXE](https://www.youtube.com/watch?v=3kGvqgiNeXE)

Good Luck!!!

---

