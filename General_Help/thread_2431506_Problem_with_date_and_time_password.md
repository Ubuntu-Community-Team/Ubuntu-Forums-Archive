---
title: "Problem with date and time password?"
date: 2019-11-17
forum: General Help
---

### Post by eastport on 2019-11-17
so im not really sure i should be asking this question as some forums do not allow it.However,if it is against forum rules,my apologies.just dismiss it.

I have a friend who brought a dell computer to me with ubuntu preloaded as the main operating system.Now i have to admit,i know absolutely nothing about ubuntu and i never knew you could buy a computer with it already preloaded.I have always worked strictly with windows.
 It is a tiny little computer with no cdrom drive.I dont really know anything about it other then it's a dell..lol
Her issue is that she set a password for the time and date on the taskbar..really?? i had no idea there was such a thing..lol..atleast i dont think there is for windows.isthere??
The last time she run the computer was almost 7 years ago..needless to say it will only run plugged in.
I was able to change the date and time in the bios.However,upon reboot,only the date was save but not the time.I can only assume that maybe it's because she set a password for it? I would think that if the date was saved,then so shouldnt the time.im lost as i dont know what to tell her.
 On another note,it seems there is an "cmos checksum" error upon boot.My only assumption is that it means it needs a new cmos battery after sitting for several years and this may effect the time.I did do a complete shutdown after changing the date and time in the bios.I rebooted and it reverted back to default's with the date and time being wrong again in the bios.So a new cmos battery it is and a new main battery.
 So now my question is,if she gets a new cmos battery,but she forgot her password to the time,is there a way to get around it? a way to reset it? I would hate for her to have to restore everything to factory defaults.On top of that,it does not have a cdrom drive,so she would have to buy an external drive.She has all the disks..installation and drivers.

---

### Post by uRock on 2019-11-17
We can't help with resetting the password. If it has been sitting for "several years" then it is likely the version of ubuntu is no longer supported. Ubuntu can be installed using a USB drive. Directions for creating a bootable USB can be found on the ubuntu download page.

---

### Post by The Cog on 2019-11-17
Setting the date but not the time sounds odd. Are you sure it's not just that the time-zone is not right?

I have never heard of specifically setting a password on the time setting, although I can imagine that setting the time requires admin (root) privilege which requires a password. Ubuntu simply asks for your password again (not root's passsword) if you try to do something that needs admin rights.

If the computer is 7 years old then the version of Ubuntu on it is well out of date, with lots of security issues un-fixed and not able to be updated. I would suggest installing a later version of Ubuntu - 18.04 is a Long Term Release version that still gets updates. But since the machine is that old and Ubuntu is heavy on resources, perhaps Xubuntu would be a better choice.

Probably not what you want to hear, but that's my advice.

---

### Post by eastport on 2019-11-17
Thankyou for your quick response.My apologies.

---

### Post by eastport on 2019-11-17
> **The Cog said:**
> Setting the date but not the time sounds odd. Are you sure it's not just that the time-zone is not right?

I have never heard of specifically setting a password on the time setting, although I can imagine that setting the time requires admin (root) privilege which requires a password. Ubuntu simply asks for your password again (not root's passsword) if you try to do something that needs admin rights.

If the computer is 7 years old then the version of Ubuntu on it is well out of date, with lots of security issues un-fixed and not able to be updated. I would suggest installing a later version of Ubuntu - 18.04 is a Long Term Release version that still gets updates. But since the machine is that old and Ubuntu is heavy on resources, perhaps Xubuntu would be a better choice.

Probably not what you want to hear, but that's my advice.


It wont even let me change the time zone.If i right click the time to adjust time and date,a box pops up asking for a password.everything is greyed out untill i can put a password in there.This is where she forgot her password.Other then that,she can get online and do everything else with it.That was until of course the date and time reverted back to defaults in the bios.

---

### Post by eastport on 2019-11-17
I will mark this as solved due to forum rules and regulations.again,my apologies..thankyou

---

### Post by coffeecat on 2019-11-17
> **eastport said:**
> I will mark this as solved due to forum rules and regulations.again,my apologies..thankyou

Rules and regulations? What rules? We have no rule against anything discussed in this thread. What we do strongly discourage - but do not formally rule against - is support for obsolete versions of Ubuntu. They're a lost cause and a security risk. If you want help installing a more recent and still supported version of Ubuntu, or one of the flavours of Ubuntu, to that Dell you are very welcome to start a new thread for this.

---

### Post by CatKiller on 2019-11-17
The thing to know is that if something only affects one user, they won't need to elevate their privileges to change it. If it affects all users, like setting the time does, then they probably will. As noted up thread, if an account is configured to be able to elevate its own privileges it's only that account's password that will need to be used.

It is possible to configure a Ubuntu to automatically log in, which is why your friend can use the computer otherwise, even having forgotten the password.

Using an OS that old means that it's unsafe to use it online. You've missed out on security updates from between the last time it was used and when it went End Of Life, and you can't update it to that point now because those repositories are long gone, and you can't remember the password anyway: installing software affects all users. 

The XPS 13 Developer Edition, which is what you have there, is not a low-powered machine. Installing something modern and supported on it will be fine, regardless of the desktop environment you pick. Kubuntu 18.04 is perfectly happy on mine. Dell picked well-supported components to put in those machines and upstreamed any tweaks they needed to make.

They no longer directly sell replacement batteries for the older models, but you can still get them from third-party suppliers that bought their old stock. Replacing the battery is a fairly straightforward procedure.

It is possible to reset the password with physical access to the machine should one forget it, but the priority for that machine is getting it so that it is able to get security updates again. An Ubuntu install is painless and takes about 20 minutes. You just download the image, put it on a USB drive, and reboot. The environment that you install from is itself a fully functional Ubuntu install, so you can browse the Internet or whatever during those 20 minutes.

---

