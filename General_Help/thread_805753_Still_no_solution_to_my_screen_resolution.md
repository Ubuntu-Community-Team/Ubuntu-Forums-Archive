---
title: "Still no solution to my screen resolution"
date: 2008-05-24
forum: General Help
---

### Post by Steve Lyne on 2008-05-24
I have tried and tried to understand the recommended procedures that have been posted to try and allow my screen resolution to be adjusted. Unfortunately most of the suggestions are not detailed enough for me to follow. I am a complete beginner with Linux and to make any sense of all the advice, I need exact procedures to follow. When I am advised to enter some code, where do I enter it? Do I enter it all on one line, do I press enter after each line, etc. etc?
I would liken the advice to someone who is told to change the plugs in his car, if he has no knowledge of how to even open the bonnet, he will not be able to do what is required. Are the threads on the plugs right or left handed, don't get the leads mixedup. I hope I am not seen to be ungrateful because the speed of reply shows me that there are a lot of good hearted folk trying to help. So if someone knows how to get my screen resolution working and can provide me with 'detailed' instruction I would be most grateful.
The terms Grub, Root and Gnome sound like something out of my garden!

Many thanks Steve Lyne

---

### Post by Kevbert on 2008-05-24
What is the make and model of your graphics card and monitor ?
If you go to System-Preferences-Screen Resolution you'll see a pull down menu for resolution.  Does this allow you to set the highest resolution for your card and monitor when you press Apply ?

---

### Post by IHATEDLINK on 2008-05-24
Hey, don't panic!

Gnome is the 'desktop environment' of Ubuntu, you know, the task bars with the Applications Places System menu up and the workspace switcher on the bottom.
There are other desktop environments such as KDE. Kubuntu uses KDE. Xubuntu uses Xfce. It's just a mater of taste, although Xfce is known as 'the lighter GNOME'.

GRUB is Ubuntu's boot loader. If you are dual-booting, you will see to options at the beginning, right? Well, that screen is GRUB. If you are NOT dual-booting, then when you start your computer, you will see a 3 second countdown, if you press ESC you will see GRUB.

Root is the administrator account. It's like a superuser! When Ubuntu asks for your password (EX: when you try to change time settings) you are using Root. If you asked help here you probably already heard something about SUDO to. The little box that pops out asking for your password when you are trying to change the time is a graphical version of sudo. 

For entering Code. Applications>Accessories>Terminal. Just copy paste a code like this one: 

```
sudo apt-get update
```

It will ask you for your password(THATS SUDO!), just enter it, don't worry if you don't see it, when you finish, press enter. This will update the repositories. The repositories are the source of all your apps.
Creepy, isn't?

Remember, only paste command lines(text) from trusted sources, and **DON'T** sudo rm-f, that will DESTROY everything on your hard drive.

Hope I helped you understand Ubuntu a little more. Feel free to contact me if you have some doubts.

FINALLY, for your screen resolution. First of all, try to use the help that the other users gave you, if that doesn't resolve your problems reply this post.

Well, hope I helped somehow. Welcome to Ubuntu!
(If you think this post was useful click the little star button at the bottom right of the post to thank me ;)

---

### Post by jp734 on 2008-05-24
Please attach you xorg.conf file so we can check it which is in /etc/X11/ folder. "***/etc/X11/xorg.conf***

---

### Post by Steve Lyne on 2008-05-25
> **jp734 said:**
> Please attach you xorg.conf file so we can check it which is in /etc/X11/ folder. "***/etc/X11/xorg.conf***

Thanks for your reply. In order that I can use this forum I am using my laptop with Windows in the warmth of my indoors room, my Linux computer is in my shed where I experiment with unknown programs etc. It is obviously not possible to post the folder at the moment, so I will try some of the other suggestions (again) and get back as soon as possible.
I have had some success in changing the resolution but when I shut down and then restart my computer I am back to being unable to adjust the resolution. Is there some way of saving the changes other than the pop-up box that says 'keep changes'.
Once again thanks for your help,
Steve

---

