---
title: "is there any workaround for Adobe Flash missing?"
date: 2021-07-11
forum: General Help
---

### Post by rebeltaz on 2021-07-11
I do not understand why adobe decided to deactivate flash on systems with no regards to what the end user wants, but...

I have a DVR that REQUIRES flash to be able to view the video stream. Is there any workaround for either firefox or brave browser that I can use without having to go out and purchase a new system?

---

### Post by Dennis N on 2021-07-11
> is there any workaround for Adobe Flash missing? 
Maybe - for some uses. You can play flash .swf files with Adobe Flash Player packaged as a Flatpak. It's a stand-alone application that does not require your browser to work. I use it to play some flash games I had acquired in the past.
```
dmn@Tyana-vm:~$ flatpak search adobe
Name                        Description                                           Application ID                            Version            Branch         Remotes
Adobe Flash Player          Player for content created using Adobe Flash          com.adobe.Flash-Player-Projector          32.0.0.465         stable         flathub

```

---

### Post by HermanAB on 2021-07-11
Hmm, go to a junk shop and get a better 2nd hand DVR?

---

### Post by rebeltaz on 2021-07-11
> **Dennis N said:**
> Maybe - for some uses. You can play flash .swf files with Adobe Flash Player packaged as a Flatpak. It's a stand-alone application that does not require your browser to work. I use it to play some flash games I had acquired in the past.
```
dmn@Tyana-vm:~$ flatpak search adobe
Name                        Description                                           Application ID                            Version            Branch         Remotes
Adobe Flash Player          Player for content created using Adobe Flash          com.adobe.Flash-Player-Projector          32.0.0.465         stable         flathub

```

Will that work with streaming video through the browser? That's how the interface to this DVR is set up. I'll check it out. Thanks. 

> **HermanAB said:**
> Hmm, go to a junk shop and get a better 2nd hand DVR?

lol... out here in my neck of the woods, they wouldn't know a DVR from DVD :)

---

### Post by CatKiller on 2021-07-11
> **rebeltaz said:**
> Will that work with streaming video through the browser? 
No. The end of Flash was announced years ago, the specific date for the death of Flash was announced at least four years ago, and it was specifically killed on 31 December 2020, by which point every browser had purged all support for it. It is dead, and its death was a long time coming. 

There are some sandboxed solutions for standalone Flash applications, but not for in a browser. It's just too insecure.

---

### Post by monkeybrain20122 on 2021-07-11
old Windows firefox and old flash running in wine and block all internet access? I remember back in the bad old days there was a [Netflix desktop app for Linux]("http://www.webupd8.org/2012/11/how-to-use-netflix-in-ubuntu-through.html") which was basically a version of Windows FF running in wine because of flash.

Or maybe VM?

---

