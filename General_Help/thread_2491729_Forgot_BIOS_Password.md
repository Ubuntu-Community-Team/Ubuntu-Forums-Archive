---
title: "Forgot BIOS Password"
date: 2023-10-19
forum: General Help
---

### Post by dippieffe on 2023-10-19
[COLOR=#000000][FONT=&quot]Hello, forgive me if this question has been already raised by other users, I made a search on the forum but it was hard to find it.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]I have an old HP EliteBook 755 with Ubuntu 20.04 LTS on it and as the title says I forgot the BIOS password so I can't change its boot sequence to install a new OS from a bootable USB drive. in case something goes wrong and I need a fresh installation. I tried to fix this by using Grub-Customizer but being such a dumb user I really don't know how to configure it.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Any idea on how I can overcome this issue?[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Thank you in advance for all you valuable answers.[/FONT][/COLOR]

---

### Post by Rubi1200 on 2023-10-19
Hi and welcome to the forums :-)

Try this:
HP Elitebook: PASS123

Apparently there are default backdoor passwords to access BIOS. Never tried it, so do so at your own risk.

---

### Post by QIII on 2023-10-19
You may need to consult the machine's documentation or contact the manufacturer for a solution.  The BIOS/EFI settings on older machines are, in most cases, not available to the OS and, thus, cannot generally be changed from the OS.  A password is not generally something that can be bypassed at that level.

However, some machines can be altered if the manufacturer has provided generic functionality -- but I doubt that the BIOS/EFI password can be changed.  You'd need to old password.

In case it can be modified, there is functionality available in Linux to alter the BIOS by forcing open the hardware system settings on the next startup.  Be aware that this often sets ALL settings back to their defaults, which may mean that you may have to restore any customized settings.  Besides that, you'd just be getting to the system setup you would get to by pressing the key combination at startup as required by the hardware documentation.

[B][I]
AT YOUR OWN RISK:[/I][/B]

You may try

```
sudo systemctl reboot --firmware-setup
```

but you are still likely to need the original password to make changes.

---

### Post by MAFoElffen on 2023-10-19
If you have an Admin BIOS password set in the BIOS, you can clear it by resetting the CMOS. You can do that by disconnection the CMOS battery for about 15-20 seconds... Usually, for a laptop, this means a lot of work, but for yours, it's actually fairly easy, without a lot of specialty tools: [https://www.youtube.com/watch?v=9tp2NpcuWIU](https://www.youtube.com/watch?v=9tp2NpcuWIU)

---

### Post by ne29914 on 2023-10-19
On HPs, you can normally disconnect the CMOS cell for around a minute while holding the power switch pressed. The main battery has to be removed and power supply disconnected during this operation.
To get to the CMOS cell, you need to remove the keyboard, but that's pretty easy.

But if you're out of luck, you selected "High Security" (or something similar) when you set the BIOS password. In that case, the laptop is FUBAR. That function burns the BIOS password directly into the BIOS ROM. Depends on how paranoid you were back then.

---

### Post by MAFoElffen on 2023-10-20
> **ne29914 said:**
> On HPs, you can normally disconnect the CMOS cell for around a minute while holding the power switch pressed. The main battery has to be removed and power supply disconnected during this operation.
To get to the CMOS cell, you need to remove the keyboard, but that's pretty easy.

But if you're out of luck, you selected "High Security" (or something similar) when you set the BIOS password. In that case, the laptop is FUBAR. That function burns the BIOS password directly into the BIOS ROM. Depends on how paranoid you were back then.
Well... No. That works for th newer HP's. His is older.

Refer to the Video I posted on "his" HP laptop model. 

Summary:
To remove the battery, remove the back cover, which has slide locks to open. Take off the back cover. Same kind of slide locks to remove the battery. The CMOS battery is right there on the upper right of the battery, inside the case... Just disconnect the connector, and let it sit. Reconnect the CMOS connector. Put the battery back in and lock the slides. Put the back cover back on and lock the slides.

---

### Post by ActionParsnip on 2023-10-20
I'd suggest to let it "sit" overnight. You can also hold the power button down (with the power cable disconnected) to drain it more. Then reassemble and power up. You'll get a whinge about the time and date not being set but sort that out and configure the BIOS and you should be golden

---

### Post by yancek on 2023-10-20
Why not just create a proper menuentry in the Ubuntu 20.04 grub.cfg file to boot the iso of the new OS.  If it is a major Linux distribution, you should be able to boot the iso file from Grub and install it to another partition.  Can't give more details without more details from you.  The page at the link below should help.

 [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

---

### Post by ne29914 on 2023-10-20
> **MAFoElffen said:**
> Well... No. That works for th newer HP's. His is older.


I beg to differ. The 755 G2 was introduced in 2014.
My 6910p HPs, on which I base my information (done this a dozen times), are from around 2008. So which are older?

---

### Post by kurt18947 on 2023-10-20
What I would try first would be to download any official maintenance manual you can find. I can't speak to HP, my experience is with Thinkpads. I'm pretty sure those maintenance manuals have a procedure to clear the BIOS password. As an aside, if you can figure out how to clear BIOS passwords on a particular make/model, you can buy machines on Ebay with locked BIOS passwords for a nice discount.

Edit: I was wrong about resetting the BIOS password I think. Lenovo uses a two level system, user and supervisor. Supervisor cannot be reset without knowing the current password, the motherboard must be replaced.

---

### Post by MAFoElffen on 2023-10-21
> **ne29914 said:**
> I beg to differ. The 755 G2 was introduced in 2014.
My 6910p HPs, on which I base my information (done this a dozen times), are from around 2008. So which are older?
That is great that it works on yours. Thank you for sharing that.

Please look at the OP's Post #1...

IDK. I am not confrontational. I am not looking for a fight. I do know some things. I do not know everything. I do enjoy pushing myself to learn new things every day...

Being I was a certified HP, Dell and Lenovo Onsite Warranty Technician with 34 years of professional IT experience. That doesn't make me "right". I usually just go from my experience and the facts, and try to share that...

The OP said "old HP EliteBook 755" without any Generation notation. The first generation (not officially called G1 in the name) of that model came out in 2008. So the same age as yours. Gen2 of that model didn't come out until 2014, as you noted, BUT...

HP BIOS features do not go by the date something came out. They go by the model and generation of that model. I have to look in the HP Partner Portal to see what those included BIOS features are for the Model, Gen and BIOS revision. 

For example, that same model of a later generation (Elitebook G5, circa 2018) included "HP Sure Start", which came out included as a BIOS feature on other models much earlier... That feature, if before you power-up (i.e. from powered-down), you hold down the <Windows>, and <B> keys, then simultaneously press the "Power" button... will start "HP Sure Start", which will attempt to recover a corrupted BIOS image, which that process will also clear the CMOS settings... But his doesn't have that feature. It is assumed that it is what he said it was.

Some HP mobile devices have a pinhole in the back cover, that is above a CMOS clear switch, which his also does not have.

So me? I'm just going off what was given, and what I know. There could be other ways. I never said it was the "only way". But I do know that what I suggested will work. (I also know that the CMOS battery in that Model is not under the keyboard... LOL That would send him on a wild goose chase.)

Right?

---

