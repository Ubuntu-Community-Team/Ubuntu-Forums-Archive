---
title: "Virtualbox and Seamless Virtualization"
date: 2007-04-28
forum: General Help
---

### Post by ronald_stall on 2007-04-28
I am running Feisty and have installed Virtualbox so my wife can still user her WinXP programs. I followed the instructions that were fantastic by the way at [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox[/COLOR]]("http://ubuntuforums.org/showthread.php?t=340113&highlight=VirtualBox")

It worked first time though. I installed WindowsXP Media Center Edition which I guess is based on WinXP Pro.

This is my question: How do I implement the "Seamless Virtualization". I understand I have to setup Host networking but not sure how to accomplish this as well as rdesktop. Is there a step-by-step tutorial that anyone can confirm works?

Oh just another note, Once Virtualbox was installed, then my WinXP guest. It setup with NAT and accessed the internet, other computers on my home network, and to my home printer on another WinXP printer. All with no addition configuration. And it seems to be fast as well.

Please help with my above question and thank you!

---

### Post by SendDerek on 2007-04-29
Maybe this will help?

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

I understand that it's a guide on qemu, but the seamless virtualization carried the same concept across the VM's.

---

### Post by ronald_stall on 2007-05-02
I've got host networking working but when I try and run the command 

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p passwor
```d of course using my VM IP and user and password as required.

I get this output

Autoselected keyboard map en-us
ERROR: connect: Connection refused


Any ideas what I've done wrong?

---

### Post by Term1n4l on 2007-05-09
I had the same problem until I tried it in a terminal as root. Then I received a new problem, 
I am using Feisty Fawn with a KQemu WindowsXP.img 

I input this...

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:3389 -u "admin" -p "password"

and receive......

Autoselected keyboard map en-us
ERROR: Failed to open display:

Has anyone else ran into this problem, or knows how to fix it?

I am using an NVIDIA graphics card with the NVIDIA settings found here:
[http://www.albertomilone.com/guides.html](http://www.albertomilone.com/guides.html)

---

### Post by ronald_stall on 2007-05-14
I got the same error at first, this is what I found out.

This is the only way I can get this to work but just does not seem quite right.

I startup my Virtualbox guest which is WinXP, I must login, then logout. Silly huh. If I skip this step it fails completely and get the error mentioned.

Then I launch a WinXP application like

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\System32\sol.exe" 192.168.1.105 -u user -p password
```

And I'll be darn it works! Problem is once you close out of the app you launched you must power off your guest and startup and do it all over again or it will not run any other app. This certainly does not seem "Seamless".

Anyone else have any success?

---

### Post by Term1n4l on 2007-05-14
Hey I did exactly as you said and it DID work! You're right though, this doesn't seem very seamless at all. I will try using CMD.EXE to see if I can open multiple programs through one session of QEmu. Even with KQemu it runs very slow. If you find anything else please post! :)


EDIT:

using CMD allowed me the ability to open more than one program using one session of QEmu. I'm going to continue messing with it, so far I have crashed when opening adobe acrobat reader.

---

### Post by starfry on 2007-07-16
When I tried this, CMD.EXE was the one thing that would not appear. I think it is down to how it is coded - it's somehow different to a "normal" windows app. The solution suggested to me at the time was to download an alternatve to CMD.EXE.

---

