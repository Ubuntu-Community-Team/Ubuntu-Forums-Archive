---
title: "How to use NVidia gpu and intel integrated graphics simultaneoulsy"
date: 2015-08-22
forum: General Help
---

### Post by this.foo on 2015-08-22
[FONT=arial][SIZE=2]Recently, i asked this question on askubuntu.com ([https://askubuntu.com/questions/664245/how-to-use-nvidia-gpu-simultaneously-with-intel-hd):](https://askubuntu.com/questions/664245/how-to-use-nvidia-gpu-simultaneously-with-intel-hd):)  [/SIZE][/FONT]

[COLOR=#111111][FONT=Ubuntu]"My laptop has an high-end NVidia Geforce GTX 860m graphics card and the intel integrated graphics (Intel HD 4600, pretty weak)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So in my case, i have to work in ue4 (very heavy on the graphics card), while from time to time switching to the browser to watch tutorials and find answers to questions.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So is there any way to use the NVidia card for heavy tasks, while at the same time using the intel graphics for browser? Because currently videos stutter extremely, and even web forms are very hard to fill out (a lot of lag while typing)
If anybody could have a solution for this problem, i would thank him very much.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Also, my problem is not the one described here:[How to use Intel HD Graphics for regular desktop usage, while just using my NVIDIA GPU for DNN training]("https://askubuntu.com/questions/530398/how-to-use-intel-hd-graphics-for-regular-desktop-usage-while-just-using-my-nvid")
because i do not want to switch between GPU's, but run them simultaneously.[SIZE=2]"

[FONT=arial]As per request by pilot6 i have now moved this thread to Ubuntu [B]forums.
[/B]
[/FONT]I would also like to ad that i have installed bumblebee, however it used the intel integrated graphics for the desktop, which resulted in quiet a bit of lag.
So to specify what exactly i would like:

-at regular use, only the nvidia gpu is working
-at intense use of only one program, only the nvidia gpu is working
-at intense work of a programm, and a non intense use of one or several other programs the nvidia gpu is used for the resource intense program, and intel hd 4600 is used on the less demanding programs.

If that would be possible, i would thank the person providing a valid answer very much.
[/SIZE]
[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-08-22
Have you tried doing that in windows?

From my understanding of Nvidia Optimus technology I do not think it is possible. The purpose of Optimus is automatic switching between a more powerful GPU for high intensity graphic tasks with likewise high battery drain and a less powerful GPU for low intensity graphic tasks with the benefit of less battery drain.

In Linux we have yet to get an Nvidia driver that will do automatic switching.

I am guessing that the problems you are having with video play back are nothing to do with which GPU is being used but in connection with the CPU being under intensive use and needing to task switch. The Nvidia GPU should handle video playback easily. If it is not then it could be a case of too much going on at the same time.

Regards.

---

### Post by this.foo on 2015-08-23
Thank you for your reply,
but when i said that from time to time i have to switch to the browser i actually meant not closing the ue4 editor, but leaving it open and at the same time doing something on the internet because it takes quiet long for the editor to open. 
you said that the nvidia gpu is simply using all it's resources on the resource heavy program.  
Would using the intel integrated graphics parallel to the nvidia gpu even make it better?  
Also, can i somehow solve the problem by telling the computer to stop using the nvidia gpu for the current program and instead focus it on another process? (without closing the previously used program)
thanks

---

### Post by QIII on 2015-08-23
I do not believe that you will be able to do what you ask.

You can either have the dedicated or the integrated GPU working at any time, not both.  That is, you won't be able to assign one GPU to one task and the other to another task during the same session.

In a hybrid graphics arrangement, one GPU is "turned off" while the other is "turned on".  They won't both run at the same time.

---

### Post by this.foo on 2015-08-23
Not possible at all?  
Not even if some kind of special driver come out at some point if time?
So the integrated graphics will remain useless forever.

---

### Post by QIII on 2015-08-23
Not possible at this time.  Whether or not it will be is up to the hardware manufacturers releasing drivers that would allow that.

Again:  You may use either the integrated or dedicated graphics.  Each will work -- one at a time -- but you have to switch between them.  The switch is not on-the-fly as it is in Windows.  You have to reboot.  This is simply how the OEMs have designed things and there's not much we can do about it here in Linux Land.

---

