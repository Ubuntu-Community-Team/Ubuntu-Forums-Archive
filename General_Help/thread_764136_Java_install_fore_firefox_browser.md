---
title: "Java install fore firefox browser"
date: 2008-04-23
forum: General Help
---

### Post by 72da9 on 2008-04-23
Why is this not made more simple.  I am unable to install java into my firefox browser because ubuntu will not accept my administer password.

I followed the instructions on the java download page.  I opened the terminal and typed "su".  Then it asks for the administer password so I type mine in and nothing.  Why would they not make a self installing application like everything else in ubuntu.  So is there a section here or at Sun Microsystems explaining how to install java into your browser or do I not use java.

It's these unneccassary little quirks that keep people away from linux as an operating system.  Self installing and uninstalling apps are the way to go without using a terminal window.  I did dos once.  I do not need to go back to command line installations.

I do however like ubuntu and believe it is the most promising of all the linux installations to go mainstream and user friendly.  90% of it seems to be self efficient now without a need for complex linux or unix knowledge.

I do appreciate any help in my java installation problems.  Faqs, help menus, or forum conversations on the subject will also help.

Next step is to takle wine.  Which I could install but not run at all.  I did find a forum on this I can look through.  I'll start there for that.  Now, I'm just concerned on the Java applet install for the browser.

---

### Post by y-lee on 2008-04-23
You should use sudo instead of su in ubuntu. Root account is by default locked & closed in Ubuntu for security reasons. Unless you set one Ubuntu has no root password. You should use sudo instead and note that sudo requires your own (normal user) password, not the root password. 

See [[COLOR="RoyalBlue"]_Root Sudo_[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

For instructions on installing java see [[COLOR="RoyalBlue"]_Java community docs_[/COLOR]]("https://help.ubuntu.com/community/Java").

> I followed the instructions on the java download page. I opened the terminal and typed "su". Then it asks for the administer password so I type mine in and nothing. Why would they not make a self installing application like everything else in ubuntu.

Programs are easy to install in Ubuntu, add and remove programs and or synaptic make it much easier than windows. Compiling programs can be tricky sometimes BUT for the record you can compile programs in windows or any other operating system I know of. Most windows users don't install programs that way but it doesn't mean it can't be done or it is not done.

> It's these unneccassary little quirks that keep people away from linux as an operating system. Self installing and uninstalling apps are the way to go without using a terminal window. I did dos once. I do not need to go back to command line installations.

This is not a quirk this is you being new to the Operating system. Give it a chance and learn how to use it and you will find why people often say it is a superior operating system. :)

---

### Post by 72da9 on 2008-04-23
Well, thank you for the info and link to some help.  Unfortunately for users like myself.  This does nothing to install the java on my machine.  There has to be some information somewhere that correctly shows how to install this java.  My version is the new jre-6u5-linux-i586.bin.

This info does not regard ubuntu.  [http://www.java.com/en/download/help/5000010500.xml#selfextracting](http://www.java.com/en/download/help/5000010500.xml#selfextracting)

This info "sudo apt-get install sun-java5-bin" worked until I got to the user agreement and hit enter for the ok to continue and nothing happened.  The terminal just sat at the end user agreement.

Then I changed it to this "sudo apt-get install sun-java6-bin" and got the response for this "sudo dpkg --configure -a".

After some more stuff happened that was it.  So I'm at a lost for the correct method of installing java.

---

### Post by jocko on 2008-04-24
> **72da9 said:**
> This info "sudo apt-get install sun-java5-bin" worked until I got to the user agreement and hit enter for the ok to continue and nothing happened.  The terminal just sat at the end user agreement.
Do you mean you could not accept the agreement?
Sometimes you need to scroll to the end of the agreement before you can proceed (they do this because they think people actually would read the agreement this way).


> **72da9 said:**
> Then I changed it to this "sudo apt-get install sun-java6-bin" and got the response for this "sudo dpkg --configure -a".

After some more stuff happened that was it.  So I'm at a lost for the correct method of installing java.
The "sudo dpkg --configure -a" part is because you forced apt to quit during your installation of java 5, if you run it, the install will continue.
If you open up synaptic and search for "sun-java5-bin" and "sun-java6-bin", are they marked as installed? If they are, then you already have installed it.
If not, use synaptic to install them. There's no reason for you to download the installer from sun's homepage.

If you want it to be even simpler: use synaptic to install the package "ubuntu-restricted-extras". It will get java, flash, ms fonts and restricted multimedia codecs.

---

