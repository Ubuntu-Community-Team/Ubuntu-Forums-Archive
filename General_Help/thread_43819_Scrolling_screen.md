---
title: "Scrolling screen"
date: 2005-06-23
forum: General Help
---

### Post by swong1 on 2005-06-23
Dear fellow ubunters O:) 

Like many people, I registered because I have a problem. I recently downloaded the Ubuntu live CD and ran it on my laptop (Dell 6000 widescreen 1280x800, ATI x300). When I typed <ENTER> at the prompt, my screen won't stop scrolling. However, I kept typing <ENTER> to select the default settings (language, etc.). When Ubuntu finally finished booting, the screen stopped scrolling and the Ubuntu desktop appears. I checked the display setting and it correctly shows 1280x800, 60Hz. So, my question is, what caused the problem and how to solve it? I searched this forum and there were a few posts that relates to similar problem, I couldn't understand any of the solution. Any help is much appreciated. Thank you for your time.

---

### Post by desdinova on 2005-06-23
[QUOTE=swong1]Dear fellow ubunters O:) 

Like many people, I registered because I have a problem. I recently downloaded the Ubuntu live CD and ran it on my laptop (Dell 6000 widescreen 1280x800, ATI x300). When I typed <ENTER> at the prompt, my screen won't stop scrolling. However, I kept typing <ENTER> to select the default settings (language, etc.). When Ubuntu finally finished booting, the screen stopped scrolling and the Ubuntu desktop appears. I checked the display setting and it correctly shows 1280x800, 60Hz. So, my question is, what caused the problem and how to solve it? I searched this forum and there were a few posts that relates to similar problem, I couldn't understand any of the solution. Any help is much appreciated. Thank you for your time.[/QUOTE]

Is it still scrolling in X (the graphical side) - if its just scrolling during boot one way around it may be to install splashy and use a custom graphical boot

---

### Post by swong1 on 2005-06-23
Hi destinova,

Thanks very much for your reply. I don't exactly know what X is. But if you mean the login screen and the gnome desktop, yes, they don't scroll. It only scroll during the boot process. Your suggestion is interesting, but does it work on live cd? Furthermore, the problem is still there. Is it some bug the developer should know about?

---

### Post by virgule on 2005-06-23
What do you mean by 'scroll'?
 Does it look like a 'bad signal' kind of scrolling or is it some white texts scrolling by real fast?

---

### Post by swong1 on 2005-06-23
[QUOTE=virgule]What do you mean by 'scroll'?
 Does it look like a 'bad signal' kind of scrolling or is it some white texts scrolling by real fast?[/QUOTE]

Hi Virgule,

Both the text and the dialog box (language settings, etc.) scroll up real fast, like when you watch tv and the images move up vertically. This only happens during the boot-up process. As a result, I don't know which settings I chosed. I just click <ENTER> blindly until it finished booting-up.

---

### Post by desdinova on 2005-06-23
[QUOTE=swong1]Hi destinova,

Thanks very much for your reply. I don't exactly know what X is. But if you mean the login screen and the gnome desktop, yes, they don't scroll. It only scroll during the boot process. Your suggestion is interesting, but does it work on live cd? Furthermore, the problem is still there. Is it some bug the developer should know about?[/QUOTE]

As it boots it should all scroll by as it tells you which services etc have run - pressing ctrl-Page up as i recall enables you to read it but once you've selected to boot linux there should be no more interaction from you till the Graphical Login

---

### Post by swong1 on 2005-06-23
[QUOTE=desdinova]As it boots it should all scroll by as it tells you which services etc have run - pressing ctrl-Page up as i recall enables you to read it but once you've selected to boot linux there should be no more interaction from you till the Graphical Login[/QUOTE]

I understand what you mean. It is not the normal scrolling of text I talk about. I am familiar with that. It scrolls way faster than that. It also scrolls when it prompts you to select a language setting, date/time etc. I don't know what else is there, because they scroll by so fast, I couldn't see clearly. I just press <ENTER> to select the default settings.  Thanks very much for your time. 

Here is an example of the screenshot you normally see.

[http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=2](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=2)

However, in my case, the screen keeps scrolling up very quickly.

---

### Post by swong1 on 2005-06-24
Dear destinova and virgule,

Thank you very much for your kind response. I was able to solve the problem by typing

live vga=771 <ENTER>

intead of just <ENTER> at the  command prompt prior to boot-up.

---

