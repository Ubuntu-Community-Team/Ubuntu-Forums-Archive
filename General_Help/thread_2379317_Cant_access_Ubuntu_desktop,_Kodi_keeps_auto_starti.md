---
title: "Cant access Ubuntu desktop, Kodi keeps auto starting"
date: 2017-12-04
forum: General Help
---

### Post by buksida on 2017-12-04
I cant stop Kodi auto-starting, not sure how it got setup like this in the first place.

I can pull up a terminal box and kill the process, but then get a black screen on exit. Rebooting brings Kodi back again and every time I exit Kodi it starts again.

How can I stop this and get back to my Ubuntu desktop? 

I've tried updating grub but it had no effect.

Thanks!

---

### Post by ajgreeny on 2017-12-04
I do not use Ubuntu and don't know kodi but check if your system is set to remember and restore the previous session when it is shutdown or rebooted; I use Xubuntu and that can save sessions from the shutdown dialogue so have a look at that and clear any selection box if it exists, and also look in your startup applications list and remove kodi, if it is there.

You may also find saved sessions in the hidden .cache/sessions folder in your home, so have a close look there and remove them if they are found.

---

### Post by buksida on 2017-12-04
Thanks for the reply but I have no idea how to do this, I cant access the desktop, only Kodi starting in a loop.

---

### Post by howefield on 2017-12-04
Which release of Ubuntu are you using ?

```
cat /etc/*-release
```

---

### Post by buksida on 2017-12-04
17.10

I can ctrl+alt+F1 to get the terminal screen, but on exit Kodi comes back on. Rebooting does the same thing, the GUI has gone.

---

### Post by vasa1 on 2017-12-04
> **buksida said:**
> 17.10

I can ctrl+alt+F1 to get the terminal screen, but on exit Kodi comes back on. Rebooting does the same thing, the GUI has gone.

Please post the ENTIRE contents of what has been asked of you. Don't pick and choose what to show.

Once again, show the output of```
cat /etc/*-release
```

---

### Post by buksida on 2017-12-04
I took a screenshot but the forum wont let me upload an image.

It just says stuff like Ubuntu release-17.10, codename=artful, version=artful aardvark, home URL, etc. Nothing specific.

---

### Post by vasa1 on 2017-12-04
Use copy/paste.

---

### Post by buksida on 2017-12-04
I'm posting from a Windows machine. I cant access anything on the linux box, only the terminal screen and Kodi.

What line do you specifically want?

---

### Post by buksida on 2017-12-04
Ok, I've uploaded the image to my server.

[IMG]http://digitalmetrix.net/release.jpg[/IMG]

---

### Post by howefield on 2017-12-04
Click on the cog wheel at the login screen and select "Ubuntu"...

---

### Post by buksida on 2017-12-04
Done that, just get a black screen - no desktop. Then Kodi starts and I cant exit out of it.

Evidently this is not fixable then so I will have to format and reinstall an earlier version.

---

### Post by howefield on 2017-12-05
> **buksida said:**
> Done that, just get a black screen - no desktop. Then Kodi starts and I cant exit out of it.

Hmm.. tried and tested before posting so I know that it works. The session manager should offer 4 environments, two for Kodi, one for Ubuntu (with Wayland) and one for Ubuntu with Xorg. Did you try both Ubuntu options ?

---

### Post by buksida on 2017-12-05
Ok, with you now, thanks! Somehow Kodi had created its own login - there are also two logins one for Ubuntu console and the other the desktop which I was trying to get back all along.

So the next question, how do I stop Kodi creating its own logins and taking over the machine?

---

### Post by howefield on 2017-12-05
> **buksida said:**
> Ok, with you now, thanks! Somehow Kodi had created its own login - there are also two logins one for Ubuntu console and the other the desktop which I was trying to get back all along.

So the next question, how do I stop Kodi creating its own logins and taking over the machine?

Cool, it'll need to be someone more experienced with Kodi than me to answer that. I'm not sure there is anything short of configuring your Ubuntu session to auto login.

---

### Post by buksida on 2017-12-05
No worries, thanks anyway - have my desktop back without having to reformat!

---

### Post by iioodii on 2017-12-11
I am facing same issue what was the solution ?

---

### Post by howefield on 2017-12-11
> **iioodii said:**
> I am facing same issue what was the solution ?

If you have a problem which reading this thread doesn't solve, then please start a fresh new thread with as much information as you are capable of.

---

