---
title: "Computer won't boot after apt-get update"
date: 2015-07-14
forum: General Help
---

### Post by JaredRuiz on 2015-07-14
TLDR: [http://paste.ubuntu.com/11879449/](http://paste.ubuntu.com/11879449/)

(Not)TLDR: I got a new Logitech headset (model 390: [http://www.logitech.com/en-us/product/stereo-headset-h390](http://www.logitech.com/en-us/product/stereo-headset-h390)) and foolishly assumed that upon plugging it in my computer would magically be able to use it. That was false. Ubuntu wasn't properly recognizing it, so I followed the advice here: [http://askubuntu.com/questions/131812/logitech-usb-headset-not-working-on-12-04](http://askubuntu.com/questions/131812/logitech-usb-headset-not-working-on-12-04). 

I ran: 
[COLOR=#111111][FONT=Consolas]sudo add-apt-repository ppa:ubuntu-audio-dev/ppa[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] 
    sudo apt-get update; sudo apt-get dist-upgrade -y[/FONT][/COLOR]

After doing this I restarted, and I couldn't boot. I tried a few more times, with the headset both plugged in and unplugged. I then ran boot-repair from a linux boot disc, and it told me the issue was resolved, but upon trying to boot again I had the same issue. Hence the above boot repair link. Oh, and the headphones were unplugged this entire time.

I assume the issue is a bad driver somewhere, but I am definitely out of my league right now. Any help would be appreciated. Thanks!

---

### Post by branau on 2015-07-14
I'll be honest with you when I say I don't have a clue as to why this is happening but I'd be happy to help try! Do you get any error messages or anything of the sort? Some sort of clues to start with?

---

### Post by monkeybrain20122 on 2015-07-15
I too have no idea, except to say that  the person who gave the instruction dist-upgrade -y was rather reckless,  dist-upgrade would remove packages (as oppose to upgrade) if it finds a conflict, and -y means saying yes automatically to all the prompt so basically you are telling the system "remove whatever you think appropriate and don't bother me about it". It is very bad combo.

---

### Post by QIII on 2015-07-15
Hello!

Could you clarify what you mean when you say it won't boot?

Do you mean that you don't reach a graphical login, that you get a black screen with a blinking cursor, etc?

Do you get dropped to the command line?

Do you see the grub menu?

Can you give us the specs of your machine?  Are you using a USB2 port or USB3?

---

