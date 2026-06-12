---
title: "How can I boot without loading X?"
date: 2007-07-02
forum: General Help
---

### Post by mattym129 on 2007-07-02
Hi all,

Sorry if this has been asked many times before, you may flame me and call me an ignorant British retard etc. etc., but I could not find a straight answer withing 20 minutes of Googling. I have set up Ubuntu on my server perfectly, as Windoze was being a slug at the best of times, and now I want to boot into a console and have the ability to start X with 'startx' if I need it. I am asking for someone to give me simple instructions to configure my system to do this. I am fairly confident with the console, and actually prefer it to going though the GUI configurations, hence me wanting to boot to a console.

Oh, and please don't bother warning me about the huge, detrimental, life-threatening side effects of being in root for more than 3 nanoseconds, a reinstall is not a real problem.

Thanks in advance, Matty :p.

---

### Post by oldmanstan on 2007-07-02
one option would be to just boot into x then shut it down by doing ctrl-alt-F1 then issuing ```
sudo /etc/init.d/gdm stop
```
that work?

[this thread]("https://answers.launchpad.net/upstart/+question/6093") on launchpad has a solution, 3rd reply down, not sure if it works though but the other people seemed happy...

---

### Post by craig1709 on 2007-07-03
Assuming it boots into runlevel 5 by default, remove Gnome Desktop Manager from runlevel 5:
```
ls /etc/rc5.d/
```
Note gdm's name, in the form Sxxgdm, then do the following:
```
sudo rm /etc/rc5.d/Sxxgdm
```

You'd have to create a new symlink to get it to work again, but you'll have to look elsewhere for that.

---

### Post by persoontje on 2007-07-03
Well that will work, but runlevel 5 is special made for X, so you should configure your computer to boot in another runlevel. You should boot in runlevel 3 instead of 5.

You can do that, if it's just for once in grub, add the number you want (3) to you boot options.
You used to change that in /etc/inittab, but that's changed in the new version. You could search in your system tools in kde/gnome or maybe another user know how to change this?

---

### Post by fragos on 2007-07-03
You can boot to a terminal without X from Grub.  Select the "Recovery" image.

---

### Post by mrblack448 on 2007-07-05
i found this thread looking for the same answers the other day, but there is another one with more info here:

[http://ubuntuforums.org/showthread.php?p=2970128](http://ubuntuforums.org/showthread.php?p=2970128)

---

### Post by oldmanstan on 2007-07-05
another option, if you want to boot into a terminal all the time, you don't even have to install a gui, use the alternate install CD, it's one of the options in the menu when you boot from the CD

---

