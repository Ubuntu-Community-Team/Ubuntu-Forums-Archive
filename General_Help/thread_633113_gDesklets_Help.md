---
title: "gDesklets Help"
date: 2007-12-06
forum: General Help
---

### Post by UK-Wobbie on 2007-12-06
Hello all i like to know how do you save gDesklets so the desktop saves what i put on it when i reboot the pc!

Thanks :)

---

### Post by frodon on 2007-12-06
It's done automatically, however you may have to add gdesklet in session startup script or maybe just run a "gnome-session-save" command.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> It's done automatically, however you may have to add gdesklet in session startup script or maybe just run a "gnome-session-save" command.

Ok cool!

When i logout or reboot the pc the desktop icons what i put down do not load so i have to keep clicking on gDesklet what is doing my head in a bit :lolflag:

So if i add gnome-session-save to my sessions it will load? :confused:

Thanks

---

### Post by frodon on 2007-12-06
lol no, "gnome-session-save" is a command to save your session which will hopefully include Gdesklet but i'm not sure, you just have to run it once.
Anyway if you want to be sure to load gdesklet automatically add it to your session startup scripts and you will be done.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> lol no, "gnome-session-save" is a command to save your session which will hopefully include Gdesklet but i'm not sure, you just have to run it once.
Anyway if you want to be sure to load gdesklet automatically add it to your session startup scripts and you will be done.

Hey am sorry about this :lolflag: But do i run "gnome-session-save" into terminal? I had a go and logout and log back in and all it's doing is opening termina :lolflag:

And i had a go adding "Gdeskle" to my sessions and it did not do anything :(



I am saying that your not right lol But is it "gdesklets"? Or "Gdeskle what you put into sessions ](*,)

When looking at the file start link name it says gdesklets :lolflag: So i may have a go and see what it do! 

Thanks for your help :)

---

### Post by UK-Wobbie on 2007-12-06
It worked :) But now it's keeps opening Terminal when login :( Do any one know how to stop this :lolflag: All i did is add "gnome-session-save" to my terminal and it keeps opening it when load ](*,)

---

### Post by banewman on 2007-12-06
I added gdesklets to my desktop then went to  - applications-system-preferences-sessions-startup tab and typed gdesklets and they start at boot. :)

---

### Post by UK-Wobbie on 2007-12-06
> **banewman said:**
> I added gdesklets to my desktop then went to  - applications-system-preferences-sessions-startup tab and typed gdesklets and they start at boot. :)

Hey banewman,

It works but when i click on the logout button at the top! It do not open the list window for reboot and logout.. So I made a file what run! And put  "gdesklets" in it and linked it up to my sessions! And all is good now all work and the logout window works to! :)

---

### Post by banewman on 2007-12-06
I'm happy for you!
Gdesklets are good eyecandy. :)

---

### Post by UK-Wobbie on 2007-12-06
> **banewman said:**
> I'm happy for you!
Gdesklets are good eyecandy. :)

The only thing what is doing my heading now is Terminal keeps opening on start up lol When i login it pops up :lolflag:

I added "gnome-session-save" to my Terminal and i can not fix it :(

---

### Post by banewman on 2007-12-06
The only things I did was set my desktop up with the six gdesklets I want then went to  
applications-system-preference-sessions-startup and typed "gdesklets"
Didn't have to do anything else.
Get no terminal - all load as set up.Hope that helps.
 :)

---

### Post by frodon on 2007-12-06
It's because your terminal was open when you saved your session ;)

In the session window you have an option to save the session each time you log out, if you use it your desktop will just be like it was the last time you logout each time you login.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> It's because your terminal was open when you saved your session ;)

In the session window you have an option to save the session each time you log out, if you use it your desktop will just be like it was the last time you logout each time you login.

The funny thing is :lolflag:I had a look at sessions in the session options! And the box is not tick :) So i do not know what to do lol Hmm I have got a nvidia card in my computer and the plugins..

I say when i put the logout window was not opening it as got something to do with them or it may be "Advanced Desktop Effects Settings" :confused:

Anyway that works now but it's this what is doing my head in now :lolflag:](*,)](*,)](*,)

---

### Post by banewman on 2007-12-06
OK - if gdesklets are loading at boot can you say what the new problem is?
just to be clear. :)

---

### Post by UK-Wobbie on 2007-12-06
> **banewman said:**
> OK - if gdesklets are loading at boot can you say what the new problem is?
just to be clear. :)

Ok be for gDesklets was not working! Some guy or girl :lolflag: Put up "gnome-session-save" To make it boot!
But i did not now what to do with it :lolflag: So i put it in Terminal to see if it will open! Like if you put "desklets" in sessions it will open! 

But all it is doing when i added gnome-session-save to Termina is loading Terminal on startup :lolflag:

I fixed the gDesklets thing but it's now come down to this :(

I had a go adding gnome-session-save to my sessions but it did not do anything so i had a go on  adding it toTermina! And it's loading Termina on startup :confused:

---

### Post by frodon on 2007-12-06
Hum, you didn't read my post with enough care.

Choose "save session on logout" then close all the windows you have opened, logout then right after this login again and you will be good. After this you can unselect "save session on logout" if you wish.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> Hum, you didn't read my post with enough care.

Choose "save session on logout" then close all the windows you have opened, logout then right after this login again and you will be good. After this you can unselect "save session on logout" if you wish.

Dam lol I see what you are getting at now :lolflag: In sessions tick the box what will save all the stuff on the desktop! ](*,)](*,) I did not now there was a box at start lol But then i was playing about with Ubuntu i seen it ](*,) Never mind lol Thanks for your help and i will do a nice restall on my computer to fix this Termina opeing thing :lolflag:

Thanks :)

1 more thing!  Wnat i am telling you is right? :lolflag:  Where is "save session on logout"? The only one i know now is in sessions :)

---

### Post by frodon on 2007-12-06
It is not needed to reinstall but if it's your wish ...

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> It is not needed to reinstall but if it's your wish ...

But i can not stop Termina opeing on login lol ](*,)

---

### Post by frodon on 2007-12-06
I just explained you how to solve this, why you don't try to just follow the instructions ?

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> It is not needed to reinstall but if it's your wish ...

May i ask where is "save session on logout" :confused: Is it the one in sessions options?

Thanks for your help :)

---

### Post by frodon on 2007-12-06
I don't have the english version so i can't give you the exact text, it's in the session properties window, the same window where you set your startup scripts.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> I just explained you how to solve this, why you don't try to just follow the instructions ?

1) was i did not now there was a Automatic save desktop tool!
2) Was when you put "save session on logout" WHERE IS IT?

And i was following  the instructions!

Automatic save button on sessions is not the same as "save session on logout" :lolflag:

So where do i go to get to this "save session on logout"?

Thanks

---

### Post by frodon on 2007-12-06
You were able to put your gdesklets command on session startup scripts right ?
**_[COLOR="Red"]It's in the last tab of this window[/COLOR]_**, sorry can't explain this more clearly.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> I don't have the english version so i can't give you the exact text, it's in the session properties window, the same window where you set your startup scripts.

Any way i fixed it now and it's working so all i am going to do is to reinstalling Ubuntu and do what i was doing be for with the file thing :lolflag: 

Thanks for your help :)

---

### Post by frodon on 2007-12-06
If you reinstall for this i'm scared that you will have to reinstall each day, anyway good luck.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> If you reinstall for this i'm scared that you will have to reinstall each day, anyway good luck.

 reinstall each day? :confused: What do you mean on that?

---

### Post by frodon on 2007-12-06
I mean if you give up and reinstall just because a terminal opens you will find surely  each day good reasons to give up and reinstall.

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> If you reinstall for this i'm scared that you will have to reinstall each day, anyway good luck.

It was that "gnome-session-save" thing what is making Termina to open on startup! 
So reinstalling my computer will FIX it :)


I made a run file and put in the name "gdesklets" In it and linked it up to my sessions and it all worked well! :)

Before i had a go on doing all this on only adding the name "gdesklets" to my sessions and worked but the logout button at the top did not work!

Show doing it my way works :) Do not know why  but works :lolflag:

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> I mean if you give up and reinstall just because a terminal opens you will find surely  each day good reasons to give up and reinstall.

Now i will not! I will be happy lol That  terminal will stop opening on ever time i login :lolflag:


Anyway it has been fun chatting to you :) And thanks for everything and all the help.

Thanks :)

---

### Post by frodon on 2007-12-06
You're welcome ;)

---

### Post by UK-Wobbie on 2007-12-06
> **frodon said:**
> You're welcome ;)

):P:mrgreen:\\:D/:-({|=:biggrin: thanks

---

