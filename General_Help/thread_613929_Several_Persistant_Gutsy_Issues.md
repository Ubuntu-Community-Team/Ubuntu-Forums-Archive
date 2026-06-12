---
title: "Several Persistant Gutsy Issues"
date: 2007-11-15
forum: General Help
---

### Post by armware on 2007-11-15
I've been having a few issues since my upgrade to gutsy (updater crashed midway) that I've been trying to avoid posting about until I've spent some time researching them.
Well, I don't have much time to do so and things have been getting bad. Real bad. Like reboot every 10 minutes bad. So I'll post my issues, hopefully I can get some answers/links/help here.

running kubuntu gutsy on an hp dv8230us, compiz-fusion, kbfx menu

1] no biggie, but i have no user icons in the login screen.
2] when i log in, after the desktop loads and i see my icons, i have no menu panel. the process kicker is sometimes running, sometimes not, either way i have to run 'killall kicker; kicker' every login.
3] after screwing with kicker, my system tray icons aren't always in the tray. this gets irritating as knetworkmanager doesn't always appear. ktorrent is also notorious for this, even when others (battery, kmix) (magically?) get added, ktorrent needs killed and relaunched before it'll show up.
4] kicker crashes while upgrading/installing apps via apt-get or adept manager
5] sometimes knetworkmanager is waiting for a key request, but i have no 'enter password' dialog. so i'll logout and after the screen is black, said dialog will appear. 'course by then it's too late.
6] not too often, but about once a week my keyboard will suddenly just stop sending keys, every app. i can't even ctrl+alt+backspace or ctrl+alt+f1 to a terminal. i have to use the mouse to logout and back in.
7] quite frequently my wireless card (ipw3945) drops. i think i've gotten this narrowed down to intel's firmware, but is there anything i can do, like upgrade/downgrade to a more stable firmware/driver? this sometimes takes down the entire machine.
8] randomly kdm will restart itself, and on one occasion, in the middle of writing code (work) and listening to music, the screen went black for a few seconds, then proceeded to shutdown.
*9] when i click logout, i only have the option to logout where i used to have shutdown, reboot, sleep and hibernate.

any ideas on any of these? i'd love to wipe/reinstall, but my dvd drive is completely worthless. ok, i guess it keeps dust out of the inside of the laptop, but a strip of duct tape will do the same.

thanks a ton to anyone who has some ideas.


* = fixed, continue in thread for what worked for me

---

### Post by armware on 2007-11-16
fixed #9:

kcontrol->kde components->session manager->offer shutdown options

---

### Post by armware on 2007-12-05
so i decided that too much was effed up (upgrade to gutsy crashed), so i wiped the partition and installed gutsy. that fixed most of it, but i still have a few of the same issues, and a few more.

1] login user icons are now there
2] still happens, though it's rare.
3] still happens at every single login. i have to boot up my laptop, login, logout, and login before it works right.
4] i think this is more kbfx than kicker
5] i believe this to be related to 3, as if it's waiting for kwallet access, it (and ones after it?) wait, but the enter wallet password dialog doesn't show until after i issue a logout.
6] this has stopped entirely, though #10 has replaced it
7] still drops out, but there appears to be something to reinit it all, which works a good majority of the time. that's awesome enough.
8] still happens, though i'm pretty sure it's deeper than kdm
10] randomly (it's happened while typing in firefox/aptana/kwrite, moving windows, hell, even just moving the mouse which is what leads me to believe it's not anything specific i'm doing) the screen freezes, mouse and all, music stops, and just sits there for 10-20 seconds before it either does nothing or goes black. the only way out of this one is with ctrl+alt+sys rq. this happens 0-10ish times a day, every day, for the last few weeks.

any ideas on these?

---

