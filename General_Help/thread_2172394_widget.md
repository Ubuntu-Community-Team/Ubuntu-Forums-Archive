---
title: "widget"
date: 2013-09-04
forum: General Help
---

### Post by 3dmatrix on 2013-09-04
Can anyone kindly inform me how i can use any simple program written in python to make a desklet / karamba widget etc.
In the attached pic, you can see a very simple digital clock, which is made to run always on top. If i wish to convert this same clock in to a widget, what do i need to do ?
On one tutorial it was mentioned i have to submit my widget to gdisklet, but i wish to make one for my self. What do i do ?

---

### Post by coffeecat on 2013-09-04
*Thread moved to **General Help**.*

---

### Post by 3dmatrix on 2013-09-05
Any help from anyone ?

---

### Post by 3dmatrix on 2013-09-09
Any suggestion ?

---

### Post by Frogs Hair on 2013-09-09
I located this page. [http://gdesklets.de/develbook/ctrl-write.html](http://gdesklets.de/develbook/ctrl-write.html)

---

### Post by 3dmatrix on 2013-09-09
> **Frogs Hair said:**
> I located this page. [http://gdesklets.de/develbook/ctrl-write.html](http://gdesklets.de/develbook/ctrl-write.html)

With that can we make a desklet only for my personal use ? with out publishing it ?

Another page in that online book shows to make a Hello World with xml

"The first "Hello World!" desklet will be easy. It will just open a window saying "Hello World!" to the user.

Copy the following lines into your editor and save the file as hello.display.

[COLOR="#FF0000"]<?xml version="1.0" encoding="UTF-8"?>
<display>
  <label value="Hello World!"/>
</display>[/COLOR]
  
**Run **and enjoy your first self-made desklet."

What is this and how do we Run it ? It is not working ?

Someone else also wrote about it 
[http://ubuntuforums.org/showthread.php?t=935438](http://ubuntuforums.org/showthread.php?t=935438)
but he never received any reply.

.

---

### Post by 3dmatrix on 2013-09-09
Rather there is more help here :
[http://www.ibm.com/developerworks/library/l-script-linux-desktop-1/](http://www.ibm.com/developerworks/library/l-script-linux-desktop-1/)

---

### Post by Frogs Hair on 2013-09-09
Screenlets and Desklets are different programs and of the two I preferred Screenlets when I was using widgets . Use what works best for you purpose. :)

---

### Post by stinkeye on 2013-09-10
Are you specifically looking at working with screenlets/desklets or do you just want a desktop widget.
With conky you can display just about anything on your desktop.
Just need to install conky and then create a config file or download someone else's config.

Some example configs for clocks....

---

### Post by 3dmatrix on 2013-09-11
> **Frogs Hair said:**
> Screenlets and Desklets are different programs and of the two I preferred Screenlets when I was using widgets . Use what works best for you purpose. :)

I know they are different programmes and it is immeterial for me which one is good or bad, the problem that i am facing is with tutorials for them. I do not know how to convert my python programmes in to widgets and use them, NOT publish them.

---

### Post by 3dmatrix on 2013-09-11
> **stinkeye said:**
> Are you specifically looking at working with screenlets/desklets or do you just want a desktop widget.
With conky you can display just about anything on your desktop.
Just need to install conky and then create a config file or download someone else's config.

Some example configs for clocks....

Thanks, this conky stuff looks good  :)
I am not interested in the name as such, screenlet, gdesklet, conky, . . . anything will do as long as it helps me to use my python programmes to be displayed as widgets on my desktop. I am still learning python but would like to start using it in different ways in linux so need a tutorial and support in which ever system i use. If i can get good and basic tutorials for conky then i would love to use it.

---

### Post by stinkeye on 2013-09-11
> **3dmatrix said:**
> Thanks, this conky stuff looks good  :)
I am not interested in the name as such, screenlet, gdesklet, conky, . . . anything will do as long as it helps me to use my python programmes to be displayed as widgets on my desktop. I am still learning python but would like to start using it in different ways in linux so need a tutorial and support in which ever system i use. If i can get good and basic tutorials for conky then i would love to use it.
Oh, ok...conky maybe not the best idea then.
I don't know any programming except simple bash.
You can exec python scripts from within conky to show the output from the script, if that's what you mean.
I'll let others reply.

---

