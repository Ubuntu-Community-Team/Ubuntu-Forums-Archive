---
title: "Does changing to Wayland or changing OS to Kubuntu stop from having screen tearing?"
date: 2020-07-01
forum: General Help
---

### Post by pranav.bhattarai on 2020-07-01
My friend is a noob *(& so am I in some ways)*. I tried many things to fix tree tearing problem solutions but none of them actually worked. After a week, he told me that he is still experiencing screen tearing/glitches. There is no NVIDIA stuff. His laptop is old & surprisingly released with Ubuntu by Dell (Inspiron 3442, i3, 1TB HDD). 
 
How can I solve his problem? I am running out of options. 
 
He is starting to hate Linux, and I don't like it. 
 
What should I try?

Current Distro: Ubuntu 20.04 LTS
Current Display server: X
Current DE: GNOME 3.36

Edit:
Output of **sudo lshw -C video **>>> [https://imgur.com/m95BSUa](https://imgur.com/m95BSUa)  This can be helpfull to know every information about what video cards, drivers, etc are involved.

---

### Post by ajgreeny on 2020-07-01
I wonder if moving to Xubuntu 20.04 might help.
Previous versions of Xubuntu have often suffered from screen tearing, though it's  never been a problem for me, and other users with integrated Intel graphics have usually found that using Compton as the composting software in place of the default from wxfm window manager overcomes it effectively.
20.04 should be much better apparently even without using Compton but I can not confirm that as I do not suffer from the problem so can't  test this out.

---

### Post by pranav.bhattarai on 2020-07-01
Then what should I do? Is there something, through which I can stop this?
One of my friend suggested me to try this:

1. sudo (editor command) /etc/default/grub

2. Comment out this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

3. Add this line instead:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_psr=0"

4. Save and close your editor

5. sudo update-grub



[SIZE=4]Should I try this?[/SIZE]

---

### Post by GhX6GZMB on 2020-07-01
The 3442 i3 has Intel graphics AFAIK, which can have problems with tearing.

Possible solution: sudo open
 ```
/usr/share/X11/xorg.conf.d/20-intel.conf
```
and check that it has the following content:
```
Section "OutputClass"
  Identifier  "Intel Graphics"
  Driver      "intel"
  Option      "TearFree" "true"
EndSection


```
Otherwise add the option line.

Let us know the outcome.

---

### Post by CelticWarrior on 2020-07-01
> **ml9104 said:**
> 
Possible solution: sudo open
 ```
/usr/share/X11/xorg.conf.d/20-intel.conf
```
an check that it has the following content:
```
Section "OutputClass"
  Identifier  "Intel Graphics"
  Driver      "intel"
  Option      "TearFree" "on"
EndSection


```


This ^^^ is what I would try but with just a small yet very important change represented in bold below:
```
**sudoedit **/usr/share/X11/xorg.conf.d/20-intel.conf
```

Likewise, in your friend's suggestion, '**sudoedit**' is the now preferred method for editing system configuration files. But regarding this suggestion I also have a couple of remarks:
[LIST=1]
[*]I've never seen such parameter being used, I've no idea about what is it supposed to do.
[*]Commenting out that line to add an identical one with the added parameter is nonsense; just edit in the additional parameter.
[/LIST]

---

### Post by GhX6GZMB on 2020-07-01
Hmmm... sudoedit is a really interesting idea (I wasn't aware of it). With me it unfortunately launches a super-nerdy editor (vim?) instead of my preferred Featherpad. I'll have to play around with the $EDITOR variable I guess.
But thanks for the input.

---

### Post by ajgreeny on 2020-07-01
Add a line such as 
```
export EDITOR="nano"
```
to your hidden .bashrc file to change the editor used by **sudoedit**.

You can use whatever editor you prefer; I use nano because I'm so used to it, and like you, I've never managed to get used to vi or vim; both a bit esoteric for my needs.

---

### Post by SeijiSensei on 2020-07-01
> **ajgreeny said:**
> You can use whatever editor you prefer; I use nano because I'm so used to it, and like you, I've never managed to get used to vi or vim; both a bit esoteric for my needs.
I grew up with emacs and now use [jed]("https://www.jedsoft.org/jed/") pretty much exclusively. Like you, vi and vim never clicked for me.

---

### Post by GhX6GZMB on 2020-07-01
OP, did the "TearFree" option help?

---

### Post by TheFu on 2020-07-01
> **ml9104 said:**
> Hmmm... sudoedit is a really interesting idea (I wasn't aware of it). With me it unfortunately launches a super-nerdy editor (vim?) instead of my preferred Featherpad. I'll have to play around with the $EDITOR variable I guess.
But thanks for the input.

Any editor can be used safely with sudoedit, even gedit, because the editor runs as the normal userid, not with elevated privileges. For example:
```
export EDITOR="/usr/bin/geany"
```

Though everyone knows that vim is the most powerful, most flexible, most extensible, editor that exists for every platform.  I&#8217;ve never seen nano on a router, but there is always vim if only the minimal version.  But we each have different needs in an editor based on our skills.  Eventually, everyone learns vim.

i have mostly intel iGPUs but never notice tearing in my fvwm + X/Windows setups.  But I&#8217;m still on 16.04 with 4.15.x kernels.

---

### Post by kurt18947 on 2020-07-01
Wayland is having issues suspending or shutting down for me. It works fine except for the power issues. I have an AMD Ryzen system.

---

### Post by GhX6GZMB on 2020-07-03
> **TheFu said:**
> Any editor can be used safely with sudoedit, even gedit, because the editor runs as the normal userid, not with elevated privileges. For example:
```
export EDITOR="/usr/bin/geany"
```


Well, I've now tried sudoedit, and I don't like it, no matter which editor. It disturbs me that I'm editing a file in /var/tmp with a cryptic name (why in /var/tmp, /tmp should be enough, or?).
It means that I'm not quite certain exactly which file I'm editing. I'll stick with my old way of doing this.

---

### Post by TheFu on 2020-07-03
> **ml9104 said:**
> Well, I've now tried sudoedit, and I don't like it, no matter which editor. It disturbs me that I'm editing a file in /var/tmp with a cryptic name (why in /var/tmp, /tmp should be enough, or?).
It means that I'm not quite certain exactly which file I'm editing. I'll stick with my old way of doing this.

Guess we know where security goes in the priority list there.  Can't remember what filename you typed a few seconds ago?  Sometimes I have that issue too, but then the great-grandkids remind me.  ;)

---

### Post by GhX6GZMB on 2020-07-03
> **TheFu said:**
> Guess we know where security goes in the priority list there.  Can't remember what filename you typed a few seconds ago?  Sometimes I have that issue too, but then the great-grandkids remind me.  ;)

I see no security issues with the way I always do this (which you don't know).

Concerning my memory: don't worry. But sudoedit assigns a filename looking like a YouTube video to a file in /var/tmp.
Like: /var/tmp/aPtjfj6675 which I did NOT type. OK?

I understand that sudoedit operates on a copy of the original file, but with several files open in different editor windows it's not an option. And I still don't understand /var/tmp vs. /tmp. In fact, /var/tmp is _less_ secure than /tmp.


@QIII: you didn't like me pulling this thread back to the OPs question and deleted parts of my previous post trying to do that? Fine. This is apparently now a post about sudoedit.
Great Job. And now you can ban me for being constructive.

---

