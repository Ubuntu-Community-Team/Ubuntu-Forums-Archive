---
title: "'emacs' blank files...but 'sudo emacs' works"
date: 2012-11-23
forum: General Help
---

### Post by amhainen on 2012-11-23
I've tried apt-get purging and reinstalling emacs, but if I run:

```
emacs ~/.bashrc
```

I get a blank file (emacs.d) that looks like this:

[IMG]http://i.imgur.com/ZlG0Q.png[/IMG]

If I run the same command as root:

```
sudo emacs ~/.bashrc
```

I get the correct file that looks like this:

[IMG]http://i.imgur.com/N3uQX.png[/IMG]

I've never understood the buffer thing, but emacs has worked great for me in the past. I don't know why it keeps going to this emacs.d file. Note that this is the same for any file (even new ones), I just used .bashrc for an example.

Thanks for the help!



P.S. Switching to VI/VIM might work, but let's not try that ;)

---

### Post by Zill on 2012-11-23
> **amhainen said:**
> ...P.S. Switching to VI/VIM might work, but let's not try that ;)
IMHO both emacs and vim are far too complex and are overkill for simple text editing jobs.

I recommend nano for these jobs because it "just works"!
```
nano ~/.bashrc
```

---

### Post by amhainen on 2012-11-23
> I recommend nano for these jobs because it "just works"!

Thanks, but no thanks...just trying to fix my emacs.



I do agree that nano is great!

---

### Post by Impavidus on 2012-11-23
Purging and reinstalling resets system-wide configuration, but doesn't remove/reset the user's configuration file. Try removing your .emacs.d manually.

---

### Post by amhainen on 2012-11-24
> **Impavidus said:**
> Purging and reinstalling resets system-wide configuration, but doesn't remove/reset the user's configuration file. Try removing your .emacs.d manually.

Worked great! Thanks so much!

I just ran:

```
rm -rf .emacs.d/
```

Not sure what was in that folder, but now 'emacs .bashrc' works fine.

---

