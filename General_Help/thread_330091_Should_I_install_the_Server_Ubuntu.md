---
title: "Should I install the Server Ubuntu?"
date: 2007-01-02
forum: General Help
---

### Post by comfixit on 2007-01-02
I want to use a spare laptop (HP Pavillion ze100 Series) as a test Unix server. I am just looking to do some internal testing. I want the server to have MySql, PHP, Python an Apache server and some sort of FTP server.

Will the Ubuntu Server Installation with LAMP work for me?

I am guessing the MySql, PHP and Python, Apache will be installed and configured automatically, what about an FTP server, does it auto install that or do I need to download and install manually?

Should I worry about computability since the machine being used is a laptop? 

Would I be better off installing the desktop Ubuntu and installing the other items manually (assuming Desktop Ubuntu has better hardware compatibility for laptops then the server version.)?

The laptop does not have an Ethernet Port (how sad is that) so I have a Linksys USB100M which seems to be on Linux compatibility lists. Should this be plugged in as I am installing Ubuntu, or plugged in after the installation is complete?

---

### Post by Quillz on 2007-01-02
Why not try it? Is the server distribution available as a Live CD? I wish I could be more helpful, but you never know for sure how well something will work until you try it for yourself.

---

### Post by comfixit on 2007-01-02
I don't think the server is a live CD, but testing with a LIVE CD is not a bad idea, I can always try out my desktop live CD in the laptop and see how it works, if the hardware detects fine then perhaps I can feel more confident that the server install should accept all the hardware likewise.

---

### Post by pjbgravely on 2007-01-02
Ubuntu server is a command line only distro. You can install Gnome afterwards, but I'm not sure how well it will work with the special server kernel. I did the lamp install, and everything just works. I decided to install a chat program and I had it running in 2 hours after having no previous experience with web apps. 

   There is no live mode, so you won't know it it will work until you try it. A ftp client can be apt-get installed and up and running after editing some config files. 


Paul

---

### Post by koenn on 2007-01-03
> Ubuntu server is a command line only distro. You can install Gnome afterwards, but I'm not sure how well it will work with the special server kernel.
it works. 
you can install "server", then
add some X and gnome packages (panels, session, gdm etc) (I have a list somewhere ...)
then install any other app.

---

