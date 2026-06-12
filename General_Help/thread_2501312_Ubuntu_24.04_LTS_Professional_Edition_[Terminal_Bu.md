---
title: "Ubuntu 24.04 LTS Professional Edition [Terminal Bug]"
date: 2024-10-01
forum: General Help
---

### Post by aunonno2024 on 2024-10-01
Hello everyone,

I am using "OS: Ubuntu 24.04.1 LTS x86_64" and "Kernel: 6.8.0-45-generic". I am having a issue which is every single day when i boot my laptop which is "ASUS X543UA vivobook" and check for update from terminal the keyboard keys start auto-pressing like "sudo~~~~~~~~~~~~~~~~~~~~~~~~~~~~" only it's stop when i press "backspace" key first i thought that maybe it's my keyboard problem although my laptop is only 4 years old so to diagnose the issue i opened up my notepad which is "gedit" and try to type on it and the keyboard is working fine. Also when i use firefox and write anything the URL it's also working fine. And now i am writing this post with laptop keyboard it's still working good but when ever i use the stock terminal application this issue occurs but if i use my laptop longer time then terminal won't behave like this anymore so what i noticed is it's only happen when i boot my laptop. Also when i code in my "VScodium" application my keyboard go crazy again! So please if there is any bug fix it as soon as possible that's my only request. :-)

And thank you you giving me your valuable time and reading this post.

Sincerely, 
One of your GNU/Linux desktop application developer "Aunonno" :-)

---

### Post by deadflowr on 2024-10-01
Support thread
Moved to General Help sub-forum

---

### Post by yancek on 2024-10-01
I don't think I'll be much help but, just to clarify this problem is only when you are using a terminal?  Is the example you give something that actually happens, meaning you can type sudo without problem but then it starts printing the ~~~~~~ key?  That seems bizarre as you would need to hold down the shift key to get the ~ symbol.  Or is that just an example.  Maybe if you could copy or take a screenshot of what actually happens someone a little more familiar would be able to help.

---

### Post by 1fallen on 2024-10-01
This sounds like your keyboard has issues, can you check to see if "~" is stuck. Are you sure it's not showing something like this
```
^["^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[3~^[[
```
Also check with another Keyboard if possible.

Also please reply to yancek's post above, you have us scratching our heads here.:o

---

### Post by TheFu on 2024-10-01
Could it be that different keyboards/languages are setup for consoles and GUIs?
Normally when that happens, people have trouble logging in.

BTW, what is this "Ubuntu 24.04 LTS Professional Edition" - never heard of it.

---

### Post by him610 on 2024-10-01
You might consider trying a different terminal emulator. There is normally more than one included in each *buntu installation.

---

### Post by TheFu on 2024-10-01
Almost forgot, sometimes if we ask to look at a binary file, our terminals will get screwed up.  To fix that, use
```
<cntl>c
stty sane<enter>
```
Inside the terminal showing the issue.  I normally just open a new instance of an xterm myself and close the old one, but for people using tab-based terminal programs (no accounting for taste!), this would be a handy thing to have ready.  When you are doing those keystrokes, they won't be seen, so you need to be certain with your typing.

---

### Post by aunonno2024 on 2024-10-03
Yes i can confirm it's not showing like above. Okay let me give you a screenshot that might helpful.

---

### Post by aunonno2024 on 2024-10-03
Sorry for that i actually mean this "https://ubuntu.com/pro"

Normally people use LTS  non-pro version gives use max 5 years of updates. But pro gives you 10 years of support. It's free for personal use but when you run ubuntu on your server you have to pay some money to them. :-)

---

### Post by aunonno2024 on 2024-10-03
This person have similar problem like mine! Not same to same but similar maybe this one might helpful for you to understand my current situation. 

"https://askubuntu.com/questions/1454666/keys-start-repeating-as-if-they-were-stuck-ubuntu-20-04-and-others-on-laptop"

And also as he/she mentioned in the above link which is to upgrade the BIOS/UEFI. I am not sure how much good asus is when it's comes to a BIOS update. Because HP releases BIOS updates often i don't know about the other brands but i am giving you my laptop website link as you see in the below link the latest BIOS Firmware Version is "Version 303  (2019/06/06)". But the current BIOS i am using right now in my asus laptop is "Version 307" which is obviously the latest one right now. I bought this laptop in 2020 but if you go to below link you will see they didn't release any new BIOS updates from (2020 to 2024) that's why i am little bit concern. It's not a huge problem but it's a little bit annoying specially when i write code on vscodium and it's write random characters it's weird. So the Terminal & The vscodium are two software which affected but notepads like gedit or leafpad working just fine. 

Link of my ASUS Website : [https://www.asus.com/supportonly/x543ua/helpdesk_bios/](https://www.asus.com/supportonly/x543ua/helpdesk_bios/)

---

### Post by TheFu on 2024-10-03
I had a problem with the keyboard on my Asus Vivabook laptop.  In the beginning it was fine. Over time, well-used keys became harder and harder to get work.  Eventually, about 10 keys stopped getting any input at all or once pressed would get stuck down flooding the USB bus with extra keystrokes.  Because changing a new keyboard was $90 parts + $100 labor (lots of labor to get to the keyboards in thin laptops), and the laptop was only worth about $150, if the keyboard was working perfectly, I decided to just retire it.  I did try using it as a desktop with an external USB keyboard, but the extra, random, keystrokes that would just show up made it useless.  Disconnecting the internal keyboard connector prevented it from booting at all.  Nothing else wrong with the laptop. 

After buying 3 laptops made with crappy keyboards from 2012 until 2017, I finally decided to stop that and picked up a Dell laptop in July.  Dell tests their keyboard designs for over 1M presses per key.  Of course, they also try to manufacture them as cheaply as possible, so they do break, just hopefully years after we've decided to get a new laptop.

None of this is probably helpful ... except maybe you could connect an external USB keyboard and see if that shows the same problem?  That would rule out hardware if it happens there too.  It would not be the keyboard hardware then.

---

### Post by 1fallen on 2024-10-03
[COLOR=#CCCCCC][FONT=&amp][COLOR=#CCCCCC]This is testing this and that ~~~~~~~~~~~~~~~~~~~~~~~~ >>>>>>>>>>>>>>>>>>> ````````````````````[/COLOR]
[COLOR=#CCCCCC]All good here:[/COLOR]

```
[COLOR=#CCCCCC]Version: 1.93.1[/COLOR]
[COLOR=#CCCCCC]Release: 24256[/COLOR]
[COLOR=#CCCCCC]Commit: [/COLOR][COLOR=#808080]<[/COLOR][COLOR=#569CD6]Snip[/COLOR][COLOR=#808080]>[/COLOR]
[COLOR=#CCCCCC]Date: 2024-09-12T18:27:33.186Z[/COLOR]
[COLOR=#CCCCCC]Electron: 30.4.0[/COLOR]
[COLOR=#CCCCCC]ElectronBuildId: undefined[/COLOR]
[COLOR=#CCCCCC]Chromium: 124.0.6367.243[/COLOR]
[COLOR=#CCCCCC]Node.js: 20.15.1[/COLOR]
[COLOR=#CCCCCC]V8: 12.4.254.20-electron.0[/COLOR]
[COLOR=#CCCCCC]OS: Linux x64 6.11.1-2-cachyos-lto[/COLOR]
```
[COLOR=#CCCCCC]I did earlier in my first reply suggest another "keyboard" along with TheFu.[/COLOR]

[COLOR=#CCCCCC]I have a very strong hunch this is your keyboard aging.  Even with two only applications showing that error.[/COLOR]

[/FONT][/COLOR]

---

