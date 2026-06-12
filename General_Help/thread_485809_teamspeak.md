---
title: "teamspeak"
date: 2007-06-27
forum: General Help
---

### Post by XRichX on 2007-06-27
OK, i hate posting up many questions but i think this is one of my last hopefully, i have a problem with Teamspeak, Sometimes when i open it up it mutes my microphone and speakers so i cant use the program to talk or hear other people, although i turn on Jukebox and i can listen to music etc.

But other times it works perfectly, until i open Amarok... well Amarok wont even open if i have TS open lol. Even if i close TS then open Amarok it still wont open and then if i go to shut down/restart it just freezes Ubuntu. If i have Amarok open and then i open TS then it will mute my speakers and mic in TS but i can listen to music in Amarok. 

Is there a conflict here between the two apps?

please help, i cant really run a Unreal Clan with this problem.

thanks 

XRichX

EDIT: iv realised that only one program at a time can use the audio channel, is there anyway to change this?

---

### Post by Brucevdk on 2007-06-27
You can use a command/program called *aoss* to prevent TeamSpeak from hogging the sound system. Straight from the man pages: *aoss  is a simple wrapper script which facilitates the use of the ALSA OSS compatibility library. It just sets the appropriate LD_PRELOAD path and then runs the command.*

```

sudo apt-get install alsa-oss
aoss ./TeamSpeak

```

Or edit the TeamSpeak shell script and add the *aoss* command there.

---

### Post by XRichX on 2007-06-27
oh, thankyou :)

i shall try that 

thanks,

Rich

---

### Post by XRichX on 2007-06-27
i typed the aoss command in and i installed it, but when i type aoss ./TeamSpeak it says it cant find file, i searched for it in my USERNAME folder but cant find the Teamspeak folder, although i have installed it using Package Manager.

---

### Post by Cable on 2007-06-27
Try just typing
```

aoss teamspeak

```
Simply remove the ./.

---

### Post by XRichX on 2007-06-27
thanks for your help :)

it hasnt given any output, so il assume that its worked, i shall try now.

thanks again :-D

---

### Post by XRichX on 2007-06-27
it hasnt worked, got Jukebox playing and TS just doesnt use my mic or speakers, closed Jukebox and it works so im still at square one :(

---

### Post by Devour on 2007-09-17
I am having a similar problem. Teamspeak used to work fine except that when I had it open I could not hear sounds from any other programs except Teamspeak. So I messed around with the settings on Teamspeak. Now everytime I use Teamspeak and join a server it automatically mutes my speakers and mic and when I try and unmute them nothing happens, but I can hear sounds from other programs while Teamspeak is open. I think I have tried uninstalling and reinstalling but I'm not sure if there are hidden files somewhere, but when I reinstalled the same thing keeps happening. Help please. Thanks.

---

### Post by buzzmandt on 2007-09-17
teamspeak uses oss instead of alsa, oss requires the sole use of the sound device it uses, it closes the device out to anything else.  If something is using the sound device when teamspeak is started it will mute itself since it cannot take over the device.  Unfortunately it's the way the teamspeak.org folks coded it for linux.  I've never been able to get the oss-alsa thing to work but i have gotten it to work in wine, and in the winecfg sound section have oss unchecked and alsa checked.

there is also a work around if you have more than one sound card.  you'll have to search for that one but it's out there somewhere.

---

### Post by Adramelech on 2007-09-17
heres how you fix it, run this two commands:

echo 'APPLICATION direct' > /proc/asound/card0/pcm0p/oss
echo 'APPLICATION direct' > /proc/asound/card0/pcm0c/oss

APPLICATION should be the teamspeak binary name, by the way, this solution is on teamspeak FAQ page, so you can look there for the entire explanation.

---

### Post by Devour on 2007-09-18
How do you change the Wine config to point to ALSA instead of OSS? I'm not sure where the wine cfg is and if I found it I wouldn't know what to do. Lol, I will google in the mean time.


EDIT: I figured it out. Winecfg is a program. Haha. Ok, I'm trying it now. I hope I don't break anything.

EDIT2: Ok, I edited it and checked ALSA instead of OSS and when I used TeamSpeak with wine this is what the console spat out.

devo@devo-desktop:/media/sda1/Program Files/Teamspeak2_RC2$ wine TeamSpeak.exe
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGING: stub
fixme:richedit:RichEditANSIWndProc WM_STYLECHANGED: stub
fixme:wave:widDsCreate DirectSoundCapture not implemented
fixme:wave:widDsCreate The (slower) DirectSound HEL mode will be used instead.
fixme:alsa:ALSA_AddRingMessage two fast messages in the queue!!!! toget = 63(WINE_WM_STARTING), tosave=1(UNKNOWN(0x00000000))
err:ntdll:RtlpWaitForCriticalSection section 0x190bb8 "dsound.c: DirectSoundDevice.mixlock" wait timed out in thread 0013, blocked by 0012, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x190bb8 "dsound.c: DirectSoundDevice.mixlock" wait timed out in thread 0013, blocked by 0012, retrying (60 sec)

---

### Post by Devour on 2007-09-19
Help plzkthx?

---

### Post by Devour on 2007-09-20
Bump.

---

