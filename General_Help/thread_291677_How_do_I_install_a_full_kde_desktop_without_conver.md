---
title: "How do I install a full kde desktop without converting to Kunto"
date: 2006-11-02
forum: General Help
---

### Post by DagonX on 2006-11-02
I would like to switch between KDE and Gnome desktop. I do no how to convert to Kunbuntu. But I don't know how to convert back. Is any way to easily switch between desktops?

---

### Post by darkhatter on 2006-11-02
I believe

'apt-get install kde' will do the trick

---

### Post by skierkegaard on 2006-11-02
If you have both installed you would log out, and then select the one you want to switch to from the options on the login screen.

---

### Post by d3v1ant_0n3 on 2006-11-02
In terminal, enter this:

sudo aptitude install kubuntu-desktop

Then your password.

This will install all of the Kubuntu components, but it won't touch any of your GNOMe things.
When you login, there will be the option to select KDE or GNOME desktops.

---

### Post by nalmeth on 2006-11-02
yes, use aptitude for a large metapackage like kubuntu-desktop, it will makes things terrible easy to remove if you don't want it.

There is also a 'slightly' faster kde-core alternative, though if you're using edgy, the difference will be minimal.

As stated, you will change the DE at the login manager.

---

### Post by Snoopy1966 on 2006-11-12
> **d3v1ant_0n3 said:**
> In terminal, enter this:

sudo aptitude install kubuntu-desktop

Then your password.

This will install all of the Kubuntu components, but it won't touch any of your GNOMe things.
When you login, there will be the option to select KDE or GNOME desktops.

I did this exact steps that was mentioned, but I do not see the choice to select KDE or Gnome at the login.  It loads Kubuntu  When it got to the installation point, it asked me what I want for default and I picked Gnome because I did not want to mess up what I have now.  It said something about configuring something to make the choices available, but it is a little over my head right now.  I was able to get my ATI card going, and my SB Audigy with all speackers working now!  After a long search I found all I needed to do was double click the volume and then I chose the correct sound card.  Viola,  Surround Sound :)

Any help in this for me so I can choose between the desktops?

---

### Post by podunk on 2006-11-12
did you see the menu button on the log in screen - it's very small. click it then chose "Session" and you should have a choice between kde and that other desk manager. :-) Also a failsafe there if you ever run into problems.

When you're in KDe be sure to check out Konquror! Truly awsome.

---

### Post by Snoopy1966 on 2006-11-12
Oh yeah!  I like it very much :)  Thanks for the help
I like the looks of KDE much better so far.  Got the sound card working.  Need to get ATI configured though.  It gave me an error about something not supported.  Well time to play with this now. :)

---

