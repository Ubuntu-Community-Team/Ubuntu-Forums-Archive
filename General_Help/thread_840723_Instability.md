---
title: "Instability"
date: 2008-06-25
forum: General Help
---

### Post by tomparkca on 2008-06-25
I have installed Ubuntu for the 3rd time just recently because of Instability with my Windows XP OS.
I have never had problems before, I have ran Ubuntu on this same computer twice before, the only difference is I have a second Hard Drive, that is not being used.

Ubuntu is very unstable this time around, Sometimes it freezes at the loading screen, or at a black screen before the login screen.
Other times it freezes completely while transferring files, or windows will close for no reason.
I also had problems loading the OS a few times.

Installing Ubuntu was a pain in the ***. Because my computer would freeze sometimes in the middle of the installation.
I believe that it may be a serious hardware error, and their may be nothing anybody can do to help, But any advice would be much appreciated.


I have also been unable to update Ubuntu and their are 226 Updates ready to install.
Read Other Thread for details on Update problem.
[http://ubuntuforums.org/showthread.php?p=5261569#post5261569](http://ubuntuforums.org/showthread.php?p=5261569#post5261569)


My firefox just closed by itself after posting this.

---

### Post by Pjotr123 on 2008-06-25
Most of these weird problems are caused by defective RAM memory. Run memtest (third option in Grub) to test your RAM. 

If a RAM strip is defective, simply yank it out and replace it with a new one. RAM strips are not very expensive these days.

Greeting, Pjotr.

---

### Post by jimv on 2008-06-25
I wonder if it could be a RAM problem.  Try running Memtest86 on your machine.  It should be at the bottom of your Grub menu when you boot the machine.

---

### Post by tomparkca on 2008-06-25
I was going to run that test, but it seemed like it was going to take to long, so I closed it, 
I wasn't sure that was related to the problem, so I didn't think it was necessary to test.

How can you tell what type of RAM is right for your CPU I once put RAM from another computer in mine, and my computer went insane.

---

### Post by jimv on 2008-06-25
I think it could just be bad ram.  I was having some similar behavior after buying new ram, and it turned out one of the sticks was bad.  So just start Memtest86 and go eat or something.  It can take about an hour or so to run...maybe longer.

---

### Post by breadbin on 2008-06-25
I saw a link exactly to tell you what kind of ram is in the mobo but i can't see it at the moment. you might find it about 2 weeks ago in the ubuntu forums but i had no luck.

alternatively you can go to 

[http://www.komplett.ie/k/kc.aspx?bn=10232]("http://www.komplett.ie/k/kc.aspx?bn=10232")

with the manufacturer and model of your motherboard and it tells you the type of ram thats ok to use. obviously you don't have to buy it from them but its handy. hope that helps

---

### Post by tomparkca on 2008-06-26
I did the mem test, and I think it just starts over every time it finishes,
So I'm pretty sure the test finished and passed about 4 or 5 times, because I had the test running for a few hours.
So I'm not sure if its the ram, because no errors where found.

---

### Post by tomparkca on 2008-06-26
I just realized I am running Ubuntu 7.04
I am currently trying upgrade to 7.10 then 8.04 LTS

Sorry about the double posts

also things seem a lot more stable now after I got the updates working

---

### Post by jimv on 2008-06-26
> **tomparkca said:**
> I did the mem test, and I think it just starts over every time it finishes,
So I'm pretty sure the test finished and passed about 4 or 5 times, because I had the test running for a few hours.
So I'm not sure if its the ram, because no errors where found.

If it passed MemTest, then the RAM is fine (yeah, it keeps looping).

---

### Post by tomparkca on 2008-06-26
Well, Firefox closes still, and During my update to ubuntu 7.10 something went wrong, and when i looked to see what, I couldn't move the cursor because the computer was frozen, I turned it off, and when I logged on next time, It was a blue loading background, instead of the orange one from 7.04.
But the Desktop didn't load, I am typing this now using GNOME Failsafe session.

Is their anything I can do to fix this upgrade, or upgrade further,
preferably using the terminal which seems to be a lot more stable and reliable.

---

### Post by jimv on 2008-06-26
You could try the 8.04 live cd and use that for awhile to see how things work for you.

---

### Post by tomparkca on 2008-06-26
I have managed to update to 8.04 I have found myself having to use the 'dbjk configure -a' command or whatever it is, a few times.

I cannot log in normally I always have to use failsafe, I am thinking about reinstalling windows, just so I can download the 8.04 distribution and burn it off, I am planning on running a duel Boot, Ubuntu and XP once I find a version of XP that I like.

Any ideas why I can't log in normally, Because I could the last time I used Ubuntu on this computer, Is their any fix for it?

I'm currently searching the forums for a thread I saw with a similar problem, but no luck yet.


Computer has started freezing again.

---

