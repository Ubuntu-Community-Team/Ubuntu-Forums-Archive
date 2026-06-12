---
title: "Beryl,emerald with nvidia (solved)"
date: 2006-10-13
forum: General Help
---

### Post by xpod on 2006-10-13
Help....Finally installed my nvidia geforce mx 4000 and even seemed to get "Beryl" and the emerald theme manager all installed...but

I got them all showing up and the card is set up correctly according to the checks i followed by way of the how to i followed.
When i boot "nvidia" splash comes up just prior to logon.
I do the "ctrl+alt+arrows and all i get is a normal desktop switcher in the middle of the screen like the one on the panel

Its all there in my preferences and in added the relevant scripts and other stuff as advised so could someone tell me how to check,try and work this thing......I knew it was a bad idea cause i could`nt even do the bloody "Rubiks cube" when it was out so god knows how i got this far

EDIT.This is the relevant part of glxinfo so i know its set up ok

 dad@home1:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync,
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control,
    GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 4000/PCI/SSE/3DNOW!
OpenGL version string: 1.5.6 NVIDIA 87.62
OpenGL extensions:


I THINK???????????????????:confused:

---

### Post by xpod on 2006-10-13
I`ve since checked everything with what i think was the how to i followed and all is in order it seems so please somebody who knows this stuff tell me what im doing wrong.

I got my little red emerald up there on the panel and all the themes installed to the emerald theme manager but i cant seem to work anything....
No fancy graphics,no themes,no cubes......

It`s a new install and i had the "3ddesktop" basic thing from synaptic working on the last one with only onboard graphics(via kde desktop)
so whats wrong now that i have a proper card and everything set up correctly is beyond moi........NO DOUBT the stupidest of things ive not done or am not doing:confused: ](*,) :twisted: ....anyone???

---

### Post by meborc on 2006-10-13
you might try the beryl forum thread... it is under edgy development... i guess you will get better responce there... my videocard is too old to try anything like this yet... sorry for not helping :)

---

### Post by xpod on 2006-10-13
Hey..dont be silly m8.Everybody on this thing is "helping" just by being a member:mrgreen: 

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)


Thats what i followed but if a nice mod would like to mabey move this to somewhere more appropriate???
I`ve just got so used of this forum and after only a few months on a pc i reckon it`ll be my "home from home" for a while yet....lol

Cheers anyway..i found the "thread to beat all threads" as it describes itself with all the compiz(beryl)xlg etc so i`ll plough through it .

I was using onboard graphics till yesterday but i was still able to use the "3ddesktop" in synaptic which is like a basic version but it was good to get a taste........It only seemed to work though in the kde desktop and not if i was in ubunto(gnome).........i might just go back to that:D

---

### Post by mozetti on 2006-10-13
When you right-click the red emerald, on the "Select Window Manager" menu, is Beryl selected, or Metacity? It needs to be Beryl.

---

### Post by xpod on 2006-10-13
Sorry so long...when i choose "beryl" any apps open at that point sort of flash on and off for a couple of secs but zilch.
Even if i disable the "use default if beryl crashes" and sort of force it to use beryl..the little beryl check stays checked but nothing happens.

i followed this guide and have added all the relevant lines,repos etc and all seems in order?????

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

I noticed another guide suggesting another line ot 2 to add under the "device" section part of my Xorg file which i thought i`d tried but upon looking at my xorg.cong since then the 2 lines i recall adding aint there.

I`ve tried the various"startup" entry options at the bottom of the how to...
Theres so many guides and i dont want to start making matters worse by following different ones...

As i think i mentioned it`s a fresh updated install of dapper but my setup yesterday had both gnome and kde desktop environments and the wee basic "3ddesktop" app in synaptic worked great on kde even before i put the new card in...all worked fine from my s3 savage onboard graphics.

SO.....ive just now finished installing kubunto desktop ...again,and was wondering if i should try it on here......as the basic one would only work in kde and not gnome so mabey thats my best bet with this too???????

But then THAT will raise even more isuues regarding kde specific requirements no doubt....arrrhhhhhhhh:twisted: 

Any further suggestions would be greatly appreciated as ever

---

### Post by jordanmthomas on 2006-10-13
Right click on the beryl manager and go to quit.

Then, run 
```
beryl-manager
```
from a terminal and try switching window managers again.

Post any errors that get put in your terminal.

---

### Post by bulldog on 2006-10-13
> **xpod said:**
> Sorry so long...when i choose "beryl" any apps open at that point sort of flash on and off for a couple of secs but zilch.
Even if i disable the "use default if beryl crashes" and sort of force it to use beryl..

Any further suggestions would be greatly appreciated as ever

Well,Sir,with your knowledge of computers,you should stay miles away from programs like Beryl.:D 

But to stick you a helping hand,I used this Howto and with succes I can tell.

[http://ubuntuforums.org/showthread.php?t=268036](http://ubuntuforums.org/showthread.php?t=268036)

Maybe you can compare with yours and see if there are things done different.

But don't go altering everything without knowing what you're doing.

I have no more time this evening,but I'll be back tomorrow.

---

### Post by xpod on 2006-10-13
All sorted mate and all up and running.......although i did have to do it through kde as it just was`nt having it in ubunto...

Wibble wobble:mrgreen:

---

### Post by xpod on 2006-10-14
Just wondering....in the "beryl settings manager" what are the "super,hyper,meta,mode and mod 1 through to 5 options???? ...

Im trying to setup a decent lot of simple key or mouse options but seem to be getting a bit confused as always....

Anybody fancy enlightening me as to how best to set things AND what those keys are?????
Im basically asking for someone who already has it set and working great to tell me what the best setup options are for showing off to my doubting windows buddies........

It all works fine here in kubunto and im not bothered about ubunto as im finding loads of new wonders in kubunto so im sticking with it for now.
Got a separate kubunto pc but the kids use it so im just starting out with kde really..

SO..."super,hyper,meta,mode and mod 1 through to 5 options:confused: 

Great toys though......respect to whoever does this stuff....for FREE???

---

### Post by PriceChild on 2006-10-14
*moved to general help*

Beryl is not a beginners subject and you should get better help in General Help.

---

### Post by xpod on 2006-10-14
Thank you....i asked for that to be done already i think.
Im just set in my ways but will try and use the relevant forums for the relevant topics in future......sorry.

EDIT:Looks like i`ll have to suss out out myself anyway eh:rolleyes:

---

