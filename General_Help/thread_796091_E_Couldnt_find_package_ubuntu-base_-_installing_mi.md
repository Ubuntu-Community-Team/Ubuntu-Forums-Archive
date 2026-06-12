---
title: "E: Couldnt find package ubuntu-base - installing minimal gui on server"
date: 2008-05-16
forum: General Help
---

### Post by garethsimpsonuk on 2008-05-16
Hello ppl I'm trying to install a minimal gui on my gutsy home server and I get the above error after doing sudo apt-get install ubuntu-base. 
I have uncommented out all the extra sources in my sources list and have apt-get updated to. 
All other insallations seem to work fine i.e. i can do ubuntu-desktop and it installs fine (although I have prblems upgrading to hardy but thats a story for another day)
I am  using the default repositories so I assume this 1 would always be up to date and never outof sync. 

Someone please help me out! I'm very stuck. Thanks again everyone

---

### Post by garethsimpsonuk on 2008-05-16
Ok I'm bumpin this thread cos I'm back from work and would like to get my server set up tonight. Does anyone have any suggestions please. The error I get is 'E: Couldnt find package ubuntu-base' after trying sudo apt-get install ubuntu-base. 
I've tried again and it's still doing it.
While I'm here does anyone think it's worth staying with gutsy? is there a lot of problems during install because it went wrong when I tried it hence the reason I've started from fresh. 
Is it hard to update the lamp components manually also is it an update samba to. I have looked and couldn't find the info.
Thanks

---

### Post by chrisccoulson on 2008-05-16
I'm sure ubuntu-base was deprecated a few releases ago. What you need is:
```
sudo apt-get install ubuntu-minimal ubuntu-standard
```

---

### Post by garethsimpsonuk on 2008-05-16
Thanks a lot chris no wonder it isn't working! what if i just install just the minimal or vice versa? i just want the basic gui and then install my own apps. Then I will reconfigure the run levels so the gui doesn't boot up unless I tell it to. My plan is to learn how to do all this and have it finished by the end of the night!

---

### Post by chrisccoulson on 2008-05-16
You'll probably need both ubuntu-standard and ubuntu-minimal. They contain a basic set of tools for a text based system. They won't provide you a graphical environment. I'm not sure what other packages are essential for a working minimal graphical environment.

---

### Post by garethsimpsonuk on 2008-05-16
Oh so will it be a command line interface still? do you think it will be best to just get the ubuntu-desktop? i'm trying to keep it all on a 4 gb ide drive so I dont have to partition the others which are ntfs. The minmum requirements say at least 4 gb for ubuntu desktop but will I run out of space for the os?

---

### Post by chrisccoulson on 2008-05-16
You'll still need the 2 packages I mentioned even if you install ubuntu-desktop I think, as I don't think all the utilities will be pulled in.

4GB might be pushing it for a complete desktop install.

For a minimal install, you could try
```
sudo apt-get install ubuntu-standard ubuntu-minimal gnome-core xorg gdm
```
...then add bits to it as you need

---

### Post by garethsimpsonuk on 2008-05-16
I think you maybe mistaken there I've tried it and it seemed to install everything. I don't kno whether to to install the desktop or your way because Im new to nix and ont wanna run into problems later on. Ill be running it headless so I shouldn't really. dos anyone think it would be ok to install the desktop and then uninstall open office etc. will it leave loadsa redundant files?

---

### Post by garethsimpsonuk on 2008-05-16
oh come on guys im sat here refreshing cos i dont know what to do.  the blinkin cursor on my server box is getting a bit boring. shall i go ahead and install the whole desktop or will chris' way be ok. i will wanna remote connect aswell, just thought d mention that bcause im sure i read you cant do this with kde which is why i've chose gnome

---

### Post by decoherence on 2008-05-16
You have two approaches. You can either install ubuntu-desktop and start taking things out, or you can install xorg and start adding things in. For someone new to the system, it's probably easier to take things out than figure out what needs to go in, but either approach is valid and safe.

You could also try installing xubuntu-desktop, which is a lighter weight version of ubuntu-desktop.

The full ubuntu-desktop install will fit in 4GB, but feel free to add and remove things to your heart's content! That's the whole point of using a system like apt (Synaptic or Add/Remove Programs, in the GUI world.) Apt will keep you from messing things up, as long as you stick to the official repositories.

---

### Post by garethsimpsonuk on 2008-05-16
Thats brilliant mate its downloading the packages now, I will add all then remove stuff I dont use it makes more sense. I was just worried about leaving loads of redundant files behind so didn't wanna do it that way butI think Ive gotta remind myself tat this isn't windows lol. thanks a lot mate (and u chris)

---

