---
title: "aspell without being root"
date: 2013-11-27
forum: General Help
---

### Post by brancalessio on 2013-11-27
Dear all,
  I use a computer with Ubuntu 12.04 installed. I need the aspell French spell-checker, but it is not installed (and I am not the administrator).

I would like to install the French spell-checker. I downloaded it, "compiled", but I do not know where to install it.

On the internet someone says that it is to be installed in

```
$HOME/.config/enchant/aspell
```

other on

```
$HOME/.aspell
```

Nevertheless, it does not work and, e.g., gedit only recognizes the system-wide installed dictionaries only.

Thank you for your help!

---

### Post by steeldriver on 2013-11-27
I think $HOME/.aspell.conf works as far as aspell itself is concerned e.g. if I do

```
$ aspell list <<< "bird oiseau dog chien"
oiseau
chien
```

and then

```
$ cat > ~/.aspell.conf
lang fr
dict-dir /home/steeldriver/aspell
```

(where I have installed aspell-fr-0.50-3 to /home/steeldriver/aspell), then

```
$ aspell list <<< "bird oiseau dog chien"
bird
dog

```

If it's not being picked up in gedit then that might be down to the gedit spelling plugin - I couldn't see anything obvious in the gedit-2 gconf database - maybe it uses the user's LOCALE information?

**EDIT: actually gedit *does* seem to respect the ~/.aspell.conf file, although the dialog box still indicates the language as 'English (Canada)' the checker plugin is in fact highlighting English words as misspellings:**

[ATTACH=CONFIG]248157[/ATTACH]

---

### Post by brancalessio on 2013-12-04
Thank you for your answer!

I confirm that gedit ingnores aspell.conf. I think that in order to make gedit work, we should work on enchant, but there is no documentation as far as I know.

I was actually able to use dictionary installed in my home with with aspell.conf

```

data-dir $HOME/Documents/aspell-extra
local-data-dir $HOME/Documents/aspell-extra

```

Nevertheless, in this way aspell does not see any longer the system wide installed dictionaries.

---

### Post by pbrane on 2013-12-04
When you configure aspell you should use the [FONT=Courier New]--prefix=/usr[/FONT] option. i.e., [FONT=courier new]./configure --prefix=/usr. [/FONT]That is what tells the compiler/linker where to install the binary. Compile under your user and install as sudo. The binary should end up in /usr/bin.

If you don't have administrative rights then change the path to [FONT=courier new]$HOME. --prefix=$HOME[/FONT] and installation will be in your home directory.

Gedit doesn't use aspell directly. It uses enchant which is a frontend for multiple spell check dictionaries. I have aspell-en installed and enchant. On my system the aspell dictionaries are installed in [FONT=Courier New]/usr/share/aspell[/FONT]. My guess is that under a user account those dictionaries should be in [FONT=courier new]~/.local/share/aspell[/FONT]

---

### Post by brancalessio on 2013-12-20
> **pbrane said:**
> 
Gedit doesn't use aspell directly. It uses enchant which is a frontend for multiple spell check dictionaries. I have aspell-en installed and enchant. On my system the aspell dictionaries are installed in [FONT=Courier New]/usr/share/aspell[/FONT]. My guess is that under a user account those dictionaries should be in [FONT=courier new]~/.local/share/aspell[/FONT]

It seems that $HOME/[FONT=courier new].local/share/aspell is not the right folder. Probably enchant works only for system for system-wide installed dictionaries.[/FONT]

---

