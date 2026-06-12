---
title: "Won't Take Username / Password"
date: 2006-07-25
forum: General Help
---

### Post by tonyr1988 on 2006-07-25
I think this all happened after I upgraded my linux kernel (if I did...I kind of did all the updates automatically...oops).

Anyways....I booted up today, and GRUB was showing two kernels. I booted into the newer one, went into Synaptic, deleted the older one (I saw that piece of advice on another thread). However, when I boot into Ubuntu, it asks for my username / password, but then just returns to the username / password page.

Any ideas?

I'm posting this now from recovery mode. When Ubuntu was working, I had it automatically log me in to the only user I had set up (for convenience...I know, not the BEST idea).

Thanks in advance!

---

### Post by tonyr1988 on 2006-07-25
Update: within the recovery mode, I changed my password (using passwd tony in Terminal), and it still won't let me in. I've tried twice.

Should I just write down all my installed programs from Synaptic, re-install Ubuntu, and re-check them all?

---

### Post by KaeseEs on 2006-07-25
Are you disallowed graphical login, or all login?

---

### Post by DayTripper on 2006-07-25
Hi,

This happened to me too. It looks like something went wrong with upgrade ... in my case I could see that upgrade has changed a few passwords in shadow file (comparing new and old file with diff).

I fixed this with help of liveCD. I renamed corupted etc/shadow file to something else and replace it with old version that I find in the same folder (I dont remember the name of that file, but it was obvious that it was backup version created before upgrade ... looking at file timestamp).

Best Regards,
Simon

---

### Post by tonyr1988 on 2006-07-25
A few things:

1) It has a graphical login. However, it doesn't tell me that my password is incorrect or anything. The login screen goes away, it pretends like it's going to load (my cursor turns into the "Loading" circle), but then goes back to the login screen.

2) I changed my etc/shadow file entry to:

tony::0320320932:0202 (I made up those numbers - I deleted the password).

It wouldn't let me in when I didn't type a password. That time it told me it was incorrect.

3) I then changed the password to my usual (I had to use the passwd command to get it encrypted). When I rebooted, it went back to doing what it used to do.

4) This is the craziest one - I re-installed Ubuntu from the CD. I reformatted my root folder. It still doesn't work!

I have my /home in another partition, which I didn't format. But that wouldn't mess it up during login, would it?

I hate using WinXP! Give me back Ubuntu, please??? :P

---

### Post by tonyr1988 on 2006-07-25
Apparently it was something in my /home that was messing it up. I have my /home in another partition. I re-installed Ubuntu, but this time didn't make that other partition my /home, and it works. Any idea what could've gone wrong?

---

### Post by KaeseEs on 2006-07-25
I didn't notice whether you tried a command-line login while your GUI login was broken.  What you said however, was that your desktop manager's login screen didn't reject your password, but rather went back to your login screen after accepting it.

  To me, it sounds like your password was fine, but your desktop manager was somehow borked, failing early in the launch process, and restarting, thus giving the appearance of a failure in the authentication process.

    If you encounter similar problems in the future, try a CLI login (press Ctrl + Alt + F2 to go to tty2, your second terminal, and login from there).  If that succeeds, your login is fine, but your desktop manager is broken, which should be fixable with an uninstall/purge/install cycle through APT.  Here's hoping, thus, that it doesn't break again!

---

### Post by tonyr1988 on 2006-07-25
Oh, poop. It's such a pain going through and installing / re-configuring my programs (especially on dial-up). Oh well - it's definately worth it.

If it breaks again (crossing my fingers), I'll definately take your suggestion. Thanks!

---

