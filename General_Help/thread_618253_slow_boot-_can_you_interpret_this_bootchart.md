---
title: "slow boot- can you interpret this bootchart?"
date: 2007-11-20
forum: General Help
---

### Post by dennis_m@hotmail.com on 2007-11-20
Hello all,

Recently installed gutsy after a year of edgy- the only problem I have is with a much slower boot. Ive attached my bootchart- can anyone help me interpret it and point me in the right direction?

Many thanks in advance.

---

### Post by dennis_m@hotmail.com on 2007-11-20
bump

---

### Post by doctorgreg on 2007-11-20
Open up terminal and type in sudo gedit /etc/usplash.conf   ..........then type in your password.  it will show x and y values for a screen resolution but it will be different then yours.  Change the values to the resolution you are currently using.  Then click save at the top of the window.  Then you should reboot and notice a world of difference.

---

### Post by dennis_m@hotmail.com on 2007-11-22
Thanks drgregg-

Changed from 1024 to 800 (as listed in SYS..-PREF...-SCREEN RES...) and it had an effect, alas it ended up taking a fair while longer to boot (new bootchart attached).

I noted this in my syslog:
NFSD: starting 90-second grace period
could that be of any relevance?

On switching on after the grub screen, there seems to be no hard-drive activity for a minute or so, before it starts flashing and then loading gnome- not sure if relevant, just thought id mention it.

(sorry if the above is somewhat noobish- if its a case of PEBKAC let me know)

cheers in advance.

---

### Post by doctorgreg on 2007-11-22
Hey there.  Sorry i forgot to tell you one thing.  Type this in the terminal.

sudo update-usplash-theme usplash-theme-ubuntu

This updates the theme or something.  But before you do this just double check the upsplash again as i posted earlier just make sure the changes saved.  Then after you put this code in reboot and it should be fine.  Sorry about the forgetfulness.  LOL

---

### Post by doctorgreg on 2007-11-22
Hey there i forgot to tell you one thing.  Type this in the terminal.

sudo update-usplash-theme usplash-theme-ubuntu

This updates the theme or something.  Before you do this just double check the upsplash thing I posted earlier to make sure the settings saved.  Then after you enter in this code do a reboot.  If that don't work then I don't know but it should.  It did for me.  Sorry bout the forgetfulness.  Cheers

---

### Post by dennis_m@hotmail.com on 2007-11-22
doctorgreg, you are a star

worked a treat mate; 31 seconds in fact, a big improvement on 6 minutes,

thanks once again, den

---

### Post by doctorgreg on 2007-11-22
Hey not a problem man.  That's what the community is for right.  I got help and now can help others as I learn.  Enjoy!

---

### Post by mrat on 2007-12-20
Thanks doctorgreg !!!

My problem solved.

I was trying to get Edubuntu onto an old laptop for my niece and was having this issue. The "/etc/usplash.conf" had values way over 1024x768, which is the max it would do.

I noticed that there was no splash screen when booting, so thought to try your suggestions.

Phew !!!

Regards
Mark

---

