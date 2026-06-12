---
title: "(Internet Related)Ubuntu is dependent on my other OS?"
date: 2008-06-21
forum: General Help
---

### Post by Aaron_Griffiths_92 on 2008-06-21
Here is the story, I need a solution to this problem as well. 
A couple of months ago I had windows xp and ubuntu on a dual boot. They worked fine and both connected to the internet. I then swapped both of them for vista. it lasted a few weeks on my usb wireless adapter and then told me my DHCP was missing. I then reverted back to xp and ubuntu. Problem is, I Cannot get sound or internet on xp and i cannot get internet on ubuntu. I have an asus P5LD2-X Motherboard and I have Hardy 8.04 32 bit on a dual core processor. The ethernet card i have is an atheros base t 10/100. I have no internet access what so ever on my computer. all i have to transfer data is a memory stick, please respond ASAP. Im stuck completely!

---

### Post by hariprs on 2008-06-21
Post how you connect to internet.

---

### Post by Aaron_Griffiths_92 on 2008-06-21
I use an ethernet cable connected to a router shared by 2 other computers, 1 wireless, 1 through usb and me, through my ethernet cable. I read other tutorials about this and even downloaded a file called atl2.ko, i put it in my drivers/net folder using nautilus but it shows as an unrecognized file type and is not doing me any favors at all.

---

### Post by guppygould on 2008-06-21
Does the eth0 interface show up? Sounds like a possible problem with your mobo.

-Leo

---

### Post by Aaron_Griffiths_92 on 2008-06-21
i cant find eth0, i will take this time to underline the fact that i was having DHCP related errors on vista and havent had internet acsess since

---

### Post by Aaron_Griffiths_92 on 2008-06-21
i need help desperately, please reply with solutions

---

### Post by LunatikOwl on 2008-06-21
If you said you had DHCP problems with Vista I wouldn't be surprised. But if Ubuntu has difficulties with wired card thats something odd. I NEVER had any problem like that. Does the connection works from the liveCD? Also have you tried to do cold reset to your routed(and install the latest firmware while your'e at it)? Routers do tend to misbehave in my little experience.

---

### Post by jerome1232 on 2008-06-21
You've had problems in 3 OS's with it, that has hardware problem written all over it, sounds like your onboard NIC (or is it and add on card?) is toast to me...  If Ubuntu and XP aren't even showing a device it's possible it's disabled in your CMOS.

---

### Post by Aaron_Griffiths_92 on 2008-06-21
hmmm cmos... never thought about that, tell me more

---

### Post by jerome1232 on 2008-06-21
When you first boot up you should see you're BIOS info, depending on what you have it'll look diff but usually tells you to hit 'insert key here' key to enter setup, usually 'del' or 'F2' or 'enter', that'll bring you into CMOS setup, in here there should be something like intergrated periphials (verbage will vary wildly) at any rate search around there will be an option to enable/disable on-board lan. Try to avoid getting curious in here :)

---

### Post by Aaron_Griffiths_92 on 2008-06-21
thnks, il look, but i have been told this is because of a bad xp install? would this affect ubuntu too?

---

