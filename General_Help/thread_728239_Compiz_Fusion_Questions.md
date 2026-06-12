---
title: "Compiz Fusion Questions"
date: 2008-03-18
forum: General Help
---

### Post by LinuxNewb092 on 2008-03-18
Hey guys I was wondering how to make it so I can see a cube and rotate it around.  Heres a link for an example, [http://www.youtube.com/watch?v=bvnQE1EAEZY]("http://www.youtube.com/watch?v=bvnQE1EAEZY").
What I want to do starts on 0:14 and stops on 0:20 of the video.  I was also wondering what dock he had if anyone could tell me please.

---

### Post by forrestcupp on 2008-03-18
Try going to System->Preferences->Appearance and click the Visual Effects tab.  Try to enable it in there.  If it works, you can have your cube.

---

### Post by LinuxNewb092 on 2008-03-18
Umm...i need more of an explanation.  I dont think thats how you did it.  Just watch the video and youll see what Im talking about.

Thanks in advance,
-LN

---

### Post by forrestcupp on 2008-03-18
You have to have the Visual Effects enabled to be able to have a rotating cube.  If you can get them enabled like I said last time, then we'll help you understand how to set up the cube.

---

### Post by LinuxNewb092 on 2008-03-18
Ok, I had that done so what I should I do?

---

### Post by forrestcupp on 2008-03-18
Look in System-Preferences and see if there is Advanced Desktop Effects.  If there is, open it.  If not, type in a terminal
```
sudo apt-get update
sudo apt-get install compizconfig-settings-manager
```

Then look for it in Preferences again.

When you have it open, click the General Options and go to the Desktop Size tab.  Make sure the Horizontal Virtual Size is set to 4 for the 4 sides of the cube.  The top and bottom sides aren't used as desktops.

Then click the Back button, and in the Desktop section, check the boxes next to Desktop Cube and Rotate Cube if they are not checked.  Then you can close it and you will have a cube.

The way you use it is by pressing ctrl+alt and press your left mouse button and drag your mouse to move the cube around.  You can also press ctrl+alt+left or right arrow key.

---

### Post by LinuxNewb092 on 2008-03-18
Ok great that worked, thanks for your help!  I am wondering how to put an image on the top of the box and how to see gears in the box, can someone help me with this?

---

### Post by ajgreeny on 2008-03-18
There is a useful bit of info here [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) with a lot of tips about getting different things to happen.  The compiz-switch is also an incredibly useful little script to turn compiz on and then off, it alternates at each click, and I use it a lot when using the programs that don't enjoy running with compiz enabled.

---

### Post by forrestcupp on 2008-03-18
> **LinuxNewb092 said:**
> Ok great that worked, thanks for your help!  I am wondering how to put an image on the top of the box and how to see gears in the box, can someone help me with this?

In the Advanced Desktop Effects settings, look in the Effects section for Cube Gears and Cube Reflections.  In the Utilities section, look for Cube Caps.  You can check the boxes to enable them, and you can click on the words to change their settings.

You'll just have to look around all of these settings to find out all the stuff you can do with Compiz.

---

### Post by wilburforce on 2008-03-18
im trying to do the same within system preference appearance i select extra and i get 

error failed to execute child process compiz missing file/ directory

---

### Post by LinuxNewb092 on 2008-03-18
Ok, thanks a lot guys, this helped a lot.

---

### Post by forrestcupp on 2008-03-19
> **wilburforce said:**
> im trying to do the same within system preference appearance i select extra and i get 

error failed to execute child process compiz missing file/ directory

If you're still around, post the contents of:
```
gksu gedit /usr/bin/compiz
```
You may need to edit a few lines in there.

---

