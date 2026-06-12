---
title: "How do i uninstall Real Player on ubuntu 12.04?"
date: 2014-01-12
forum: General Help
---

### Post by deaton25 on 2014-01-12
I installed Real Player right from their website with a debian package sent to my download file that was opened up through the software center. I decided to uninstall it. And deleted the debian file.And destroyed the trash. It did not work!
There was no record of it at the software centre; hence, nothing there to uninstall.I went to the console and used a wide variety of methods recommended on Ubuntu forums.. One response said that I could not uninstall it because it was "virtual"! HUH???
Where i come from, if you can't uninstall something easily, we call it MALWARE.
Can you help,please.Thanks

---

### Post by grier-devon on 2014-01-12
try.....
```
                              sudo dpkg -r realplay xxxx
```

Where the xxxx is you need to put the correct version of realplayer. if I may ask since it has been years since I have even seen real player is what do you use it for? Isn't it just a media player that supports a lot of formats? Why not just use VLC?

---

### Post by deaton25 on 2014-01-12
Many thanks for your help! Your idea worked!
The reason i wanted Real Player was because it has Helix-Player. On the forums here, I heard that the installation of Helix-Player was a way to get text/html decoder plugins for python 2.7 that I needed in order  to get 
some internet radio stations on an internet radio portal to work, In other words, it had nothing to do with Real Player!!!!

How do I get text/html decoder plugins for Python 2.7? I have tried all the methods suggested on the forums here.They did not work. In addition to the above, I also tried Gecko Media Player as Gnome Player and all the Ubuntu restricted programs.They did not work either!Python 2.7 keeps looking for these text/html plugins but cannot find them! 
Can you help or should I open up another question box

Also, I work off of Chrome on Ubuntu. The TCP Optimizer people claim that my Rwin values are way to low
I know that TCP Optimizer is designed for Windows. But there is a Wine based version available.
Is this worth checking out? Failing that what codes should I punch in at the console to crank up my Rwin?
I'm told that Linux now auto-adjusts these things. But if that's the case, then why are my Rwin scores so low?!
A print out is available upon request
Can you help or should I open up yet another question box?

Anyways, thanks for helping me get rid of that Real Player junk!!!!!!!!!

---

### Post by grier-devon on 2014-01-13
I would open another question box, those are not something I familiar with. Glad that worked though for you.

---

### Post by 3rdalbum on 2014-01-13
"text/html" is not an audio or video format. It's a web page. Those stations might only be able to be listened to through a web browser, or maybe you need to open that address in your browser and you'll then receive a link to the actual radio stream.

Nothing can play "text/html" because it's not something to play. It's like trying to listen to a JPEG.

I don't know much about TCP but I do know that a Windows program running in Wine would not be able to make changes to the internal Linux system settings. If you've had any readings on Windows through that program, most of them wouldn't apply to any other operating systems on the same computer. If you've had any readings when running that program in Wine, you can probably safely assume they are erroneous.

---

