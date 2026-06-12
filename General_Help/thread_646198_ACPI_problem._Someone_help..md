---
title: "ACPI problem. Someone help."
date: 2007-12-20
forum: General Help
---

### Post by BnetTheAwesome on 2007-12-20
Ok, I'm having ACPI problems. I'm a noob so bear with me. I get an error:

ACPI SCI Allocation Failed

ACPI unable to start interpreter

Someone please help. It won't boot.

---

### Post by BnetTheAwesome on 2007-12-20
UPDATE!

acpi=off works when appended in the kernal thing but doesn't permanently solve the problem.

What should I do?

---

### Post by teryowen on 2007-12-20
i know i had to do acpi=forced

not sure what the problem is

---

### Post by BnetTheAwesome on 2007-12-20
I should append acpi=forced in /boot/grub/menu.lst under #defoptions=quiet splash? Is that what you're suggesting I do?

---

### Post by BnetTheAwesome on 2007-12-21
Anyone? Can anyone help?

---

### Post by teryowen on 2007-12-21
ya try it out, it worked for me, im not really sure, the problem for me it was saying something about an old BIOS... dont remember it was a while back.

---

### Post by BnetTheAwesome on 2007-12-21
did not do anything at all. Anyone got any other suggestions?

---

### Post by BnetTheAwesome on 2007-12-21
Does anyone have any ideas?

---

### Post by plucky on 2007-12-21
Shouldn't that be **acpi=force** not [color=red]acpi=forced[/color]

I googled your error and found that there might be a **BIOS** setting that might work for you.
Something to do with the **ACPI HPET** setting,but as my system doesn't support it I don't know what it does. Maybe you can check it out but be careful not to screw up your BIOS.

Hope this helps

---

### Post by BnetTheAwesome on 2007-12-21
I'm running a laptop so BIOS is limited.

I'll try acpi=force

---

### Post by BnetTheAwesome on 2007-12-21
Anyone? Any ideas?

---

### Post by DeathOnJuice on 2007-12-21
I thought you said off, not forced, works. Try that in the same place.

---

### Post by BnetTheAwesome on 2007-12-21
They both do the same. My computer runs slower if acpi is off. I tried appending this to my #defoptions in /boot/grub/menu.lst but it wouldn't work.

---

### Post by BnetTheAwesome on 2007-12-21
I can post my /boot/grub/menu.lst if someone needs to see it.

---

### Post by BnetTheAwesome on 2007-12-21
Can someone help? My thread keeps getting ignored.

---

### Post by Slade Winstone on 2008-01-04
I've had all sorts of problems with acpi and the latest kernel.  I've had to append acpi=off to my grub options to get my laptop to boot. 

I just added the text acpi=off to the kernel line and saved menu.lst ;)  However, this is probably not the correct way to update grub.   I believe that you should use update-grub instead.

Check the man page for update-grub which should help you generate the menu.lst you need.

Slade.

---

### Post by Slade Winstone on 2008-01-05
Hi, 

I have a quick update:

2.6.22.14 Kernel set nosmp noapic

UPDATE I have now found kernel boot parameters that will allow ACPI to run. Instead of setting acpi=off to disable all ACPI (which previously was the only way of booting my A8M), I now use nosmp and noapic which allows some ACPI functionality and a good boot

Add to the end of defoptions and the end of the current kernel in /boot/grub/menu.lst

nosmp noapic

Best of luck,
Slade.

---

