---
title: "Why hasn't the sound been fixed?"
date: 2008-05-22
forum: General Help
---

### Post by CShadowRun on 2008-05-22
Ok, most of you probably know what i'm talking about. The whole ALSA, OSS, and PulseAudio all sitting there happily conflicting with eachother. I've been trying to fix this for months now! I've made posts on the forums, i've asked in the ubuntu IRC channel countless times, and i've seen so many people with exactly the same problems i'm having.

Why hasn't this been fixed? Seriously, i'm not a coder. But couldn't this simply be fixed by having ubuntu by default loaded with something that mixes all the audio together? I mean it's not hard. Windows managed to pull it off, so did mac!...infact, most devices now days have sound, it's not really that much to ask for. I've even seen certain users been searching for YEARS for resolutions to this issue.

So far i've tried switching all my options in System > Preferances > Sound to PulseAudio, this helped, but didn't completely solve.

I tried upgrading my ALSA, this made the situation worse.

I tried to edit firefoxrc as so many people guide you to do, only problem is it doesn't exist.

So, is anyone actually going to fix this issue? I've installed ubuntu on 3 of my PC's so far, and they all have the same issue. Also my friend who tried ubuntu has exactly the same problem.

If it isn't going to get fixed, i'm going to have to go back to windows again.



Edit: Finally, a year later.I found a solution to this. A kind person in winehq pointed me in the right direction.
killall pulseaudio
system > preferences > sound.
change all to ALSA.

problems magically dissapear.

---

### Post by strabes on 2008-05-22
What exactly is the problem you're having?

I agree that the pulseaudio implementation in hardy is annoying but keep in mind that pulseaudio support had to be written into most of the applications, and this hasn't happened upstream for many apps yet.

---

### Post by mikewhatever on 2008-05-22
> **CShadowRun said:**
> Ok, most of you probably know what i'm talking about. The whole ALSA, OSS, and PulseAudio all sitting there happily conflicting with eachother. I've been trying to fix this for months now! I've made posts on the forums, i've asked in the ubuntu IRC channel countless times, and i've seen so many people with exactly the same problems i'm having.

No idea. The sound is fine here.


> So, is anyone actually going to fix this issue? I've installed ubuntu on 3 of my PC's so far, and they all have the same issue. Also my friend who tried ubuntu has exactly the same problem.

Hmm, who knows. May be, and may be not.

> If it isn't going to get fixed, i'm going to have to go back to windows again.

Good idea. Off you go.:popcorn:

---

### Post by medic2000 on 2008-05-22
I have not a problem on my desktop nor on my laptop? The sound works like a charm. Also 2 of my friends using ubuntu on their laptop and they don't have a problem related to sound. 

What exactly is your problem?

---

### Post by Allen111 on 2008-05-22
I think I might have the same problem as you. You didn't really specify what was wrong. Are you getting sound? No sound? Low Sound?


My problem is that when I'm at Youtube (Or any site with sound emitting from it) I can't hear sound in my Apps (Like VLC, Amarok, etc..) and when I'm using VlC or Amarok, I can't hear Sound from the Internet (Youtube, Metacafe, etc..). I don't know if this is intentionary, or if its a Known Bug, but is there anyway I can fix this issue? 

(I'll start a New thread if necessary.. )


-Allen

---

### Post by wkulecz on 2008-05-22
> but keep in mind that pulseaudio support had to be written into most of the applications, and this hasn't happened upstream for many apps yet

I feel very strongly that a change in a subsystem that forces changes in applications that use it does not belong in a LTS release!

I personally didn't find anything lacking in the sound support for 6.06.  But now on the same hardware I've issues with 8.04.  This is not progress.  Different is not better, better is better.  I don't see any "better" in pulse audio.  Perhaps I'm just too unsophisticated a user of sound, but no sound is a lot worse than what I've had before!

--wally.

---

### Post by atomkarinca on 2008-05-22
> **wkulecz said:**
> I feel very strongly that a change in a subsystem that forces changes in applications that use it does not belong in a LTS release!

I personally didn't find anything lacking in the sound support for 6.06.  But now on the same hardware I've issues with 8.04.  This is not progress.  Different is not better, better is better.  I don't see any "better" in pulse audio.  Perhaps I'm just too unsophisticated a user of sound, but no sound is a lot worse than what I've had before!

--wally.

If I remember correctly, in Dapper you couldn't even get two applications concurrently outputting sound. Or you would have to jump through hoops to come near that. Now with just a little bit configuration you can get sound from every application you run concurrently. I call that "better". By the way, I can even get sound with flash *and* other applications.

Pulseaudio *is* an improvement, I believe with Intrepid it will be innovation, if not with 8.04.1.

---

### Post by CShadowRun on 2008-05-22
Yea, i'm talking about the old flash and other applications problem (Although pulseaudio seems to fix it, good job on that.)

Basically it's a very difficult problem to describe. Certain applications conflict with other applications (When a conflict occurs, one or both gets no sound at all.) And it happens alot.

I spent a long time finding out that i needed to go into the sound settings and change to pulseaudio (Instead of the default, auto) This fixed the flash and other applications problem. The only other iron-clad problem i have now is that wine applications monopolize sound completely. (That means if i start playing games in wine, I can't hear people typing in IRC, or listen to music, etc.) If anyone has any ideas for tests i can run them...Sorry for being so bitchy about it, i've just been asking for such a long time to have a fix for it.

---

### Post by 3rdalbum on 2008-05-23
> **CShadowRun said:**
> Ok, most of you probably know what i'm talking about. The whole ALSA, OSS, and PulseAudio all sitting there happily conflicting with eachother.

Why hasn't this been fixed? Seriously, i'm not a coder. But couldn't this simply be fixed by having ubuntu by default loaded with something that mixes all the audio together? I mean it's not hard. Windows managed to pull it off, so did mac!

The Macintosh only ever had one sound system. Windows has multiple sound systems, but Microsoft never created anything to have them co-exist. Microsoft just told developers to use the new sound system. Even today, on Windows, if you play an older game that uses the old API, all sound from other programs will cease.

Pulseaudio *will* wrap up all the other sound systems except JACK (pro-audio sound system), it's just not fully integrated into Ubuntu. Most people don't have trouble with audio now except where proprietary software developers don't understand Linux, and decide to use the old APIs.

---

### Post by artisan on 2008-05-23
There does seem to bean issue with sound
I have just instaled HH.
I am getting an error message 
No volume control GStreamer plugins and/or devices found

Gstreamer is installed.

---

### Post by durkhrod chogori on 2008-05-23
> **CShadowRun said:**
> If it isn't going to get fixed, i'm going to have to go back to windows again.

No, do something better than that:

[IMG]http://i29.tinypic.com/16i2hc.jpg[/IMG]

---

### Post by Trollslayer on 2008-05-23
Works fine for me, HDMI audio even works in 8.04 - MythTV on a 42" plasma with surround sound through the AV receiver!

---

### Post by Allen111 on 2008-05-27
Found fix :)

Rep Please (j/k)

> 
    sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
    sudo mkdir -p /tmp/.esd/
    sudo touch /tmp/.esd/socket 

---

### Post by slavoy on 2008-05-30
Hi, I had a lot of problems with HH sound and pulsaudio/alsa/flashsound...
[This is the best way to fix pulsaudio problems]("http://ubuntuforums.org/showthread.php?t=776739").

This works for me...

---

