---
title: "What terminal command line to uninstall Snes9x?"
date: 2014-11-28
forum: General Help
---

### Post by michael-piziak on 2014-11-28
What terminal command line(s) can I use to uninstall Snes9x.  It works on my system but won't work on my sisters system.

This is what I used to install it

```
sudo add-apt-repository ppa:bearoso/ppa
sudo apt-get update
sudo apt-get install snes9x-gtk
```

Now, how to uninstall it with Terminal  - I can't seem to drag it to the trash.

---

### Post by deadflowr on 2014-11-28
Replace the word install with the word purge.
```
sudo apt-get purge snes9x-gtk
```
Then to remove the ppa add --remove
```
sudo add-apt-repository --remove ppa:bearosa/ppa
```
I would run an apt-get clean,
then re-run apt-get update.
```
sudo apt-get clean
sudo apt-get update
```

---

### Post by michael-piziak on 2014-11-28
ok, when I ran "sudo add-apt-repository --remove ppa:bearosa/ppa" 
I got the message "Cannot access PPA ([https://launchpad.net/api/1.0/~bearosa/+archive/pp](https://launchpad.net/api/1.0/~bearosa/+archive/pp)) to get PPA information, please check your internet connection."

?

Can I skip this part and go on to the clean and update code lines ?

---

### Post by deadflowr on 2014-11-28
Try removing the second ppa, the one at the end, that looks like /ppa.
(simply ppa:bearosa --no /ppa at the end) ;
Running clean and update commands won't mean anything if the ppa is not removed or disabled.

---

### Post by mcduck on 2014-11-28
```
sudo add-apt-repository --remove ppa:bearoso/ppa
```
It's just a typo in the command, the PPA is called bearos**o**, not bearos**a**... ;)

---

### Post by deadflowr on 2014-11-28
> **mcduck said:**
> ```
sudo add-apt-repository --remove ppa:bearoso/ppa
```
It's just a typo in the command, the PPA is called bearos**o**, not bearos**a**... ;)


:lolflag:
I should learn to read again.

---

### Post by michael-piziak on 2014-11-28
Thanks for that mcduck

also thanks deadflowr

thread marked solved

---

### Post by mcduck on 2014-11-28
> **deadflowr said:**
> :lolflag:
I should learn to read again.

Happens to everyone.

My sound designer's been complaining about the security guards in the game I'm making not playing some dialogues for months now, and today I just realised the slightly misspelled "play_gaurd_searching" event in the middle of the AI code. I must have gone through the code hundreds of times without spotting that one... Typos and coding & shell commands don't seem to work well together :D

---

