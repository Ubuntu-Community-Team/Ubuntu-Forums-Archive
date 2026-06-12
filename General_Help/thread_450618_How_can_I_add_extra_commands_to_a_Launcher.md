---
title: "How can I add extra commands to a Launcher?"
date: 2007-05-21
forum: General Help
---

### Post by franck3d on 2007-05-21
this is my first post here so be gentle;)

I want to be able to run two commands from one "icon"
I have beryl installed and it's beautiful, but I often run Blender for some freelance cash money type deals.
Ideally I would click on the Blender icon in my top menu bar and this would kill beryl and launch blender.
then when I was done blender and closed it, beryl would restart automatically.

This seems like a lot to ask, but I have a feeling it (or some of it) is possible.

any ideas?
thanks in advance

---

### Post by bmartin on 2007-05-21
Try the following for the application launcher's command: **metacity && blender && beryl**

You could type those things into the terminal to see how it works before creating the application launcher. Also, I've never used Blender, but I assumed the command to launch it was **blender**.

This should:
[LIST=1]
[*]Run the normal Gnome window manager (Metacity)
[*]Start Blender after Metacity is done loading
[*]Start Beryl after Blender is closed
[/LIST]

Let me know if this works for you.

---

### Post by franck3d on 2007-05-22
thanks for the suggestion!
i gave it a shot but when I ran my launcher from the terminal, it gave me an error saying that a window manager was already running...
when looking at the beryl menu i saw the panel where you can choose your WM and i had entries for beryl, metacity, beryl and compiz.  there has to  be a way for me to set that value via a command with out actually killing beryl.  I'm going to have a look over at the beryl forums and see if I can get some info there.
thanks anyway!

---

### Post by bmartin on 2007-05-22
Try **metacity --replace** instead of simply metacity.

You actually are killing Beryl and starting it up again later.

---

### Post by franck3d on 2007-05-22
okay, I 'll give that a shot when I get home tonight.

thanks

---

### Post by dannyboy79 on 2007-05-22
well if I am understanding you right, you already have a window manager and beryl running and all you want to occur using this launcher is beryl to be killed, then start up blender, then restart berly when you close blender. Is that correct? If so, then there's no need to start by loading metacity for your beryl window manager as that already gets started when you start your computer. so the command would be:

killall beryl && metacity && blender && beryl

not entirely sure if this is what you want but hopefully it helps ya.

---

### Post by franck3d on 2007-05-22
thanks, I'm testing while at work with feisty in a virtual box, my real setup is at home.

in the virtualbox, i haven't got the nvidia drivers working, (not sure if it is even possible) so I'm testing by substituting firefox for blender in this example
beryl is running but not "working"

when i ran:

killall beryl && metacity && firefox && beryl

the script failed because there was no process called beryl, so I switched it to killall beryl-manager and that killed it, but it seems to want to restart.

then I tried
 
metacity --replace && firefox && beryl

the script hung saying;
Windows manager warning:   " "  found in config database not valild value for keybinding "toggle_shaded"

but I looked at the beryl icon still sitting up there and the wm in the beryl menu has changed to metacity, so I think I'm on the right track!

I'll just have to edit the config database, if I can find it!;)

thanks so much for your help!

---

### Post by bmartin on 2007-05-22
You're welcome.

When you say "it hangs", does is start Firefox or not?

If it does start Firefox, then it's hanging on Firefox. When you close Firefox, it should load up Beryl again. If that's the case, you're all set.

If not, it's hanging on Metacity. If that's the case, try the following:

**metacity --replace & firefox ; beryl**

Notice there's only one & after Metacity this time. That runs Metacity in the background. The only potential problem I foresee is that this might allow Firefox (or Blender) to load up *before* Metacity is done loading.

I wouldn't worry about the config database warning. If everything's working fine, I'd leave it as-is. I searched Google for a similar warning message, but couldn't find one.

---

### Post by franck3d on 2007-05-22
It does stop before it runs firefox...

i tried your other suggestion and this time firefox did run.

looking a little closer, it looks like I was wrong before, although the beryl icon is still on the menu bar
beryl never really is running, is kicks back to metacity when it cant find the glx on the display.

but, this version of my launcher seems promising:p

I'll have to wait until tonight to test it out.

thanks again.

---

### Post by bmartin on 2007-05-22
If you want a hand getting Beryl running, we can discuss that in a PM. Send me info about which type of card you have (ATI or Nvidia) and whether or not you're using XGL (if you don't know what that is, you're probably not using it). I'll be home around 6 PM Eastern (6 hours from now).

---

### Post by franck3d on 2007-05-22
thanks, I actually have beryl running fine, it's just the transition between these two apps that I'm working on.

I usually don't have time to get anything done on my computer at home until 8 or 9 (central)  but I may shoot you a message if i run into anything weird.

---

### Post by Dod_basim on 2007-05-24
hey man

i had same problem like you do, (same errors and all) but it was "Neverball" and not Blender.

The way forward;
On sessions i run 'beryl' and not 'beryl-manager' therefore i don't get the red icon on top (i don't think it's for a daily use, if you want to change setting you can simply jump to Apps -> System tools -> beryl manager or alternate use no GUI method)

okay, when you're on with beryl (check if it is good for you)

you can add to your launcher the code: (sometimes when running with terminal 'beryl' it keep the terminal open)

```
 killall beryl && blender && beryl 
```

tell us if it's good.

---

### Post by franck3d on 2007-05-24
thanks, I'll give that a shot!

---

### Post by franck3d on 2007-05-25
it looks like whenever I kill beryl, without beryl-manager running(or with, same result)
I get the error about the configuration database and blender never launches.

For now I'll just do the switching manually.  I'm getting a little tired of waiting for the animations on the windows anyway.
I'll probably just pull up beryl whenever I want to show anyone linux, and quietly shut it off when I need to get some work done...;)

thanks again for your help, everybody.

---

