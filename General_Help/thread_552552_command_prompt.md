---
title: "command prompt"
date: 2007-09-16
forum: General Help
---

### Post by Solitus3989 on 2007-09-16
i am currently dual partitioned with windows XP and ubuntu feisty fawn.

my graphics card recently stopped working, i am borrowing one. Since windows drivers are retarded, it thinks it's not installed and doesn't work, even though it's working to full capacity. but since windows doesn't recognize it, ubuntu won't load. 

how do i get to a command prompt when i start ubuntu? from there, i think 'xforcevesa' command should work?

---

### Post by Rozenrot on 2007-09-16
CRISIS AVERTED! 

Once again, you guys are my heroes and have saved the day! :D

Compiz Isn't working now.  But I think that's for me to figure out.

---

### Post by Solitus3989 on 2007-09-16
bump?

---

### Post by splintercellguy on 2007-09-16
To reach the terminal as root, just boot in Recovery Mode. And I'm not sure what XP has to do with Ubuntu.

---

### Post by Solitus3989 on 2007-09-16
when i boot in recovery mode, i think it freezes. because i tried that but never got to a prompt

it just stops on a line that looks like this

____________________
------------------------------

then nothing happens when i type

---

### Post by altonbr on 2007-09-16
Does hitting "Ctrl + Alt + F2" or "Ctrl + Alt + F3", etc. (can be between F1-F7), bring up a prompt that allows you to type?

Should look something like this:
> user@computer-name:/root#

---

### Post by lisati on 2007-09-16
> **splintercellguy said:**
> To reach the terminal as root, just boot in Recovery Mode. And I'm not sure what XP has to do with Ubuntu.

I doubt that Windows "retarded" drivers would prevent Ubutnu coming up, unless it's being run as a virtual machine.

---

### Post by Solitus3989 on 2007-09-16
well windows doesn't recognize the driver, either. there is an exclamation point next to video driver in the device manager, even though the card is working just fine.

---

### Post by lisati on 2007-09-16
IMO the Windows exclamation mark indicator shouldn't make a difference to Ubuntu when you're using a dual-boot.

---

### Post by Solitus3989 on 2007-09-16
alright i tried Ctrl+alt+Fkey

same problem when i tried to boot in recovery mode

there are tons of things flying past, then it just stops... the last line is

[    13.669609] ===============

---

### Post by Solitus3989 on 2007-09-16
bump with redescription.

when i tried to load ubuntu, the loading screen comes on that says ubuntu and has the orange loading bar.

when it gets three notches in, it quits working. just locks up.

i tried starting in recovery mode, and the last line is 
[ 13.669609] ===============
but i never get a command prompt.

i tried booting and pressing ctrl+alt+f2

and the same thing happens. it moves quickly then ends with 
[ 13.669609] ===============

---

### Post by altonbr on 2007-09-16
How are you talking to us? Another computer?

Can you list any and all of your hardware?

There are plenty of tools in Linux to do this for you, but if you can't boot Linux, I can't help you there.

---

### Post by Solitus3989 on 2007-09-16
no i am dual partitioned: linux and XP. 

windows XP boots just fine so im there posting and then restarting and trying to fix the problem.

what do you all want to know? 

i have a theory, though. my normal videocard broke, so im borrowing one and i havn't been able to get linux to boot since i got the videocard. the lender is a radeon9250.

---

### Post by Solitus3989 on 2007-09-16
any ideas altonbr?

---

### Post by altonbr on 2007-09-16
What about a liveCD, can it boot?

If so, type in the terminal (Applications > Accessories > Terminal)

```
lshw -html > lshw.html
```

Then post it here.

Actually, if you can boot to a liveCD, then that's good because we know it's simply a configuration file that we need to change.

---

### Post by bigboy_pdb on 2007-09-16
Solitus3989, it is very highly unlikely that your Windows installation is affecting your Ubuntu installation. Ubuntu is expecting you to be using your original video card, but you changed it and that is what is causing your problems (Ubuntu cannot communicate with the card because it thinks that another card is being used). I agree with altonbr that you should attempt to boot using the Live CD to check if Ubuntu can recognize the new graphics card when there is no assumption that a certain card is being used.

Regarding what you were saying about the exclamation point appearing near the device in Windows. I'm guessing that Windows might be recognizing that the card is a graphics card, but it doesn't have the correct drivers so it's using generic drivers. You should go to ATI's website, download the drivers for the card, and install them. You can get them here (by selecting your version of Windows, Radeon, Radeon 9250 Series):
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by Solitus3989 on 2007-09-17
i definitely already installed the correct drivers for the radeon 9250. my new video card is in the mail, but i don't know if im going to run into the same problems. 

and where do i get a liveCD?

---

### Post by altonbr on 2007-09-17
> **Solitus3989 said:**
> i definitely already installed the correct drivers for the radeon 9250. my new video card is in the mail, but i don't know if im going to run into the same problems. 

and where do i get a liveCD?

Try here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Burn it to a CD, leave it in your disc tray and reboot. Then you should be presented with a screen asking if you want to Install or Try Ubuntu. Hit enter. It then boots up a fully functional Ubuntu from CD but please don't complain about its speed: it's running off a CD and not your Hard Drive, so it will be 10x slower.

However, if it does boot up, then we know there's something wrong with your current Ubuntu install.

---

### Post by Solitus3989 on 2007-09-17
im downloading right now. 5 hour download.

ill message you when i get the iso burned.

---

### Post by altonbr on 2007-09-18
As I said in the PM, try booting with:

```
acpi=off
```

In the kernel boot options. Tell me how that goes.

---

