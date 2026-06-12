---
title: "I messed up mu USB memory key and I don't know what to do"
date: 2007-01-14
forum: General Help
---

### Post by Ulysses on 2007-01-14
Hey

Evening everyone
I received a 1GB Lexar Secure II memory key for Christmas from my wife. It worked like any other memory key with no problem until I started messing around with it.
I went about formatting it and removing all of the software that came on the key but now the key won't let me write anything to it because I don't have permission

How do I correct this so I can write to the key? Any ideas?

Regards,
RAR

---

### Post by randomnumber on 2007-01-14
I am not sure this is what you want but the command to change file permissions is chmod.
To get a description of how to use it type "man chmod". You will likely have to use sudo as in "sudo chmod 660 filename"

If you have time I suggest looking into Linux file permissions more or ask me to explain a little and I will try.

Good Luck

---

### Post by kolinab on 2007-01-14
Hi,

I don't know the best solution but I know what worked for me. I uninstalled the silly 'u3' software with an uninstall utility from u3. Then I reformatted the entire drive FAT32 in GParted I think. That worked for me and I didn't have ownership problems. I couldn't remember the easy way in Linux to label the drive with my own label so i simply plugged it into my windows box and hit rename in there to give it the nice label . . . 

Hope you get things sorted out.

K

---

### Post by DarkN00b on 2007-01-14
I did something silly like this myself. The easiest solution was to reformat in WinXP. See XP is good for at least 1 thing...formatting drives. :D

---

### Post by Ulysses on 2007-01-14
Hey

I never go with the easiest solution when the hardest solution has the potential to drive me crazy and offer the greater amount of satisfaction!

My laptop is all Ubuntu / took Windows off of it completely, so I would have to turn on my work computer (yeck! It's Sunday / the thought is abhorrent) and use it to finagle a solution

I downloaded [**_GPartEd_**]("http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3-1.iso&use_mirror=internap") Live CD and burnt it to a CD, ran it, and fixed my problem with my USB key

Which meant that I had to consolidate my data from my other 2 USB keys and proceed to screw them up the same way.

Now, my friends, that is the way to start a Sunday

Thanks a tonne for your suggestions. One more reason why Ubuntu rocks among the distros. Does any other distro have this kind of community support?

Regards,
RAR

---

