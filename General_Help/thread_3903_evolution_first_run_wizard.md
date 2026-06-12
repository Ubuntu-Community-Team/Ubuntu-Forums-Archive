---
title: "evolution first run wizard"
date: 2004-11-10
forum: General Help
---

### Post by keemo on 2004-11-10
Hi everybody

I'm trying to setup evolution and the wizard comes up, but everytime i get stuck on the same section....I fill in my details and get to the time zone section, i select my time zone and click forward, and thats where it freezes and oges nowhere.

I did upgrade it through the 'hoary' repositories before i first used it.

I tried running it with debug mode on, and i've attached the resulting file, if it helps!

any suggestions?  Thanks in advanced guys!

---

### Post by JonAtkinson on 2004-11-10
Could you try deleting your .evolution folder:```
$ rm -rf $HOME/.evolution
```then run the program again? If it still fails, could you post the resulting debug log?

Cheers,

--Jon

---

### Post by keemo on 2004-11-10
Thanks for your reply JA. I will try that when I get home.

I'm just wondering, would that be evolution's temp folder?

---

### Post by JonAtkinson on 2004-11-10
Yes, .evolution/ is where Evolution stores its data, but it's by no means temporary.
Deleting this folder will basically reset Evolution to the state it was in when you first installed Ubuntu, so it may be easier to diagnose what is going wrong from a 'clean slate'.

--Jon

---

### Post by kastorff on 2004-11-10
Actually there is a folder, .gconf/apps/evolution, that also contains configuration info, so if you are trying to create a "first run" state it should be removed too.

---

### Post by keemo on 2004-11-11
hi guys
i tried deleting the $HOME/.evolution first and it didnt work, Then I tried deleting both directories, and still the same.

I've attached the debug file.

Thanks for your help guys.

---

### Post by JonAtkinson on 2004-12-05
Sorry for the late reply on this one.

You could try to removing the evolution-exchange package:
```
sudo apt-get remove evolution-echange
```Then try running evolution again.

Let me know how you get on.

--Jon

---

### Post by keemo on 2004-12-05
JA..
thanks for your reply.
I've had a couple of issues with ubuntu on my PC, one being this issue and the other is to do with xmms (I have an nVidia based graphics card) and a couple of other little stupid problems which are very fixable, but I dont have the time to do that, so I moved to mepis, and its been working ok..

I still have ubuntu on my laptop though, and its working flawlessly!  in fact, the fan is working so much less with ubuntu (I had win xp before)

by the way, I have a HP ze2400 with a celeron 1.6GHz, 256MB DDR, ATI graphics card, and a conexant modem...

Thanks for help guys...I really appreciate it.

---

