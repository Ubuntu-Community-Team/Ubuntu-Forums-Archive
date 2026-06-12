---
title: "KMFL and SCIM not working and worse...Chaos!!!"
date: 2007-05-31
forum: General Help
---

### Post by balshan on 2007-05-31
This is my first go with SCIM and KMFL as I've just switched back to Linux
after a 3-year hiatus! I've sunk more than 8 hours now into configuring
this and it caused a system crash, so I'm at my wits' end.

I followed the (albeit old) installation instructions from kmfl.sourceforge.net and set
up SCIM. I used the Feisty repositories to find it, and wound up with
v1.4.4 of all the important files (but 0.9.4 of scim-qtimm).
I then created ~/.bash_profile as directed. Later on I found I needed
quotes to set GTK_IM_MODULE and XMODIFIERS and added them. Feisty already
uses the correct locale.

Here's where problem 1 occurs: Nothing can get SCIM to start on login. I
created the startscim file and tried putting it in /bin, /usr/bin, and
~/bin (the last one was the one recommended). None of them work. No
SCIM-related processes are running when I log in.

Then, the next problem. I can run scim -d in bash to kick SCIM to life, but
there's no icon in the system tray for me to use to configure KMFL. I've
explored man scim and the available options under scim -l plenty and
haven't found any way to configure SCIM to use the KMFL imengine.

And here's the last, most awful problem. Through some weird configuration
tricks I managed to get scim_kmfl_imengine installed. But it wouldn't work,
because it was a Dapper package, and it was 0.9.5 while the rest of the
KMFL files as noted above were 0.9.4, so there was some sort of compatibility
issue. (Of course I wouldn't have known if it HAD worked because it
wouldn't show up in the scim -l options or in the system tray.) So I went
through all my SCIM and KMFL files and reinstalled them, but
scim_kmfl_imengine would not reinstall because it is not in any Ubuntu
repository. So I went to sourceforge and found the 0.9.4 version of
scim_kmfl_imengine. And tried to install it using the directions in the
package. It would respond to ./configure but not to make or make check or
make install. And this is where my machine started freaking out and going
crazy. I'm not sure exactly what happened, but basically System Monitor,
GNOME and Nautilus all crashed, leaving me with a blank X window and X
cursor and no OS.

Oh yeah and one more thing: even when SCIM is up and running, it only
interfaces with GEdit, not with OpenOffice.

I'm a field linguist, and make a lot of use of IPA characters in
particular, and it's worth my while to put time and effort into making this
work, but I've put in a bunch already, and I'm just messing things up, I'm
sure!

PS: When is 1.0 coming out? Thought that should have been last year!

---

### Post by Vajra Vrtti on 2007-06-18
I'm also trying to install SCIM+KMFL. SCIM was already installed and after following the instructions in [http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu](http://www.scim-im.org/wiki/documentation/installation_and_configuration/ubuntu_kubuntu) it seems to be working OK. The required package **scim-kmfl-imengine** is missing from the Feisty repositories and I was unable to compile it. I reported this in [https://bugs.launchpad.net/ubuntu/+bug/120937](https://bugs.launchpad.net/ubuntu/+bug/120937).

---

### Post by Jara on 2007-09-19
There are some recent instructions on [http://linux.lsdev.sil.org/wiki/index.php/Installing_KMFL_on_debian#Tweaking_the_scim-kmfl-engine_package](http://linux.lsdev.sil.org/wiki/index.php/Installing_KMFL_on_debian#Tweaking_the_scim-kmfl-engine_package).
I followed the guide lucky enough to find my SCIM installed in my Xubuntu Feisty Fawn Linux in the end, even with the KMFL plugin integrated. You are supposed to add a new SIL repository into your source list (see the guide). The trouble is that even with all that stuff installed I still cannot get any single KMN file working. If anyone happens to know how to persuady the KMFL to read them, I will be happy to know either. Anyway, despite the trouble, it seems to me that the procedure described in the above link could be the right one, moreover both safe and simple, leaving system in peace and requiring no expert knowledge.
Well, but what is wrong with the KMN files? I changed the BITMAP declaration, so that it does not hint at any Windows path any more but still the KMFl fails to read them. I am new to Linux, so the trouble may be quite trivial.

---

### Post by Jara on 2007-09-19
After some struggle, I have come to make the KMFL work with the KMN files formerly compiled in Windows. In fact, I cannot say how it happened that the KMFL did not want to read them. I did not change a letter in the code, just copied the content to another file, section by section, trying continually if the compiler could digest it. The problem must have lied in wrong coding of some characters, which was exactly what I could see at the end of one of the KMN files. As I got to the last line, it became obvious that the KMFL cannot read it. I deleted the line, typed the same characters (in a Linux text editor), saved and tried to load. Now it worked. I would not believe but it is true.

---

### Post by aethralis on 2007-11-28
There is a good guide here ([http://www.tedcarnahan.com/2007/11/09/koine-greek-in-ubuntu-gutsy-gibbon/](http://www.tedcarnahan.com/2007/11/09/koine-greek-in-ubuntu-gutsy-gibbon/)), but just in case I'll repost it here. It worked for me without any problems.

1. Make sure you have scim installed
2. Add this repository to your apt sources: deb [http://packages.sil.org/ubuntu](http://packages.sil.org/ubuntu) gutsy main
3. ```
sudo aptitude update
```
4. ```
sudo aptitude install scim-kmfl-imengine kmflcomp
```
5. Download [scim-greek-koine.tar.gz]("http://www.tedcarnahan.com/wp-content/uploads/2007/11/scim-greek-koine.tar.gz").
6. Extract the tarfile and compile the kmfl file by running ```
kmflcomp GrkPolyComp.KMN
```
7. Run ```
scim-setup
```, click on the new &#8220;KMFL&#8221; option, click install, browse to the GrkPolyComp.kmfl file you just compiled.

(Instructions by [Ted Carnahan]("http://www.tedcarnahan.com/"))

_____
Edit: Step 6. is (I'm told) optional. Seems that kmfl will load uncompiled kmn files just fine so there is no need to compile the keyboard beforehand.

---

### Post by Jara on 2007-12-02
Thanks for the tip. I tried to make use of the polytonic keyboard but there seems to be a problem with my local settings to the effect that the diacritical marks do not work properly. In fact, I got used to typing via a Greek keyboard of my own fabrication, so I would stick to it further on rather than learning new habits. But again there is the trouble with the local settings. The key codes supposed to be recognized by KMFL as they normally are by Keyman return in some cases (quotes etc.) wrong characters. I was trying to turn on and off the mnemonic layout in the preamble of the KMN file, changing the keyboard layouts in SCIM, varying the input code in KMN, incl. the key constants, all in vain. Do you, or does anybody else, have some suggestion what could be the mistake? Isn't is that the KMFL should be fine with all non-English platforms? Especially the deadkeys in my Czech keyboard setting resist any change and address. Even if I redefine them by applying the [K_EQUAL] etc. constants, as recommended in such cases, they do not work. They are just "mute".

---

### Post by aethralis on 2007-12-04
Hmm.. can't help you much further on this one, as I'm just following the instructions (quite blindly) myself. But the default locale I use is Estonian and I have had no problems with diacritics... I disabled all other keyboards and left only Greek, so I have only two choices Greek and English. I understand that the "English" is in reality "default", or so it at least works.

---

### Post by simosx on 2008-03-16
Does this help you,

[http://ubuntuforums.org/showpost.php?p=4525603&postcount=7](http://ubuntuforums.org/showpost.php?p=4525603&postcount=7)

---

