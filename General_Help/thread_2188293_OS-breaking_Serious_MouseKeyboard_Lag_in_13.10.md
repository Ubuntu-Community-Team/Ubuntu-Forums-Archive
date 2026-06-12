---
title: "OS-breaking Serious Mouse/Keyboard Lag in 13.10"
date: 2013-11-16
forum: General Help
---

### Post by luke-chasteen on 2013-11-16
So I'm finally getting around to updating my Ubuntu installations to 13.10, but while it worked just fine on my laptop, my desktop has turned into a real head-scratcher. And before anyone asks, I pretty much always do clean installs, and I've certainly stuck to that method in this case. So here's the story: originally I was going to install Xubuntu, but when I booted up into the live CD environment I found that mouse and keyboard input was horrifically slow. The OS itself ran smoothly as evidenced by animations and quick responses whenever I actually managed to click something, but input was totally messed up. Initially I thought the mouse just wasn't working at all, but then I realized that it was moving just the slightest bit. Keyboard was even worse, though, because while at least the mouse worked--albeit unusably slowly--every key press I made repeated itself exactly 10 times. I thought perhaps it was just an issue with the live CD, so I went ahead and installed Xubuntu--which took me *45 minutes to start.* *45 minutes *in that installation wizard that I normally breeze through in five. That's how slow we're talking, here. Of course, to type in a user name and password I had to open up Mousepad, type one letter, let it repeat 10 times, copy just one of the letters, paste it, and repeat. That certainly added to the time, considerably. And after all that, the installed Xubuntu was no different. Booted up and the lag was still there.

So then I tried normal Ubuntu. The live CD fared better here. Keyboard worked, and although the mouse acceleration was oddly slow, it was entirely usable. And hey, no biggie, I can adjust mouse acceleration once the OS is installed, right? Wrong. As soon as everything was installed and I booted up and found everything to be just as bad as in Xubuntu. The problem persists in a TTY environment, too. System itself is smooth, input is farthest possible thing from it without being totally broken.

I'm pretty baffled by this one, and the real trouble is the solution can't involve typing anything into a console--or anywhere, for that matter. I can still copy/paste, though, and edit Ubuntu files from Windows.

Thanks in advance.

UPDATE: Issue persists in Fedora 19 Live CD as well. Keyboard only repeated presses once instead of 10 times, though. Mouse was just as bad. Starting to think its a hardware compatibility issue, but what on earth could cause this kind of behavior? Since I last had Linux on the PC I've installed some extra RAM and an old IDE hard drive I ripped from a PC that was on its way to the trash bin. Seems like those should be harmless enough, though.

---

