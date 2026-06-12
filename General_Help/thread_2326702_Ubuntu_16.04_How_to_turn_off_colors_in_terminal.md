---
title: "Ubuntu 16.04: How to turn off colors in terminal?"
date: 2016-06-03
forum: General Help
---

### Post by abcuser on 2016-06-03
Hi,
I have been using Ubuntu 14.04 for couple of years, great system. Today I have fresh installed Ubuntu 16.04 and the first think I would like to do is turn of this coloring in Terminal:
a) turn off green color user@computername
b) turn of color when using "sudo apt update" or "sudo apt install"

How to turn of this colors?
Thanks

---

### Post by sudodus on 2016-06-03
I like the colours (I had them before they trickled down to the default). I have activated colours by a setting in the bash configuration file **~/.bashrc**, so that should also be the place to turn it off.

Please come back, if you don't find it, and I will look deeper into the details in a standard system (that is not tweaked by me).

---

### Post by ajgreeny on 2016-06-03
Open up the hidden .bashrc file in your home and comment out (add a # to the start of the line) all lines relating to colour in that file.

Save a copy first just in case it all goes wrong so you can restore the original if necessary.

I like a colour prompt and output in my terminal so have never tried this but the main one for the prompt is shown below (line 43 in my file but may be different line in yours.)

Line to comment out to stop colour prompt:-
**force_color_prompt=yes**
so it becomes
**#force_color_prompt=yes**

---

### Post by abcuser on 2016-06-04
I don't want to turn off colours completely. I like having them on grep and similar, just don't like to have green prompt.

@ajgreeny, at my .bashrc the setting [FONT=Courier New]force_color_prompt=yes[/FONT] is commented out by default, so this can't be a solution.

I figured out that commenting out the following lines:
```

case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
esac

```
or in above command change [FONT=Courier New]color_prompt=yes[/FONT] to [FONT=Courier New]color_prompt=no[/FONT] disables green prompt.

That is for my first post a) question, still looking solution for b) question.

---

### Post by sudodus on 2016-06-04
Maybe because we don't know the answer for the b) question.

I use apt-get (not apt) and I have no particular colours (only the default of the terminal window).

---

### Post by howefield on 2016-06-04
Have you tried playing with the terminal preferences ? Edit > Preferences > Colour tab

Solarized dark for "Text and Background Colour and Solarized for "Palette" is pretty good.

---

### Post by steeldriver on 2016-06-04
Well the apt manpage says

```

DIFFERENCES TO APT-GET(8)
.
.
.
       ·   The option APT::Color is enabled.

```
so likely that's what you need to change - try adding
```

-o Apt::Color=0

```
or
```

-o Apt::Color=no

```
to your apt command(s) - if that works, you could look at adding it to your /apt.conf.d/

---

### Post by abcuser on 2016-06-05
@steeldriver, this is great it works fine from command. I tried this:
```

sudo apt update -o Apt::Color=0

```
and colors disappeared. Excellent.

Now I tried to save this in config file. So I created file: /etc/apt/apt.conf.d/99progressbar and tried to do the reverse of [http://askubuntu.com/questions/445245/how-do-i-enable-fancy-apt-colours-and-progress-bars](http://askubuntu.com/questions/445245/how-do-i-enable-fancy-apt-colours-and-progress-bars) so in file I wrote just one command:
```

APT::Color "0";

```
and executed command: sudo apt update
but colors are still displayed. I even tried to logoff from Ubuntu, not success.

Any idea how to add this setting to config file?

---

### Post by sudodus on 2016-06-05
One solution is to use an alias:

```
alias sapt='sudo apt -o Apt::Color=0'
```

Test it and if it works, you can add it near the other aliases in **.bashrc**

Then you run for example

```
sapt update
```

instead of

```
sudo apt update
```

---

### Post by steeldriver on 2016-06-05
Hmm... the /etc/apt/apt.conf.d/99progressbar file seems to work for me (I must admit I hadn't tested it before posting, but tried it just now)

However I'm still on 14.04

---

### Post by hunman2 on 2016-07-24
Bit late, but changing
```
if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
    # We have color support; assume it's compliant with Ecma-48
    # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
    # a case would tend to support setf rather than setaf.)
    color_prompt=yes
    else
    color_prompt=
    fi
fi

```
to
```

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
        # We have color support; assume it's compliant with Ecma-48
        # (ISO/IEC-6429). (Lack of such support is extremely rare, and such
        # a case would tend to support setf rather than setaf.)
        color_prompt=yes
    else
        color_prompt=
    fi
else
    color_prompt=
fi

```
fixes the first question (the *case "$TERM"* sets color_prompt to yes even if *$force_color_prompt* is not set

---

