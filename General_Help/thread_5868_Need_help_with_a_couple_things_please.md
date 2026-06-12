---
title: "Need help with a couple things please"
date: 2004-11-22
forum: General Help
---

### Post by bmzf on 2004-11-22
I've had a great experience with Ubuntu so far, but there are a couple problems that I really haven't been able to solve since I switched to this distro.

I just recently installed Fluxbox from the universe section of the repository.
I need to run some programs on startup, so I put them in my ~/.xsession file. This file's permissions are 755. I've also tried .xinitrc (which probably isn't what I need since I'm using gdm), and .Xsession.
Nothing happens. It just doesn't get executed.
I even edited /etc/X11/Xsession and /etc/gdm/Xsession to check for and run the users .xsession file if it exists.
Still nothing.

I'm really stumped. If anyone could help me, that would be greatly appreciated.

I'd also like to know how to make it actually read my .bashrc and .bash_profile when it starts up. What good are these files if they aren't used?
When I was using GNOME, I ran by a tip online that said I should put settings in .gnomerc to make it work. That's no help while I'm using fluxbox and so I can't set my environment variables.

I didn't find any answers searching Google and other forums.

Somebody's gotta know what's going on here... it's not me though :confused:

---

### Post by Avicus on 2004-12-09
[QUOTE=bmzf]I've had a great experience with Ubuntu so far, but there are a couple problems that I really haven't been able to solve since I switched to this distro.

I just recently installed Fluxbox from the universe section of the repository.
I need to run some programs on startup, so I put them in my ~/.xsession file. This file's permissions are 755. I've also tried .xinitrc (which probably isn't what I need since I'm using gdm), and .Xsession.
Nothing happens. It just doesn't get executed.
I even edited /etc/X11/Xsession and /etc/gdm/Xsession to check for and run the users .xsession file if it exists.
Still nothing.

I'm really stumped. If anyone could help me, that would be greatly appreciated.

I'd also like to know how to make it actually read my .bashrc and .bash_profile when it starts up. What good are these files if they aren't used?
When I was using GNOME, I ran by a tip online that said I should put settings in .gnomerc to make it work. That's no help while I'm using fluxbox and so I can't set my environment variables.

I didn't find any answers searching Google and other forums.

Somebody's gotta know what's going on here... it's not me though :confused:[/QUOTE]
 Yeah, I too am having this EXACT same problem. I wanna run gnome-settings-daemon and fbsetbg on login and nomatter what I do to .xsession (which .xinitrc is symlinked to) it isn't read. Permissions of the file are 755 and running it separately starts my programs just fine.
So why does Ubuntu disable these files??? I don't like that.

---

### Post by Avicus on 2004-12-09
Well I found a stupid work-around....
in the ~/fluxbox/init file, WHICH I had to copy manually from /etc/X11/fluxbox, I added the value ./.xsession to session.screen0.rootCommand so the line looks like this:
session.screen0.rootCommand: ./.xsession

This does force fluxbox to read the xsession file.... but why do I have to do this, why can't ubuntu just read the .xsession file like it should?

---

### Post by Juergen on 2004-12-09
[QUOTE=Avicus]but why do I have to do this, why can't ubuntu just read the .xsession file like it should?[/QUOTE]For me ~/.xsession works. 
Did you maybe just forget to chmod +x?

---

