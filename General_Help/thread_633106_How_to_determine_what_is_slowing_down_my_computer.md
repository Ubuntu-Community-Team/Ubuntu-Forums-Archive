---
title: "How to determine what is slowing down my computer?"
date: 2007-12-06
forum: General Help
---

### Post by tetrafuran on 2007-12-06
My old edgy eft ran fairly well, but after all the necessary updating I have ended up with a tardy tortoise or slumberous snail, instead of a gutsy gibbon. 

Just drawing the user interface of k-torrent or open office seems to take several seconds. I could actually tell you the order in which buttons, texts and other things things appear on the screen one by one. Wasn't all this supposed to take just milliseconds? If I were running windows, I would automatically blame melware for all this. Resizing an open office window sends the cpu graph above 90% for a few seconds. Opening the settings from k-torrent does the same. It doesn't seem to have anything to do with memory since I have plenty of it available at all times.

Hardware clearly isn't an issue since previously everything ran very smoothly. For the sake of tradition, here's what's inside the box: AMD 64 atlon 3200+, 512 RAM, geforce 440 MX. 

I was able to come up with a list of possible reasons, so please cross out the unlikely far fetched ones. 

1) Something new and resource hungry was installed. I have no idea what it could be. I disabled all the fancy compiz effects after playing around with them for a day or two. Something else came with the update apparently. 

2) Something to do with drivers libraries or stuff. Recently I have installed lots of libraries and stuff in attempt to play a 3d game called Rigs on Rods. Perhaps too much is too much.

3) I have too much stuff installed in general. I have xfce, fluxbox and iceWM. I use none of them since all of them have their crazy configuration issues and uncontrollable "features". I have been unable to solve them despite my considerable efforts in seeking knowledge and asking questions. In fact there are lots and lots of unsolved issues all over the system.

4) I'm using gnome, but k-torrent uses some files from KDE. Perhaps some speed could be atteined by using software optimized for gnome.

---

### Post by bingoUV on 2007-12-06
See if trackerd is running. It might slow down things initially until it indexes all your stuff once. Then it should index only the changed files, and so should be generally fast.

Try killing trackerd if it is running, and see if it makes some difference in some time.

---

### Post by eentonig on 2007-12-06
install htop and see what process are running

You can sort by cpu-usage and memory footprint. You could also use the regular top for this, but htop has some nice extras like adjusting the 'nice' value of a running process, etc.

I had a similar issue and found that Xgl was stealing all my ressources, even with Compiz disabled. So I removed it and tried Aiglx instead.

---

### Post by tetrafuran on 2007-12-06
Trackerd is sleeping. I have disabled indexing any way.

htop seems to be very much like system monitor. However it did reveal that I have Xgl running and metacity running. I always thought that they weren't necessary for running gnome.

Unfortunately this doesn't explain why certain gui programs started to misbehave after the upgrade.

---

### Post by Crakie on 2007-12-06
If things got so messy, perhaps a complete reinstall is in order. Although the update proces is definetely getting better with each release, it seems it still cannot compete with a full reinstall. I know it sounds like a "Windows solution", but it works. And with a backup of at least /etc and /home, you will have your stuff running the way you want it in no time.

---

### Post by tetrafuran on 2007-12-08
I'm beginning to think so too. Perhaps this time I'll just go for fluxbuntu. First I'll need to find a place for all my important stuff. I'm kind of worried about loosing my data in re-installation process, so I'll just use another hard drive for this.

---

