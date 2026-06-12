---
title: "no module display - resolution issue"
date: 2007-01-29
forum: General Help
---

### Post by bboop on 2007-01-29
I am running Dapper and had a video card crap out - a nvidia geforce2MX,
I replaced it w/ another geforce2MX400.
When I rebooted to the new card x would not open - I started x in terminal & then kde & went to display (it was working) & configured new card.
Now when it open it does open kde correctly BUT the display is HUGE - I only see abt. 10% of the screen at a time!!
I went to  display to set the screen resolution and I am getting this message:
The module display could not be loaded. The diagnostics is:
Possible reasons
*an error occurred during your last KDE upgrade leaving an orphaned module
*you have old third party modules lying around

I have not upgraded KDE - I only did what was stated above.
I did check these forums and try the 
sudo apt get install --reinstall kde_guidance
output said operation went fine, but still same message.
HELP Please - TIA

---

### Post by bboop on 2007-01-30
Next Day
I have found if I run
<sudo dpkg-reconfingure -phigh xserver-xorg>
it picks the correct graphics card & a generic monitor
after reboot xserver will not start until I use startx from command line.
When it does I get the huge display, but I can reach settings in
system tools>display>admin mode
where I can set the monitor to the Acer 55L I have.
I have found that if I choose proprietary driver in the graphics card the xserver does start automatically w/o prompt, but there is no access to display setting (see prior message)
BUT when kde runs there is an Error message:
"I've detected a panel already running, I will now exit."
And there is an extra panel at the bottom which is x (I guess)that is always there: if I try to use the logout on the x panel it just restarts both desktops. If I choose logout on kde x is there. Commands seem to work from either panel for awhile, but now it is just a plain panel w/o icons, but if I close it x server closes.
There are 2 users on this computer and if I try to start new session w/ other user (kde) the computer locks up.
If anyone can help I will gladly post any information you need.
I am hoping to find a way other than a new install as I am on dial up (no choice) at around 500b/s... it takes me a long time to get a system set up and updated.
I did put in a Kubuntu cd and ran live - it ran fine. I looked, but didn't see any discernable difference between the xorg. conf from that and what is in my files.
I did wonder if I used envy & tried to do fresh drivers if it would help. Or if I can reinstall some element to correct the problem. I did do all listed updates today in hopes something would get better, but no.
PS: I run a system w/ a trio setup - the other HD runs an old Fedora4 which is having no issues w/ the new card.

---

### Post by bboop on 2007-01-31
I tried the envy, still no access to display setting etc.
but I have found that when I check the (extra) panel at the bottom it's GNOME!!!
Apparently this thing is booting a gnome & a kde at the same time... there is no available action from the panel tho.
What the &^($!
Any ideas - help appreciated
:confused:

---

