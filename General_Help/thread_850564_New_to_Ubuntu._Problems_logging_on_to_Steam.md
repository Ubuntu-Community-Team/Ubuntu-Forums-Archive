---
title: "New to Ubuntu. Problems logging on to Steam"
date: 2008-07-05
forum: General Help
---

### Post by HelicopterSam on 2008-07-05
This is my first post and first thread and wanted to say 
Ubuntu rocks! :guitar: Way better than xp and vista in almost every aspect.
My system is really old in gaming terms and I just put a bunch of pc parts together. Its about 4 years old and has a nvidea 6800 ultra with 2 gigs of ram and a 3.2 ghz Pentium 4 cpu.

I have searched everywhere for my answers on how to install Steam (counterstrike source) and just now found out how to install steam. I installed wine and that playonlinux thing and wala! I have steam. BUT :mad: eveythime I log in to my existing steam account it says "connecting to steam". Then a grey window pops up in front of it and says:

"This application is trying to show an HTML page. Wine needs Gecko (Mozila HTML engine) to be installed to show the page. Click install if you want Wine to automatically download and install Gecko."

And it gives me the option to "Cancel" Or to "Install"

I hit install and it says loading. The gecko loading window goes away and steam again say "connecting" but it goes away, steam closes its self! 

I cant seem to figure this thing out.

Again I am very new to Ubuntu and am sort of familiar of the terminal but I don't consider my self even that of a novice. I think somewhere lower than a novice.

---

### Post by BennBuntu on 2008-07-05
don't know why it's quitting out, you could try installing gecko manually
open a terminal
```
wine iexplore.exe http://www.winehq.org
```

Only other thing I had to do was copy a font into the windows font directory directory, (tahoma.ttf I think) ~/.wine/drive_c/windows/fonts.

Note to see the .wine folder in nautilus, you'll need to press ctrl+h to see hidden.

edit: Welcome to Linux :-)

---

### Post by HelicopterSam on 2008-07-05
Re: New to Ubuntu. Problems logging on to Steam
don't know why it's quitting out, you could try installing gecko manually
open a terminal
Code:

wine iexplore.exe [http://www.winehq.org](http://www.winehq.org)

I tried it, and it didnt seem to work. Same thing happened.


"Note to see the .wine folder in nautilus, you'll need to press ctrl+h to see hidden."

Hmmm I dont quite understand what nautilus is or why I need to see the hidden's in the virtual wine C hard disk in .wine?

"Welcome to Linux "

Thankyou :)

---

