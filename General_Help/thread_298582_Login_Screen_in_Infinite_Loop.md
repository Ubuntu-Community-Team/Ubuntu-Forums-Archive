---
title: "Login Screen in Infinite Loop?"
date: 2006-11-12
forum: General Help
---

### Post by ivanjs on 2006-11-12
Just ran an update, and suddenly when I try to log in, the login screen clears, you see terminal output for a second, then it comes back to the login screen asking for login and password. I know I'm typing in the right login/password, because when I log in from the terminal, it logs in properly.

I can jump out to the shell and login there, so I know I'm using the correct login and password.

Weirdest part of this is that once in about 10 or so tries to login, it actually logs in! 

Suggestions?

Using 6.06-LTS
Thanks.
V

---

### Post by ivanjs on 2006-11-13
Anyone? I just sccanned the forums and see that several people are having this problem, and for many of us, it started after we edited new screen resolutions in xorg.conf. I restored my original xorg.conf, but it hasn't fixed the problem. Still get to login screen, I login with correct login and password, it temporarily goes to shell, jumps back to login screen.

---

### Post by pmaker on 2006-11-13
do you connect internet by dhcp??

then you can do this.

sudo gedit /ect/dhcp3/dhclient.conf and

uncomment the line timeout 60; and put timeout 5; for example.

bye.

---

### Post by ivanjs on 2006-11-14
Thanks, pmaker, but that didn't help.

I do notice that if I choose kde instead of gnome from the login screen options menu, that I can log in everytime. Which says to me it's not Ubuntu that's messed up, just gnome. So how can I reinstall gnome without reinstalling all of ubuntu? I tried installing everything that had to do with gnome in the synaptic package, but it still doesn't work.

How do I reinstall gnome?
thanks.

---

### Post by klep on 2006-11-14
i had a similar problem. went to login, would appear to be doing it, flash up the nvidia spash, then log me right back out to the login screen. the problem was because i had no diskspace left. dont kow if that'll help you at all.

---

### Post by koenn on 2006-11-14
the program that handles the gui ('gnome') login is gdm, and when it crashes (or when gnome crashes or shuts down eg by hitting Ctrl+Del+Backspace), it automatically starts again and presents a login screen.
That's that 'infinite loop' you're seeing. Its a sympton. The problem is that gnome / gdm / ... keep on crashing. This could be caused by anything between a faulty gnome config or trouble with xorg xserver (you've edited xorg.conf ...)

Don't know if reinstalling gnome is going to help. It might. I've done a couple of custom installations of Dapper (install a 'server' and add desktop and apps later) and to get gnome installed i did:

```
sudo apt-get install x-window-system-core gnome-session gnome-panel gdm metacity ubuntu-artwork	

```


I suppose you'd want to remove gnome first. Try
```
sudo apt-get --purge remove xwindow-system-core gnome-session gnome-panel gdm metacity ubuntu-artwork

```


This might also remove a number of apps that require a desktop environment so be prepared to reinstall those as well. 

```
sudo apt-get install ubuntu-desktop
```
may be enough to reinstall ubuntu core desktop apps, or it may be not. If not, you can easily add them with apt-get statements or by installing synaptic and take it from there.

---

### Post by harty83 on 2006-11-14
I had this exact same thing happen to me once.  It turned out to be a permissions problem.  I logged in via single user (rescue) and then

```
chmod o+rwx /home/YOURHOME
```

and that cleared it up for me.

---

### Post by LenzM on 2006-11-14
> **harty83 said:**
> I had this exact same thing happen to me once.  It turned out to be a permissions problem.  I logged in via single user (rescue) and then

```
chmod o+rwx /home/YOURHOME
```

and that cleared it up for me.

It should give you an error if you don't have write permissions to your home dir, not crash.  Also, what you typed above gives other users, not you, all access to your home dir which is completely unnecessary and would not fix anything.

Try starting x from a terminal by logging in and running 'startx' to see if an error message appears.

---

### Post by harty83 on 2006-11-14
> **LenzM said:**
> It should give you an error if you don't have write permissions to your home dir, not crash.  Also, what you typed above gives other users, not you, all access to your home dir which is completely unnecessary and would not fix anything.

Try starting x from a terminal by logging in and running 'startx' to see if an error message appears.

On the contrary, I did not get an error when something similar happened to me and doing what I did fixed the problem.  Here is the thread that I started when I had the problem.

[http://ubuntuforums.org/showthread.php?t=247429]("http://ubuntuforums.org/showthread.php?t=247429")

I'm not saying it will fix it because it may be obviously a different problem. As I'm reading back over the thread, I see that it is slightly a different problem.  I couldn't log in through gdm or kdm.

Just telling it how it went for me and giving a suggestion.  :D

Oh and I DID NOT MEAN o+rwx!!!  Sorry about that; yea def do not use that.  I meant u+rwx!!

---

### Post by m0ntel on 2006-11-14
i had this problem a little while ago, try deleting the file  .recently-used.xbel in your home directory.

---

### Post by ivanjs on 2006-11-14
UPDATE:
Alright. I found what I think is a solution (working for me anyway).

I searched google and came upon this blog:

[http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/#comment-66](http://linuxfud.wordpress.com/2006/09/29/ubuntu-crashes-on-start-and-returns-to-the-login-screen/#comment-66)

He suggested the following:

"Figuring something still lingered in my Gnome that caused the crach, I delete all of the Gnome related folders in my home folder (.gnome, .gnome2, .gconf, .gconfd, .metacity). This essentially reset Ubuntu to its default settings."

It totally fixed the problem for me (for now). Hope others can use this technique.
Thanks for all the suggestions!

---

### Post by Leonivek on 2006-11-14
Thanks ivanjs!  That's my blog you are linking to.  

So it is clear (and if you don't plan on reading the post) the cause of this problem for me was setting transparency on panels after installing Murrine.  Uninstalling it didn't fix the problem and the only way I could log back in was to log in to KDE and run another login window in xnest and log in to my Gnome desktop and disable transparency.

I don't have this issue anymore since I clean-installed Ubuntu 6.10, but it happened again after installing Murrine!  Removing it fixed the problem, unlike in Ubuntu 6.06.

---

### Post by ivanjs on 2006-11-15
No, thank you! I've been trying for days to fix this, and your solution worked! I'm booting consistently now in Gnome (KDE worked fine, but I prefer Gnome). Love your blog!
John

---

