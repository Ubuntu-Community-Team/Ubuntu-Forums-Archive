---
title: "How will it work if I install Kubuntu under Ubuntu?"
date: 2005-10-16
forum: General Help
---

### Post by stoffe on 2005-10-16
Hello, I saw the advice somewhere that one can install the Ubuntu CD and then simply install kubuntu (was it kubuntu-base perhaps?) to get a complete Kubuntu system parallell to the other one.

What I wonder is, how will this work? Will I have two menu options at the boot screen or something, so I can choose if I want to go into an Ubuntu or Kubuntu session?

I like both Gnome and KDE and think both has their merits, so I'm looking for an easy way to try both without having to resort to separate installs.

Also, I like the "Desktop is Home" option of Gnome, will that break down in Kubuntu or is it possible to do it in KDE as well - and more importantly, will it work together?

Hoping for best of both worlds. :)

---

### Post by adwait on 2005-10-16
Just run the command
```
sudo apt-get install kubuntu-desktop
```

That will install all the KDE applications etc.  After that, at the login screen you'll have an option of starting a KDE or Gnome session.

---

### Post by stoffe on 2005-10-16
[QUOTE=adwait]Just run the command
```
sudo apt-get install kubuntu-desktop
```

That will install all the KDE applications etc.  After that, at the login screen you'll have an option of starting a KDE or Gnome session.[/QUOTE]
Thanks! And about the Desktop/Home thingy?

---

### Post by raggamuffin on 2005-10-16
[QUOTE=stoffe]Thanks! And about the Desktop/Home thingy?[/QUOTE]

all your programs/files will be available both in GNOME and KDE...so if you have a GNOME session running and you save a document to your desktop, it will be there when you start a KDE session, and vice versa...

---

### Post by stoffe on 2005-10-16
[QUOTE=raggamuffin]all your programs/files will be available both in GNOME and KDE...so if you have a GNOME session running and you save a document to your desktop, it will be there when you start a KDE session, and vice versa...[/QUOTE]
Maybe I wasn't clear enough: I am right in that both KDE and Gnome uses ~/Desktop as the default desktop, right?

Well, Gnome has an option to set your homedir as the desktop, something which I've been running for a while on my laptop, and I think I like that more. The desktop seems more like a natural home somehow. Basically, it uses ~ instead of ~/Desktop and so far it seems that everything works as it should anyways, no applications making any stupid things because of this.

I'm about to make a clean install of my main computer real soon, and I thought I'd try the dual environments as well as switching it to desktop-is-homedir, but only if that is a good idea. :)

So, the question is: does KDE have a similar setting, and if so, does it work well? Can anybody predict any trouble coming from running both KDE and Gnome in this manner?

---

### Post by adwait on 2005-10-16
I don't think that should cause a problem.....You can safely set your desktop as the homedir in KDE as well.

---

### Post by stoffe on 2005-10-18
Sounds good then, thanks!

---

### Post by noppie on 2005-10-18
> sudo apt-get install kubuntu-desktop

can I do this the other way
sudo apt-get install ubuntu-desktop  to get the gnome for the ubuntu


I have been using mandrake 10.1  and want to try this Ubuntu. but  I have been using kde for so long and have mail I want to transfer.. I really like the k-mail.. but I also want to use some gnome programs.

thank you in advanced
noppie

---

### Post by GameManK on 2005-10-18
[QUOTE=noppie]can I do this the other way
sudo apt-get install ubuntu-desktop  to get the gnome for the ubuntu


I have been using mandrake 10.1  and want to try this Ubuntu. but  I have been using kde for so long and have mail I want to transfer.. I really like the k-mail.. but I also want to use some gnome programs.

thank you in advanced
noppie[/QUOTE]

you can use gnome programs in KDE and vice versa, they just don't fit in well aesthetically and you have to install a lot of extra libraries (taken care of by apt-get)

---

### Post by didit on 2005-10-19
yes, why not? I am currently running kubuntu with kde 3.5 beta2. The nice thing to have to DE is that we can switch user. One is running kde and another one is running gnome. Very nice :D

---

### Post by crankcaller on 2005-10-20
I have added kde by doing the above apt-get voodoo.

Question:
Could i then remove Gnome - either using synaptic or a command line.
Would my system work ok?
What would i have to leave?

And would doing a `server` install then an apt-get for kubuntu desktop be the same thing?  This would save me downloading the kubuntu iso

---

### Post by joneall on 2005-10-23
[QUOTE=noppie]can I do this the other way
sudo apt-get install ubuntu-desktop  to get the gnome for the ubuntu


I have been using mandrake 10.1  and want to try this Ubuntu. but  I have been using kde for so long and have mail I want to transfer.. I really like the k-mail.. but I also want to use some gnome programs.

thank you in advanced
noppie[/QUOTE]

I'm not sure I understood that.  I have installed Kubuntu and want to be able to use Gnome also, so as to decide for myself which one I prefer (I like the colors of the Ubuntu Gnome desktop).  I installed gdm with apt-get.  But at logon, the LLH button only offers default and KDE as choices.  So do I have to install ubuntu-desktop and that will work?

Thanks in advance.  John

---

