---
title: "Change Bit Depth"
date: 2006-12-13
forum: General Help
---

### Post by helpdeskdan on 2006-12-13
Summary: How do I change the bit depth to 8 bit without reconfiguring X? 
System: Xubuntu 
Prefer: A simple command line solution would be nice so I can script it

Longer story:
I'm trying to get a game to run under wine. I do recall it needed 8 bit and would not run unless you agreed to let it switch.  Given the output before it crashes, I assume that *may* be why it crashed.  But, I can find no way to change the bit depth temporarily. 

It's trivial in Windows, please don't tell me it can't be done in Linux!!

dan@dan:/media/cdrom0$ wine puttcircus.exe
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1707f0) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16c030)->(0x10022,00000011)
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8

Many thanks for reading me post!

---

### Post by .t. on 2006-12-13
Hmm... Post the output of the command, "xrandr" here. If there's an 8 bit mode, it should be able to be scripted (but then again, it should also be automatic). Otherwise, post your /etc/X11/xorg.conf file somewhere.

---

### Post by helpdeskdan on 2006-12-14
Thank you for your reply!

[SIZE="1"]dan@dan:~$ xrandr 
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 283mm x 212mm )  *70   60   87  
 1    832 x 624    ( 283mm x 212mm )   75  
 2    800 x 600    ( 283mm x 212mm )   85   75   72   60   56  
 3    720 x 400    ( 283mm x 212mm )   85  
 4    640 x 480    ( 283mm x 212mm )   85   75   73   60  
 5    640 x 350    ( 283mm x 212mm )   85  
 6    720 x 450    ( 283mm x 212mm )   60  
 7    640 x 400    ( 283mm x 212mm )   85   60  
 8    640 x 384    ( 283mm x 212mm )   60  
 9    576 x 384    ( 283mm x 212mm )   55  
 10   512 x 384    ( 283mm x 212mm )   70   60   87  
 11   416 x 312    ( 283mm x 212mm )   75  
 12   400 x 300    ( 283mm x 212mm )   85   75   72   60   56  
 13   320 x 240    ( 283mm x 212mm )   85   75   73   60  
 14   360 x 200    ( 283mm x 212mm )   85  
 15   320 x 200    ( 283mm x 212mm )   85  
 16   320 x 175    ( 283mm x 212mm )   85  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none[/SIZE]

Also, this entry in the xorg.conf leads me to believe it could be changed:        

[SIZE="1"]SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection[/SIZE]

I can not seem to find the correct command line tool to change these settings.  Do you know of a good url on this subject?  I am most appreciative of your help. 

Thanks, 
-Dan

---

### Post by .t. on 2006-12-15
Hmmm... I don't know :( I had sort of assumed that xrandr (based on the error message you gave) supported changed resolutions. But, looking at it's usage now, it seems that's not the command you want, although you should have support for it. The GNOME settings applet for it doesn't want to do it either. I'm sorry I can't help. I'll look into it more later when I have the time.

---

### Post by helpdeskdan on 2006-12-19
Thanks!  Currently I'm using Xubuntu which also makes things harder.  As I said, I certainly hope that it is possible.

---

### Post by christhemonkey on 2006-12-19
This list post seems to adress a similar sort of subject [http://lists.trolltech.com/qt-interest/2001-01/thread00306-0.html](http://lists.trolltech.com/qt-interest/2001-01/thread00306-0.html)

The relevant section:
> Most X servers offer one visual. However, some offer several, and in that
case, one of the visuals is the default visual, which applications are
expected to use by default.


But that doesnt really assist....
Will have some more looking round!

---

