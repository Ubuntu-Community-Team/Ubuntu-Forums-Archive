---
title: "evoltution mail notifier?"
date: 2005-06-20
forum: General Help
---

### Post by byen on 2005-06-20
hey guys ..Is there a plug-in/ tool where an animation or a window pops up when i get a new mail on my evolution? or may be somethin on my taskbar? I just dont know when a mail comes. Evo just sits there.. any suggs??
thanks.

---

### Post by RikoW on 2005-06-21
Hi,

I use gnubiff for that kind of notifying. It's a mail notifier, which runs in your panel and is independent of the mail program you are using. You just configure the mailboxes (more than 1 if you like) you what to monitor and there you go. 

Cheers,

             Riko

---

### Post by Majlo on 2005-06-21
I use evonotify and work perfect for me

Home Page [http://www.grawert.net/software/evonotify/](http://www.grawert.net/software/evonotify/)

---

### Post by byen on 2005-06-21
[QUOTE=Majlo]I use evonotify and work perfect for me

Home Page [http://www.grawert.net/software/evonotify/](http://www.grawert.net/software/evonotify/)[/QUOTE]
 thank you majlo and riko for your response. gnubiff is a great program and i like it..but since my desktop is really cluttered with all the fancy applications ;-) i thought id give evonotify...i really do not know much about installing from tar files... i tried doing 
 #tar xvzf package.tar.gz (or tar xvjf package.tar.bz2)
# cd package
# ./configure
# make
# make install

but i keep getting various errors during configure...any suggestions?

---

### Post by chz on 2005-06-21
the errors usually correspond to dependencies...what's the error message saying..?

---

### Post by byen on 2005-06-22
[QUOTE=chz]the errors usually correspond to dependencies...what's the error message saying..?[/QUOTE]
 ok..here is what i did..chz
byen@ubuntu:~$ tar xvzf evonotify-0.2.4.tar.gz
evonotify-0.2.4/about.png
evonotify-0.2.4/remove-1.0.sh
evonotify-0.2.4/notify_ani.gif
evonotify-0.2.4/changelog
evonotify-0.2.4/setup.png
evonotify-0.2.4/copyright
evonotify-0.2.4/setup
evonotify-0.2.4/notify.png
evonotify-0.2.4/evonotify
evonotify-0.2.4/README
byen@ubuntu:~$ cd evonotify-0.2.4
byen@ubuntu:~/evonotify-0.2.4$ ./configure
bash: ./configure: No such file or directory
byen@ubuntu:~/evonotify-0.2.4$
byen@ubuntu:~/evonotify-0.2.4$ make
make: *** No targets specified and no makefile found.  Stop.
byen@ubuntu:~/evonotify-0.2.4$ make install
make: *** No rule to make target `install'.  Stop.
byen@ubuntu:~/evonotify-0.2.4$





i never did this be4 so sorry if this looks stupid...thanks.

---

### Post by RikoW on 2005-06-22
Hi byen,

no wonder you get error messages, there is neither a configure script nor a makefile in the evonotify.tar.gz. I suspect, that setup is doing what you want to do. I assume you checked the README file, which should tell you how to install it.

I don't use evonotify, so have no experience with installing it, but from the list of files that were unpacked for the tar.gz archive, the above would be my approach.

Good luck, :)
            Riko

[QUOTE=byen]ok..here is what i did..chz
byen@ubuntu:~$ tar xvzf evonotify-0.2.4.tar.gz
evonotify-0.2.4/about.png
evonotify-0.2.4/remove-1.0.sh
evonotify-0.2.4/notify_ani.gif
evonotify-0.2.4/changelog
evonotify-0.2.4/setup.png
evonotify-0.2.4/copyright
evonotify-0.2.4/setup
evonotify-0.2.4/notify.png
evonotify-0.2.4/evonotify
evonotify-0.2.4/README
byen@ubuntu:~$ cd evonotify-0.2.4
byen@ubuntu:~/evonotify-0.2.4$ ./configure
bash: ./configure: No such file or directory
byen@ubuntu:~/evonotify-0.2.4$
byen@ubuntu:~/evonotify-0.2.4$ make
make: *** No targets specified and no makefile found.  Stop.
byen@ubuntu:~/evonotify-0.2.4$ make install
make: *** No rule to make target `install'.  Stop.
byen@ubuntu:~/evonotify-0.2.4$





i never did this be4 so sorry if this looks stupid...thanks.[/QUOTE]

---

### Post by Majlo on 2005-06-22
Hi 

First install missing dependecies

sudo apt-get install libgtk2-trayicon-perl libgnome2-wnck-perl libgnome2-perl

Then 

tar xvzf evonotify-0.2.4.tar.gz
cd cd evonotify-0.2.4
./setup

The setup script will copy the files to the appropriate places and set up the evolution filter for you.This will execute evonotify everytime new mail arrives.

---

### Post by BinaryDigit on 2005-10-09
[quote=RikoW]Hi,

I use gnubiff for that kind of notifying. It's a mail notifier, which runs in your panel and is independent of the mail program you are using. You just configure the mailboxes (more than 1 if you like) you what to monitor and there you go. 

Cheers,

             Riko[/quote] 
This is excellent, been looking for something like this...thank you!! :)
BTW I am running Breezy 64 bit in Gnome, for others who are running the same.

---

### Post by vinodis on 2006-08-04
Thank you very much!

---

