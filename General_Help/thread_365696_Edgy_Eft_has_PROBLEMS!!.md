---
title: "Edgy Eft has PROBLEMS!!"
date: 2007-02-19
forum: General Help
---

### Post by HellionDarkLord on 2007-02-19
The latest released version of Ubuntu has some problems.  Many people are complaining about the install cd's that they burn not working.  There is more than a cd burning problem here.  It has something to do with the way that the Xserver was upgraded.  Perhaps it is only because there is no longer any Mesa drivers? Edgy won't, in many cases, detect video hardware in one machine, and then work great in the next. The problem isn't the cd, it's something more serious.  I have 12 machines and currently only 3 of them work using the Ubuntu 6.10 Edgy desktop cd.  All 12 machines work using the Ubuntu 6.06 LTS Dapper Drake desktop cd. 

I was able to make Three other machines work, but only after a lot of work.  The worst scenario was the most work I've ever had to do to an operating system to make it work on a machine.  I wanted to donate that machine so I wanted it to be perfect on the way out the door and that meant that I HAD to have the latese version of the operating system right?

What I had to do:  Install 6.06 LTS completely, upgrade using the alternate install cd for Edgy while running Dapper, Reboot into failsafe from the boot menu and reconfigure the xserver using the sudo dpkg-reconfigure xserver-xorg command. 

That got me to the point where I could do everything in the desktops except scroll upwards with the mouse or scrollbar because it messed everything up.  Then I attepmted to download drivers for my exact video card (thinking that they would work better) and found out that the only drivers available through the manufacturer were indeed open source, but only good for Xfree86 and not Xorg.  So I went through all the hassle to convert Ubuntu to xfree86 but in the end got nowhere. 

I did everything exactly as I was supposed to, and I know what I'm doing. After only a day of smooth running I tried to upgrade the system thinking to do some art with gimp and Whammo!! everything blew up on me.  I suppose that I shouldn't really have messed with it, but HEY I'm new to Ubuntu and have only tried a few times to really use the system.

I'm no expert, but I think that the xserver setup in Edgy needs some serious reworking because EVERYTHING works fine here in Dapper Drake 6.06 LTS

If this is a precursor to what the future holds for ubuntu then i want no part of it.  Then again Dapper works so good I would really hate to see the project go down the tubes.

Thanks for any input on how to make Edgy work better.  I really like it, I just wish it'd work better on all my machines and not just the ones with super common video cards.

have FUN and a little RUM won't hurt anything except electronic devices and driving ability.

---

### Post by koshari on 2007-02-19
why couldnt you boot into edgy in safe graphics mode?

---

### Post by llamakc on 2007-02-19
Doesn't this non-support post belong elsewhere?

---

### Post by HellionDarkLord on 2007-02-20
sorry if I posted this in the wrong place.

I am asking for support.  I'm asking if there is another reason that things won't work. and NO, It doesn't make any difference whether or not it is in safe grafix mode.

The main thing that I wanted to point out is that Dapper works where Edgy doesn't.  That way maybe some people who have never tried Ubuntu and started with 6.10 and had problems wouldn't just leave ubuntu alltogether.  It's a roundabout way of doing it, but a lot of people will read this and then go Okay so I should install Dapper instead and see how THAT works before I give up and would be more inclined to listen to someone complaining about Edgy than someone just trying to say well, give Dapper a try.  

Maybe I shouldn't have done it that way?

later

---

### Post by kerry_s on 2007-02-20
Kinda late now edgy's already been released and there not going to go backwards to fix problems. You could try feisty and see if it was fixed there, if not you should file a report so it can be fixed before feisty release. Just my 2 cents.

---

