---
title: "Urgent: Lotus Notes 8 freezes with Desktop Effects enabled"
date: 2007-12-25
forum: General Help
---

### Post by arjunrc on 2007-12-25
Hello,
I am running Ubuntu 7.10. I installed Lotus notes 8 successfully. Everything works fine, but here is the problem:

I use compiz. When I select "No Desktop effects" notes works like a charm. However, when I select any desktop effect besides none ( by going to System->Pref->Appearance->Visual effects), and start notes, it works fine, till I need to view the content of _any_ email. That is when notes freezes. Actually, the entire system freezes. I can move my mouse, but can't do anything else. I even cannot switch to a console screen besides my mouse movement my keyboard also freezes - so I have to do a hard power down.

I use a sony vaio sz650 (nvidia geforce 8400m GS) 

Any help?
thanks

---

### Post by RudolfMDLT on 2007-12-25
I use matlab and that also isn't very Beryl or Compiz friendly! :)

I solved it by doing the following:

Install Emerald and then also install Heliodor. Heliodor is a window decorator that "looks" like gnome's default decorator to applications but still allows you to play with all the cool Compiz/Beryl effects.

If I remember correctly, when you run Emerald you should get a green diamond in the system tray. Rightclick on it and select window decorator and then select Heliodor. If it doesn't work, try installing Beryl and then try clicking on the red beryl diamond and switching to heliodor.

---

### Post by arjunrc on 2007-12-25
Ok, I really mucked up something.

I tried installing emerald - all worked fine, but notes bombed with "Notes is not installed" !! 

I reverted back to my old compiz and removed emerald

Now when I try to re-install notes, I get a 
The installer is unable to run in graphical mode. Try running the installer with the -console or -silent flag.

I am sure I must have deleted something by mistake !! Help !!
(ps libmotif3 and gtk1.2 are installed)

---

### Post by arjunrc on 2007-12-25
Ok never mind - back to my old settings. It looks like libstdc++ was deleted - reinstalled and everything is ok

---

### Post by RudolfMDLT on 2007-12-26
I'm glad your back to work! but does the email client still crash?

---

### Post by arjunrc on 2007-12-26
Hi, I must have done something right. Now the email client does not crash even with effects turned on.

---

