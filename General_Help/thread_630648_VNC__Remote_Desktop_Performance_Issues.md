---
title: "VNC / Remote Desktop Performance Issues"
date: 2007-12-03
forum: General Help
---

### Post by Bottesford on 2007-12-03
Posted in newbie chat (as I'm a newbie!) but no reponse so...

I set up my new Ubuntu LAMP server yesterday with relative ease, installed the Gnome desktop but now need to put the server where it'll have no monitor so need vnc (I'm not yet confident enough to rely only on command line + I wanna play around with it a bit). 
I use vnc on my xp server with no problem but on Ubuntu I'm getting very poor performance with window redraws. Message boxes are just transparent when the first come up and only by hunting around can I find the close, etc button. Move a window around makes things worse as you loose the title bar too with all sorts of distortion.
I'm using the Remote Desktop feature and connecting with Ultra VNC from Vista. I'm on a gigabit LAN.

On XP a 'window hook' driver was installed to improve performance but I'm very new to Linux so unsure what to do.

Thanks for any help.

---

### Post by dbott67 on 2007-12-03
I take it both your Vista client and Ubuntu server are on the same Gigabit subnet.  If so, then there is something definitely wrong.

Can you try connecting to the server using your XP computer and see if performance increases?

I've got a multi-system setup at home (Ubuntu 7.10, Windows XP Pro, Vista Ultimate and OSX) and can VNC to/from any computer without any troubles (although, I haven't tried connecting to my Ubuntu box using VNC since upgrading to 7.10 --- I've been using [NoMachine]("http://www.nomachine.com/download-package.php?Prod_Id=4"), which is far faster & secure, although you can't connect to the active desktop).

Are you running compiz-fusion on your Ubuntu server (i.e. fancy graphics & what-not)?  If so, try disabling them.

Another problem I've found is that if I try to connect to my dad's computer (he runs Vista; I'm running Gutsy) and he has the Aero interface enabled, performance is ssssllllooooooowwwww.  Changing Vista to the old "Classic" view improves performance when I'm connecting to him (but I don't think this is your problem).

-Dave

---

### Post by Bottesford on 2007-12-03
Yes everything is on the one subnet - it's just a 4 port gigabit router home network style...
Tried connecting from XP (I have to VNC to XP too so a window inside a window job there...) - same result. To me it looks like Remote Desktop isn't sending out foreground window updates often enough - move them around sometimes gets bits of them back- but you loose others as well.

compiz-fusion - not sure. I've looked under Appearance prefs > Visual Effect and it's set to None if that's what you mean. 

Re Vista & Aero - I always find Aero is disabled as soon as you VNC in to a machine anyway...

---

### Post by TheMightyGirth on 2008-03-18
Did you ever get this fixed?

I have the same problem with my 7.10 laptop.

Tried Ultra and Real VNC on XP SP2 and XP SP3 and all combinations fail to render / redraw correctly. Looks to be specific controls that don't work but I am strugling to work out what exactly.

Thunderbird for example, the tree view on the left works fine but the list view on the right doesn't.

---

### Post by Dillius on 2008-03-18
Having the same problem here as well with 7.10 on a server on the same subnet as my client.

Did anyone ever figure this out?

---

### Post by Bottesford on 2008-03-18
Sorry no I never found a solution to this so tend to avoid VNCing in and use webmin instead...

---

