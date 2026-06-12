---
title: "Loading Ubuntu"
date: 2008-06-25
forum: General Help
---

### Post by LoneWolfXAxis on 2008-06-25
Hello, I am new at this. But I will describe to you my problem the best I can.

Problem: After I enter my user name and password correctly, my screen loads as a black screen for a few seconds and eventually goes to the desktop background. Nothing else loads up when the background shows. No tool bars or flash drive icons. The screen stays like this for an indefinite amount of time. I have never see the screen change at all. It also wont allow me to right click on anything either.

Things I've Done That Don't Work: I have tried restarting my computer a dozen times and the problem still persists. This is the only thing I've done so far since I am still new to Ubuntu.

Items and Effects: I have the desktop cube active on Ubuntu. I have also recently added a file of picture and a file of word documents that I transfered over from windows.

This is the best I can explain this issue. Please help, I have already have data on there that I don't want to loose.

~LoneWolfXAxis~

---

### Post by fooman on 2008-06-25
see if alt-f2 will bring up a run application box.

if it does, try typing this into the space and hit enter:

```
gnome-panel &
```

---

### Post by dexter.deepak on 2008-06-25
have you tried logging into the failsafe-gnome ?
look for it at the "sessions" option on your login window...if your login works correctly, undo the changes, especially disable the desktop effects.
report back whatever happens.

---

### Post by LoneWolfXAxis on 2008-06-25
I'll see what I can do. Give me a few minutes and I will be back with a reply!

---

### Post by LoneWolfXAxis on 2008-06-25
Alright, Dexter, your suggestion helped out. I am back on ubuntu now while replying. Will I be able to put the desktop cube settings on without issues or do I need to leave everything the way it is? I would like to have the cube feature active a long with a picture as my background.

I appreciate everything guys!

---

### Post by eapache on 2008-06-25
What's your graphics card? It might be too slow to run the cube properly.

---

### Post by LoneWolfXAxis on 2008-06-25
I am running a G71 [GeForce 7900 GS]  (Nvidia)

I am still new to everything so I can hardly tell whats slow or fast.

---

### Post by dexter.deepak on 2008-06-25
you mean ..you are still on the failsafe-gnome or back to your original session ? reply.
wherever you are , i suggest you to run this script - "compiz-check"
to see if compiz can be run safely on your comp.
[http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)

if the result is negative..you have to sacrifice compiz.:(

if you are on the failsafe-gnome, try going back to gnome session after disabling the desktop effects.

---

### Post by eapache on 2008-06-25
I think that should be fast enough. Do you have the restricted driver enabled? Do you have other desktop effects working?

---

### Post by LoneWolfXAxis on 2008-06-25
Dexter, I am still in the gnome failsafe. I misunderstood it when it said it fixed everything. Do I need to be on the original session before I run the compiz check?

Eapache, I think I might be running it as a restricted driver, but to be safe, can you tell me how to check to see if it is a restricted driver?

---

### Post by dexter.deepak on 2008-06-25
you can check it in the failsafe itself.

---

### Post by LoneWolfXAxis on 2008-06-25
I need a lot of help. I am getting lost in how to run compiz check. Can you please walk me through step by step.

---

### Post by dexter.deepak on 2008-06-25
i thought it couldnt be simpler !!:)

still i'll give it a try:
goto applications -.accessories ->terminal
try:
```
wget http://blogage.de/files/4359/download -O compiz-check
```
let it do its work ...when you get the prompt back...try :
```
chmod +x compiz-check
```
try this next :
```
./compiz-check
```


thats it !! 
you will get the output in a very readable format....and solutions to the problem (if they exist).

---

### Post by dexter.deepak on 2008-06-25
but first of all i would like to know..if you can still log on to your "gnome-session" or not.

leave compiz aside and try logging into you gnome session..as you did for failsafe-gnome.

---

### Post by LoneWolfXAxis on 2008-06-25
Give me a few minutes to try.

---

### Post by LoneWolfXAxis on 2008-06-25
I am now in a Gnome session. What do I need to do now?

---

### Post by dexter.deepak on 2008-06-25
i hope you have disabled compiz..and "everything" works fine now.
just try the steps in my last post for compiz-check.
if you get a negative result ..avoid compiz
and if its a positive..then you may go on..may be it was a temporary problem.

you have to do it on your own now coz i really need to go..hope i was of some help..

---

### Post by eapache on 2008-06-25
To check for restricted drivers, go to System->Administration->Hardware Drivers and make sure that the Nvidia driver says 'in use'.

Did you have other effects working before you enabled the cube, or did you do it all at once?

---

