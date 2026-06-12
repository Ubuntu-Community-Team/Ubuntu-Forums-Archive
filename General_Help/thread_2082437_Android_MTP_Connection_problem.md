---
title: "Android MTP Connection problem"
date: 2012-11-09
forum: General Help
---

### Post by hgergo on 2012-11-09
Hy
I have bought an Acer S500 whit android 4.0.4 and i want to transfer files from pc to the phone
I found a tutorial how to make it to work in OMGUBUNTU [http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access](http://www.omgubuntu.co.uk/2011/12/how-to-connect-your-android-ice-cream-sandwich-phone-to-ubuntu-for-file-access)
At the and after restart i must enter  commands

```
echo “alias android-connect=\”mtpfs -o allow_other /media/GalaxyNexus\”" >> ~/.bashrc

echo “alias android-disconnect=\”fusermount -u /media/GalaxyNexus\”" >> ~/.bashrc

source ~/.bashrc
```

and after the last command i get this error

```
No command '“alias' found, did you mean:
 Command '0alias' from package 'zeroinstall-injector' (universe)
“alias: command not found
“alias android-disconnect=”fusermount -u /media/Acer”
No command '“alias' found, did you mean:
 Command '0alias' from package 'zeroinstall-injector' (universe)
“alias: command not found
“alias android-disconnect=”fusermount -u /media/Acer”

```

and he same error is apearing when i log in to root from terminal

Cam sombody help me to solve this problem?

---

### Post by carl4926 on 2012-11-09
I find it easier to just use PTP

---

### Post by Steeperton on 2012-11-09
try typing the commands, rather than cut and paste... Websites tend to screw up the quote marks

" or “

---

### Post by hgergo on 2012-11-09
```
root@heavyd-Aspire-5100:/home/heavyd# source ~/.bashrc
No command '&#8220;alias' found, did you mean:
 Command '0alias' from package 'zeroinstall-injector' (universe)
&#8220;alias: command not found
&#8220;alias android-disconnect=&#8221;fusermount -u /media/Acer&#8221;
No command '&#8220;alias' found, did you mean:
 Command '0alias' from package 'zeroinstall-injector' (universe)
&#8220;alias: command not found
&#8220;alias android-disconnect=&#8221;fusermount -u /media/Acer&#8221;

```

I sould try to install zeroinstall-injector?

---

### Post by hgergo on 2012-11-09
i tryed whit " and whit the instalation but the error persists

---

### Post by sthompso on 2012-11-10
> **hgergo said:**
> i tryed whit " and whit the instalation but the error persists

Those echo commands, append lines to the ~/.bashrc file every time you run them.

If you have already executed those commands the first time with the wrong “ character, then the .bashrc file will already have the wrong lines.

I suspect you will first need to remove those wrong lines from the .bashrc file.  Or... it's probably easiest to just edit your .bashrc file and make sure the last lines look like this (with the correct " characters) - being careful not to change or remove anything else in the file:


```
alias android-connect="mtpfs -o allow_other /media/GalaxyNexus"
alias android-disconnect="fusermount -u /media/GalaxyNexus"

```

---

### Post by cwsnyder on 2012-11-10
Something else to throw into the mix. Why are you using the mtpfs at all?

According to [http://www.techradar.com/reviews/phones/mobile-phones/acer-cloudmobile-s500-1094355/review/9#articleContent](http://www.techradar.com/reviews/phones/mobile-phones/acer-cloudmobile-s500-1094355/review/9#articleContent) your phone should connect to any computer as a simple storage device like a thumb drive, just connect your micro USB cable.

MTPFS is used for Samsung Galaxy phones and others which don't connect as a storage device, but connect as a read-only storage with limited access to certain media files.

---

### Post by hgergo on 2012-11-10
> **sthompso said:**
> Those echo commands, append lines to the ~/.bashrc file every time you run them.

If you have already executed those commands the first time with the wrong “ character, then the .bashrc file will already have the wrong lines.

I suspect you will first need to remove those wrong lines from the .bashrc file.  Or... it's probably easiest to just edit your .bashrc file and make sure the last lines look like this (with the correct " characters) - being careful not to change or remove anything else in the file:


```
alias android-connect="mtpfs -o allow_other /media/GalaxyNexus"
alias android-disconnect="fusermount -u /media/GalaxyNexus"

```

where do i find the file, i found one in home folder but no familier lines there.

@cwsnyder i don have option to put in usb masstorage device mode like in gingerbread

---

### Post by cwsnyder on 2012-11-10
> Connecting the handset to a PC is a simple case of plugging it in with a micro USB to USB cable. Once done, it mounts itself as a drive and you can just drag and drop media on and off the phone.
If you're using a microSD card then another option is to remove it from the phone and plug that into the PC, which again enables you to access it like a hard drive.
.bashrc should be in your home folder **on the phone** or /home/heavyd , or /media/Acer .

---

### Post by hgergo on 2012-11-10
> **cwsnyder said:**
> .bashrc should be in your home folder **on the phone** or /home/heavyd , or /media/Acer .

This is the file from /home,  in /media/Acer there is no file

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# If set, the pattern "**" used in a pathname expansion context will
# match all files and zero or more directories and subdirectories.
#shopt -s globstar

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

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

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```


P.S. Yes under windows it&#347; like a simple mas storage device but under ubuntu is the problem while nothing popping up when pluging in!

---

### Post by cwsnyder on 2012-11-10
[http://ubuntuforums.org/showthread.php?t=814881](http://ubuntuforums.org/showthread.php?t=814881) has a better discussion.

To summarize: Make a mount point for your USB storage device, either in /media or in ~/ , use fdisk -l to find where the attached USB storage device is located (say /dev/sdc), use the mount command to attach the device to the mount point, then use the storage device as if it were simply a folder in the path designated, using the umount command when you are finished.```
sudo mkdir /media/phone
sudo fdisk -l
sudo mount /dev/sdb /media/phone
ls -a /media/phone
umount /media/phone
```I would not copy all of the above lines and run at once, they are just example code.

---

### Post by roger_1960 on 2012-11-10
Hi all

Having messed with this for hours, a new idea:

Set up the phone as an FTP server (solid explorer or a dedicated app) and connect over your wireless network with Filezilla or similar.  This works fine and gives full file and folder read/write access. 

I believe this an issue with android 4.0 and above where "connect as USB device" has been removed from the OS.  Windows users can get round it by installing Samsung drivers on their PC but there arn't any for linux AFAIK(yet).

Roger

---

### Post by sthompso on 2012-11-10
> **hgergo said:**
> where do i find the file, i found one in home folder but no familier lines there.



All your commands refer to the file **~/.bashrc** - the **~/** refers to your own home folder... (e.g. /home/*username*/.bashrc). 

In any case, you can directly edit this file as ~/.bashrc from your PC.

Example - run the following from the terminal:
```
gedit ~/.bashrc

```

---

### Post by hgergo on 2012-11-10
Ok thx file found and lines removed form end.

Now when i am exiting root i have the folowing error
```
rm: cannot remove `/run/user/root/gvfs': Is a directory

```

and the bashrc file is so now

```
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

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

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi
```

---

### Post by hgergo on 2012-11-11
Somebody hase some clue for that error?

---

### Post by davea88 on 2012-11-20
android-connect and mtpfs worked fine on 12.04 yet they fail with 12.10.
That's bad, IMHO.  Perhaps if I spend enough time researching
ftp access I can get files in-out of my Samsung Android with
Ice Cream Sandwich.  Would be nice if someone would offer a bit
more of a recipe (rather than just a suggestion) for ftp access.

---

### Post by cwsnyder on 2012-11-20
@davea88: This procedure worked for me with a Samsung Galaxy Tab 2 7.0.
1) Turn on both devices and make sure both are connected to the same router.  Your Android device will usually be connected through WiFi, your Ubuntu computer may be wireless or wired.
2)Install on Android the app Rapfox FTP server from the Google Play app store (just called FTP Server when I installed it.)
3) Install Filezilla from the Ubuntu Software Center on your Linux computer.
4) Start FTP Server on your Android.  It will probably show up in your un-assigned widgets area.  You may want to move it to one of your app screens.
5) Start Filezilla on your Ubuntu from your Applications >> Internet menu entry, copying the FTP URL from the first line in the black below your stop button on the Android device display. Example [COLOR="Blue"]*[ftp://192.168.1.102](ftp://192.168.1.102)*[/COLOR] Do not copy the colon or the number after the colon.
6) Use the same user name and password on Filezilla copied from the username and password displayed on the second and third lines below the stop button on your Android device.
7) Your port number for Filezilla is the number following the colon displayed as part of the FTP URL on your FTP Server. Example: *[ftp://192.168.1.102:2121](ftp://192.168.1.102:2121)* is displayed and your port number is 2121.
8 ) Hit the quick connect button on the line at the top following your port number.  Your Android device file structure should show on the right side of your window under your dialog box and the remote site path display.  Your Ubuntu file structure should show under the local site path display just to the right of your Android listing.
9) You can now drag & drop from one to the other, just as in File Manager.

Is that simplified enough?

---

### Post by msprng on 2012-12-03
How long must we wait for Ubuntu to recognize mtp phones and devices? Waited out 11.10, 12.04, 12.10. Thought for sure 12.10 would have adapted for mtp...come on guys...this is happening...let's get with it!

---

### Post by Automat2 on 2013-01-16
> **msprng said:**
> How long must we wait for Ubuntu to recognize mtp phones and devices? Waited out 11.10, 12.04, 12.10. Thought for sure 12.10 would have adapted for mtp...come on guys...this is happening...let's get with it!
It appears that this is not a priority for the developers. Let's hope that by 13.04...

---

### Post by Automat2 on 2013-05-03
OK. I have installed Ringtail (13.04), upgrading from Quantal and having downloaded all the libraries as described [http://askubuntu.com/questions/236779/how-to-mount-an-android-jelly-bean-phone-if-theres-no-option](http://askubuntu.com/questions/236779/how-to-mount-an-android-jelly-bean-phone-if-theres-no-option)

But it didn't work and left it until the release of Ringtail, that was supposed to sort this problem out.

And I tried it, and so far, it works. It has mounted my Motorola XT890 straight from plugging it in my machine, and I can explore all files in the internal device and the SD card.

:p

Edit: That was only the first time. I am trying again but only mounting the "Device Manager" instead of the XT890.

---

