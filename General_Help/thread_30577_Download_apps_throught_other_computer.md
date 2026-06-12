---
title: "Download apps throught other computer?"
date: 2005-04-29
forum: General Help
---

### Post by ultima2k on 2005-04-29
Well, the thing is like this.
I only got 56k internet connection (can't get any better) and then got a modem that wont work in ubuntu :(

To continue using I wanna install XMMS, the codec stuff, updates, libraries and much more. Ofcourse you can just download the programs yourself and install, but I want it to automaticly get all required libraries, add to program-menues and so on.

My question is if I can sort of just download those installers on my school-laptop and then install them at home?


Really want to have any use of ubuntu :S

EDIT: and I don't have money to buy an external modem (those works with ubuntu, right?).

---

### Post by tonym on 2005-04-29
Not quite sure if this is what you were looking for.

If you can identify the packages you want,  including dependencies,  via aptitude say,  you can then download the individual .deb files from [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/) to your school machine.

These can then be installed by dpkg -i foo.deb.  This will set up menus etc just as if installed via aptitude or synaptic.

Regards

Tony

---

### Post by ultima2k on 2005-04-29
Ok, thats nice.
Which of these should I use with Hoary[i386]?
[http://archive.ubuntu.com/ubuntu/pool/main/x/xmms/](http://archive.ubuntu.com/ubuntu/pool/main/x/xmms/)

EDIT: could you also give me some links to some package that's good to have?
Cheers! :D

---

### Post by ultima2k on 2005-04-29
I downloaded xmms ([this one](http://archive.ubuntu.com/ubuntu/pool/main/x/xmms/xmms_1.2.10-2ubuntu1_i386.deb)) and ran "dpkg -i bla.deb".
It then said it needed libglib and libgtk. Downloaded them from the ubuntu-archives too.
When I tryed installing libgtk it says it needs libglib, so I continued with glib then. Now it says it needs libc6 which I can't find among the lib-archives.

So what do I do now? Is it just me or does it seems that you need libblabla to install libhello to be able to install libbooring and so on til' you got a single program installed? :S:(

---

### Post by mrbass on 2005-04-29
You don't say..hehe
[http://ubuntuforums.org/showthread.php?t=30187](http://ubuntuforums.org/showthread.php?t=30187)

---

### Post by ultima2k on 2005-04-29
Thanks for the link, too bad I wont get to school until monday  :(

---

### Post by ultima2k on 2005-05-02
Well, I finally got the Ubuntu addon downloaded at school.
Installed the apps I wanted, XMMS and mplayer worked perfect, really felt how much more fun Ubuntu would be now that I have at least som music.

Went training table tennis(:p) a few hours and when I got home I installed Gkrellm, worked perfect too. Well, the fun stopped here. Of some reason XMMS hangs up if I try to play anything and the same with mplayer. Have tryed reinstalling it, but the same shit all the time :(

What the h**l could be the problem? And is there a possibility that Gkrellm messed it up? :S

---

### Post by dewey on 2005-05-02
Linux doesn't play well with many internal modems because, many of them are WIN modems, cheaper versions.  They offload all the work onto the computer, and rely on windows to handle everything for it, making them extremely platform dependent, but cheap to manufacture.  There are ways to get it running, but it's a hassle.  Standard internal modems often work fine with linux though, and so will external.

---

### Post by Xerampelinae on 2005-05-02
[QUOTE=ultima2k]Well, I finally got the Ubuntu addon downloaded at school.
Installed the apps I wanted, XMMS and mplayer worked perfect, really felt how much more fun Ubuntu would be now that I have at least som music.

Went training table tennis(:p) a few hours and when I got home I installed Gkrellm, worked perfect too. Well, the fun stopped here. Of some reason XMMS hangs up if I try to play anything and the same with mplayer. Have tryed reinstalling it, but the same shit all the time :(

What the h**l could be the problem? And is there a possibility that Gkrellm messed it up? :S[/QUOTE]
 Hi, you should tell XMMS to use the enlightenment sound daemon as its output (often called esound or esd).  The reason it is hanging is most likely because it is waiting for the sound device to become free, but esd is using it.

Alternatively, you could go to system -> preferences -> sound and uncheck enable sound server set up.

Alternatively, the best way (but also the most work) is to set up alsa with dmix, as shown here: [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

---

### Post by ultima2k on 2005-05-03
[QUOTE=dewey]Linux doesn't play well with many internal modems because, many of them are WIN modems, cheaper versions.  They offload all the work onto the computer, and rely on windows to handle everything for it, making them extremely platform dependent, but cheap to manufacture.  There are ways to get it running, but it's a hassle.  Standard internal modems often work fine with linux though, and so will external.[/QUOTE]
I don't think you have read the whole thread...

[QUOTE=Xerampelinae]Hi, you should tell XMMS to use the enlightenment sound daemon as its output (often called esound or esd).  The reason it is hanging is most likely because it is waiting for the sound device to become free, but esd is using it.

Alternatively, you could go to system -> preferences -> sound and uncheck enable sound server set up.

Alternatively, the best way (but also the most work) is to set up alsa with dmix, as shown here: [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)[/QUOTE]
Oh, thanks :)
Gonna try it when I get home, really hope it works.

---

### Post by ultima2k on 2005-05-03
Changet XMMS's outout-plugin to the other one and it works now :D
It was the same shit with Mplayer, had to change the audio-plugin or it wouldn't start. Well, now it works anyway, thanks so much Xerampelinae :)

---

