---
title: "I recieve this during boot up |B`e-$|B`e-$_  and it just stays there"
date: 2008-06-08
forum: General Help
---

### Post by garethsimpsonuk on 2008-06-08
As stated I receive this durting boot up, it's had me sat, aggravated in front of it all weekend, no1 seems to be able to help me in my other post, or it's because it's buried in a few posts so I thought I'd start again as this had deviated from the original posts topic anyway. This is quoted from the original post.

> yea thanx logos it was driving me mad last night! i don't know why but know when I boot up, during post I see

Verifying DMI Pool Data....
Boot from CD:..
|B`e-$|B`e-$_

I've tried to copy it exactly but there's some strange symbols that aren't on the keboard. Such as the first vertical dash ( which is again repeated before the B )has a kinda small line coming out of the left in the middle so it's a bit like this -| but they connect and he horizontal line is much shorter. The underscore isn't really an underscore more like a cursor as it's blinking and the accent is directly over the e.

Anyway whatever it is it's hard to search for the problem when I can't even copy the display so I'm stumped. I reset the bios and it's still there, and disabled anything and eveything in different combnations and still no luck. I even disconnected the CD drive altogether. ( I think I recieved a boot disk error that time )
Why is it trying to boot from CD and what is that strange set of characters. It's like it's waiting for something due to the blinking cursor but never gets anywhere.

Anyway anyone got any ideas for a very very annoyed ( with myself ) ubuntu user?

Thanks

oh and thanx 4 ur post logos, I expect you've gone now though

I really hope someone as an idea as i've been on this all weekend.

Cheers guys

---

### Post by garethsimpsonuk on 2008-06-08
bump

---

### Post by prshah on 2008-06-10
> **garethsimpsonuk said:**
> As stated I receive this durting boot up, 
I really hope someone as an idea as i've been on this all weekend.



I think it's either a CD media fault or the CD drive fault. Both can be confirmed/eliminated by testing the CD from the startup menu options. Then, if that passes, maybe you should look at memtest.

---

### Post by garethsimpsonuk on 2008-06-12
i tried unplugging the CD drive and I still got it. The install CD worked fine and I installed ubuntu no problem it was just trying to boot I recieved it.
Since then it suddenly just started working, I don't know what I done but it boots fine. The only worry is that it still displays the CD bit when I know it shouldn't if there's no bootable CD in the drive. It 's not causing problems but it's defiantely not right.
I'm just worried it causes problems further down the line.

---

### Post by plucky on 2008-06-13
> **garethsimpsonuk said:**
> i tried unplugging the CD drive and I still got it. The install CD worked fine and I installed ubuntu no problem it was just trying to boot I recieved it.
Since then it suddenly just started working, I don't know what I done but it boots fine. The only worry is that it still displays the CD bit when I know it shouldn't if there's no bootable CD in the drive. It 's not causing problems but it's defiantely not right.
I'm just worried it causes problems further down the line.

Change the boot order in the BIOS to 

1) Hard Disk
2) Floppy        -if you have one
3) CDrom
4) Other

You get the message because it is trying to boot from CD and there is no CD in the drive,so it moves on to the hard disk.This is how it is supposed to work if you have the CDrom selected before the Hard Disk.


Good Luck

---

### Post by garethsimpsonuk on 2008-06-13
this '|B`e-$|B`e-$ ' isn't right tho is it? thats what i was getting. since then i've been scared to go back into the bios!

I have options in the BIOS to do with my RAM / CPU that I've never seen b4, some of the options are locked. I guess this is to do with overclocking. Does anyone kno a good place to find out more about this plz.

thanx 4 the post

---

### Post by plucky on 2008-06-13
> **garethsimpsonuk said:**
> this '|B`e-$|B`e-$ ' isn't right tho is it? thats what i was getting. since then i've been scared to go back into the bios!

I have options in the BIOS to do with my RAM / CPU that I've never seen b4, some of the options are locked. I guess this is to do with overclocking. Does anyone kno a good place to find out more about this plz.

thanx 4 the post


Don't be scared of the BIOS.You can always reset it to Factory defaults.The bios is only a crude method of reading the MBR of a disk so the system can boot.It is very basic and writing to the screen can get corrupted,which is what I think you are seeing.

Go into the BIOS and change the boot order,so it doesn't attempt to boot from the CDrom.

To find out what the options are in the BIOS,you need to get the user manual for your motherboard.Go to the manufacturers website and download the user manual for your model of computer or get it off one of the disks that shipped with your system.

Good Luck

---

### Post by garethsimpsonuk on 2008-06-13
sorry if rushed only got a min. yea I tried reseting CMOS with the jumper on the mobo and still got the error. I salvaged the box off a m8 and recieved nothing with it. How do I find out what board / chipset I have. The manufacturer ( tiny ) is bankrupt

---

### Post by plucky on 2008-06-13
> **garethsimpsonuk said:**
> sorry if rushed only got a min. yea I tried reseting CMOS with the jumper on the mobo and still got the error. I salvaged the box off a m8 and recieved nothing with it. How do I find out what board / chipset I have. The manufacturer ( tiny ) is bankrupt

I think you might be out of luck with the user manual,couldn't find a tiny website.

**Did you try changing the boot order in the bios?**

---

