---
title: "Keyring:  Is this a bug or a feature"
date: 2007-05-14
forum: General Help
---

### Post by VorDesigns on 2007-05-14
My first Microsoft moment with Linux:

While getting WPA to work I ended up using nm-applet (last thing I tried that worked).  During this process, I was prompted for a default keyring password.  There was no warning that the password could only be alpha numeric and since I'm security conscious, I entered a password that included some of the following !@#$%^& characters that help make a good password better.
After I connected successfully, I rebooted to make sure that this wasn't a fluke.  Upon log in, I was prompted with a keyring password request for nm-applet.  Because I used a strong password, the system failed to access the key.  I had to delete the defaul keyring and start over with a less secure password.

So, my question is, is this a bug or a feature?

---

### Post by ashz on 2007-05-14
probably a bug, but if it is just a local system then i would not worry too much about the security aspect!

ash

---

### Post by hyperair on 2007-05-15
I've had this problem before, and it's nothing to do with having a strong password or not. The solution's somewhere in Ubuntuforums, but I'm rather lazy to search it up right now, so here's a summary:
```
sudo apt-get install libpam-keyring
```

As the description says: 
> PAM module that unlock gnome keyring. This PAM module unlock your gnome keyring at login time. Useful when using network-manager or other tools that requires access to gnome keyring just after login.

---

### Post by VorDesigns on 2007-06-12
I forget you have to tell the forum you want to follow threads:

My issue is that I use strong passwords and I used a strong password for my keyring but, when I went to use the strong password, I couldn't open the keyring and had to deleted and recreate it it with a weak password.

I don't have much of an issue with being prompted for a password to get further into proprietery levels of the system.  What bothers me is that the good password I used and that the keyring manager accepted bombed when I was prompted to reproduce it.

---

### Post by hyperair on 2007-06-13
Sounds like a bug to me, perhaps you should try reporting it at launchpad or something.

---

