---
title: "Gimp 2.8 tool box problem with Lubuntu 14.04"
date: 2017-02-22
forum: General Help
---

### Post by lesl2 on 2017-02-22
I just did install Lubuntu 14.04 (it's the only distro that allows my  old SIS 760 graphic card to give me the right resolution 1200 X 800) and  then did install GIMP. The problem is...no tool shows in the tool box.  The whole box is covered with black zebra lines. Then, you click where  the tool icons should be and they appear but...not those at the very  bottom (see the atttacment) Any ideas? Widening the box doesn't  help...much.
   Maybe I should say that I did download it by using the terminal typing sudo apt-get install gimp

---

### Post by DuckHook on 2017-02-23
Welcome to the forums, lesl2.

Wow. I haven't seen an SiS 760 in over a decade. Maybe closer to 15 years. Unfortunately, GIMP is unlikely to run well on such old HW.

Not all GUI apps are the same. Some, like PCManFM or LXTerminal are graphically simple. They don't require a lot of GPU horsepower. But GIMP is designed to use as much horsepower as it can get. Moreover, it assumes that—being a graphically-intensive app—it will only be run on systems that have newer video systems that support newer and more powerful graphical modes. On older hardware, the CPU probably has to emulate these modes, with varying degrees of success, not to mention the heavy load this places on the CPU itself.

You haven't provided us with your system specs. It would help if you do so now. But if they match those of your video system, then your box is likely inadequate to running GIMP. Lubuntu is a marvellous little thing that can breath new life into old machines, but it can't perform miracles. On old HW, it's meant to give them the capability to browse, word-process and manipulate spreadsheets; not perform Gaussian Blurs on semi-transparent alpha channels.

Provide us with the output from:```
sudo lshw -c system -c processor -c display -c memory -sanitize
``````
lspci -vk | grep -iA13 vga
``````
xrandr
``````
glxinfo | grep "renderer string"
```
Some of this output will be quite lengthy, so please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by lesl2 on 2017-02-23
What you did ask me to provide is like Chinese to me...and I'm not from China. The icons aren't showing but they are there. If you go over them and click it they switch on so I guess I will have to live with that. That laptop with the SIS 760 graphic card is an Acer  3003 WLMI and it's just  a back-up. I might never use it again. I guess downloading an older version of Gimp would do the trick but...maybe this isn't possible in Linux/Lubuntu ?
Seems Gimp 2.6 can be use with Linux but again, these thread looks like Chinese to me.
[http://askubuntu.com/questions/243865/how-to-go-back-to-gimp-2-6](http://askubuntu.com/questions/243865/how-to-go-back-to-gimp-2-6)

---

### Post by SeijiSensei on 2017-02-23
Does the toolbox appear if you hit Ctrl+B?

I don't know what to do about the "zebra lines."

---

### Post by DuckHook on 2017-02-23
> **lesl2 said:**
> What you did ask me to provide is like Chinese to me...and I'm not from China.:)

I've got to remember that many users have never even seen the command line, much less ever used one.

Those commands must be run by copying and pasting them into a command line app that you invoke from your menu. In Lubuntu, that command-line app is called LXTerminal and can be found in *System Tools*. You can copy the output using your mouse and paste them back to this thread within a new posting.

The info is needed to see what your current driver is, what resolution Lubuntu wants to run at vs what it actually is running at, whether any hardware acceleration is being used, and so forth. Without such info, we are essentially just taking stabs in the dark hoping that we hit something, which is a very silly and ineffective way to diagnose a problem. It's important to provide such system info and even more should it prove necessary.
> …I guess I will have to live with that.Not necessarily so if you are prepared to diagnose the problem. Of course, there are no guarantees, but only you can decide if the ultimate goal is worth the effort.
> …laptop with the SIS 760 graphic card is an Acer  3003 WLMI
It's a pretty limited machine. Your video does not have dedicated VRAM and uses shared RAM for its video memory—pretty common in the XP days—but very crippling for modern OSes. If you have not installed additional RAM to its usual default configuration, then the whole edifice is being run on 512 MB of RAM, which is barely enough for Lubuntu itself, never mind sharing with the video system. It's no wonder your video is choking.
> I guess downloading an older version of Gimp would do the trick but...maybe this isn't possible in Linux/Lubuntu ?
An older version of GIMP is unlikely to solve your problem. As already said, GIMP is a resource-heavy app—even in it's older form—that imposes heavy demands on the graphical subsystem, to which yours is frankly inadequate.
> Seems Gimp 2.6 can be use with Linux but again, these thread looks like Chinese to me.It is possible to download an older GIMP, install it, then lock it using apt-mark hold, but this involves the command-line that you seem to be allergic to. Moreover, it is unlikely to work any better than what you've got now.

If I were you, I would forego asking your little engine to pull a 200-car train. It will still serve you very well if you ask of it only what it is capable of delivering.

---

