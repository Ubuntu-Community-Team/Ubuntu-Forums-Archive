---
title: "(Ubuntu 13.10) How to use Japanese Anthy in the new Ibus"
date: 2013-10-18
forum: General Help
---

### Post by 3XymHb8 on 2013-10-18
I used to be able to use the Anthy IME to be able to type Japanese but I can no longer find that in the new Ibus.
Anyone mind pointing me in the right direction?

---

### Post by osarusan on 2013-10-18
Same problem here. I have anthy installed, and I set ibus as the input method as I used to do in previous versions of Ubuntu, but I can no longer switch between input methods. The zenkaku key on my Japanese keyboard does nothing at all, nor does super-shift-space or any other key combo. I am stuck using English input. Nor is there an icon where I can select the input method.

The im-config options are different than they used to be, and now there seems to be no way to add input methods.


Edit

Okay, I figured it out. You have to load up the "Text Entry Settings" and click on the plus sign to add an input method. It works once you do that.

---

### Post by borischan on 2013-10-18
> **osarusan said:**
> 
Edit

Okay, I figured it out. You have to load up the "Text Entry Settings" and click on the plus sign to add an input method. It works once you do that.

Same problem, and I have added Japanese in the text entry, still doesn't work, even after reboot.

---

### Post by 3XymHb8 on 2013-10-18
Can anybody give us a hand?

---

### Post by dsavi2 on 2013-10-19
Edit: Added the full process

osarusan's solution worked for me. It seems that you switch between Ibus inputs like keyboard layouts, which I think is more logical than the old system. Here are the steps I took:

First open "Language Support"

[IMG]http://i.imgur.com/fyW5aPm.png[/IMG]

Then click the button "Install/Remove Languages"

[IMG]http://i.imgur.com/zq4mdcc.png[/IMG]

Next, scroll down until you find "Japanese", check the box by it, and then press "Apply Changes"

[IMG]http://i.imgur.com/apejiXD.png[/IMG]

It installs some packages...

[IMG]http://i.imgur.com/dP0pkht.png[/IMG]

Then make sure that your input method is set to "IBus"

[IMG]http://i.imgur.com/Ohj6zxg.png[/IMG]

Next go to "Text Entry" by searching for it from the Unity menu and click the plus sign

[IMG]http://i.imgur.com/FUEDibK.png[/IMG]

Search for "japanese" or scroll down until you find "Japanese (Anthy)"

[IMG]http://i.imgur.com/3mGTPSD.png[/IMG]

Now just select "Anthy" like you would select a keyboard layout, from the thing in the menu bar.

[IMG]http://i.imgur.com/6VV0zAN.png[/IMG]

Hope this helps!

---

### Post by arm-c on 2013-10-19
Beautiful Icon for Language Switching!  TERRIBLE FUNCTIONALITY.  Korean input does not work.  Icon might swtich to KO, but it produces no Hangul characters!  Suggestions?

BTW, I got Hangul to work through ibus-setup from command line; however, the input does not matter what the language indicator says.  This is such a basic function that I cannot believe that it doesn't work!!!

---

### Post by ping-wu on 2013-10-19
I have occasional needs to input Chinese and Japanese characters.  After adding pinyin to the ibus input source, another problem arises: the default keys for switching the input source are "Super + Space".  Lo and behold, every time I tried to do that, the Dash screen would pop up, and I am still unable to use pinyin or anthy.  I know I can probably change the default setting(s) to make ibus work, but how about the next person or persons that I am planning to give the Ubuntu 13.10 USB to?  This is not something that I can explain well without excessive explanations that no one will read.  There are already enough challenges to transition a Windows user to Linux/Ubuntu, and we really don't need to go through this additional hurdle.

As I mentioned in another thread, for CJK users, my advice is to forgo ibus and switch to fcitx.  Or, better yes, we should begin experimenting with UbuntuKylin, which, although is been developed ostensibly for (simplified) Chinese users, seems to be a better fit for all CJK users in general.

---

### Post by dsavi2 on 2013-10-19
> **ping-wu said:**
> I have occasional needs to input Chinese and Japanese characters.  After adding pinyin to the ibus input source, another problem arises: the default keys for switching the input source are "Super + Space".  Lo and behold, every time I tries to do that, the Dash screen would pop up, and I am still unable to use pinyin or anthy.

Agreed, this is really weird and should be changed. Unity is known to grab some keys, most notably Alt and Super. My solution to this so far has just been to use the "previous input method" shortcut, which is also a default, instead (Shift+Super+Space). Because it's prefixed with a space, Unity doesn't grab it and it works fine, just in reverse.

---

### Post by borischan on 2013-10-19
> **dsavi2 said:**
> 

Search for "japanese" or scroll down until you find "Japanese (Anthy)"

[IMG]http://i.imgur.com/3mGTPSD.png[/IMG]



Thank you!! This worked for me, I had selected the first option, Japanese. Now Japanese (Anthy) is OK

&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;

---

### Post by ramadhan2 on 2013-10-20
> **borischan said:**
> Thank you!! This worked for me, I had selected the first option, Japanese. Now Japanese (Anthy) is OK

&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;

how can you did it?? 
i mean, i can't find japanese ( anthy ) on my laptop, what did you do ? :confused:

---

### Post by dsavi2 on 2013-10-20
> **ramadhan2 said:**
> how can you did it?? 
i mean, i can't find japanese ( anthy ) on my laptop, what did you do ? [IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]

Hey ramadhan2, I only posted the second part of the solution, sorry. Before you follow the instructions in my post you have to go to "Language Support", then click "Install/Remove Languages", then check the checkbox by "Japanese", click "Apply Changes", wait for that to install and then make sure that "Keyboard input method system" is set to "IBus".

Edit: I added the full instructions to [my original post]("http://ubuntuforums.org/showthread.php?t=2181487&p=12820598#post12820598")

---

### Post by Terrell_Broomer on 2014-02-10
so, I followed the directions, but for some reason still don't see the Japanese (Anthy) selection pop up. Something i'm doing wrong?

```
ii  ibus                                      1.5.3-6ubuntu2.1                              amd64        Intelligent Input Bus - core
ii  ibus-anthy                                1.5.3-3                                       amd64        anthy engine for IBus

```

[IMG]http://s12.postimg.org/5561n25xp/input.png[/IMG]

[IMG]http://s14.postimg.org/w1cdp0egh/language.png[/IMG]

EDIT: I was able to get something working by running ibus-setup from terminal and manually adding the input method. However, I have to invoke it using super + space. changing it to Ctrl + space doesn't seem to work. :p

[IMG]http://s23.postimg.org/hmkn83ldn/ibus_setup.png[/IMG]

---

### Post by anamenottaken on 2014-03-18
You can change the input selection keys by selecting the "general" tab and clicking on the "..." to the right of the "Next input method". Mine is now set back to  "<Control>space".

---

### Post by bb94 on 2014-04-29
Apparently, in 14.04, the IBus options won't show up in the Text Entry Settings. Does anyone know how to fix this?

---

