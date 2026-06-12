---
title: "no suitable mode found - login loop"
date: 2013-08-18
forum: General Help
---

### Post by Sarai the Geek on 2013-08-18
Hello-
I have an old-ish Pangolin Performance 5 from System 76. Around the middle of last semester (so, maybe two months ago) I decided to go back to Ubuntu from Arch Linux. However, the installer failed during installation, wiping my hard drive in the process. After that I could not get it to even boot from CD. Since I was caught up in midterms I took it to a computer shop where I used to work as they know some about linux. He ended up being able to install 12.04 from a thumb drive after much blood, sweat, and tears.

When I brought it back home, it booted and ran fine except this error message on boot:

```
error: no suitable mode found
error: no video mode activated
```

I did some cursory searching at the time and tried some of the fixes but none of them worked. Since the computer still booted past the error, I decided not to worry about it.

Fast forward to now- the computer still boots past the error but once I enter my password to log in, the error flashes back on the screen and then it sends me back to the login screen. I thought maybe something got screwed up with my password but when I enter any other password it just gives me a password incorrect error- so it's not the password. When I tried to get into a console from the login screen, it just hangs with that same error message.

Normally when booting I do not see the grub boot screen but pressing enter at the right time got it and I tried to boot into recovery mode. The error I got was (I am paraphrasing, it's not right in front of me):

```
error: no suitable mode found
booting anyway, however

```
And then it hangs. I left it overnight and found it on the same screen the next morning.

This is really perfunctory for me as I suspect I cannot fix this and will have to replace the computer, however I am asking here just in case. The computer will not boot to a live environment from CD or usb, I cannot get into console, and I cannot boot into recovery mode. Even if this error was easy to fix, I can see no way to get to a place where I CAN fix it. I have checked the BIOS and it is set up to boot automatically from CD when one is in the drive.

At the computer shop, they ran diagnostics on the hardware and said there were no errors. However, I think there is a hardware problem somewhere, maybe the motherboard. I am on summer break right now and I am afraid even if I do manage to get it working again, it will just be propped up with more duct table and willpower and fail again permanently right in the middle of my next semester. What do you guys think?

---

### Post by GwL3eNC on 2013-08-18
Hello Sarai the Geek,

I guess something but up to now i'm not familiar with it. Therefore 

@ the other guys

> **The computer will not boot to a live environment from CD or usb, I cannot boot into recovery mode. I have checked the BIOS and it is set up to boot automatically from CD when one is in the drive.**

Is it possibly something with UEFI (secure boot etc.)?

Whish you luck Sarai!

---

### Post by Yellow Pasque on 2013-08-18
I would try going to the terminal (Ctrl+alt+f1) and creating anew user: [https://help.ubuntu.com/community/AddUsersHowto#Command-line](https://help.ubuntu.com/community/AddUsersHowto#Command-line)
Then, go back to login (ctrl+a;t+f7) and try logging in as new user.

BIOS update may help too: [http://knowledge76.com/index.php/PanP4/PanP5](http://knowledge76.com/index.php/PanP4/PanP5)

---

### Post by Sarai the Geek on 2013-08-19
> **Temüjin said:**
> I would try going to the terminal (Ctrl+alt+f1) and creating anew user: [https://help.ubuntu.com/community/AddUsersHowto#Command-line](https://help.ubuntu.com/community/AddUsersHowto#Command-line)
Then, go back to login (ctrl+a;t+f7) and try logging in as new user.

BIOS update may help too: [http://knowledge76.com/index.php/PanP4/PanP5](http://knowledge76.com/index.php/PanP4/PanP5)

When I try to go to the terminal using that key combination, it simply hangs on the no suitable mode error.

As for the bios- I will go download that .iso and give it a try but I don't think it will work because my computer won't boot to CD.

> **GwL3eNC said:**
> Hello Sarai the Geek,

I guess something but up to now i'm not familiar with it. Therefore 

@ the other guys



Is it possibly something with UEFI (secure boot etc.)?

Whish you luck Sarai!

UEFI seems like an unlikely problem since the computer is fairly old and I never had problems before booting or installing. I thought this whole secure boot thing was a Windows 8 problem, but my computer came with Ubuntu installed and when it was made, Windows 7 hadn't yet come out.

---

### Post by steeldriver on 2013-08-19
It sounds to me like you have 2 different issues

[LIST=1]
[*]your primary user's X session (GUI login) can't start for some reason - often this is because of an ownership problem either of the $HOME dir or the .Xauthority file within it, or something in your .profile or .bashrc file, but in rarer case can be because the home partition (or root partition, if there is no separate home) is full 
[*]your grub video mode and console (virtual terminal) mode are unsupported by your card and/or screen 
[/LIST]
 Unfortunately the usual fix for (1) is to switch to a virtual terminal or boot into recovery mode and edit / delete the appropriate files from there - which you can't do because of (2). And the solution to (2) is usually to boot from a live CD or USB and chroot to fix the grub.cfg, which apparently you can't do either.

The only *other* workaround I can think of is to try ssh'ing in - if you already have an ssh server running and another machine on the LAN you could try that; if you don't you *may* be able to install one by 'typing blind' in the apparently dead virtual terminal e.g. Ctrl-Alt-F2 (let's start with a 'fresh' one, in case you have typed stuff in Ctrl-Alt-F1 already) then

```

<username><ENTER>
<password><ENTER>
sudo apt-get install -y openssh-server<ENTER>

```

just wait a bit for it to run, and then try to ssh in

---

### Post by Sarai the Geek on 2013-08-19
Ok- I opened a new virtual console and tried to install open ssh server- heaven only knows if it actually worked.

I am on a mac mini connected to the same large intranet (though the mac is on wifi and my laptop is on wired because I only have one ethernet jack in my office). It seems to me that I ought to be able to at least contact my laptop by pinging its hostname, however it says destination unreachable. I don't have any sort of experience with ssh, unfortunately. I have read a bit about setting up ssh and it seems like some configuration is necessary which I am not sure how to do "blind".
Do you have any hints?

---

### Post by steeldriver on 2013-08-19
No configuration should be necessary unless your LAN or host firewall blocks the standard ssh port (22) - however if you can't ping it then probably you won't be able to connect via ssh either

What kind of network is it? are you in a corporate environment or is it a home LAN / router?

---

### Post by Sarai the Geek on 2013-08-20
It's a poorly set up and maintained corporate network. Half the time the internet doesn't work at all- the company is not quite big enough to be able to retain their own IT staff so they rely on whichever poor schmuck the cable company sends out to try and fix it.
It's a family run business and my father seems to have taken the router passwords to his grave so it's a free for all. I doubt there's a firewall of any kind, but I don't necessarily think it's robust enough or even properly configured to do anything like ssh, unfortunately.

---

### Post by steeldriver on 2013-08-20
Well depending how much effort you want to put into this, if the Mac is on the same LAN segment you could maybe install nmap on it and then do a port 22 scan and see if you could identify your Ubuntu box by IP, e.g.

```
sudo nmap -p22 192.168.1.0/24
```

(replacing the 192.168.1.0/24 as appropriate based on the IP address / netmask reported by the Mac)

You could then try to ssh in using that LAN IP

---

### Post by Sarai the Geek on 2013-08-20
I would be willing to put that kind of effort into fixing it if it didn't have other problems, namely the issue of not booting into a live environment.
I sucked it up and ordered a new computer- I loved this computer but I got out of IT precisely because I don't have the patience for this. I think the hard drive and probably some other parts are still good, so I am sending it back to System 76 and they donate it to a charity to build computers for impoverished people. 
I appreciate your time very much, thank you!! :)

---

