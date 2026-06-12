---
title: "GNOME sound recorder problem"
date: 2004-11-20
forum: General Help
---

### Post by aarnem on 2004-11-20
Hi,

i have a problem with GNOME sound recorder.  I open it and record some music. Then i try to save it under some name. And no file is created. Any Ideas?

---

### Post by WW on 2004-11-20
This is a bug in Sound Recorder; see bugzilla report 2813.  While you're at it, take a look at bugs 2816 and 2818.  It appears that Sound Recorder is useless.

I was asking about this yesterday on the IRC, and someone suggested using the command line program **rec**.  The **rec** command is part of the **sox** package, available in the universe repository.

---

### Post by aarnem on 2004-11-20
Thanks. Sad to hear. The program looked nice. 

Some additional hints on alternative would be welcome.

---

### Post by WW on 2004-11-20
I'm still figuring it out, but I can tell you what I've done so far.

First, if you haven't already done so, you must enable the universe
repository.  Here a link with some hints on how to do that:

   [http://www.ubuntulinux.org/wiki/SynapticHowto](http://www.ubuntulinux.org/wiki/SynapticHowto)

Next, install the package **sox**.  Use Synaptic, or use the
command

$ **sudo apt-get install sox**

You now have the commands **sox** and **rec** available.
You can learn more about **rec** with the command **man rec**.

For a quick test, try this:

$ **rec -r 16000 testing.ogg**

This will start recording, with a sample rate of 16000 samples per
second, and the recording will be saved in the file testing.ogg.
To stop recording, press ctrl-c.  This has worked for me, but so
far, the sound quality is terrible.  This may be because (1) my mic
is very cheap, and/or (2) I have no idea how to optimize the
settings for high quality recording.

You now know as much about **rec** as I do!  Check out the
**rec** and **sox** man pages for more information.

---

### Post by aarnem on 2004-11-20
I tried also sox & rec. I have a problem with terrible sound also. Basically i use some older cassette tape player (walkman type).  I take output from headphones and put it into soundcard input. I guess audiophiles got heart attack already.

I used **rec -c 2 mysong.ogg**
or **rec -c 2 -r 44100 mysong.ogg**
 
If i play the music everything is OK. When i try to play recorded song the white noise is too strong. I thought it might be because of my terrible technical setup. At the same time when i was using GNOME sound recorder the recorded music was good quality (only with that saving problem).

I got stuck here right now. Tomorrow might be slightly better day.

---

### Post by aarnem on 2004-11-21
I've got things more or less working. I had to touch some mixer buttons and
the command
**rec -c 2 -r 44100 -s w mysong.ogg**
did the rest.
Good enough for me. Thanks for help.

---

### Post by bogl on 2004-12-04
The best program for recording & manipulating sound has to be Audacity, also available from universe.

---

### Post by WW on 2004-12-04
> I had to touch some mixer buttons and ...Same here. On my computer, the Volume Control app has two mixers, one OSS and one ALSA.   I had to unmute "Mic as Center/LFE" and "Mic Boost (+20dB)" in the mixer labeled "Intel ICH5 [Alsa Mixer]".

bogl, thanks for the tip. Audacity is working nicely so far.

---

### Post by ankitmalik on 2005-02-01
Thanks a lot guyz!

but after i posted this problem, I checked out

'sound-recorder' and it sure works good. no crashes like gnome-....

for eg. sound-recorder ankit.wav works good !


thanks !

---

### Post by machiner on 2005-02-02
As in most things computer - there are myriad ways to accomplish a task.

I, too, use the gnome-sound-recorder. I've got little chil'en and I like to record our conversations.

I have been able to record with this proggy employing the following technique:

Open the proggy, record your sounds. I set it to lossy - ogg files.

After I have stopped the recording I open my temp file. The file is there - temporarily saved as a gibberish title and extension.

You only have to rename the file: sound.ogg. Then move it to wherever you save such files.

THen I close the sound-recorder.

Where there is a will, there is a way.

Happy computing.

---

### Post by ankitmalik on 2005-02-02
[QUOTE=machiner]As in most things computer - there are myriad ways to accomplish a task.

I, too, use the gnome-sound-recorder. I've got little chil'en and I like to record our conversations.

I have been able to record with this proggy employing the following technique:

Open the proggy, record your sounds. I set it to lossy - ogg files.

After I have stopped the recording I open my temp file. The file is there - temporarily saved as a gibberish title and extension.

You only have to rename the file: sound.ogg. Then move it to wherever you save such files.

THen I close the sound-recorder.

Where there is a will, there is a way.

Happy computing.[/QUOTE]
 It is not a question of 'will or way'!

It is a question of ease - of use!

I hope this is corrected in Hoary. After all this is supposed to be a distro for n00bies!

---

### Post by machiner on 2005-02-02
So - what's your point? You found something that works for you, terrific.

It works for me...I'd like it to work without bugs -- but it doesn't so this workaround.

You never employed a work around? 

Ba haha.

Ease up, kid. You're ranting to the wrong (person).

Happy computing.

---

### Post by ankitmalik on 2005-02-02
[QUOTE=machiner]So - what's your point? You found something that works for you, terrific.

It works for me...I'd like it to work without bugs -- but it doesn't so this workaround.

You never employed a work around? 

Ba haha.

Ease up, kid. You're ranting to the wrong (person).

Happy computing.[/QUOTE]
 Oops! No I wasn't ranting!

But what I wanted to say is 'This is a Final Release so there shouldn't have been bugs, but hey ok but Ubuntu Developers, if you are listening, plz ensure that this won't be a prob in the next 'final' release!'

That a) wasn't a rant
b) wasn't a direct comment on you 

So chill! :D

And I HATE BEING CALLED A KID! I suggest you call me by my username or just say 'hey ubuntu user'!

I am 15, doesn't mean you call me a kid :(

---

### Post by piedamaro on 2005-02-02
[QUOTE=ankitmalik]Oops! No I wasn't ranting!

But what I wanted to say is 'This is a Final Release so there shouldn't have been bugs, but hey ok but Ubuntu Developers, if you are listening, plz ensure that this won't be a prob in the next 'final' release!'

That a) wasn't a rant
b) wasn't a direct comment on you 

So chill! :D

And I HATE BEING CALLED A KID! I suggest you call me by my username or just say 'hey ubuntu user'!

I am 15, doesn't mean you call me a kid :([/QUOTE]
 I'm 27 and gnome sound recorder never worked for me afaicr. It's just stupid to have a non-working software as a part of the CORE desktop. I can't believe it, t never worked since years.

---

### Post by machiner on 2005-02-02
The software in question works - it just has a bug.

If you want to use it, complete with bug, then find a way to make it work for you as I did.

If you choose to not use it, then terrific. Don't use it.  Use something else with similar functionality.

Who cares how old you are - I called kid a kid because of his attitude not because his sig says he's 15.


Finished here...use it or not. Make it work or not.  WHat the hell do I care - I didn't make the software only offered up a solution to make it work.

sheesh....GTFU!

---

### Post by piedamaro on 2005-02-02
Are you answering to me or? I'm sorry if it was for me. I'm only ranting against gnome-recorder, I have absolutely no problem with you.
However it has a bug which prevents it from working. Thus it doesn't work. The bug is already there, so there is little to do.

---

### Post by Gary Nored on 2006-04-12
[QUOTE=aarnem]Thanks. Sad to hear. The program looked nice. 

Some additional hints on alternative would be welcome.[/QUOTE]

My Ubuntu came with another program called simply "sound-recorder." It works from the command line and sound quality is excellent. The gnome-sound-recorder appears to be working, but the files are just full of hiss and static. 

Hope this helps

---

