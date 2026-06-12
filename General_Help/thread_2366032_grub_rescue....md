---
title: "grub rescue..."
date: 2017-07-13
forum: General Help
---

### Post by fortesque2 on 2017-07-13
Hello, I am new to ubuntu forums, and Linux systems in general. I have tried to install Ubuntu, and Lubuntu on my pc. I already had windows Xp on it but it was starting to work slugish since its an old pc at my vacation home. 
Specs are something like this 
Asus A7V600
1gb ram
Amd Althon XP 2000+
Ati Radeon 9200SE 128mb or something like that

Now i know the pc is acient, but for simple web browsing, music play and emails+some work its ok. Since I tried Ubuntu on my laptop, I tought I would install it on pc to revive it, and I did. I made seperate partition, so it would work alongside XP that I already had instaled. The problems started there. At first, I couldn't get Linux to show in boot menu, it only booted to windows, even though there was a partition with linux on it. It just didnt show it. I managed again somehow to enter linux, and saw a thread about how to fix grub/boot menu from inside Linux. When I did that, I restarted pc, and sudenly I had that grub menu, but my screen said it was wrong resolution, and didnt show anything. I only knew that was it because when i moved arrow key down, it booted to XP, and when I waited, it just booted to linux. 
Well, I could have left it like that, but I really have a problem with things not working correctly, and since this was such a hassle I lost whole day just trying to get it to work, I got angry, entered XP and just formated all space except C: partition where XP was, and left it like that, in hope I would just do it all over again, boot linux and install it in that space.
My problem started there, since when I restarted pc, i was greeted with 
error: unknown filesystem.
entering rescue mode...
grub rescue>
I am new to Linux, and didnt know that would happen, and honestly its a big dissapointment in my book, I mean why would a simple formating of drive break whole pc. If you do that to windows, it would just not boot, but not enter this retarded mode...
Still, I am determened to instal linux at some point, after I fix this, but the problem is, nothing is booting now!
I got 1 CD drive, and 1 DVD drive, that both died recently, so that is out of the question, and I just barely got it to boot once when I did.
I tried putting Linux or even XP on usb stick to boot with that, but it doesnt even give me any boot error, it just goes to grub rescue like there is nothing inserted.
And I got no option to get another CD or DVD drive, since that would be more of a hassle and this PC is not worth that, so please if I could hear any suggestions that are not related to going and buying stuff (dont even have a store here, I would have to return to the city and later come back with anything, and I would like to fix my pc while im here :) )
Sorry if that seemed rude, but as I searched this problem, saw a lot of threads where people explicitly say "I dont have a dvd drive", and pointless suggestions that included use of said dvd drive. :)
Thank you for your time

---

### Post by RobGoss on 2017-07-13
Hello and welcome, are you able to create a bootable USB?

You stated you don't have a working CD or DVD drive correct? Then your only option is using a USB drive for your installation, and if this is the case your machine may not recognize a USB drive and you may not have many options if so

Windows XP is no longer supported and is a big security risk, if you're not connected then it's OK but other then that I don't see why anyone would use Xp anymore 

This is just my view on this, With the limited hardware for that machine. I would just use a lightweight distribution like Lubuntu, choose the install alongside Windows, unless you want to use the entire disk space them it would simplify things

You might find this community page helpful if you decide to dual boot [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Lubuntu is the best choice for this machine and you should be able to install it

Linux requires time and patience, it's all part of the learning process once you've master that everything else is easy

---

### Post by fortesque2 on 2017-07-13
Hey man, thank you for the quick reply. Yeah, as I have stated, drives  dont work (+even if I wanted new one, its still like 20$ in my country,  and this whole pc isnt worth that much, id rather throw it in the lake :P).
XP is sucks, I know,  thats why Im here, but I would like an option to dual boot just for the  convinience if one system fails. Honestly, at this point, I would just  like to even have any system, and not this grub. :)
But to answer  your question fully, no optical drives, and as you noticed, cant even  get it to boot from flash. But, before this happened, at least I got an  error, and I knew it at least tried to boot off usb but failed (in bios,  there is an option to boot from flash), now it just enters grub not  even trying to boot.
So yeah, my question is, is there anything I  could try (im not that familiar with linux, but I learn fast) to return  to the XP that is already on drive C? Since I only formated rest of  drive, and restarted, that Xp should be intact on hard drive. Is there a  way to skip this grub and boot into XP that is on my hard drive? 
After that I would manage, thats how I even instaled lubuntu, by saving boot files on C and booting from hard drive.

---

### Post by RobGoss on 2017-07-13
First I would have to advise if Windows XP is your only OS I wouldn't want to tell you anything incorrect that may cause you to loose anything

Hopefully you have some sort of backup just in case something goes wrong 

If you tried to Install Ubuntu as a dual boot them I'm certain the Windows **MBR** boot manager was over writen by Ubuntu's bootloader that's why you're seeing Grub at boot up

Do you have any recovery disk for XP?

I'm on my mobile so I'm kind of limited on information I can provide

The question is do you want to dual boot or just install Ubuntu on this machine?

---

### Post by fortesque2 on 2017-07-13
Losing data or anything is not a problem. If there was a way that I can return old boot loader by deleting everything, I would. :) My problem now is, I can't get anything to boot. 
Usb boot got me an error before (I booted and instaled this linux directly from hard drive, there is an option in unetboot program), and now it doesn't even show error, it just goes directly to grub rescue...

So my question is, what are the options to get a system to boot (any system, you asked what I wanted, I want any system, since now none will load)
**If I can't boot from optical, and my mb doesn't seem to boot from usb bootable flash** (beleave me I tried everything, it just gets error, flash works on any other pc but that), **what are other options of instaling a new OS?** (if you are an expert on linux, write for linux, if you know about windows, add that too, as I said, I just want any system)(also keep in mind that pc is still stuck on recovery)

I bolded question, because I would still like the answer to it if this happens to me again for any reason, be it I get a hold on some netbook with no optical, or whatevs. 
Buuut, there has been a development in my situation. My neighbour has arrived here, and he has a PC in his home, and he lent me his drive to try and boot (Cd rom drive). Well, since I want to instal linux, I got Lubuntu 14.04 version (saw that is latest that fits on a CD), got to the boot screen, went on option to install Lubuntu, and now when it starts it gives me this message and just stops:

panic occurred switching back to text console

That is in the end, there is some more text but I don't quite understand it all, its just list of processes that it did and failed (i think).

When I boot that same disc on 2 other PC, it works, even in Try mode, it boots into Lubuntu.
On this PC, it won't even load try mode, it gets me that panic error...
I will try later to just install XP SP3 on it, since Im sure that will work, but I don't see why Lubuntu has so many problems loading on PC that so easily loads windows...

---

### Post by RobGoss on 2017-07-13
You might want to change the Title of your thread to something along the line of, How to** installing Ubuntu **you might get better help that way

---

