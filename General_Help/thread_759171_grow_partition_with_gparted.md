---
title: "grow partition with gparted"
date: 2008-04-18
forum: General Help
---

### Post by agim on 2008-04-18
I need to grow a partition toward the left. Is this possible with gparted or any other tool? I installed hardy beta on the end of my hd, and it works well enough to make it my main partition. I hope someone can help, I have the desktop in a great condition and I don't want to have to redo all of my settings.
Thanks

---

### Post by ibuclaw on 2008-04-18
Boot into the Ubuntu LiveCD, and GParted should be in the Menu named as "Partition Editor".

You can only resize or move a partition when it's unmounted. hence the LiveCD.

Though if things do go wrong...

enter this in the terminal
```
dpkg --get-selections | awk '{if ($2="install") print $1" "}' | tr -d '\n' > ~/installedpackages
```
Backup your entire "/home/" directory (Though it would be better to have it in as a separate partition).

And when you re-install, add your users, delete their folders and replace them with your backed-up ones.

Then go into the directory with the installedpackages file (the code above produces it)
And type in:
```
sudo apt-get install `cat ~/installedpackages`
```
And your system will be exactly how you left it 8)

Regards
Iain

---

### Post by agim on 2008-04-18
Wow, thats a great solution. Thanks, I really need to learn more bash scripting. Every time I see a bash solution I just can't believe how elegant it is. If you know of any good bash tutorials at the intermediate or advanced level, let me know. I am still very much a bash novice.

---

### Post by ibuclaw on 2008-04-18
BASH is just the jelly.

The more you know about the power of the Linux apps, the more elegant you can write them ;)

I'm not too sure on where a good tutorial might be. I'm not really the sort of person to learn from that stuff.

Though first site I bumped into was here:
[http://www.computer-books.us/](http://www.computer-books.us/)

The books you probably want to look at are under [Linux]("http://www.computer-books.us/linux-books.php"). And [Debian]("http://www.linux-books.us/debian.php") or [Ubuntu]("http://www.linux-books.us/ubuntu.php") will do.
Also, under the link [Linux General]("http://www.linux-books.us/linux_general.php") there is a [BASH Guide for beginners]("http://www.linux-books.us/linux_general_0001.php") too.

Though as you learn more.
You'll definately find that [Perl]("http://www.computer-books.us/perl.php") and/or [C]("http://www.computer-books.us/c.php") comes as two very helpful languages indeed.

I also use a bit of [Awk]("http://www.computer-books.us/awk.php"), and there just so happens to be a few books on that app on the page too.
So I guess the rest are just bonus points...

Regards
Iain

---

