---
title: "Fresh install of Kubuntu 18.04 and it's freezing!"
date: 2018-05-26
forum: General Help
---

### Post by cwm.030 on 2018-05-26
Hi All!

I just eraced windows and installed Kubuntu 18.04 
( I run Windows 7 in a VM now ) 

Anyways, I can be sitting here and my mouse starts studdering ( as in it barely moves across the screen) then freezes then works fine for a sec then freezes.

If you need me to give you my hardware info, I will need to get the command so I can tell you

Thanks,
Chris

---

### Post by SeijiSensei on 2018-05-27
First, open a terminal and type the command "top".  Leave it open and running while you do other things.  When it freezes see what top reports for the load average and what programs are at the top of the list.  Make sure you keep track of what you ran prior to the freeze.  Then we might be able to help.  I'm running Kubuntu 18.04 on three machines.  One of them has frozen because of issues with ktorrent and file access.  That's been it over the past month or so.

Do you have any other mice you can test?  Is it hard-wired, wireless with a proprietary method like Logitech uses, or does it use Bluetooth?  If that one, maybe it's a problem with Bluetooth.

When this problem arises, is the keyboard still active?  Can you use Alt-Tab to switch between applications?

---

### Post by cwm.030 on 2018-05-28
> **SeijiSensei said:**
> First, open a terminal and type the command "top". Leave it open and running while you do other things. When it freezes see what top reports for the load average and what programs are at the top of the list. Make sure you keep track of what you ran prior to the freeze. Then we might be able to help. I'm running Kubuntu 18.04 on three machines. One of them has frozen because of issues with ktorrent and file access. That's been it over the past month or so.

Do you have any other mice you can test? Is it hard-wired, wireless with a proprietary method like Logitech uses, or does it use Bluetooth? If that one, maybe it's a problem with Bluetooth.

When this problem arises, is the keyboard still active? Can you use Alt-Tab to switch between applications?


Hello!

When the computer freezes it freezes up and the the clock completly stops because I have the clock in the tray to show H:M:S
and it will go in and out of this state ( Freeze, unfreeze). And during that time the mouse sometimes will let me take control and sometimes I can move the mouse while the computer is completly frozen and all of a sudden the cursor starts moving on its own like its possessed lol ( I think it's tryign to catch up with me moving the mouse) 

No, the keyboard doesn't work... alt tab does nothing. Eventually after the lock up happens, I gain access back to the keyboard. Or If I do ALT TAB it's lke the mouse it takes awhile to catch up ( A LONG time) or sometimes it doesn't remember that I did that key sequence. 

My mouse plugs into the green jack in the back of the computer... It's one of those old timey mouses that, how do I explain this... Its got the red light on the bottom when you pick it up. But it plugs into the standard mouse port. Because the part you plug in has pin's on the inside. Unfortantly, no... I don't have another mouse. 

And the keyboard plugs into the purple port. 


So far I have:


Disabled all effects............. Settings > Desktop behavior > Desktop Effects

Settings > Startup And Shutdown > Start with a new session ............
( That was just to get numlock to work ) I tried numlockx, wound up purging from the command line it didn't work... But it's working fine now.  


Settings > Compositor > changed that to XRENDER ( I read on google that helped some people )  


I've ran fsck from the installation CD ... File system as came back as cleam ( Yes CD, I don't have a USB stick handy ) 


I ran the CD's intergrity check... " No Errors Found"


So far no problems now that i've turned off all effects. I just want to be sure i am going to be problem free.. Any other ideas?

Thanks,
Chris

---

