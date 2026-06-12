---
title: "Is it possible to install software using apt to a user's ~/?"
date: 2007-12-18
forum: General Help
---

### Post by smartboyathome on 2007-12-18
I know there is a mini filesystem in each user's ~/ directory. Would it be possible to configure apt to install there instead of installing to /usr/share, /usr/local/share, /usr/bin, etc?

P.S. If you don't know about the mini filesystem, here is how it is set up. Instead of /usr/share, in your home directory, there is (you might need to create it) a ~/share directory. Also, instead of /usr/local/share, there is ~/local/share. There is even a /usr/bin directory there, in this case it is at ~/bin/. (I can't remember if these folders are hidden or not, but I am pretty sure they aren't)

---

### Post by shae on 2007-12-18
They are not all  there for me:

```

shae@shae-laptop:~$ ls -a
.                           .fontconfig        Music
..                          .fonts             Pictures
.adobe                      .fonts.conf        .profile
.bash_history               .gnupg             .qt
.bash_logout                .google            .strigi
.bashrc                     .gtk_qt_engine_rc  .sudo_as_admin_successful
.config                     .gtkrc-2.0-kde     .thumbnails
.dbus                       .ICEauthority      Ubuntulite
.DCOPserver_shae-laptop__0  .kde               .Xauthority
.DCOPserver_shae-laptop_:0  .local             .xine
Desktop                     .macromedia        .xsession-errors
.dmrc                       .mcop
Documents                   .mozilla

```

Anywho I do not think you can force deb packages to install in your user directory.  Especially because the programs they contain are not compiled to do so.

---

### Post by smartboyathome on 2007-12-18
It might be hidden then (in this case ~/.bin, and ~/.share, and ~/.local/share). Also, I don't think Ubuntu uses this concept, so I wouldn't be surprised if the folders weren't there.

---

