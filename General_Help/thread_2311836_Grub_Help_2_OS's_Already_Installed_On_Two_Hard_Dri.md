---
title: "Grub Help: 2 OS's Already Installed On Two Hard Drives"
date: 2016-01-30
forum: General Help
---

### Post by Clifurd on 2016-01-30
Immediately after typing this question, I restarted my computer and used the F11 key during boot to use my motherboard's boot selection option
and booted into the windows drive.  Then, I shutdown and restarted and booted into the Ubuntu drive and GRUB came up on it's own.
Now, I have a completely different issue, and that is that windows does not appear in the Grub list. 
I will look into this the best I can.  I think I remember something about Boot-Repair on windows to get this to work.

I really wish I could delete my threads.  I'm sorry if I have wasted anyone's time.  I will do what I can and edit this post again if I can't figure anything out.
Any input is highly appreciated.  I just figured I would come back and edit the thread as fast as I could before anyone read it.

######

I have 2 hard drives.  One containing Ubuntu 15.10 and the other, Windows 7.
I have never had both drives connected to my motherboard at the same time because the last time I tried that,
I did something wrong and ended up unable to boot into the windows HDD.

Now I want to have them both connected at the same time and boot into Grub,
 having Ubuntu be the primary OS to boot (I want it to boot into Ubuntu automatically if I hit my power button and walk away
 but have the option to manually boot into windows if I select it before the timer runs out).
I have both drives connected now and it boots into whichever HDD is selected as #1 in the boot order on my motherboard.

I had Grub working at one point, but I think it was because I had my windows HDD installed at the time of installing Ubuntu.

Is there any way for me to get GRUB to work now that I've already had both OS's set up separately for awhile now?

If it weren't for some games that I play, I would never use windows ever again.


Something tells me that this is an annoying question which has been asked a million times but I couldn't think of a way to search for it with the 2 hard drives issue.
Something also tells me that this is easy and I'm just lacking sleep and just need to do more research.    Any help at all would be much appreciated.  I do have 15.10 on a disc, also.

If this question has been asked to the point where this is pretty much spam, please just let me know and delete this thread, lol (and my first/previous thread). 
I have no idea what my problem was on my first thread but it is cringe-worthy and no way to introduce myself to this community. So for that, I'd like to profusely apologize.

---

### Post by grahammechanical on 2016-01-30
Stop and think for a moment. If we install Ubuntu and the drive with Windows on is not connected then Ubuntu's boot loader (Grub) cannot possibly know that Windows is an alternative OS. Can it? So, we need to tell Grub that Windows is there. So, with both drives connected load into Ubuntu and run

```
sudo update-grub
```

You should see a printout that includes a reference to the Windows boot loader. That means that there will be an option to load Windows in the Grub boot menu. Continue booting from the Ubuntu drive.

One of the great things about this forum is that we treat people as individuals. We do not mind giving the same advice that was given to someone else a short time earlier. It is nice if people browse the forum for answers. It is nice if people see from the threads already started the kind of information that is useful for us to know. So, that we do not waste effort asking for information. It is nice if someone who has their problem fixed then joins in and helps others with the same problem. These kind of things make a great user forum.

Regards.

---

### Post by Clifurd on 2016-01-30
Amazing.  Such a simple solution, Thank You very much. 
I should have been able to figure that one out myself, as I had stumbled across a thread where
someone mentioned it but I didn't understand quite what they meant.
Also, thanks for alleviating my concern about posting questions which may have already been
answered multiple times.
I'll get the hang of all of this eventually.

---

