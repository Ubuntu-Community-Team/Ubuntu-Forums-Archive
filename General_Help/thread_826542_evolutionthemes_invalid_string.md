---
title: "evolution/themes: invalid string"
date: 2008-06-12
forum: General Help
---

### Post by Crypty on 2008-06-12
When I try to strat evolution nothing happens, I just get a loadting wheel. After about 2 mins evolution finally starts.

Starting it in terminal spits this out:

steve@steve-laptop:~$ evolution
/home/steve/.themes/Aurora Nite/gtk-2.0/gtkrc:389: error: invalid string constant "theme-combo-arrow", expected valid string constant


Any help is appreciated.

---

### Post by iaculallad on 2008-06-12
It seems like you have a problem with your current theme. Try (disabling your current theme) using the default Ubuntu theme instead and re-run you Evolution if it still lags on loading and if it shows the same error when executed using the terminal.

---

### Post by Crypty on 2008-06-12
When I enable a standard theme and run from terminal it doesnt give me that error. Instead it says:
steve@steve-laptop:~$ evolution
  
  
  
  
  
  
  
  
  
  
  
  
*stops here*

So I enter the command, and it basically hits return a bunch of times to make like 12 blank lines.

---

### Post by Crypty on 2008-06-12
I got to work and now it works fine. It seems like it might have something to do with checking the exchange server. At home, it probably fails to connect and takes a long time to start as a result. I need to find away to tell it not to check mail on startup, only when I press send/receive.

---

### Post by Crypty on 2008-06-12
back home and its taking forever to start again.

---

### Post by Crypty on 2008-06-13
its set up to sync to an exchange server. I've read that this causes slow startup but I cant seem to find a solution. Its unbearably slow, like 2-5 minutes.

---

