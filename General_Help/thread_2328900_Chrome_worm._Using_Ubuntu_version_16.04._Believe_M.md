---
title: "Chrome worm. Using Ubuntu version 16.04. Believe Malware."
date: 2016-06-25
forum: General Help
---

### Post by irv on 2016-06-25
It started yesterday. I don't know how I got the worm but it keeps opening new browser windows. They all have red backgrounds and want me to buy software to get rid of the worm. This is the first time this ever happened in Linux and I have been using it for many years now. It is really Malware that got installed in chrome.
I completely removed chrome and deleted the folders. I tried clearing the history and data but this didn't do it.
After completely removing it and then downloading it new and Installing it, this seemed to fix the problem. I tried running ClamTK but it didn't find the problem.
Two questions.
Did anyone else have this problem?
and what is a good Malware checker for Ubuntu Linux?

---

### Post by RobGoss on 2016-06-25
I've never encountered anything like this can you tell me how you think you acquired this so call worm?

I've heard and read about this open software that might be of use with this
[http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

And do you still have this issue or did were you able to remove it

Here is also an interesting read you might want to check out
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by ajgreeny on 2016-06-25
I don't use chrome but I do use chromium and I have never seen anything like this on my system.

I suggest you try a new profile as a start, and then if still seeing the problem, install the uMatrix extension or similar which ought to stop it in its tracks.
[https://chrome.google.com/webstore/detail/umatrix/ogfcmafjalglgifnmanfmnieipoejdcf?hl=en-GB](https://chrome.google.com/webstore/detail/umatrix/ogfcmafjalglgifnmanfmnieipoejdcf?hl=en-GB)

---

### Post by banceu_sergiu_ione on 2016-06-25
Here is a good [Wiki]("https://en.wikipedia.org/wiki/Linux_malware#Anti-virus_applications") you may want to read is you still think your pc is infected. 
I never had any issues as this. I use Firefox and the only extra I have installed is the adblock plus with its relative adblock plus pop-up addon as extensions wich I would recommend.

If i was you I would try rkhunter or chkrootkit. But if your pc run normal, as temperature, resources used like ram/cpu i would just leave it as it is.
Get an pop-up addon blocker for future.

---

### Post by irv on 2016-06-25
The problem seems to be gone for now. It looks like the complete removal and reinstall did the trick.
I have no idea how this happen. I wish I would have taken some screen shots of the red windows in Chrome, but I didn't. I am marking this thread solved but I wanted to put it our here in case someone else has a problem like this. It was only in Chrome that this happened. FireFox worked Okay.
Thanks for the input on this thread.
Edit: I forgot to mention that when this happen it keep making a loud irritating noise until I rebooted the computer.

---

### Post by ardouronerous on 2016-06-25
Damn that is scary, I guess you debunked the myth that Linux is immuned to viruses, malwares and worms.

That's probably why I have NoScript, Adblock Plus, Ghostery, HTTPs Everywhere installed on my Firefox.

---

### Post by Omar_Jair on 2016-06-25
No system is invincible, even linux has its tiny holes where a virus can get in.
By the way, did you download any 3rd party thing? maybe you could have gotten infected with that.

---

### Post by ardouronerous on 2016-06-25
Good you admit that, because in my 5 years of using Xubuntu, I've come across users that make claims like, "there is no virus for Linux".

---

### Post by ajgreeny on 2016-06-25
> **ardouronerous said:**
> Good you admit that, because in my 5 years of using Xubuntu, I've come across users that make claims like, "there is no virus for Linux".
And it is still true; there are no Linux viruses in the wild, only proof of concept viruses.
There are, however, trojans and worms that are potentially dangerous and often cross platform.
Don't forget the biggest security weakness in most computers is the person pressing the buttons, not the software.

---

### Post by irv on 2016-06-27
Now I am not saying this is what happen, but the only thing I can think of that was downloaded was a windows exe. No, I am not using Wine.
Let me explain. I got an email that looked like it was from WinZip, the file name was "wzsus45.exe" I have a win10 on the same machine so I switch to windows and ran Malwarebytes and it found malware in the file so it deleted it and I didn't install it.
When I rebooted and got back into Ubuntu 16.04 that's when it seem the problem popped up. Like I said, I can't see how that had anything to do with this problem, but I can't think of any other download from a third party. I update software a lot so maybe?
In any case, the problem is fixed and I am back to normal, but my wife tells me I never was normal.

---

### Post by Habitual on 2016-06-27
Any File you ever have doubts about, upload it to virustotal.com and let them have their way with it.

Were you expecting email from Winzip ?

---

### Post by X-RED_Tech on 2016-06-27
If your Chrome in Windows was compromised then it synced to your Chrome in Ubuntu.

> [COLOR=#000000]There are, however, trojans and worms that are potentially dangerous and often **cross platform**.[/COLOR]

(My bold)

Web browsers are the attack vector, not the OS itself. Trojans/worms and similar often masquerade as "addons"/extensions and are synced to a user's profile regardless of the OS the same way legitimate addons are.

PS - Unless you cleaned it really good in Windows it will certainly reappear in Ubuntu as soon as you login with your Google account at you newly installed (and not yet synced) Chome in Ubuntu.

---

### Post by irv on 2016-06-27
You have a good point here. Chrome is one of those browsers that keeps your profile on a server that syncs to every device you use Chrome on. Like phones, tablets, Chromebooks, and computers. If your profile is compromised then it will carry over to all devices.
Before I removed Chrome I deleted the addons and extensions. After rebooting and reinstalling Chrome I then added them back in.

---

### Post by irv on 2016-06-30
Okay, today I got an email via gmail account See image: I opened it on my Chromebook and went to unsubscribe and got a red screen like I did on my Linux machine. (Malware). It seems that it is coming from bing from Microsoft.
[ATTACH=CONFIG]269870[/ATTACH]
[ATTACH=CONFIG]269871[/ATTACH]

---

### Post by uRock on 2016-06-30
> **Habitual said:**
> Any File you ever have doubts about, upload it to virustotal.com and let them have their way with it.

Were you expecting email from Winzip ?

It seems they've already had a look at it. [https://www.virustotal.com/en/file/5c5bcdcda837f6827f498d749e7e291cbc3b21c3a04bf3be48979eae94078088/analysis/](https://www.virustotal.com/en/file/5c5bcdcda837f6827f498d749e7e291cbc3b21c3a04bf3be48979eae94078088/analysis/)

---

