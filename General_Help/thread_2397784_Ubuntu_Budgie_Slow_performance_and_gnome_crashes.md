---
title: "Ubuntu Budgie Slow performance and gnome crashes"
date: 2018-08-03
forum: General Help
---

### Post by mohammadfiroz on 2018-08-03
I recently bought an inexpensive machine to learn some java on, my main laptop has ubuntu 18.04 on and runs extremely smoothly. I got the exact same configuration for the pc, 4th generation i5, 8 gb ram with the exception of using a hard drive as opposed to the m2 drive in my laptop. 
The laptop had a "u" type processor so I was easily expecting a performance bump. However to my surprise windows runs smoothly, a hiccup here and there but nothing to complain about.Budgie on the other hand has consistent crashes of system programs like settings etc. using wifi through a dongle and getting mediocre speed and so on. Programs start up slow and I think it's related to gnome control panel not opening. 

When it works, control panel does work but the rest of the time you get no error or anything, I even tried running it form terminal in verbose mode and nothing no output at all.

 
If someone can help me out it'll be greatly appreciated, I tried my best to check if some other thread could help but no cake.

---

### Post by speartip on 2018-08-03
First thing to check when it comes to performance is Graphics. What Graphics Card do you have? If anything other than Intel integrated graphics have you install the proprietary drivers?
I run Budgie on an Intel i3 processor with integrated graphics. I need to turn off animations in Budgie Desktop Settings, but other than that it's the fastest Gnome derivative I've ran.

---

### Post by mohammadfiroz on 2018-08-03
I don't have a graphics card installed, everything was working when I was in live usb mode. I have intel integrated graphics,  I didn't install any drivers I let ubuntu handle it all. I don't think it's just an animations issue, I'm using windows 10 (dual boot) and everything is super smooth and programs are starting up at decent speeds for a hard drive. 

The actual **gnome-control-centre** keeps crashing, which is very weird. I don't even think it's crashing because I'm getting no errors, even when I run it from terminal in verbose mode, nothing. Any commands you'd want me to run for more clarity on the issue?

---

### Post by speartip on 2018-08-03
This is a fully installed system isn't it? & not something you're running from a live DVD/USB?
If so, you're specs are better than mine & I would expect better performance. Did you checksum the iso image before installation? You also mention gnome-control-centre, but Budgie doesn't ship with that, as it has it's own desktop settings program. More details about how you installed would be useful.

edit. actually gnome-control-centre is installed, but has no gui in itself. You could try reinstalling it in synaptic, see if that helps.

---

### Post by mohammadfiroz on 2018-08-03
Well I was guessing that it shouldn't have the gnome-control-centre since budgie was made from the ground up. However there's literally no information available regarding the bug I'm getting, first the ubuntue budgie settings app would start crashing on me randomly, then the default control panel started just not working. It's weird cause it works the first few hours but just doesn't after a while, worst part is that I have never found a DE that I could so easily customise to my liking.

And Yes it's a complete install on my hard drive I may not be the smartest when it comes to Linux but I have about 1-2 years of experience fiddling with Linux.

---

### Post by speartip on 2018-08-03
Has this been happening since install? Or since you've customised it to your liking? I did have to disable a panel applet that was causing issues. It might help to create a new user with a clean configuration, login to that user, and see if your issues still persist. Otherwise a clean install might be the only way. Do checksum your iso image though to make sure it has no errors.

---

### Post by mohammadfiroz on 2018-08-04
Now thats a good question, I have about 6-7 applets running that I installed. I do think the first few crashes of the budgie settings app happened while I was customising.
Okay so I'll make a clean user and run a checksum, could you give me a distro that's as beautiful as Ubuntu budgie and has the software availability of Ubuntu.

---

### Post by speartip on 2018-08-04
Ubuntu Budgie IMO is probably the best looking, leanest, Gnome based Distro there is. I would try disabling all your applets 1st, if that resolves the problem, add them all back one by one until you find the culprit. In my case it was the "Windows Preview" applet, which I can live without, using the "Workspace Switcher" instead.
As far as Distro's as beautiful as Budgie, my own personal recommendation would be KDE Neon. It's not Gnome, but it's a fast, smooth, minimalistic Distro, that's well worth a look.

---

### Post by mohammadfiroz on 2018-08-05
Okay so I'll give some background to my mistakes. When I read that other people were having trouble running their settings app theyst remove gnome-control-centre through apt and reinstall. However when I remove that it remover a bunch of other things like budgie-desktop and budgie settings. I did reinstall gnome-control-centre but it didn't install those things tho 

So I just made a new user and got a really weird error.
[IMG]https://imgur.com/a/YMcPaEg[/IMG][IMG]https://i.imgur.com/S0sNNmm.jpg[/IMG][https://imgur.com/a/YMcPaEg](https://imgur.com/a/YMcPaEg)

---

### Post by mohammadfiroz on 2018-08-05
And this is what the desktop looks like [IMG]https://i.imgur.com/vm8bPTO.jpg[/IMG]

---

### Post by speartip on 2018-08-05
```
sudo apt install gnome-control-center budgie-desktop ubuntu-budgie-desktop
```
Should resolve the problem. Logout/In after running the command.

---

### Post by mohammadfiroz on 2018-08-10
Okay I'm really sorry for the late update. I tried the fix, didn't make much difference however disabling the window preview applet helped performance a bit.

I couldn't really take more delays so I just installed popOS! and it's extremely smooth so far.
Thank you so much for the help though, really appreciate it!

---

