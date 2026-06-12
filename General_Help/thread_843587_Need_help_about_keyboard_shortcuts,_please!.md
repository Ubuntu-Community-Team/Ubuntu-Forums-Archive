---
title: "Need help about keyboard shortcuts, please!"
date: 2008-06-28
forum: General Help
---

### Post by Cheshirecat86 on 2008-06-28
Hi, I need help in resolving few questions. I am a complete newbie to Linux (few days experience). I tried to google it , but found nothing relevant.

1) when I press shift+w shift+p (right now i can't type capital 'w' or 'p' because of that; could be a problem with other capital letters too, didn't try them all yet)  or ctrl+f (which is used to "find" in many programs) a command line window (like terminal but with black background) opens. why does it happen, how do i stop it.

2) also, since windows OS  I'm used to use ctrl+a shortcut to select all text, but in Ubuntu it doesn't work, how can I make it work?

3) I wanted to create a shortcut using the standard System/preferences/Keyboard Shortcuts  so that when I press the windows+d all windows would hide and focus on desktop (like in windows OS), but I only was able to bind just the window key to do that, not the window+d together, By the way the window key was recognized as "Super L" key by the "Keyboard Shortcuts" utility. How can I make it work for win(Super L)+D, not just win(Super L)???

---

### Post by Darkade on 2008-06-28
try opening a terminal and type ```
gconf-editor
``` then goto Edit>find and search for ```
/apps/gnome_settings_daemon/keybindings/media

``` this will show you every keyboard shortcut right click in actions you think are giving you problems. and select "unset" 

For your third question: in the window we just open (gconf-editor) look for the shortcut you want to create. and write it by hand, just follow the syntaxis of the other entries, it's not that hard :D

---

### Post by Cheshirecat86 on 2008-06-28
thanks for reply
after I chose "unset" for those buttons, they stopped working at all. After I reactivated them with System->Preferences->"Keyboard Shortcuts" the still don't work properly. When I try to lower or raise the volume level the sound level bar window appears, but instead of lowering the sound when I press "volume -" button it shows that the sound is muted (though it's actually NOT muted, I can still hear the music, a video soundtrack etc.), when I press "Volume +" it shows that the sound is unmuted. But the bar indicating the volume level doesn't change.
I don't understand the reason of this problem, everything was working fine, why does such a simple thing have to be such a pain in the neck. :confused: 
---------------------------
oops, edit, ^^this^^ reply above is concerning my another problem from [this topic]("http://ubuntuforums.org/showthread.php?t=843629") . Your advice was relevant for this problem as well so I got mixed up a little bit. :D



Concerning about "hide all windows and focus on desktop" feature, I found it with gconf, but it doesn't work when I use Super_L with 'd' letter. However I was able to use Super_L + <Control>, which is still better for me then just Super_L, because now I can assign Super_L to do something else useful. This is because of syntax, Super_L value doesn't have brackets, therefore it cannot be combined with any other character buttons (like "d" and such), but it can be combined with buttons the corresponding value of which is enclosed in <> brackets, like <Alt>, <Control> etc.




> **Cheshirecat86 said:**
> Hi, I need help in resolving few questions. I am a complete newbie to Linux (few days experience). I tried to google it , but found nothing relevant.

1) when I press shift+w shift+p (right now i can't type capital 'w' or 'p' because of that; could be a problem with other capital letters too, didn't try them all yet)  or ctrl+f (which is used to "find" in many programs) a command line window (like terminal but with black background) opens. why does it happen, how do i stop it.

2) also, since windows OS  I'm used to use ctrl+a shortcut to select all text, but in Ubuntu it doesn't work, how can I make it work?


WEIRD, after I had restarted, these problems #1 and #2 went away. It's normal now. WTF was that?  O_o

---

### Post by Darkade on 2008-06-28
Did you installed Ubuntu in a laptop? if that's so what the model of it?
Some laptop keyboards don't work properly

---

### Post by Cheshirecat86 on 2008-06-28
Yes! It is a laptop HP dv9700t.
Here is the config info:
----------

HP Pavilion dv9700t customizable Notebook PC

    * Genuine Windows Vista Home Premium (32-bit)
    * Intel(R) Core(TM) 2 Duo Processor T9300 (2.50 GHz, 6 MB L2 Cache, 800MHz FSB)
    * 17.0" WSXGA+ High-Definition HP BrightView Widescreen Display (1680 x 1050)
    * 2GB DDR2 System Memory (2 Dimm)
    * 512MB NVIDIA GeForce 8600M GS
    * HP Imprint Finish (Radiance) + Fingerprint Reader + Webcam + Microphone!!
    * Intel(R) PRO/Wireless 4965AGN Network Connection and BluetoothTM!!
    * 240GB 7200RPM SATA Dual Hard Drive (120GB x 2)
    * LightScribe SuperMulti 8X DVD+/-RW with Double Layer Support
    * No TV Tuner w/remote control
    * 8 Cell Lithium Ion Battery
    * System Recovery DVD with Genuine Windows Vista Home Premium (32-bit)
    * Microsoft(R) Works 9.0

-------------

---

### Post by Darkade on 2008-06-30
According to the ubuntu laptop testing team your laptop should be working pretty fine. (you can check in [this]("https://wiki.ubuntu.com/LaptopTestingTeam/HPdv9700t") page) 

> WEIRD, after I had restarted, these problems #1 and #2 went away. It's normal now. WTF was that? O_o

So summarizing. What are your troubles with your keyboard now? ;)

---

### Post by Cheshirecat86 on 2008-07-02
> **Darkade said:**
> According to the ubuntu laptop testing team your laptop should be working pretty fine. (you can check in [this]("https://wiki.ubuntu.com/LaptopTestingTeam/HPdv9700t") page) 


So summarizing. What are your troubles with your keyboard now? ;)

My problem is summarized in this topic: [http://ge.ubuntuforums.com/showthread.php?t=843629]("http://ge.ubuntuforums.com/showthread.php?t=843629")

Thanks

---

### Post by drs305 on 2008-07-02
If you look at System, Keyboard Shortcuts:
Are the values for Volume Down "0xae" and Volume Up "0xb0" ?  Those appear to be the default values on my computers - perhaps they got changed to something else.

For others offering assistance: I tried using "xev" to get a keycode symbol for the volume buttons on my laptop but it appears xev only responds to actual keyboard keys.

---

