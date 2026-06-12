---
title: "Flash, shockwaev &amp; Java"
date: 2005-10-15
forum: General Help
---

### Post by ubuntu27 on 2005-10-15
HI Guys! I been online in this forums for more than two hours trying to figure out how to install Flash for my Firefox. NO luck at all, I've even followed the instruction on the ["Restricted Formats"](https://wiki.ubuntu.com/RestrictedFormats)

Can someone guide me step by step on how to enable Flash, Shockwave and Java?

Thank you in advance !! ^.^

---

### Post by aclaunch on 2005-10-15
FWIW, I had no problem with using the instructions in "Restricted Formats". But you can also go to the Macromedia Flash download page and follow the instructions (basically install Flash and copy the plugins to the /usr/lib/mozilla-firefox/plugins directory).

Good Luck,
Alan

---

### Post by ToastedToad on 2005-10-15
As far as I know, Shockwave is not available for linux at all.

---

### Post by Syphin on 2005-10-15
For firefox and java i did this:
First make sure you have deb "http://us.archive.ubuntu.com/ubuntu/ breezy multiverse" in your sources.list file

Then type this in the terminal for Flash:
sudo apt-get update
sudo apt-get install flashplayer-mozilla

That should be all for flash to work in mozilla, now for Java:
fist download the version you want from [Here]("http://java.sun.com/j2se/1.5.0/download.jsp") (get the Linux Self-extracting file)

Then in terminal go to the directory you saved your file in and type (replace the file names with the one you downloaded):
sudo apt-get install fakeroot java-package java-common
fakeroot make-jpkg jre-1_5_0_05-linux-i586.bin
sudo dpkg -i sun-j2re1.5_1.5.0+update05_i386.deb

Now its installed, But before you close the terminal type:
sudo update-alternatives --config java

And select the newly installed java for default.

There are a cpl other methods in the HowTo section for installing java also, if you want to try them instead. As for shockwave, dont know.

---

### Post by WW on 2005-10-15
For flash: I tried flashplayer-mozilla first, and on the first flash site that I tested, I didn't get any sound.  So I replaced it with flashplugin-nonfree, and sound worked.  Both are in the multiverse repository.

---

### Post by ubuntu27 on 2005-10-15
Thank you guys for the replay.

I got the following error when I tried to add deb "http://us.archive.ubuntu.com/ubuntu/ breezy multiverse" in the repository.

[[IMG]http://img411.imageshack.us/img411/1921/screenshotsynaptic16ao.th.png[/IMG]](http://img411.imageshack.us/my.php?image=screenshotsynaptic16ao.png)

And when I didn't add the deb "http://us.archive.ubuntu.com/ubuntu/ breezy multiverse" or when I removed it after having the previous error, I get this:

[[IMG]http://img430.imageshack.us/img430/3102/screenshotsynaptic6ei.th.png[/IMG]](http://img430.imageshack.us/my.php?image=screenshotsynaptic6ei.png)

[[IMG]http://img430.imageshack.us/img430/4544/screenshotwarning7oo.th.png[/IMG]](http://img430.imageshack.us/my.php?image=screenshotwarning7oo.png)

---

### Post by WW on 2005-10-15
Your images are too small to read!

For universe and multiverse, you don't have to edit sources.list manully. Start Synaptic, and use Setting->Repositories. Then click on "+Add", and check the appropriate components.

---

### Post by Syphin on 2005-10-15
im sorry, i quoted the wrong part of the deb :P

supposed to be:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse

sry bout that ><


And the second 2 errors, its because the backport repo's arnt up yet i believe.

---

### Post by ubuntu27 on 2005-10-15
[QUOTE=WW]Your images are too small to read!

For universe and multiverse, you don't have to edit sources.list manully. Start Synaptic, and use Setting->Repositories. Then click on "+Add", and check the appropriate components.[/QUOTE]

It is a thumbnail image. Click on it and it will be open anew tab or a new window with the bigger pic :) The reason I used a thumbnail instead of the whole pic is because I didn't want to make traffic on this wonderful site.

[QUOTE=Syphin]im sorry, i quoted the wrong part of the deb :P

supposed to be:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy multiverse

sry bout that ><


And the second 2 errors, its because the backport repo's arnt up yet i believe.[/QUOTE]

ahh... ok, thank you Syphin. Now it dosn't give me error #1 in my previous post :P


Oh!! I see :D haha. Now it explains why I have so many errors for the Repositories...

---

