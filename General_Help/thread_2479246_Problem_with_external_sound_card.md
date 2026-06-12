---
title: "Problem with external sound card"
date: 2022-09-19
forum: General Help
---

### Post by akaravial on 2022-09-19
Hi there, just a new linux user here. Recently I removed windows and move on to linux. I solved some problems on my way to setup everything. But there is only one that is giving me nightmares, i cannot solve it:

Problem: On discord, audacity, etc. When using any mic ( internal or the one i connect to external sound card unitek y-247A ). I have a really annoying noise, I mean, captured audio has it. It is really noisy, a mix of interferences and popping.

SO Version: Ubuntu 22.04.1 LTS Linux 5.15.0-47-generic #51-Ubuntu SMP Thu Aug 11 07:51:15 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Gnome version: 42.4

Sound card: ( aplay --list-devices command , lspci do not display it today, dont know why ) PCH [HDA Intel PCH] ALC256 Analog 

Alsa: [internal]("https://i.postimg.cc/6Qr3DjQK/Screenshot-from-2022-09-19-18-51-46.png")     [external]("https://i.postimg.cc/vZ3M9JDc/Screenshot-from-2022-09-19-18-56-37.png") 

I tried some solutions i found, but it didnt work. 

If more info is needed, tell me, i will post it ASAP.

Thanks!

---

### Post by HermanAB on 2022-09-22
OK, this may sound silly, but the usual solution with sound issues is to run a volume control application (pavucontrol) and turn ALL volume knobs down, then turn them up one by one to figure out what they do.  One of the inputs is probably stuck at 100% and picking up electronic noise.

---

### Post by gsahli on 2022-09-22
Sorry, I don't know the cause of this problem, but...
I had exactly this problem too. I changed microphone AND USB external sound card brands, and the problem went away. The one that's working also says Y-247A.

---

### Post by ActionParsnip on 2022-09-22
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Follow that until Step 3. Please give the URL generated.

---

