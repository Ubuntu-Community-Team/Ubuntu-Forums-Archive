---
title: "remap menu key to right control (in and outside X)"
date: 2008-06-06
forum: General Help
---

### Post by stairwayoflight on 2008-06-06
**[COLOR="Red"]FOR A BETTER SOLUTION, SEE [[COLOR="Blue"]MY POST BELOW[/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?p=6244881#post6244881")**


Hey folks!

Just got my new 4g eeepc, and it rocks. Whats next? Well I can't do my normal  <right-control>b, f, etc., in bash, emacs, and family, because there is no right control key on this puppy.

I'm trying to use the Menu key as a right control key.

The following command will cause the menu key to show up in xev as "Control_R", but Menu-p doesn't have the same effect as Control-p in bash.

xmodmap -e "keysym Menu = Control_R"

Any ideas?

---

### Post by stairwayoflight on 2008-06-06
Ahh, I got it finally.

```
xmodmap -e "keycode 117 = Control_R"
xmodmap -e "add Control = Control_R"
```

To use it at startup, you can put it in a script:

```
!
! controlR - remap Menu key to Control.
!
keycode 117 = Control_R
add Control = Control_R
```

Assuming the script was saved as /home/youruserid/controlR, in eeeXubuntu you can click Applications=> Settings=> Autostarted Applications=> +Add. Type whatever you want for a name and description, then for the command you would enter:
```
xmodmap /home/youruserid/controlR
```
For (Ku|U)buntu desktops, the last step should be similar. If anyone has a better approach I'd still like to hear it.

Thanks, 
Stairway

EDIT: ironically, I passed over an important feature of ***x***modmap, that being that it modifies the keymap for ***X***. Hence, it doesn't work outside X. (Technically as implemented here it won't work outside of the window manager. I'll get around to that soon enough, I suppose.)

---

### Post by stairwayoflight on 2008-06-09
Ok,

I found out what I needed to know about xmodmap, but how to get it to load on startup?

I put the command "xmodmap ~/.xmodmap" into ~/.bash_profile and the menu key is remapped properly in one window manager but not in xfce.

---

### Post by bingoUV on 2008-06-09
~/.xsession is the place to put the commands. ~/.xmodmaprc does not work always for me.

---

### Post by stairwayoflight on 2008-06-09
Which commands? I did
$ echo "xmodmap ~/.xmodmap" > .xsession
and on logging in xfce would refuse to start, gtk2 complained about being run setuid.

I ran the xmodmap command from ~/.bash_profile and forgoing it I renamed .xmodmap to ~/.Xmodmap -- both these attempts resulting in the key remap occuring in wmii, and not occurring in xfce. Odd.

---

### Post by bingoUV on 2008-06-09
The full commands that you run through terminal i.e. something like
```

xmodmap -e 'xmodmap code goes here'

```

Put these in ~/.xsession. I don't know why it is complaining about setuid. Do the following to be sure
```

chmod 0755 ~/.xsession

```

---

### Post by joesmoe10 on 2008-06-14
I was just trying to do the same thing.  Here's how I did it.

Create ~/.xmodmap and add these three lines

!Make the menu key another control
keysym Menu = Control_R
add Control = Control_R

Log out and log back in, a dialog should pop up asking if you want to load it.  Select .xmodmap and click load.  And click okay.  Should be good to go!

---

### Post by stairwayoflight on 2008-07-18
This definitely does not work, I can't log in. Other than what I added, there is nothing in the file. I'm not sure if it should have an "exec gnome" or something as well?

> **bingoUV said:**
> The full commands that you run through terminal i.e. something like
```

xmodmap -e 'xmodmap code goes here'

```

Put these in ~/.xsession. I don't know why it is complaining about setuid. Do the following to be sure
```

chmod 0755 ~/.xsession

```

---

### Post by stairwayoflight on 2008-08-28
Well, just as a postscript here, I'll leave a comment or two. I wanted to remap the keys on my eeepc, and I have settled on wmii as my window manager. It appears that wmii executes ~/.xsession on startup, while xfce does not. (Hmmf.)

What I didn't realize earlier is how .xsession actually works, and that it is a bash or sh script. So when I had created my original ~/.xsession, I didn't put the magic "#!/bin/bash" at the top, hence the errors.

So yes, putting the xmodmap commands in a file such as joesmoe10's above, then putting that file into ~/.xsession eg:
```
#/bin/bash
xmodmap $HOME/.Xmodmap
exec yourwindowmanagerhere
```worked for me. Thanks for the tips, everyone.

---

### Post by stairwayoflight on 2008-11-24
For those interested, in Hardy Heron, I had to set the Session variable manually in .dmrc, like this:
```
Session=custom
```I also have the following in .xsession:
```
#!/bin/bash
xmodmap $HOME/.xmodmap
exec wmii
```and my ~/.xmodmap contains: ```
!Turn the Menu key into a Right Windows key.
keysym Menu = Super_R
!add Super = Super_R
```
This works out well for me as I am using the Mod4 key (Super, or Windows key) for wmii navigation, and none of the shortcuts clobber shortcuts for emacs. I am still using gdm, so I don't know if it works with xdm or kdm.

---

