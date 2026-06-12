---
title: "What's With Sound in Linux?"
date: 2008-02-21
forum: General Help
---

### Post by GenuineXP on 2008-02-21
I don't understand why Linux seems to only allow exclusive access to sound. Somehow, Windows seems to magically dish sound resources out to just about every application, and only on very rare occasions did I ever encounter a situation where I had to close one application to allow another access to sound hardware.

With Ubuntu, this problem happens all the time. Virtually everyday, actually. If I want to play Teewars, but a YouTube video is open in some tab in Firefox, BOOM! No sound for Teewars. Or Ardour. Or Aldrin. In fact, if any of these four applications are in use, they kill sound access between one another. Why should having a YouTube video sitting idle in a browser tab kick out sound in games like Teewars and Sauerbraten?

This is a bit frustrating, particularly when a media application fails because another application is still running minimized in another workspace. I don't like having to switch back in forth via closing and rerunning applications. Are there any fixes for this? Why does sound work this way in Ubuntu and not Windows?

Any insight is appreciated. Thanks.

---

### Post by Steveway on 2008-02-21
You have to use a soundserver like Pulsaudio, ESD or Jack (though Jack is for more advanced sounduses).
If you are running one of these then set up the applications so that they use the soundserver.

---

### Post by loserboy on 2008-02-21
i've heard some people fixing by going to sound setting and selecting OSS, but I also hear that OSS is suppose to be lower quality

edit: er it sounds like steve knows more than me....

---

### Post by jespdj on 2008-02-21
Sound in Ubuntu is most likely going to be much better in the next version (8.04), because then the PulseAudio sound system will be included.

See this week's Ubuntu Newsletter: [Ubuntu Weekly Newsletter issue 78](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue78)

---

### Post by GenuineXP on 2008-02-21
> **jespdj said:**
> Sound in Ubuntu is most likely going to be much better in the next version (8.04), because then the PulseAudio sound system will be included.

See this week's Ubuntu Newsletter: [Ubuntu Weekly Newsletter issue 78](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue78)
Sounds cool. In the meantime, is there a way I could set up one of these sound servers such as PulseAudio? I know I have JACK installed since I connect to it in order to use Ardour, but I don't know much about it. If there's a guide, I'll probably need it! :p

Thanks for the replies.

---

### Post by jespdj on 2008-02-21
Have a look at: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

