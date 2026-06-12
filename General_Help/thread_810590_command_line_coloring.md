---
title: "command line coloring"
date: 2008-05-28
forum: General Help
---

### Post by derdud on 2008-05-28
This is probably a really dumb question but I did a quick search and didn't turn up exactly what I'm looking for.

I just installed 8.04 server on a machine I have here. Everything works great so far. My only issue is a cosmetic one: the command line is all black and white. With Gentoo and Sabayon I was spoiled because it was turned on by default. How do I turn this on under Ubuntu?

Thanks, and excuse my newbishness. ;)

---

### Post by derdud on 2008-05-28
Something else of note: the tab key doesn't auto-complete. It inserts a tab space instead. So while we're on the topic of changing stuff, how can I change that back too?

---

### Post by Forlong on 2008-05-28
What 'command line' are you referring to? GNOME terminal?

---

### Post by derdud on 2008-05-28
Just the straight command line for the OS. I downloaded and installed a server version of 8.04 and I don't believe it installed X at all. It boots right to a text-only login prompt, which is exactly what I want. I just miss the coloring and tab auto-complete that Gentoo and Sabayon gave. :)

This might be of interest too:  When I finally put the machine on the network, I SSH'd into it using the OS X terminal on my MacBook Pro. Colors are visible there, and the tab works properly (auto-complete). It's just when I'm at the machine itself it doesn't seem to do that stuff.

---

### Post by Forlong on 2008-05-28
Do you have a .bashrc in your home directory?

---

### Post by cdtech on 2008-05-28
Here is a site for available color codes:
[[COLOR="DarkRed"]Prompt Magic[/COLOR]]("http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/")

If you want to play around with different color combinations try this:

Run (in a terminal) the command "dircolors", copy the output to, for instance, ~/.dircolors, then source that file in ~/.bashrc (such as I did here):
```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
[COLOR="Blue"][ -e "$HOME/.dircolors" ] && DIR_COLORS="$HOME/.dircolors"
[ -e "$DIR_COLORS" ] || DIR_COLORS=""[/COLOR]
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
    #alias dir='ls --color=auto --format=vertical'
    #alias vdir='ls --color=auto --format=long'
fi
```

You can of course change the colors for each filetype as you wish within your newly created ~/.dircolors file.

Another useful site: [[COLOR="DarkRed"]Bash Prompt Howto[/COLOR]]("http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html")

Hope this helps.....

---

### Post by zwj on 2008-05-28
Thank you for the code, cdtech! 'dircolors -p' prints out the color mapping (in the comments). I was wondering if it is possible to add some new color. For example, I find the green color too light, and want to re-associate its code (32) to something darker.

Thanks in advance.

---

### Post by cdtech on 2008-05-28
> **zwj said:**
> Thank you for the code, cdtech! 'dircolors -p' prints out the color mapping (in the comments). I was wondering if it is possible to add some new color. For example, I find the green color too light, and want to re-associate its code (32) to something darker.

Thanks in advance.

If you mean for your prompt, you can change that value using the command line:```
PS1="${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ "
```
For example, and changing the colors using the ANSI Color Codes listed from the link I provided above.

These are ANSI Color Codes and can only be modified using ~/.bashrc or from the command line as shown above.

Using my previous post you can modify the colors in .dircolor by replacing the ANSI color code to a value you prefer which will list your directory text  in whatever color you choose.

---

### Post by zwj on 2008-05-29
Thank you, cdtech. What I actually want is to have more colors than those coded 30-37, e.g. colors with arbitrary RGB values. Since I changed my terminal background to be light grey and foreground to be black, I can't see the executable files listed using 'ls', which are colored green+bold. I just found that removing the bold attribute would solve the problem. Thanks anyway.

---

