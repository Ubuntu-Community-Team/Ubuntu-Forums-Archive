---
title: "I have strange issue when copy some piece of code in konsole ..."
date: 2024-03-31
forum: General Help
---

### Post by nilovsergey on 2024-03-31
I have rather a strange issue on my fresh Kubuntu 22.04 installation, when I try to copy some piece of code in konsole or enter some text
in console command :


    [https://youtu.be/ocCnoMiy3E4](https://youtu.be/ocCnoMiy3E4)


```
$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 22.04.4 LTS
6.5.0-26-generic
x86_64




$ kf5-config --version
Qt: 5.15.3
KDE Frameworks: 5.92.0
kf5-config: 1.0




$ dpkg -s  konsole
Package: konsole
Status: install ok installed
Priority: optional
Section: kde
Installed-Size: 4658
Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
Architecture: amd64
Version: 4:21.12.3-0ubuntu1
Provides: x-terminal-emulator
Depends: konsole-kpart (= 4:21.12.3-0ubuntu1), kio, libc6 (>= 2.34), libkf5configcore5 (>= 5.71.0~), libkf5configwidgets5 (>= 5.71.0~), libkf5coreaddons5 (>= 5.71.0~), libkf5crash5 (>= 5.71.0~), libkf5dbusaddons5 (>= 5.71.0~), libkf5globalaccel-bin, libkf5globalaccel5 (>= 5.71.0~), libkf5guiaddons-bin, libkf5guiaddons5 (>= 5.71.0~), libkf5i18n5 (>= 5.71.0~), libkf5kiowidgets5 (>= 5.71.0~), libkf5notifyconfig5 (>= 5.71.0~), libkf5widgetsaddons5 (>= 5.77.0), libkf5windowsystem5 (>= 5.82.0), libkf5xmlgui5 (>= 5.71.0~), libqt5core5a (>= 5.15.1), libqt5gui5 (>= 5.15.0~) | libqt5gui5-gles (>= 5.15.0~), libqt5widgets5 (>= 5.15.0~), libstdc++6 (>= 11)
Suggests: lrzsz
Description: X terminal emulator
Konsole is a terminal emulator built on the KDE Platform. It can contain
multiple terminal sessions inside one window using detachable tabs.
.
Konsole supports powerful terminal features, such as customizable schemes,
saved sessions, and output monitoring.
Homepage: https://apps.kde.org/en/konsole
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>



```

Why I got it and how it can be fixed ?

---

### Post by nilovsergey on 2024-04-03
I tryexplian in words : [COLOR=#0C0D0E][FONT=-apple-system]I try 1) to select some text in terminal to copy it 2) To enter some text in console text. Sorry I do not know how exactly to call this strange effect - like entry point was some distance rigth from place where I enter text[/FONT][/COLOR]

---

### Post by nilovsergey on 2024-05-27
I tried to install and use xterm - but found it very unconvinient. Are there some other alternative console app which I cab use in kubuntu 22.04?

---

### Post by MAFoElffen on 2024-05-27
In graphical terminal apps (as in console), when you paste text, it is not like in an editor. You have to move your cursor manually to where you want the paste to begin. If you just paste, it will start where ever the cursor currently is. All of them are like that because they directly interact with console.

Is that what you are trying to describe?

---

### Post by currentshaft on 2024-05-27
ap

---

### Post by nilovsergey on 2024-05-28
Do you mean these files :

```
# cat   /etc/bash.bashrc
# System-wide .bashrc file for interactive bash(1) shells.


# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.


# If not running interactively, don't do anything
[ -z "$PS1" ] && return


# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize


# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi


# set a fancy prompt (non-color, overwrite the one in /etc/profile)
# but only if not SUDOing and have SUDO_PS1 set; then assume smart user.
if ! [ -n "${SUDO_USER}" -a -n "${SUDO_PS1}" ]; then
  PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi


# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac


# enable bash completion in interactive shells
#if ! shopt -oq posix; then
#  if [ -f /usr/share/bash-completion/bash_completion ]; then
#    . /usr/share/bash-completion/bash_completion
#  elif [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#  fi
#fi


# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ] && [ ! -e "$HOME/.hushlogin" ] ; then
    case " $(groups) " in *\ admin\ *|*\ sudo\ *)
    if [ -x /usr/bin/sudo ]; then
        cat <<-EOF
        To run a command as administrator (user "root"), use "sudo <command>".
        See "man sudo_root" for details.


        EOF
    fi
    esac
fi


# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found -o -x /usr/share/command-not-found/command-not-found ]; then
        function command_not_found_handle {
                # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
                   /usr/lib/command-not-found -- "$1"
                   return $?
                elif [ -x /usr/share/command-not-found/command-not-found ]; then
                   /usr/share/command-not-found/command-not-found -- "$1"
                   return $?
                else
                   printf "%s: command not found\n" "$1" >&2
                   return 127
                fi
        }
fi

```

Not shure, which "[COLOR=#000000] control characters[/COLOR]" have I to search in it ?

and no file like "[COLOR=#000000] .zshrc[/COLOR]" in my OS...

---

### Post by currentshaft on 2024-05-28
-x

---

