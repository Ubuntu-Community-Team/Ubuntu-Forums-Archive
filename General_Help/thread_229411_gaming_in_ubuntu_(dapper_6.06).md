---
title: "gaming in ubuntu (dapper 6.06)"
date: 2006-08-04
forum: General Help
---

### Post by paperdiesel on 2006-08-04
I just did a fresh install of kubuntu (6.06).  Whenever I'm playing a game online, I keep having the same problem:

I notice that about once every five minutes, I'll get this huge lag spike, that lasts about 5 seconds.  The lag spike causes my game to completely freeze, and I lose control for about 5 seconds.  I'm thinking that there's some process running in the background that is using my net connection.

At first, I thought it was the adept package manager checking for updates.  I turned it off, but I still get this huge lag spike.

This problem exists no matter what game I play.  When I play that native linux client of Enemy Territory, I get the lag spike.  When I play call of duty through cedega, I get the lag spike.

Until a few days ago, I was running Win XP Pro, and never had any problems.  I'm pretty sure there's some background process that's using either my CPU or my net connection. 

Can someone help me troubleshoot this?

---

### Post by Lord Illidan on 2006-08-04
When that lag happens, do a quick CTRL + ALT + F1

Login the terminal, and run top

Tell us which is the top app listed.

---

### Post by FenrisAbraxas on 2006-08-04
> **Lord Illidan said:**
> When that lag happens, do a quick CTRL + ALT + F1

Login the terminal, and run top

Tell us which is the top app listed.

Hmmm or probably you will want to do a netstat -tpl and have top running on different consoles, that way you can see what apps are accesing the net, on which port, if you have servers and top to see whats accesing the resources and how much ram cpu and vram is using :P.

Also you can try nice -15 et.x86 to change priority :) good luck

---

### Post by Hairy_Palms on 2006-08-04
i had the exact same problem, for me it wa  problem with the repos nvidia driver, i had to install the official drivers.

---

### Post by paperdiesel on 2006-08-04
> **Hairy_Palms said:**
> i had the exact same problem, for me it wa  problem with the repos nvidia driver, i had to install the official drivers.

Really?  How did you uninstall the repo's nvidia driver first?  Did you have to modify your xorg.conf file?

---

### Post by Lord Illidan on 2006-08-04
For me the problem was with gam_server. It made Q3 unplayable.

---

### Post by paperdiesel on 2006-08-04
> **Lord Illidan said:**
> For me the problem was with gam_server. It made Q3 unplayable.

What is gam_server, and how would I disable it?

---

### Post by paperdiesel on 2006-09-19
By the way, I fixed my problem.  I had my desktop picture set so that it would download a new pic from the net every five minutes.

Doh!

---

### Post by Gioutsaman on 2006-10-05
hey guys i have recently installed wow under dapper kubuntu 6.06 successfully but it seems that something goes wrong with my X server. when i run the game with Wine 0.9.6 i can see the intro but when the intro finishes it crashes me out. I should clarify that my screen resolution is 1280x1024 and that when the game starts my screen resolution goes to 1024x768.....when the game "xrashes"  i get the following message:
 
 fixme:advapi:SetSecurityInfo stub
 fixmeowrprofllMain (0x7c220000, 1, (nil)) not fully implemented
 fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
 fixmeowrprofllMain (0x7c220000, 0, (nil)) not fully implemented
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eee8,0x00000000), stub!
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f158,0x00000000), stub!
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f4,0x00000000), stub!
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6f4,0x00000000), stub!
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9ee60,0x00000000), stub!
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f65c,0x00000000), stub!
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f648,0x00000000), stub!
 fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
 fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9ee60,0x00000000), stub!
 fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
 fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
 fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
 fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
 fixme:wininet:InternetSetOptionW Option 45 STUB
 fixme:imm:ImmGetContext (0x10022): stub
 X Error of failed request: BadMatch (invalid parameter attributes)
 Major opcode of failed request: 143 (GLX)
 Minor opcode of failed request: 13 (X_GLXCreateGLXPixmap)
 Serial number of failed request: 386
 Current serial number in output stream: 387

thanks in advance :D

---

