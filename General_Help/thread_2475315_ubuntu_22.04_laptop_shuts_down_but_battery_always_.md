---
title: "ubuntu 22.04 laptop shuts down but battery always runs out when its off"
date: 2022-05-22
forum: General Help
---

### Post by mason64 on 2022-05-22
hi everyone 

i am new to Linux (windows user for 20 plus years).

keep trying to get in to Linux over the years but finally took the leep and put it on my main laptop.

I have Lenovo thinkpad T460s i5 20gb memory and 256 ssd 

I have installed ubuntu and it works great apart from when i shut down by going to the top right hand side menu and clicking on power off / Log off it shuts down well so it seems 

the Esc ley (has a small light on it to switch the function keys around. that seems to stay lit up even when its fully shut down. if the battery has 50% for example and i shut it down and come back to it in 3 hours the laptop is dead and needs charging again. also it doesnt power as i need to keep my finger on the power butotn for 5 to 10 seconds then start it up. its like its still shutiting down but everything is off so by doing a hard shut down it then boots back up but with no battery left. 

Any ideas what this could be?

Thanks

---

### Post by Rex Bouwense on 2022-05-22
I suspect that you are not powering the computer off.  Immediately underneath the drop down menu that you where you clicked to Power Off/Log Out is the word Suspend.  I suspect that you have inadvertently selected that option.  So your computer will suspend rather than power off.  To get your computer to power off, you must select power off from the drop down menu and then select power off from the new window that opens up.

---

### Post by mason64 on 2022-05-22
Hi

I am definitely using log off / power off works on my PC just fine. not sure if its a bug on 22.04 on this laptop or not. 

Thanks for the quick reply.

---

### Post by grahammechanical on 2022-05-22
In System Settings>Power there is a setting for the power button behavior with three options - Power off; Suspend; Nothing. Check that it is not set to suspend. The fact that you need to do a hard power off to restart seems to indicate the OS has gone into a deeper state of suspension called hibernation.

Regards

---

### Post by Impavidus on 2022-05-22
Even in suspend the battery shouldn't drain in just 3 hours from 50% to empty. My laptop with 11 year old battery can still easily handle 12 hours of suspend mode on battery power.

When you see the splash screen during shutdown, hit escape and watch the messages scroll by. Maybe there's something interesting. You can also check the logs, but if something goes wrong too late during shutdown, the filesystem may already be unmounted (remounted read-only), so nothing can be saved to the logs.

---

### Post by mason64 on 2022-05-31
[https://drive.proton.me/urls/67ZNFWNJVR#S6J67MiqEsIR](https://drive.proton.me/urls/67ZNFWNJVR#S6J67MiqEsIR)

this is what is happening 

when i press esc on shut down and it seems to all say ok in green 

the video shows me pressing the power button after shut down and nothing happens but the fn light is on still like its in stand by. if i keep my finger on the power button for 5 to 10 seconds it shuts down ( hard shut down ) then press the power button and it boots. 

its like its hanging after shut down and hanging before the end of the shut down.

Hope that helps. 
sorry about the poor video

---

### Post by mason64 on 2022-06-02
Not sure if anyone is following this but i wiped my laptop and installed 21.10 and the problem never happened. Must be something in 22.04 

How do you report bugs for ubuntu like this?

Thanks

---

### Post by gbeps on 2022-06-22
i have the same problem with Lenovo T460S. i do not came back 21.10 . Is there a solution with ubuntu 22.04 ?

---

### Post by mason64 on 2022-06-22
Glad am not the only one. I have tried a few things but am not as good on linux as i am windows so limited to what i can do.

---

