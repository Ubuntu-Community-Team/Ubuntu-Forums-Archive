---
title: "Where are programs and restricted drives installed?"
date: 2007-12-03
forum: General Help
---

### Post by lszanto on 2007-12-03
Hey, this may seem like a dumb question but i just wanted to know where restricted drivers and programs are installed ect. As I am reinstalling and about to make my partitions and wanted to know as my installs keep mucking up after a few hours and each time I get all my applications I want installed so I just want to put things in my /home/ on a different partition so I don't have to reinstall everything each time.

thanks in advance, Luke

---

### Post by -grubby on 2007-12-03
the executables are in /usr/bin and your configs are under their respective ./ directories in /home/username (see by hitting ctrl-h or alt-dot)

---

### Post by erfahren on 2007-12-03
> **lszanto said:**
> ... and each time I get all my applications I want installed so I just want to put things in my /home/ on a different partition so I don't have to reinstall everything each time.

That really wouldn't work. Having a separate /home is handy but it's so you can reinstall the OS without having to move/overwrite all your configuration, saved files and the like.

One thing I wanted to mention: when you install programs using Synaptic (or apt I imagine) the downloaded .debs are stored, see: [http://ubuntuforums.org/showpost.php?p=1889472&postcount=6](http://ubuntuforums.org/showpost.php?p=1889472&postcount=6)

You can also make a download script using Synaptic (File > Generate package download script)
(I guess you could also use the terminal to get a list of the .debs in the directory and then do "sudo dpkg -i <package.deb> <package.deb> <package.deb>" , etc. )

if you used both of those procedures together it could take a lot less time and trouble to install the programs. 

I ended up reinstalling two or three times when I first started using Ubuntu (I'm assuming your somewhat new to it). I'm sure alot of people do. I found that over time I messed everything up less and less though. Some things I did in the beginning that I thought would be difficult/impossible to fix I now know are quite fixable. 

So if your installs are getting messed up over something you inadvertently did I don't think you need to expect that to continually happen.

---

### Post by disturbedite on 2007-12-03
if you wanna know where the files of a particular program/package are installed you can look in synaptic under "Installed Files".

---

