---
title: "Xubuntu 14.04.3 32bit Won't Restart"
date: 2015-11-29
forum: General Help
---

### Post by 2guntom on 2015-11-29
Dell Optiplex 755 SFF
Intel Core 2 Duo E8600 3.33GHz
3GB RAM
ATI Radeon DH 3400

Everything is up-to-date and runs fine. It starts fine. It shuts down fine. But, like the title says, it won't restart. During restart, the Xubuntu screen comes up with the the swirling circle graphic, and right about the time the screen *should* go black, instead it freezes. I have to hold the power button to power it down.

I'm sure this is something simple, but i don't know where to look.

 - -

---

### Post by Sweet_Baby_Jamie on 2015-11-30
Is this a fresh install or an upgrade to 14.04?  It matters because previous versions used a different setup for start up, screensaver (lightlocker instead of xscreensaver), and other stuff.  

If you still have the Live DVD, boot from it and remove xscreensaver from your existing install if it's in there.

---

### Post by matt_symes on 2015-11-30
Hi

> **2guntom said:**
> Dell Optiplex 755 SFF
Intel Core 2 Duo E8600 3.33GHz
3GB RAM
ATI Radeon DH 3400

Everything is up-to-date and runs fine. It starts fine. It shuts down fine. But, like the title says, it won't restart. During restart, the Xubuntu screen comes up with the the swirling circle graphic, and right about the time the screen *should* go black, instead it freezes. I have to hold the power button to power it down.

I'm sure this is something simple, but i don't know where to look.

 - -

There are a number of ways to make Linux reboot the PC. 

It does require a bit of tinkering in the command line and, as this is your first post here, i don't want you to run a mile at that thought :)

Basically we need to pass a parameter to Linux (specifically the kernel) telling it how to reboot the PC.

This will involve editing a file (/etc/default/grub) passing in the reboot= parameter to the kernel and then calling update-grub.

If your still interested in this then post back and i (or someone else on these forums) will talk you through the steps required. We may have to try a number of the reboot parameters before hitting one that works on your PC.

Ref: Documentation/x86/x86_64/boot-options.txt:

```
Rebooting

   reboot=b[ios] | t[riple] | k[bd] | a[cpi] | e[fi] [, [w]arm | [c]old]
   bios   Use the CPU reboot vector for warm reset
   warm   Don't set the cold reboot flag
   cold   Set the cold reboot flag
   triple Force a triple fault (init)
   kbd    Use the keyboard controller. cold reset (default)
   acpi   Use the ACPI RESET_REG in the FADT. If ACPI is not configured or the
          ACPI reset does not work, the reboot path attempts the reset using
          the keyboard controller.
   efi    Use efi reset_system runtime service. If EFI is not configured or the
          EFI reset does not work, the reboot path attempts the reset using
          the keyboard controller.

   Using warm reset will be much faster especially on big memory
   systems because the BIOS will not go through the memory check.
   Disadvantage is that not all hardware will be completely reinitialized
   on reboot so there may be boot problems on some systems.

   reboot=force

   Don't stop other CPUs on reboot. This can make reboot more reliable
   in some cases.

``` 

Kind regards

---

### Post by 2guntom on 2015-11-30
> **Sweet_Baby_Jamie said:**
> Is this a fresh install or an upgrade to 14.04?  It matters because previous versions used a different setup for start up, screensaver (lightlocker instead of xscreensaver), and other stuff.  

If you still have the Live DVD, boot from it and remove xscreensaver from your existing install if it's in there.

I downloaded 14.04.3, made a bootable USB. 
Out of 5 computers, this is the only one that does this

---

### Post by 2guntom on 2015-11-30
> **matt_symes said:**
> Hi



There are a number of ways to make Linux reboot the PC. 

It does require a bit of tinkering in the command line and, as this is your first post here, i don't want you to run a mile at that thought :)

Basically we need to pass a parameter to Linux (specifically the kernel) telling it how to reboot the PC.

This will involve editing a file (/etc/default/grub) passing in the reboot= parameter to the kernel and then calling update-grub.

[SIZE=3]**If your still interested in this then post back and**[/SIZE] i (or someone else on these forums) will talk you through the steps required. We may have to try a number of the reboot parameters before hitting one that works on your PC.

Ref: Documentation/x86/x86_64/boot-options.txt:

```
Rebooting

   reboot=b[ios] | t[riple] | k[bd] | a[cpi] | e[fi] [, [w]arm | [c]old]
   bios   Use the CPU reboot vector for warm reset
   warm   Don't set the cold reboot flag
   cold   Set the cold reboot flag
   triple Force a triple fault (init)
   kbd    Use the keyboard controller. cold reset (default)
   acpi   Use the ACPI RESET_REG in the FADT. If ACPI is not configured or the
          ACPI reset does not work, the reboot path attempts the reset using
          the keyboard controller.
   efi    Use efi reset_system runtime service. If EFI is not configured or the
          EFI reset does not work, the reboot path attempts the reset using
          the keyboard controller.

   Using warm reset will be much faster especially on big memory
   systems because the BIOS will not go through the memory check.
   Disadvantage is that not all hardware will be completely reinitialized
   on reboot so there may be boot problems on some systems.

   reboot=force

   Don't stop other CPUs on reboot. This can make reboot more reliable
   in some cases.

``` 

Kind regards

Yes, I am indeed interested :D

---

### Post by matt_symes on 2015-11-30
Hi

> **2guntom said:**
> Yes, I am indeed interested :D

Firstly, this may not be the reason it's hanging at reboot. 

It may be a driver such as wireless that's causing it to hang so this is just one avenue to explore. I think this may be unlikely however as it shuts down correctly so this is worth a first investigation.

If it does not fix the reboot issue we can look at what else it may be.

Open a terminal and *copy and paste* this into it. Don't type it but copy and paste as case is important and this is an important file.

```
sudo sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"/GRUB_CMDLINE_LINUX_DEFAULT="quiet splash reboot=t"/' /etc/default/grub
```

Enter your password when prompted. It will not be echoed to the screen. This is normal.

It'll add the parameter reboot=t to the command line. This will attempt a reboot by triple faulting and is a good place to start.

Then type

```
sudo update-grub
```

then, after the above command has finished, reboot your PC and post back on efficacy.

Kind regards

---

### Post by Sweet_Baby_Jamie on 2015-11-30
Please forgive me if this sounds insolent, I really don't mean it to sound so.... but if he can't *boot* the computer to begin with, how can he open a terminal?  Do you mean for him to do it in a Live session from his bootable medium?

---

### Post by matt_symes on 2015-11-30
Hi

> **Sweet_Baby_Jamie said:**
> Please forgive me if this sounds insolent, I really don't mean it to sound so.... but if he can't *boot* the computer to begin with, how can he open a terminal?  Do you mean for him to do it in a Live session from his bootable medium?

I think you may have misread post #1 - or maybe i have.

> Everything is up-to-date and runs fine. **It starts fine**. It shuts down fine. But, like the title says, **it won't restart**.

It's not restarting. 

> I have to hold the power button to power it down.

It's hanging when 2guntom reboots the PC. That's how i read it anyway.

If 2guntom's issue is what i think it is then I've seen this issue before. 

Whether the fix is the same is another question.

If i have misunderstood 2guntom's post #1 then 2guntom will correct me.

Clarification:

This is how i read post #1.

2guntom clicks the option to reboot the PC.

The PC displays the plymouth shutdown screen (swirling icon). It's hanging here and 2guntom has to hit the power button to switch it off.

The PC *should* black screen and reboot, show the plymouth startup screen (swirling icon) and then display the lightdm screen (login screen). It's not doing these steps.

Kind regards

---

### Post by 2guntom on 2015-11-30
> **Sweet_Baby_Jamie said:**
> Is this a fresh install or an upgrade to 14.04?  It matters because previous versions used a different setup for start up, screensaver (lightlocker instead of xscreensaver), and other stuff.  

If you still have the Live DVD, boot from it and remove xscreensaver from your existing install if it's in there.

Oh, I missed the bit about xscreensaver... I checked- it's not there.

---

### Post by 2guntom on 2015-11-30
> **matt_symes said:**
> Hi



I think you may have misread post #1 - or maybe i have.



It's not restarting. 



It's hanging when 2guntom reboots the PC. That's how i read it anyway.

If 2guntom's issue is what i think it is then I've seen this issue before. 

Whether the fix is the same is another question.

If i have misunderstood 2guntom's post #1 then 2guntom will correct me.

Clarification:

This is how i read post #1.

2guntom clicks the option to reboot the PC.

The PC displays the plymouth shutdown screen (swirling icon). It's hanging here and 2guntom has to hit the power button to switch it off.

The PC *should* black screen and reboot, show the plymouth startup screen (swirling icon) and then display the lightdm screen (login screen). It's not doing these steps.

Kind regards

Yes, you are correct.

I started the pc without the wifi adaper. I attempted restart and got the same results.
I started the pc without the printer attached (for the sake of being thorough) and got the same results.
I copy/pasted the command lines that you offered, I attempted restart and got the same frozen screen.

 - -

---

### Post by Sweet_Baby_Jamie on 2015-11-30
Oh thanks for clarifying it, sorry I misread it.  :D

---

### Post by matt_symes on 2015-11-30
Hi

As you have an older computer, let's try rebooting using the PCI register.

Open a terminal and copy and paste this into it.

```
sudo sed -i 's/reboot=t/reboot=p/' /etc/default/grub
```

Then type 

```
sudo update-grub
```

Then reboot. Does it work this time ?

reboot=p

---

### Post by 2guntom on 2015-11-30
Ah! It WORKS! Or, should I say it restarts :)

Question: I've copy pasted the original rebooting menu/list you posted and am looking at the last command prompt copy/paste you offered... reboot=t, t being "tripple", but what is the "p"?

---

### Post by matt_symes on 2015-12-01
Hi

> **2guntom said:**
> Ah! It WORKS! Or, should I say it restarts :)

Question: I've copy pasted the original rebooting menu/list you posted and am looking at the last command prompt copy/paste you offered... reboot=t, t being "tripple", but what is the "p"?

The (reboot=p) PCI reboot is not in the kernel source Documentation directory (that was where i got the text from that i referenced in a post #3), but i only ever use the kernel source documentation as a place to start research as the kernel documentation is sometimes out of date and incomplete. 

Anyway, to answer your question: from here:

[https://wiki.ubuntu.com/BIOSandUbuntu](https://wiki.ubuntu.com/BIOSandUbuntu)

> By forcing a Intel PCI reset by writing 0x2 and then 0x04 to port 0xCF9 (reboot=p) 

You can also look at the kernel source code to get an up to date and complete understanding of what the kernel is doing; if you understand the c programming language.

I'm glad it's working now and, if you're happy, i'll mark this thread as SOLVED for you.

Kind regards

---

### Post by 2guntom on 2015-12-01
Thank you again! Yes, mark it SOLVED! (and happily so :) )

Peace and good tidings to you and yours for the holidays :D

---

