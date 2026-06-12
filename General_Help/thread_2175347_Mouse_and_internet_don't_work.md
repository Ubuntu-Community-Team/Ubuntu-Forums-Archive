---
title: "Mouse and internet don't work"
date: 2013-09-18
forum: General Help
---

### Post by bjngchn on 2013-09-18
Installed alt-cd kub 12.04. Mouse right-click and wired internet don't work. No errors, they just don't work, no information.  (Why do I have to spend any time on this). Thanks for help in advance.

---

### Post by TheFu on 2013-09-18
Thanks for the abundant troubleshooting information!  
* [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
* [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
* [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware)
might help.  Being just a little more specific would be helpful?

---

### Post by bjngchn on 2013-09-19
I know nothing about all this. Things just have to work. If I buy a new car gas pedal should work. Why do I need to read a technical book just to fix a problem which shouldn't exist.

---

### Post by bjngchn on 2013-09-19
And third problem: Flash disk doesn't mount. Again nothing happens, no error, no warning, no options. Just a dead system which doesn't allow anything to happen. I change mounting preferences to: automatically mount removable media. Still nothing happens. Why???  Who is responsible for all this?  Are all these done intentionally? If thisis happening because of defauls: These defaults are awful.

---

### Post by bjngchn on 2013-09-19
Ok flash disk works, but memory stick connected thru card reader doesn't work, unless a flash disk is connected at the same time. So  essentially third problem is not serious. ................. Mouse right-click still doesn't work. There is a menu which allows mouse actions to be defined. Only one thing can be done there: add or remove left button action. Other actions, like defining right button action is not possible. Why the hell do I have to define right button action; and why I can't still define it.  .................. Still can't connect to internet. Wired connection: there is nothing there. You can't click something to start doing something. Totally dead, no information, no hints, no button to click. Just an empty menu. ................... Are alt-cd's made more tricky intentionally maybe, because absolute security for user,  is lack of security for authority?

---

### Post by Impavidus on 2013-09-19
[http://ubuntuforums.org/showthread.php?p=12793033](http://ubuntuforums.org/showthread.php?p=12793033)

That's why things don't always just work. If you buy a new car it works, if you buy a computer with an operating system it works. But if you buy a new motor to put in your car it's not guaranteed it will fit, just as installing a new OS can give trouble.

It may be possible to fix your problems, but we need more information. And yes, the alternate iso can make things more complicated, but this has nothing to do with security for any authority.

---

### Post by TheFu on 2013-09-19
> **bjngchn said:**
> I know nothing about all this. Things just have to work. If I buy a new car gas pedal should work. Why do I need to read a technical book just to fix a problem which shouldn't exist.

I can read that you are frustrated. Taking it out on us is not productive.

At this point, we don't know **anything** about the car you are driving. It could be a 30 yr old Yugo or so new that only the "dealership" can work on it.  I can promise this, **complaining over the phone to the care shop will not get your car fixed.** Do you see the analogy?  You have to bring the car into the shop, see if it is covered under warranty, and/or pay for repairs.

If you purchased the computer pre-installed with Ubuntu, take the computer back to the vendor and they will help or replace it.

Anyway, we volunteers, would like to help, but we need for you to do some of the work.  If that is not to your liking, then you should take your computer to a computer shop and pay $300-$500 for them to "fix it."

OTOH, if you are willing to provide the requested information, we are very willing to help.  Solving issues is fun for us.

---

### Post by CitadelUniversal on 2013-09-19
If the flash disk doesn't mount and other hardware don't mount aswell do you have selinux installed? SELinux protocols can disable access to the flash drive and among other hardware for the computer - please check if you installed or have selinux pre-installed..... And also posting system specs might help the situation for other users on this forum.

---

### Post by buzzingrobot on 2013-09-19
Ubuntu users typically do not have these problems.  Logically, then, there is something about your hardware and/or configuration that's causing your problems.

You can help people here help *you* by providing some very basic information to identify your hardware and to be prepared to answer questions that are trying to elicit more data. If you don't know how to get the info to answer a question, that's fine.  Just say so and someone will likely explain it.

---

### Post by mastablasta on 2013-09-19
we are just users.

[Suggestions on how to get your support questions answered as quickly as possible]("http://ubuntuforums.org/showthread.php?t=1422475")

we need Model, type of mouse
system specs

regarding the flahs/usb stick issue it is configuration issue on install. again we do not know how you did the install. i've only installed linux about 6 times and have never seen such mouse issues. i ran it live many times more. so you problem seems like a nice challenge (if i can find the time) ;-)

---

### Post by buzzingrobot on 2013-09-19
Knowing the reason for the choice of the alternative install image (hardware related?)  and if any issues were noticed during the install coud be useful.

Also useful:  Do the problems exist when a live image is booted and used?

Also, was net connectivity available during the install? Is it available now via wireless?  Have updates been installed, or has that been prevented by lack of connectivity? (Perhaps one or more of the problems are due to missing or unupdated packages.)

How has lack of net connectivity been verified? When "ping ubuntu.com" is entered in a terminal, what's the response? If that fails,what does "ping 91.189.94.156" produce?

---

### Post by bjngchn on 2013-09-19
New Asus computer. Installing from alt-cd was easy, but first I had to find a way to enter BIOS and change a few things (booting from cd first; otherwise installation cd is ignored completely).   (There must be some incompatibility between computer (defaults) and linux (defaults). I blame the computer, but linux community should  find the problem and complain about it , maybe (assuming many others had the same problem in the past). )  I think mouse (embedded mouse) and internet was working when it was on windows. I resized partitions to install linux on remaining part, but changed  my mind and decided to erase windows completely, and use the whole disk for kub....   Wireless seems to work. It was showing two wireless channels which I could try, but I didn't try. I disabled the wireless to reduce radiation...  Wired networking is completely dead. There is "disconnected"  icon. Ping doesn't work either. ..  Last time I installed linux, there was a problem, and after updating the linux, the problem was solved automatically. This time  since there is no (wired) internet I can't do update....   While installing linux I was being asked IP's or other connection info; which didn't make any sense so I skipped such stuff. ... One more thing: I installed linux from alt-cd, but forgot the password (so I couldn't login even once); and so I installed it again from the cd. ... Btw authority should be extremely angry with alt-cds, so there must be some pressure on creators of them, and maybe it works.

---

### Post by buzzingrobot on 2013-09-19
BIOS settings are whatever ASUS set them at for compatibility with Windows.  There is no default.  You probably had to change the boot order to boot of the CD or USB stick, as you would have had to install Windows on a machine running another OS.

If  you can boot and run a live image without the problems you are reporting, that indicates that it s very likely a configuration issue, not a driver issue. Knowing that, one way or the other, would be helpful.

If wireless works, then you can update, and then see if the wired ethernet works. I assume one or both of the wirelss networks on offer are *your* networks.

The standard Ubuntu install does not ask for IP addresses. I can't recall ever using any Ubuntu or any Linux install method that prompted for raw IP addresses.  If your install asked for them, and you ignored the request, perhaps your install was faulity.  Ignoring requests like that and expecting things to still work OK usually goes wrong.

So...

Laptop?  Desktop?

Wired Mouse? If so, USB or PS/2?

Wireless Mouse?  Bluetooth or wifi?

Mouse brand and model?

If you attach a USB stick, and open the file manager, do you see an option to mount the stick? 

Can you test if the ethernet is working via another machine?  

Can you test if you can Ping a URL versus an IP address?  If you cannot ping a URL but you can ping an IP, that indicates an issue with address resolution, not basic connectivity.

---

