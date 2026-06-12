---
title: "Login prompt overwrite"
date: 2022-01-19
forum: General Help
---

### Post by steinrr on 2022-01-19
Running Ubuntu 16.04 without GUI - just command line.

After upgrading from 14.04 I have this strange issue, where the login prompt (after boot) sometimes are overwritten with what I type.

Example - the login prompt might show:

[FONT=Courier New]MyServer username:
[/FONT]

When I start writing, the text will not appear behind "[FONT=Courier New]username:[/FONT]", but will actually overwrite the text "[FONT=Courier New]MyServer...[/FONT]". 
It still gets the correct input, but it looks very confusing.

Any ideas? Is this a common issue? Tried Googling, but did not find anything relevant.

---

### Post by guiverc on 2022-01-19
Ubuntu 16.04 LTS has reached the end of it's *standard* support life  (*community support is over*).  *You don't mention trying to move to a supported release either.*

See [https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/](https://fridge.ubuntu.com/2021/03/13/extended-security-maintenance-for-ubuntu-16-04-xenial-xerus-begins-april-30-2021/)

Ubuntu 16.04 ESM support is available, see also [https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm](https://ubuntu.com/blog/ubuntu-16-04-lts-transitions-to-extended-security-maintenance-esm)

---

### Post by steinrr on 2022-01-19
Yes, I see that it is out of support, but somebody might know about this anyway? There might be a simple reason/solution to it. 

(The server is used on a LAN (not on Internet) as a Minecraft server for a youth club, so it is not critical to be on latest version)

---

### Post by yetimon_64 on 2022-01-19
I use a console only boot and have been doing so since 14.04, I have noticed since 16.04 strange prompt effects after a fresh boot or on restarting the system. When it happens for me I usually delete what I've typed (by backspacing) then hit the enter button to get a fresh prompt and continue from there. I usually only have to do it the once on any console. It is a minor issue here only and I've learnt to bypass it and continue. By console only boot I mean by default I boot to a text screen (console) and manually boot into a desktop (GUI) with a "sudo systemctl" command to start lightdm etc when needed.

Mostly here the prompt disappears completely as if it has dropped off the left side of the screen and when I keep typing the end of my command sometimes comes onto the screen where the prompt previously was; if the command is complete, even with the prompt gone, hitting enter still has the command work properly and a new prompt appears, it just makes a bit of a visual mess to put up with. I am currently on Xubuntu 20.04 and still occasionally have it happen, no idea why though; I've gotten used to working around it.

I have no fix for it, and really haven't looked for one. It doesn't always happen here and when it does it seems to only be after a restart or on opening a new console. But once the console is open for a while I don't remember ever seeing it. I got used to working around it when it happens by clearing anything I've typed then hitting the enter button to get a new prompt which always seems to hold after the first instance of disappearing.

I've noticed these effects on all of my installs since 16.04. Since this started I've seen it on 16.04, 18.04 and now 20.04. I only use LTS releases so I don't know if such happens on the intermediate releases. I've always assumed the problem to be because of the alterations I do to get a permanent console only boot set up and the use of mingetty to have automatic login on the consoles (with a log in pause before opening the console, ie."Press enter to log in."). Though I never had the problem on 14.04.

Regards, yeti.

---

### Post by steinrr on 2022-01-19
Yes, I think this is the same for me - I guess it only happens on a fresh reboot. Did the upgrade yesterday - so have not fully tested it.

I also have console only boot (multi-user.target) - but are not using automatic login.

---

### Post by yetimon_64 on 2022-01-19
> **steinrr said:**
> Yes, I think this is the same for me - I guess it only happens on a fresh reboot. Did the upgrade yesterday - so have not fully tested it...If after a fresh start your prompt is missing just hit the enter key that brings up a fresh/full prompt here. You could also test by just typing a command and see if it works upon hitting enter, even without the prompt or if the prompt is "scrambled".

> **steinrr said:**
> ...I also have console only boot (multi-user.target) - but are not using automatic login.
Probably not a good idea to use auto login where there are many people about (youth club). I am the only one who has access to this laptop, though I do accept it is a bit of a risk should anyone else get access to this machine.

---

