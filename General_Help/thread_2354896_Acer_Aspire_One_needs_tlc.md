---
title: "Acer Aspire One needs tlc"
date: 2017-03-07
forum: General Help
---

### Post by Philip_Edwards on 2017-03-07
Hi, I've an aging Acer Aspire One netbook. It has been running Lubuntu for a while now. It doesn't want to upgrade its software from 15.10 to 16.04.1

It tells me "Failed to download repository information"

Anny suggestions?

Phil

---

### Post by RobGoss on 2017-03-07
I would recommend doing a fresh installation of 16.04 to avoid further issues, start with the live desktop and see how it runs if all goes well start your installation. Make sure you have your current OS backed up

---

### Post by Philip_Edwards on 2017-03-08
Indeed, I would love to do that. At the moment, I can't get the machine to run USB before it starts to load my old Ubuntu installation. So, it won't load a new operating system. Also, it doesn't want to upgrade on-line.

Yours,
Frustrated of Wales.

---

### Post by RobGoss on 2017-03-08
Can you access the BIOS and change the boot order and maybe you'll be able to set the USB as first boot

Netbooks maybe a little different then a Laptop, I have a HP mini and in order for me to boot from a USB I have to tap F-9

I also think if you change the Download source, it may fix your issue you have now. Go to Software & Updates, choose other and you should see other download sources to choose from

---

### Post by Philip_Edwards on 2017-03-09
OK, so this is what happens.

On startup, I get two options.

Press f12 to alter the boot order. I get this screen.

[IMG]https://content-eu.drive.amazonaws.com/cdproxy/templink/EGJSj_6Z-7rtvVP1gEBcmc4HqhYgBD3d_bn3szaTmaopX92IB?viewBox=1266[/IMG]

Notice, there is no USB option. Maybe there should be. I've tried all three USB ports.

I also get the option at F2 to go to setup.
One of the options here is BOOY.

I've changed the boot order here so that it looks like this.

[IMG]https://content-eu.drive.amazonaws.com/cdproxy/templink/t6Zq0_ujXAXoR0SJQRupkcy1cHSy49i_2Cs3kr7SPtYpX92IB?viewBox=1266[/IMG]

Still, when I try to startup with a USB drive in the USB slot, it just freezes at startup.

So.......I can't load in a new distro from a pen drive. Also.......and this is another issue......I can't get the computer to update.

I've a feeling that my problem lies with the fact that I don't get a USB option in my F12 screen.

You know, I used to feel somewhat confident about my Linux abilities but over the last few days I feel totally helpless.

Thanks for your help....Phil

---

### Post by RobGoss on 2017-03-09
You do have Lubuntu running on this machine correct?

Have you tried installing the ISO for 16.04 using a DVD?

Some older machines will not recognize a USB stick and in most cases will only boot from a DVD

---

### Post by RobGoss on 2017-03-09
>  You know, I used to feel somewhat confident about my Linux abilities but over the last few days I feel totally helpless. 

Sometimes we run in to problem like this and it may require a bit more trouble shooting, on older machine it may be a bit harder to fix, this may be the case I'm sure someone else may have other ideas how to get pass this issue

---

### Post by Philip_Edwards on 2017-03-09
Hi Rob, and thanks for sticking with me.

[COLOR=#000000]You do have Lubuntu running on this machine correct? Yes.......version 15 ish. It has been running perfectly for years but recently reported that it wouldn't upgrade any more and I'd need to get version 16.[/COLOR]

[COLOR=#000000]Have you tried installing the ISO for 16.04 No.......I have a DVD drive but it is for a Mac......but I've a feeling that is what I should try next?[/COLOR]

[COLOR=#000000]Some older machines will not recognize a USB stick and in most cases will only boot from a DVD. In the past, I did manage to get Linux distros to boot from USB.

I'm pretty sure that I owe you a beer by now.
Thanks,
Phil[/COLOR]

---

### Post by Philip_Edwards on 2017-03-09
Just tried plugging my Mac DVD drive into the Acer Aspire.
Nothing.

Phil

---

### Post by RobGoss on 2017-03-09
Is this Mac DVD drive an external one?
When you say nothing what exactly do you mean, the machine does not recognize the drive

**15.10** does not have any support and I'm sure this may be part of the problem moving to a supported version would be the best move


How did you install **15.10 **on this machine?

---

### Post by Philip_Edwards on 2017-03-09
Ssssshhhhh Rob..........It appears to be updating to version 16.04. I'll try not to stare at it.

---

### Post by RobGoss on 2017-03-09
Let me know how it goes =d>

---

### Post by Philip_Edwards on 2017-03-09
Well, it was doing the upgrade thing when I went out at 7:30 p.m. Just arrived home at 11.20 p.m. and it is still upgrading. It hasn't stopped though. Maybe it will be ready by breakfast time?

---

### Post by Philip_Edwards on 2017-03-10
9:40. It is about two thirds of the way through 'Clearing Up'

---

### Post by Philip_Edwards on 2017-03-10
10.09 a.m.
All finished. Restarted and everything appears to be working.
Big Thanks  :O)
Phil

---

### Post by Topsiho on 2017-03-10
I am confused: I possess an Acer Aspire One myself, and am not able to find any DVD or CDROM drive in it.
I've never had any trouble booting from a **bootable** USB-stick, when installing a new version of Ubuntu.


So what I think is that for some reason the USB-stick you boot from is not bootable.

Topsiho

Edit: sentence deleted which was incorrect. Sorry for this

---

### Post by RobGoss on 2017-03-10
How long did it take to upgrade I'm surprise it took so long maybe it had something to do with your connection as far as upgrading speed is concerned

---

### Post by Topsiho on 2017-03-10
It might also be due to the very little SSD (8GB) the (my) AA1 has. And the 1GB memory. It installs quite well from a USB-stick, but upgrading I never tried, that's quite another cup of tea.

Topsiho

---

### Post by Philip_Edwards on 2017-03-10
Solved

---

