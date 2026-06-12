---
title: "Customize tty colors...."
date: 2018-12-12
forum: General Help
---

### Post by Furycd001 on 2018-12-12
HI Guys.. How would I go about converting ["this"]("https://paste.ubuntu.com/p/7SVBmKzbgT/") xresources color scheme to work with a tty ?? I use tty1 a lot and would like to have it match my xfce4-terminal & xterm colors. Many thanks in advanced for replying & helping....

---

### Post by NM5TF on 2018-12-12
@Jonny6...

if you are talking about changing the default colors in terminal, you can edit the 
preferences to use whatever you like...or add a background image....screenie
attached showing what I use....

or maybe I misunderstood what you meant....

tommy

---

### Post by Furycd001 on 2018-12-12
I think you have misunderstood. What I want is to change the colors within a **"TTY"** to match the color scheme in my gui terminal. I'm pretty sure that I have seen it done before. I just don't know how to do it myself....

---

### Post by NM5TF on 2018-12-12
simple search found this.....have NOT tried it myself.....

add this to your ~/.bashrc file....change colors as needed....

```
if [ "$TERM" = "linux" ]; then
    echo -en "\e]P0222222" #black
    echo -en "\e]P8222222" #darkgrey
    echo -en "\e]P1803232" #darkred
    echo -en "\e]P9982b2b" #red
    echo -en "\e]P25b762f" #darkgreen
    echo -en "\e]PA89b83f" #green
    echo -en "\e]P3aa9943" #brown
    echo -en "\e]PBefef60" #yellow
    echo -en "\e]P4324c80" #darkblue
    echo -en "\e]PC2b4f98" #blue
    echo -en "\e]P5706c9a" #darkmagenta
    echo -en "\e]PD826ab1" #magenta
    echo -en "\e]P692b19e" #darkcyan
    echo -en "\e]PEa1cdcd" #cyan
    echo -en "\e]P7ffffff" #lightgrey
    echo -en "\e]PFdedede" #white
    clear #for background artifacting
fi
```

found here [http://archive.is/QSYHd]("http://archive.is/QSYHd")

tommy

---

### Post by Furycd001 on 2018-12-12
> **NM5TF said:**
> simple search found this.....have NOT tried it myself.....

add this to your ~/.bashrc file....change colors as needed....

```
if [ "$TERM" = "linux" ]; then
    echo -en "\e]P0222222" #black
    echo -en "\e]P8222222" #darkgrey
    echo -en "\e]P1803232" #darkred
    echo -en "\e]P9982b2b" #red
    echo -en "\e]P25b762f" #darkgreen
    echo -en "\e]PA89b83f" #green
    echo -en "\e]P3aa9943" #brown
    echo -en "\e]PBefef60" #yellow
    echo -en "\e]P4324c80" #darkblue
    echo -en "\e]PC2b4f98" #blue
    echo -en "\e]P5706c9a" #darkmagenta
    echo -en "\e]PD826ab1" #magenta
    echo -en "\e]P692b19e" #darkcyan
    echo -en "\e]PEa1cdcd" #cyan
    echo -en "\e]P7ffffff" #lightgrey
    echo -en "\e]PFdedede" #white
    clear #for background artifacting
fi
```

found here [http://archive.is/QSYHd](http://archive.is/QSYHd)

tommy

Nice find dude. That's actually where I''d seen it done before ^^* Gona go give it a try. Thanks again dude....

---

### Post by Furycd001 on 2018-12-12
Ok ok.. Soooo I just tried what was on the link above and I don't think it worked. I added the code and changed the colors, yet the colors in the tty still look the same and have not changed. Any ideas ??

---

### Post by NM5TF on 2018-12-12
did you reboot after ???

---

### Post by Furycd001 on 2018-12-12
> **NM5TF said:**
> did you reboot after ???

Yep I rebooted and then checked. Here's a copy of what I put at the bottom of my .bashrc file....

```

if [ "$TERM" = "linux" ]; then
    echo -en "\e]P282828"
    echo -en "\e]Pca1444"
    echo -en "\e]P789aba"
    echo -en "\e]Pb3879f"
    echo -en "\e]P94469b"
    echo -en "\e]Pcb6fa1"
    echo -en "\e]Pfb6e93"
    echo -en "\e]Pcf98c1"
    echo -en "\e]P98218e"
    echo -en "\e]Pcb515d"
    echo -en "\e]P5a87b1"
    echo -en "\e]P9c61ab"
    echo -en "\e]P9a77b1"
    echo -en "\e]Pf2a297"
    echo -en "\e]Pf4436f"
    echo -en "\e]Pebdbb2"
    echo -en "\e]Pf2f2f2"
    clear #for background artifacting
fi

```

---

### Post by The Cog on 2018-12-12
No need to reboot. I tried one of the commands (echo -en "\e]P0222222") in my tty and it kinda worked. It changed the background colour, the foreground stayed white.
This changes the normal foreground (colour 7) from lightgray to a kind of orangey-brown: **echo -en "\e]P7dd7733"**
So I put all the above (except for the if and fi lines) in a text file and sourced it in bash, and it changed the foreground to bright white.

So the script works on my Xubuntu 18.04. 

Hmm. Why am I not on 18.10???

---

### Post by again? on 2018-12-12
Do you have a ~/.bash_profile file?
If you have a ~/.bash_profile, tty will read that first I think.

---

### Post by Furycd001 on 2018-12-12
> **The Cog said:**
> No need to reboot. I tried one of the commands (echo -en "\e]P0222222") in my tty and it kinda worked. It changed the background colour, the foreground stayed white.
This changes the normal foreground (colour 7" from lightgray to a kind of orangey-brown: **echo -en "\e]P7dd7733"**
So I put all the above (except for the if and fi lines) in a text file and sourced it in bash, and it changed the fireground to bright white.

So the script works on my Xubuntu 18.04. 

Hmm. Why am I not on 18.10???

Thank you very much for checking & for adding some detail ^^* [Here is two screenshots]("https://imgur.com/a/YgvUjIK") showing what both sets of colors look like. I'm a tad confused so sorry in advanced if I I'm stupid in any way....

---

### Post by Furycd001 on 2018-12-12
> **guber2 said:**
> Do you have a ~/.bash_profile file?
If you have a ~/.bash_profile, tty will read that first I think.

In my home folder I have..


[LIST]
[*].bash_history
[*].bash_logout
[*].bashrc
[*].bashrc
[/LIST]

I can see no ~/.bash_profile....

---

### Post by Holger_Gehrke on 2018-12-12
.bashrc is for interactive non-login shells. login-shells don't read it unless .profile or .bash_profile tells them to (which the ~/.profile in Ubuntu does by default, I think).

Instead of using unreadable (and probably not portable) escape sequences, you might want to take a look at the program tput and the manual for terminfo to get the names and possible values of terminal capabilities to use with tput. For example:
```

tput colors # outputs the number of colours the terminal can use (8 on the console of my machine, numbered 0 to 7)
tput set_ab 0 # set background to colour 0
tput set_af 7 # set foreground to colour 7
tput initc 0 1000 0 0 # initialize colour 0 to a bright red (rgb, components from 0 to 1000)

```

Holger

---

### Post by Furycd001 on 2018-12-13
> **Holger_Gehrke said:**
> .bashrc is for interactive non-login shells. login-shells don't read it unless .profile or .bash_profile tells them to (which the ~/.profile in Ubuntu does by default, I think).

Instead of using unreadable (and probably not portable) escape sequences, you might want to take a look at the program tput and the manual for terminfo to get the names and possible values of terminal capabilities to use with tput. For example:
```

tput colors # outputs the number of colours the terminal can use (8 on the console of my machine, numbered 0 to 7)
tput set_ab 0 # set background to colour 0
tput set_af 7 # set foreground to colour 7
tput initc 0 1000 0 0 # initialize colour 0 to a bright red (rgb, components from 0 to 1000)

```

Holger

Thanks for the suggestion & for going into some detail. Going to look into this now....

---

### Post by Furycd001 on 2018-12-13
After some research I have found that this can be accomplished, but it is not easy & would take a fair amount of time / work. Marking this thread as solved....

---

