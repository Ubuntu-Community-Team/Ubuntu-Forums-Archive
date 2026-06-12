---
title: "Help! Can't boot Fiesty after adding programs to startup"
date: 2007-08-30
forum: General Help
---

### Post by pumblechook114 on 2007-08-30
Greetings,

I am a new Linux user coming over from Windows.  I've been playing around with Ubuntu for awhile, just trying to get the hang of it, but right now its got me stuck.  After reinstalling Ubuntu 4 times in the past week, I'm determined to try and fix this problem without going through all that again.

Last night I finally got beryl, avant window navigator, and gdesklets to play nice together.  So, I added avant window navigator and beryl to the startup programs (gdesklets had already been there successfully) and rebooted my machine.  I get the login screen, login with my account, and then just a black screen.  Figuring beryl or avant manager to be the culprit, I restarted and created another account.  I login to that account, start beryl-manager, and it works fine.  Then started avn, that works.  So I try to add just beryl to the startup programs, reboot, and see if the same thing happens.

After the Ubuntu loading screen on reboot, I get a message that states "The GDM user 'gdm' does not exist.  Please correct GDM configuration and restart GDM".  So I hit enter and the machine starts to go through the boot process, then eventually stops at a prompt that asks me for my login.  It looks kind of like this:

kinit: No resume image, doing normal boot...
Ubuntu 7.04 <computer name> tty1
<computer name> login:

So I try to put in my user name and hit enter, and after I do so, it gives me this:

configuration error - unknown item 'CLIENTADD' (notify administrator)

This message repeats about ten times, then this follows it:

configuration error - unknown item 'ADD' (notify administrator)

This repeats about ten times more as well, then asks me for my password.  I put it in, then it just simply says "Login Incorrect".  I've tried repeating this with different user names/passwords, but it always does the same thing.

Trying to start in recovery mode yields no better result, not even a command line.  When I try to do that, it goes through the process of booting, then eventually ends with a blinking cursor, with the last line of code saying:

init: rcS-sulogin main process (4552) terminated with status 139

I've tried searching the forums and researching this problem online, but so far nothing because I can't get to any sort of login screen or any command line to even try something.  I am dual booting Ubuntu and Vista, so I can get the GRUB command line, but as I've only been using Linux all of a week and a half, I'm pretty much clueless.  If I have to reinstall its not the end of the world, but I would really like to fix this without that, not only so I can learn, but so I don't have to spend all that time remembering what I did to set everything up. :)  Any help would be greatly appreciated!

---

