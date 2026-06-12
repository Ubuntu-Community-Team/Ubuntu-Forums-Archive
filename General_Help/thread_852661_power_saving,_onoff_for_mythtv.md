---
title: "power saving, on/off for mythtv"
date: 2008-07-07
forum: General Help
---

### Post by DJYoshaBYD on 2008-07-07
ok.. my pc heats up my apartment and wastes electricity when Im not using it.. 2 questions:

1: How can I set up my pc to go to sleep after 3 hours, and wake up using my IR remote.. its a windows media center remote...

2: How can I turn my pc on/off, or hibernate and wake up, using the remote.. so I dont have to walk up to the pc and turn it on..

really, I just want it to hibernate or sleep and save power, and come back on with the remote only...

any suggestions

---

### Post by DJYoshaBYD on 2008-07-07
bump

---

### Post by DJYoshaBYD on 2008-07-07
nother bump

does anyone know about power saving or mythtv, in general? I could assume its something easy

---

### Post by sdennie on 2008-07-07
First, don't bump your threads this often.  It actually makes it less likely that people will look at it.

You should first see if you system supports suspend or resume.  Does it present those option in the shutdown menu?  If so, depending on your machine, just pressing a button on the remote may actually resume the machine automatically.  After that, assuming mythbuntu is running gnome underneath, you could just go to System->Preferences->Power Management and set the machine to standby after a certain amount of activity.

---

### Post by DJYoshaBYD on 2008-07-07
if I didnt bump it, then I would be a page back, and for sure wouldnt get answered.. lol.. its sometimes the only was I can get people to notice on this forum.. sorry

Its a stand alone mythbuntu system.. my system isnt old.. it will support that.. but I just need to know what packages to install for power saving features on mythbuntu.. and I want to know how to turn it off/on with the remote, if possible..

---

### Post by DJYoshaBYD on 2008-07-07
thats exactly what I meant.. 2nd page.. no one will look at it there.. lol..

soooo bump.. I know this is something very easy, I just need to be pointed in the right direction...

I know someone here can help me

---

### Post by sdennie on 2008-07-07
There is no need to bump your thread once an hour.  [http://ubuntuforums.org/showthread.php?t=82471](http://ubuntuforums.org/showthread.php?t=82471)

---

### Post by DJYoshaBYD on 2008-07-07
trust me.. I understand.. but how can I be the only one to ask about this?
I have searched
My question is plain as day
I KNOW someone here knows
But no one posted.. lol

do YOU have any suggestions, besides telling me to wait for 24 hours, and my thread to be on page 10, where it will never get seen? If I didnt bump it, it would already be hella far from viewing eyes... this forum moves to fast to not bump, otherwise I would wait a week, for a simple solution...

there has to be SOME package that does this, but I cannot find it.. I have been searching for a week and a half, BEFORE I even posted..

Id prefer to not have to put gnome or kde on JUST for power saving.. 

any suggestions for another forum that might be more in tune with mythbuntu that arent dead?

---

### Post by bodhi.zazen on 2008-07-07
> **DJYoshaBYD said:**
> any suggestions

Turn it off when you are not using it :lolflag:

I do not understand the big deal, you are not going to interact with it via a remote, so when you are ready, get up, walk over to your computer, and turn it on. When you are done turn it off and walk away.

Second, as vor indicated it is considered rude to bump your posts this frequently. We do also have an unanswered posts team, but they can not identify you thread as it is no longer unanswered if you bump it :guitar:

[http://ubuntuforums.org/forumdisplay.php?f=216](http://ubuntuforums.org/forumdisplay.php?f=216)

---

### Post by DJYoshaBYD on 2008-07-07
> I do not understand the big deal, you are not going to interact with it via a remote, so when you are ready, get up, walk over to your computer, and turn it on. When you are done turn it off and walk away.

the whole point of having this media center is for it NOT TO BE A PC.. even if I cannot turn it off and on with the remote, I need to know how to have it go into sleep mode.. I am human, and tend to fall asleep while watching tv, and that now also includes my pc.. power saving package.. is there one? Do you know of it? 

> 
Second, as vor indicated it is considered rude to bump your posts this frequently.

Its also considered rude to answer a post, and not give a helpful answer about the question at hand.. I KNOW I can turn it off by hand.. thats not my question..

---

### Post by DJYoshaBYD on 2008-07-07
> they can not identify you thread as it is no longer unanswered if you bump it 

true.. Ill leave it till tomorrow.. its just so hard to get an answer in these forums.. I have been on so many forums, and have never had trouble..

this is just the only one thats not dead, and eventually, I get an answer.. even if its weeks later..

---

### Post by cprofitt on 2008-07-08
> **DJYoshaBYD said:**
> if I didnt bump it, then I would be a page back, and for sure wouldnt get answered.. lol.. its sometimes the only was I can get people to notice on this forum.. sorry

While this might be true on most forums... the reality is that this forum software has a feature that allows the unanswered posts team to see posts with no 'answers'... and when there is a reply it is seen as an answer... so it does not show up in the list.

---

### Post by cprofitt on 2008-07-08
As for your original question...

Try using gconf-editor - |apps|gnome-power-manager and set the 'timeout' sleep_computer_ac value to 9000.

---

### Post by DJYoshaBYD on 2008-07-08
what will that do? Isnt there a gui gui that can do that? It seems kind of primitive to have to do that.. lol.. 

I actually installed gnome-power-manager, but couldnt figure out how to use it.. haha.. how long will that set the sleep mode to go on? and just curious, what does it shut down? How much does it actually help?

---

### Post by alexeix on 2008-10-01
Re-posting in the correct forum.

---

