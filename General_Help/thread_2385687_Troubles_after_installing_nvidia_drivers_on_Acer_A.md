---
title: "Troubles after installing nvidia drivers on Acer Aspire 7 A715-71G-76Z5 UEFI"
date: 2018-02-23
forum: General Help
---

### Post by koene2 on 2018-02-23
Hi All,

I'm having some troubles booting up gnome after installing nvidia drivers on ubuntu gnome with Linux 4.13.0-32-generic.
What I did was install grub and gnome next to windows which was working after a lot of tinkering with allowed boot and boot order in the bios. This was stable as I was able to use this setup for a few days.

Everything was running fine untill I tried to update nvidia drivers and now I can no longer boot up gnome (I may have also turned on and off secureboot). When I choose ubuntu gnome from the grub menu, I end up in this terminal view which flickers:
[https://i.imgur.com/X238in7.jpg](https://i.imgur.com/X238in7.jpg)

I've tried installing several nvidia drivers via root shell prompt using system recovery but none seem to fix the issue.
My current drivers: [https://i.imgur.com/pUfLF39.jpg](https://i.imgur.com/pUfLF39.jpg)
The screen I end up on when I try to boot gnome: [https://i.imgur.com/X238in7.jpg](https://i.imgur.com/X238in7.jpg)

Is there someone who can help me get gnome working again?

---

### Post by Bashing-om on 2018-02-23
koene2; Hello - Welcome to the forum :)

Let's see what we can do .
At that login_ prompt as shown from your image posting, what results when you enter your username at that prompt ?
follow the username entry with entering your password . There will be no response when the pass word is entered,  enter the password blindly and hit the enter key .

Once logged in execute terminal commands :
```

sudo lshw -C display
dpkg -l | grep -i nvidia 

```
and post back the outputs.
With "sudo" - SUper_user DO - you will be asked for the password . same as above; enter the password and hit enter blindly .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

I have confirmed that the 390 version driver is appropriate for your card . Maybe we have a driver conflict ?


[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by koene2 on 2018-02-23
Hi Bashing-om):P,
I can't login in that screen because it flickers and I have to press a key several times before it's oke. For the username it's oké, but password is impossible.
When I do it in the root shell this is the output:
[https://i.imgur.com/YFAR9bq.jpg](https://i.imgur.com/YFAR9bq.jpg)

---

### Post by Bashing-om on 2018-02-23
koene2; Surprise, surprise :

That says that the issue is with the Intel graphic's set . No driver for Intel loaded.
As the data from nvidia passes through the on-die Intel chip. we must have Intel operational. 

Upfront. I am not to conversant with Intel graphic's. I have seen conflicting documentation and I do not have an Intel box to test with.
But, we can poke at it and see what we can learn.

what shows:
```

lsb_release -a

```
be aware that 17.10 with wayland does not play nice -  yet - with nvidia.
Intel: what have we installed ?
```
 
lspci -k | grep -EA2 'VGA|3D'
dpkg -l | grep xserver-xorg-video-intel
dpkg -l | grep xserver-xorg-core

```

again, see what we can do.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by koene2 on 2018-02-23
Ha! getting a bit closer than.
Here is the output:
[https://i.imgur.com/C4lbG3Q.jpg](https://i.imgur.com/C4lbG3Q.jpg)

---

### Post by Bashing-om on 2018-02-23
koene2; Well !

Looks like we need to re-install the Intel graphic's driver.

Confirm what we are indeed working with :
```

dpkg -l | grep linux-

```

By the way .. you are not updated .. as the latest point release for 16.04 ( .4) is out now . 
Maybe we need to deal with that soonest after getting Intel functionable ?

[INDENT][INDENT]progress made :)
[/INDENT][/INDENT]

---

### Post by koene2 on 2018-02-23
Hi bashing-om. What is the best way to update to 16.04.4? I'll post the output of the dpkg command tomorrow morning

---

### Post by Bashing-om on 2018-02-23
koene2; Well, update -

If/when the system is in a consistent state, then:
```

sudo apt update
sudo apt upgrade

```
"should" do that trick  to bring you up to 16.04.(4)  


[INDENT]all in the process
[/INDENT].

---

### Post by koene2 on 2018-02-24
Good morning,
seems like the update went ok, see [https://i.imgur.com/YOFASbd.jpg](https://i.imgur.com/YOFASbd.jpg)
Now what would be the best next step?

---

### Post by koene2 on 2018-02-24
Aftter install intel video drivers ([COLOR=#111111][FONT=Consolas]sudo apt-get install --reinstall xserver-xorg-video-intel xserver-xorg-core), I tried to boot in secure graphic mode but got the following error :/ 

[/FONT][/COLOR]https://i.imgur.com/nta3iRW.jpg

edit1:
Update: I tried nvidia-xconfig which failed because I didn't had access to etc/x11/ so I tried this which worked ([https://ubuntuforums.org/archive/index.php/t-1691572.html](https://ubuntuforums.org/archive/index.php/t-1691572.html)).
Now I was able to enter my username and password (not via secure startup).

edit2: 
new logging output:[https://i.imgur.com/kDHwtZr.jpg](https://i.imgur.com/kDHwtZr.jpg)

---

### Post by Bashing-om on 2018-02-24
koene2; Hummmm ...

Acer == vendor lock in ??

with :
[http://ubuntuforums.org/showthread.php?t=2330267](http://ubuntuforums.org/showthread.php?t=2330267) <-  set "trust" on the Ubuntu/grub .efi files on Acer .

in mind, what do you now boot too ?

[INDENT][INDENT]look'n like still driver issues .
[/INDENT][/INDENT]

---

### Post by koene2 on 2018-02-25
> **Bashing-om said:**
> koene2; Hummmm ...

Acer == vendor lock in ??

with :
[http://ubuntuforums.org/showthread.php?t=2330267](http://ubuntuforums.org/showthread.php?t=2330267) <-  set "trust" on the Ubuntu/grub .efi files on Acer .

in mind, what do you now boot too ?
[INDENT][INDENT]look'n like still driver issues .
[/INDENT]
[/INDENT]

I already had to trust it in order to install gnome. Let me try that again because I noticed uefi sometimes resets boot order (so it may also reset rust).

---

### Post by koene2 on 2018-02-25
I gave up and reinstalled gnome. Everything is oke now except I don't have any good drivers for nvidia. My tactics for updating nvidia drivers next time is to work with backups which I can restore from the root terminal (I hope this also backs up kernel stuff etc). Is the backup program in gnome sufficient for this?

edit: default installed drivers [https://i.imgur.com/EF7qOyg.png](https://i.imgur.com/EF7qOyg.png) (which don't work with my d6000 docking station :/)

---

### Post by koene2 on 2018-02-25
On second thought it might have been the displaylink drivers that have caused all this. I just updated succesfully to an nvidia driver. Only after install displaylink drivers I get system errors (still boots for the moment)

---

