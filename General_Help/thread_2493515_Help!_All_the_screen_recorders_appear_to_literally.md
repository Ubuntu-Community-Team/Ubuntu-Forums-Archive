---
title: "Help! All the screen recorders appear to literally be broken on Ubuntu 22.04 LTS"
date: 2023-12-17
forum: General Help
---

### Post by SpaceManJack on 2023-12-17
So the only screen recorder that worked well for me on 20.04 LTS was Simple Screen Recorder, all the others didn't work as I remember. Now here we are on 22.04 LTS and it seems none of the screen recorders work at all. 

So if I'm not mistaken, if I'm correct, 22.04 LTS uses Wayland as the default. Well according to what someone said here [https://askubuntu.com/questions/1347489/ubuntu-22-04-any-screen-recorders-not-working-showing-black-screen-only](https://askubuntu.com/questions/1347489/ubuntu-22-04-any-screen-recorders-not-working-showing-black-screen-only) 

"This may be because Ubuntu 21.04 uses Wayland by default, which restricts screen recording for "security". In your login screen, you can switch to the "Ubuntu" session, which uses X.Org, and it should allow screen recording software to function properly."

Ok before we go on, first things first, I downloaded all the major 4 screen recorders from the "Ubuntu Software" and on Wayland all I get are black screens and none of them record sound apart from 1 or 2 of them, so they all have black screens and only 1 or 2 of them even have sound. But when I switch to X.org by doing that via the login screen, so even on X.org I still get the pesky black screen, except for Simple Screen Recorder (Snappy Edition). Simple Screen Recorder (Snappy Edition) actually works, it records both video and sound! Except there's a problem with the image quality of the video, the video appears to be recording at less than 24 frames per second or something, the video quality just looks terrible as hell, it just looks bad. 

Oh! So Ubuntu 22.04 LTS has a built-in screen recorder that works great! Except guess what? it doesn't record sound! So the built-in screen recorder on 22.04 works well, the image quality seems to be good, but it doesn't record sound.

So it appears to me that literally all the screen recorders are broken on 22.04 LTS. 

Just to let you know my PC was built back in 2015, it's got an AMD CPU and an AMD mid range GPU (mid range for 2015 when I built it), with 16 gigs of ram. Because I have seen people say that Kazam works well for them on 22.04 but Kazam doesn't work for me at all, but maybe it's cause my PC is almost 9 years old now?

So just to clarify when I was on 20.04 LTS the only screen recorder that worked well for me was Simple Screen Recorder (I'm not sure if it was the Snappy Edition or not, can't remember that part).

So this is very disappointing, because not a single screen recorder is working correctly on 22.04 for me! The built-in screen recorder appears to work well but it doesn't record sound, why would the developers make a built-in screen recorder that doesn't record sound? That just doesn't make any sense.

 Seriously I feel very discouraged right now, I needed to record something earlier and that's when I realized that none of the screen recorders worked. I mean am I the only one having issues with this?

Edit: On X.org on Kazam, it actually does record the screen but it's way zoomed in on the upper left portion of the screen, and there's sound, so Kazam works but it's not working properly, none of the screen recorders work properly.

---

### Post by TheFu on 2023-12-17
Don't use wayland, use xorg and SSR will work.  Before you login, select the "gear" icon and choose the X11 or Xorg option. Then use your system as normal.

As for sound not being recorded, you'll need to pick the correct input for the sound you want recorded.

---

### Post by SpaceManJack on 2023-12-18
> **TheFu said:**
> Don't use wayland, use xorg and SSR will work.  Before you login, select the "gear" icon and choose the X11 or Xorg option. Then use your system as normal.

As for sound not being recorded, you'll need to pick the correct input for the sound you want recorded.

Did you read my post in it's entirety? I'm having issues on X.org as well. I mean I will try it again at least just to make sure.

So you're having absolutely no issues with the screen recorders?

And you know what kind of irritates me, is that 22.04 has a built-in screen recorder that seems to work very well, but it doesn't record sound, why would the developers do that? This is something I hope they fix with 24.04 LTS.

Do you think I'm having issues because my computer is almost 9 years old?

---

### Post by TheFu on 2023-12-18
> **scott130 said:**
> Did you read my post in it's entirety? I'm having issues on X.org as well. I mean I will try it again at least just to make sure. You say X11 works, then complained about 21.04, so I figured you were venting.  

> **scott130 said:**
> So you're having absolutely no issues with the screen recorders?

I use SSR and it works. If something works, I don't go looking for other software.

> **scott130 said:**
> 
And you know what kind of irritates me, is that 22.04 has a built-in screen recorder that seems to work very well, but it doesn't record sound, why would the developers do that? This is something I hope they fix with 24.04 LTS.

We've been over that in another thread. You consider it broken. Not everyone does.  You could record the audio using another program.  I do that sometimes when I want the screen from 1 website and audio from radio, for example. Afterwards, I mux the two streams and synchronize them using a few key locations in both recordings.

> **scott130 said:**
> 
Do you think I'm having issues because my computer is almost 9 years old?
I think you are having issues because you don't have the correct settings for what you want to record that match the performance characteristics for what your computer can handle.  9 yrs ago, computers weren't necessarily slow, but they weren't as fast as they are today.  When setting the video recording parameters, choose a video codec that trades file size for using less CPU.  If you can, reduce the resolution too.  This will make for better quality recordings. After the fact, perhaps overnight, you can re-encode the streams down to much smaller file sizes.  I can't look at my normal SSR settings - hardware issue happened yesterday that I haven't figured out. It runs, but doesn't have any video output, so I've been using a different workstation and accessing the programs on that other box using remote X11 (which has been part of X11 since the 1980s).  From memory, I select a fixed rectangle to record and check teh Record audio box pointing at the PulseAudio devices and pick the same stream I send to the speakers on the system.

I use MKV containers, h.264, 30 FPS, "superfast" as the preset with QR at 23 and vorbis 160 Kbps as the audio codec.  Superfast with h.264 means the files will be 3x larger than I'd like, buy saving them uses much less CPU.  If I need higher quality, I'll lower the QR, perhaps to 20.  This changes the CPU used a bunch.  

If I'm recording a website that isn't video, I'll drop the frame rate to 5 fps in stead of 30 fps.  That alone makes the CPU needed about 1/6th.  For presentations and a talking head, this is more than sufficient.  It isn't like I'm recording explosions in a movie.

---

### Post by SpaceManJack on 2023-12-19
@TheFu It is totally unacceptable that the developers made a built-in screen recorder for 22.04 that doesn't record audio, this is totally unaccepable!!!! I repeat, that is totally unacceptable and I hope they fix it with 24.04 LTS. Who the hell wants a screen recorder that doesn't also record the audio?

"You say X11 works, then complained about 21.04, so I figured you were venting."

What's the difference between X11 and X.org, are they the same thing? Listen to me, I never said a dang thing about 21.04, will your please go back and read my post in it's entirety? Please read it carefully cause I'm very specific about what's going on.

From what I can remember, Simple Screen Recorder was the only screen recorder that worked properly for me on 20.04 LTS. Now here I am on 22.04 LTS and none of the screen recorders are working properly for me. Please go back and read my post again, I'm very specific about all of this.

So just a couple of years ago SSR worked for me and now on 22.04 it doesn't. The only screen recorder that works properly for me on 22.04 is the built-in one but it doesn't record sound so it's useless for me. 

Again, it's completely unacceptable that they made a built-in screen recorder that doesn't record sound, this infuriates me actually. I want to pull my hair out cause none of the screen recorders are working properly.

If my PC is too slow to run a screen recorder then how come it was working fine just a couple of years ago?

---

### Post by SpaceManJack on 2023-12-19
So actually I just checked and the built in screen recorder doesn't work properly at all, the video comes out all juttery. You know my PC was built in 2015, the CPU in my PC originally came out in 2012. So yeah I've got an old PC at this point. I bet I'm having these issues simply cause I'm using ancient hardware. Though to be fair on Windows 8 I never had any problems. But everything has been designed for Windows to begin with, that's why. Everything we buy has been designed to work for Windows. 

I've got a 1080p webcam that worked fine on Windows but it doesn't work properly on Linux. Logitech doesn't even off their first party software for Linux at all. Everything was made for Windows. 

Well I hope I can get some answers here from the experts?

---

