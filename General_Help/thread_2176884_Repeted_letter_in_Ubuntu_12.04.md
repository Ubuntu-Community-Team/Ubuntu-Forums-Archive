---
title: "Repeted letter in Ubuntu 12.04"
date: 2013-09-26
forum: General Help
---

### Post by MightyJoe777 on 2013-09-26
Folks, a real newbie here on Ubuntu and just installed 12.04 on an Intel Dual Core 2.4 Ghz with Nvidia (256MB) (I know pretty old). 

For some reason as soon as I login, the letter "w' keeps getting pressed. 

I did install Utorrent and teamviewer. These are the only 2 applications that I installed sepearately. 

Is there some way you know of this error of repeated characters(just 'w' only). I cant do anything really. I doubt its a laptop HW function because it lets me enter my password correctly at login. 

Any Idea. Should I do a clean install again?

---

### Post by varunendra on 2013-09-27
Welcome to the forums MightyJoe777 ! :)

The problem you describe sounds like a typical keypad issue in older laptops, most common in Toshiba models. But yes, programs like Team Viewer can also cause it if you or someone tries to establish a remote session with it, and there is some problem. So please answer a few questions -

1) Is it a laptop? If yes, which brand/model?

2) Does that happen in a live session also? (when you boot with the cd/usb that you installed from, and choose "Try Ubuntu" option).

3) In the installed one, does it stop after a while? Does it allow you to work at all?

4) Did it happen before installing Team Viewer? If not sure, can you remember some specific point since when it started?

Hopefully, answers to these may help pin-pointing the cause and fix it.

---

### Post by MightyJoe777 on 2013-09-27
Solved. For sure this is a Hardware Issue. 

I used  command : xinput set-int-prop 11 "Device Enabled" 8 0 

to disable the internal keyboard and it worked. 

Thanks again for your help.

---

### Post by varunendra on 2013-09-28
> **MightyJoe777 said:**
> Solved. For sure this is a Hardware Issue. 

I used  command : xinput set-int-prop 11 "Device Enabled" 8 0 

to disable the internal keyboard and it worked. 

Thanks again for your help.

No problem, but does it mean you are using an external keyboard now?

Is the change you made with above command persistent (retained in next boot)? If so, I thing you found a great solution and as such, you should consider marking the thread as [SOLVED] by using the "Thread Tools" link above the top post.

It helps others by indicating that the thread contains a solution to the topic.

And thanks for sharing with us. :)

---

### Post by MightyJoe777 on 2013-09-28
Folks, I know many already know the solution but I can repeat it just incase :) 

Just to recap incase you suspect you have a faulty Laptop Keyboard and you would like to disable it (I had an issue where the "W" kept getting pressed. 

1. You should have an external Keyboard and have it setup
2. Run "xinput --list" in terminal to identify which input device to disable

this is what I get when i run it. 


&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; KYE NetScroll+ Traveler                     id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sony Vaio Keys                              id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; UVC Camera (05ca:183f)                      id=10    [slave  keyboard (3)]
    &#8627; CHICONY USB Keyboard                        id=12    [slave  keyboard (3)]
    &#8627; CHICONY USB Keyboard                        id=13    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]

3. You cannot disable the "CORE" input devices. Here I identified that the Laptop keyboard is "AT Translated Set 2 keyboard                id=14    [slave  keyboard (3)]"
4. To disable the keyboard enter the command: 

xinput set-int-prop <ID> "Device Enabled" 8 0 

0 = Disable
1 = Enable. 

Example Command which I used. = xinput set-int-prop 14 "Device Enabled" 8 0 


You can do the same for the trackpad which in this case is id-15

Hope I helped you guys and Good luck

Regards,
Joe

P.S : Thanks Varun :)

---

