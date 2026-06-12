---
title: "In a non-GUI environment, how do I edit a file and save?"
date: 2006-10-30
forum: General Help
---

### Post by dbqp on 2006-10-30
I have a really good understanding of Ubuntu in a GUI sense, and am even attempting to tackle a LAMP Server install to play around with. But beyond the essentially required commands in a terminal, I don't know my way around the command prompt in Unix/Linux.

I found a really good article on setting one up and understand most of what will be required. In one of the steps, it asks you to:
```
vi /etc/network/interfaces
```

The page in question can be found [here]("http://www.howtoforge.com/perfect_setup_ubuntu_6.10_p3")

I have gotten to the point where I open the file from the command above, but how do I save it once I finish and return to the prompt? I just can't get my head around that...](*,) 

This is why I have posted this here - not server, not LAMP, not "vi", but just simply how do I do this simple step?

:neutral:

---

### Post by stickmangumby on 2006-10-30
There are two modes in vi, command and insert. Press esc to enter command mode, then type :wq and press enter. This will write to the file, and quit vi.

In the terminal, type vitutor for a great tutorial for vi. It is invaluable :)

---

### Post by dbqp on 2006-10-30
> **stickmangumby said:**
> There are two modes in vi, command and insert. Press esc to enter command mode, then type :wq and press enter. This will write to the file, and quit vi.

In the terminal, type vitutor for a great tutorial for vi. It is invaluable :)

Wow! Thank you for such a quick reply. I will definitely read up using vitutor. I tried going with [this setup]("http://www.howtoforge.com/lamp_installation_ubuntu6.06") (using a GUI, but man is it slow!) and it is geared towards people who are new to Ubuntu - not new to LAMP and a web server...DOH!

n.b.
I have been learning Ubuntu for the past 6-8 months now using a test box as I have to find away out of this licensing mess with M$ and this forum has been a wealth of info and much of those thanks go to the community such as yourself. Thank you.

---

### Post by CatKiller on 2006-10-30
For a less hardcore way of editing files than vi(m), you could use **nano**. vi is a hugely powerful and efficient editing environment, but it does have a tendency to make new users mess themselves.

---

### Post by tortus on 2006-10-31
> **CatKiller said:**
> vi is a hugely powerful and efficient editing environment, but it does have a tendency to make new users mess themselves.

Yeah but vi is a right of passage for new *nix users :)

---

