---
title: "Cannot access starship.toml from inside ~/.config"
date: 2023-04-20
forum: General Help
---

### Post by kabirgandhiok on 2023-04-20
Hi,

According to the [official documentation]("https://starship.rs/config/") for configuring starship, all that I need is a starship.toml file inside ~/.config and have the STARSHIP_CONFIG environment variable point to it. But I just cannot get it to work. Bash complains permission denied (os error 13). 

However, when I move starship.toml outside ~/.config and place it in $HOME it works. So I'm a little confused, aren't the user specific config files supposed to be placed in ~/.config? 

Does my ~/.config directory have incorrect permissions?

```

(starship.toml inside ~/.config)
/home/kabir took 6s 
&#10095; source ~/.bashrc
[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

/home/kabir 
&#10095; exec bash
[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

/home/kabir 
&#10095; echo $STARSHIP_CONFIG
/home/kabir/.config/starship.toml

drwx------ 28 kabir kabir  4096 Apr 21 01:21 .config
-rw-rw-r--  1 kabir kabir   714 Apr 21 01:27 starship.toml

(starship.toml moved outside ~/.config)

~/.bashrc (starship config and env variable)
eval "$(starship init bash)"
. "$HOME/.cargo/env"
export STARSHIP_CONFIG=~/starship.toml

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;/home/kabir 
&#9492;&#9472;> echo $STARSHIP_CONFIG
/home/kabir/starship.toml

```

Thanks for helping me understand.

---

### Post by ne29914 on 2023-04-20
_Never_ use ~ within scripts or setup files. In this case, use $HOME/.config instead.
~ is only understood by your Shell, which will translate it to $HOME, but there's no guarantee that you have a shell running at the appropriate time. $HOME will always be understood by the full OS.

---

### Post by kabirgandhiok on 2023-04-20
> **ne29914 said:**
> _Never_ use ~ within scripts or setup files. In this case, use $HOME/.config instead.
~ is only understood by your Shell, which will translate it to $HOME, but there's no guarantee that you have a shell running at the appropriate time. $HOME will always be understood by the full OS.

If I use $HOME/.config I get a permission denied error

```

&#10095; exec bash
[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

(inside ~/.bashrc, setting up starship)
eval "$(starship init bash)"
. "$HOME/.cargo/env"
export STARSHIP_CONFIG=$HOME/.config/starship.toml

&#10095; echo $STARSHIP_CONFIG
/home/kabir/.config/starship.toml

(on opening a new terminal instance)
[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

/home/kabir 
&#10095; 

drwx------ 28 kabir kabir  4096 Apr 21 03:00 .config

``` 

does this mean I will have to change $HOME/.config permissions?

Thanks!

---

### Post by ne29914 on 2023-04-20
Well, you've progressed! Now your program at least attempts to read the file in $HOME/.config/
cd to $HOME/.config and issue an ll command. Post the output.

---

### Post by kabirgandhiok on 2023-04-21
Thanks, here's the output of ll from inside $HOME/.config

```

/home/kabir/.config 
&#10095; ll
total 144
drwx------ 28 kabir kabir 4096 Apr 21 03:00 ./
drwxr-x--- 28 kabir kabir 4096 Apr 21 03:21 ../
drwxrwxr-x  2 kabir kabir 4096 Apr  7 01:38 autostart/
drwx------  4 kabir kabir 4096 Apr  1 02:35 cef_user_data/
drwx------  2 kabir kabir 4096 Apr 21 15:43 dconf/
drwx------  2 kabir kabir 4096 Mar 29 14:46 enchant/
drwx------  2 kabir kabir 4096 Mar 26 02:27 eog/
drwx------  3 kabir kabir 4096 Mar 26 02:15 evolution/
drwxr-xr-x  2 kabir kabir 4096 Mar 29 14:47 gedit/
drwxr-x---  4 kabir kabir 4096 Apr  5 19:45 gnome-builder/
drwx------  3 kabir kabir 4096 Mar 26 02:33 gnome-control-center/
-rw-rw-r--  1 kabir kabir    3 Mar 26 02:25 gnome-initial-setup-done
drwx------  3 kabir kabir 4096 Mar 26 02:43 gnome-session/
drwxr-xr-x  2 kabir kabir 4096 Mar 26 02:24 goa-1.0/
-rw-rw-r--  1 kabir kabir    0 Mar 26 02:15 .gsd-keyboard.settings-ported
drwx------  2 kabir kabir 4096 Apr 21 15:42 gtk-3.0/
drwxrwxr-x  2 kabir kabir 4096 Mar 26 02:56 gtk-4.0/
drwx------  2 kabir kabir 4096 Mar 26 02:54 htop/
drwx------  3 kabir kabir 4096 Mar 26 02:15 ibus/
drwxrwxr-x  5 kabir kabir 4096 Apr 16 14:48 JetBrains/
drwxrwxr-x  2 kabir kabir 4096 Apr 10 00:17 jgit/
drwxrwxr-x  3 kabir kabir 4096 Mar 30 20:05 libreoffice/
-rw-------  1 kabir kabir  326 Apr  9 22:03 mimeapps.list
-rw-rw-r--  1 kabir kabir  554 Mar 26 03:59 monitors.xml
-rw-rw-r--  1 kabir kabir  554 Mar 26 03:59 monitors.xml~
drwxr-xr-x  2 kabir kabir 4096 Mar 26 02:15 nautilus/
drwxrwxr-x  2 kabir kabir 4096 Mar 26 04:23 neofetch/
drwx------  2 kabir kabir 4096 Mar 26 02:15 pulse/
drwxrwxr-x  3 kabir kabir 4096 Apr 21 03:21 qBittorrent/
drwxr-x---  2 kabir kabir 4096 Mar 28 21:36 remmina/
-rw-rw-r--  1 kabir kabir  716 Apr 21 02:22 starship.toml
drwx------  2 kabir kabir 4096 Apr 21 03:21 totem/
-rw-rw-r--  1 kabir kabir  507 Apr 20 06:16 touch
drwx------  2 kabir kabir 4096 Mar 26 02:16 update-notifier/
-rw-------  1 kabir kabir  633 Mar 26 02:15 user-dirs.dirs
-rw-rw-r--  1 kabir kabir    5 Mar 26 02:15 user-dirs.locale
drwx------  2 kabir kabir 4096 Apr  8 18:55 yelp/

/home/kabir/.config 
&#10095; 

```

---

### Post by ne29914 on 2023-04-21
Looks OK to me.
But why are you running "exec bash" ?

---

### Post by kabirgandhiok on 2023-04-21
> **ne29914 said:**
> Looks OK to me.
But why are you running "exec bash" ?

To restart bash. But either way, bash is unable to read the file. I get the permission denied (os error 13) message whether I run source $HOME/.bashrc or exec bash or launch a new terminal. I do not get the permission denied error if I place the starship.toml file outside $HOME/.config, ie: anywhere inside $HOME

---

### Post by ne29914 on 2023-04-21
Don't really know what "starship" is. Is it this?
[https://starship.rs/](https://starship.rs/)

---

### Post by kabirgandhiok on 2023-04-21
> **ne29914 said:**
> Don't really know what "starship" is. Is it this?
[https://starship.rs/](https://starship.rs/)

Yes, that's what it is. I had installed the starship snap package. But in order to configure the shell prompt according to the docs, I need to place a starship.toml file inside $HOME/.config and point the environment variable STARSHIP_CONFIG to it.

starship config docs: [https://starship.rs/config/](https://starship.rs/config/)

To get starship to work, eval "$(starship init bash)" needs to be added to $HOME/.bashrc. It does work but I cannot get it to read the .toml file so that the configuration may take effect.

At the end of the ~/.bashrc I added:
```

eval "$(starship init bash)"
. "$HOME/.cargo/env"
export STARSHIP_CONFIG=$HOME/.config/starship.toml

```

But it doesn't read the file if I place it inside $HOME/.config

On launching a new terminal window I get the error:
```

[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

/home/kabir 
&#10095; 

```

I don't get that error and my configurations do take effect, if I place the starship.toml file outside of the $HOME/.config directory

---

### Post by #&amp;thj^% on 2023-04-21
Mark that "starship.toml" as "run as a program"
```
ls '/home/me/.config/starship.toml' 
/home/me/.config/starship.toml

```

---

### Post by kabirgandhiok on 2023-04-21
> **1fallen said:**
> Mark that "starship.toml" as "run as a program"
```
ls '/home/me/.config/starship.toml' 
/home/me/.config/starship.toml

```

I marked it as executable, but still get the permission denied (os error 13)

---

### Post by #&amp;thj^% on 2023-04-22
Sorry i forgot about you today please show this first:
```
ls -la '/home/me/.config/starship.toml'
```
and change "me" to your user name.
Mine:
```
ls -la '/home/me/.config/starship.toml' 
-rwxrwxr-x 1 me me 707 Apr 21 17:10 /home/me/.config/starship.toml

```
And lets take a peek at that toml file.
```
# Get editor completions based on the config schema
"$schema" = 'https://starship.rs/config-schema.json'

# Inserts a blank line between shell prompts
add_newline = false

# Use custom format
format = '''
[&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>](bold green)
[&#9474;](bold green)$directory$rust$package
[&#9492;&#9472;>](bold green) '''

# Wait 10 milliseconds for starship to check files under the current directory.
scan_timeout = 10

# Disable the blank line at the start of the prompt
#add_newline = false

# Set 'foo' as custom color palette
palette = 'foo'

# Define custom colors
[palettes.foo]
# Overwrite existing color
blue = '21'
# Define new color
mustard = '#af8700'

```
The screenshot shows the expected.

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> Sorry i forgot about you today please show this first:
```
ls -la '/home/me/.config/starship.toml'
```
and change "me" to your user name.
Mine:
```
ls -la '/home/me/.config/starship.toml' 
-rwxrwxr-x 1 me me 707 Apr 21 17:10 /home/me/.config/starship.toml

```

No worries, 
here is the output of the command you asked.
```

kabir@kabirsubuntu:~$ ls -la '/home/kabir/.config/starship.toml'
-rw-rw-r-- 1 kabir kabir 716 Apr 21 02:22 /home/kabir/.config/starship.toml

```

Just now looking at yours, I changed permissions of mine to chmod 775 but still get the error when I launch it.
```

kabir@kabirsubuntu:~$ ls -la '/home/kabir/.config/starship.toml'
-rwxrwxr-x 1 kabir kabir 716 Apr 21 02:22 /home/kabir/.config/starship.toml

```

On launching sharship
```

[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

/home/kabir 
&#10095; source ~/.bashrc
[ERROR] - (starship::config): Unable to read config file content: Permission denied (os error 13)

/home/kabir 
&#10095; 


```

I hope it helps.
Thanks!

---

### Post by #&amp;thj^% on 2023-04-22
You do close the terminal first to see the changes right?
Also will you show me your .bashrc file along with the toml file.
thanks

---

### Post by kabirgandhiok on 2023-04-22
the toml file:

```

 Get editor completions based on the config schema
"$schema" = 'https://starship.rs/config-schema.json'

# format = "->"
# Inserts a blank line between shell prompts
add_newline = true

#format = '''
#[&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>](bold green)
#[&#9474;](bold green)$directory$rust$package
#[&#9492;&#9472;>](bold green) '''


# Replace the '&#10095;' symbol in the prompt with '&#10140;'

[character]     # The name of the module we are configuring is 'character'
success_symbol = '[&#10140;](bold green)'      # The 'success_symbol' segment is being set to '&#10140;' with the color 'bold green'

# scan_timeout = 10

# Disable the package module, hiding it from the prompt completely
[package]
disabled = true


```

---

### Post by #&amp;thj^% on 2023-04-22
Try this, where your toml file reads "add_newline = true" change to "# add_newline = true"

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> You do close the terminal first to see the changes right?
Also will you show me your .bashrc file along with the toml file.
thanks

yes, I close and restart a new terminal to see the changes.

.bashrc:
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
case $- in
    *i*) ;;
      *) return;;
esac

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
if [ -z "${debian_chroot:-}" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi
# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color|*-256color) color_prompt=yes;;
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

# colored GCC warnings and errors
#export GCC_COLORS='error=01;31:warning=01;35:note=01;36:caret=01;32:locus=01:quote=01'

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
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
alias power_state='cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor'
eval "$(starship init bash)"
. "$HOME/.cargo/env"
export STARSHIP_CONFIG=$HOME/.config/starship.toml

```

Thanks and sorry for not putting it all in one post.

---

### Post by #&amp;thj^% on 2023-04-22
Think nothing of it. ;) I edit my posts a lot.
 Will you try the change to:
```
export STARSHIP_CONFIG=$HOME/.config/starship.toml
``` 
to now read:
```

eval "$(starship init bash)"
```
save and close and try the terminal again.

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> Try this, where your toml file reads "add_newline = true" change to "# add_newline = true"

still the same error. why is it that the toml file gets read and the changes apply if I place the file anywhere in $HOME but outside the .config directory? It's only when I put it in ~/.config that it doesn't work.

---

### Post by #&amp;thj^% on 2023-04-22
> **kabirgandhiok said:**
> still the same error. why is it that the toml file gets read and the changes apply if I place the file anywhere in $HOME but outside the .config directory? It's only when I put it in ~/.config that it doesn't work.
Ahh I just read where this is snap, and mine is not.
When I have the chance to avoid snaps I take it :)
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cargo install --list
cargo-update v13.0.1:
    cargo-install-update
    cargo-install-update-config
starship v1.14.2:
    starship
topgrade v10.3.3:
    topgrade

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> 

```
BTW If your interested I can show how to use cargo to install it.

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> Think nothing of it. ;) I edit my posts a lot.
 Will you try the change to:
```
export STARSHIP_CONFIG=$HOME/.config/starship.toml
``` 
to now read:
```

eval "$(starship init bash)"
```
save and close and try the terminal again.

ok, with this change I don't get the permission denied error, but the changes from the toml file don't get picked up. it shows the default starship prompt.

---

### Post by #&amp;thj^% on 2023-04-22
Recheck my toml file, or back yours up and replace with mine to check.

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> Ahh I just read where this is snap, and mine is not.
When I have the chance to avoid snaps I take it :)
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> cargo install --list
cargo-update v13.0.1:
    cargo-install-update
    cargo-install-update-config
starship v1.14.2:
    starship
topgrade v10.3.3:
    topgrade

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> 

```
BTW If your interested I can show how to use cargo to install it.

yes, please!! thanks!!

---

### Post by TheFu on 2023-04-22
I don't know the answer.

Snap packages don't like certain types of storage.  Is the file system for /home/ a native linux file system, say ext4?  I don't have all my HOME directories under /home/ and snap programs refuse to work on those systems.  The error I see is this:
```
$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209) for details.
```

If you have setup sharing of a directory through samba using a GUI, that can block some things from working too. About 2 yrs ago, we were trying to help someone for 3 weeks and it turned out that he'd shared the directory using his file manager "Sharing" right click.

Any chance the file has been chattr'd to +i, making it immutable?  **lsattr** can show attributes for a file.

---

### Post by #&amp;thj^% on 2023-04-22
> **kabirgandhiok said:**
> yes, please!! thanks!!

Please first remove/purge the snap package, for a clean slate.
when that's done run:
```
sudo apt install cargo
```
That will take a minute or two and now the fun when the cargo install completes run:
```

cargo install starship
```
Stop on any errors and post them here for me to see please.
This is what happens after, see [https://pastebin.ubuntu.com/p/PXsvbYYwKZ/](https://pastebin.ubuntu.com/p/PXsvbYYwKZ/)

---

### Post by Holger_Gehrke on 2023-04-22
Since starship installed through the 'curl ... | sh' command given on the website has no problem with a configuration in '~/.config/starship.toml' (with permissions 664), I suspect the fact you're using snap to install it is the reason for your problem. I might misunderstand something, but I think the AppArmor profiles of snaps denies access to hidden direct sub-directories of $HOME. That's why snaps have their configuration in directories in "$HOME/snap/" for example firefox has it's configuration in '~/snap/firefox/common/.mozilla/'.

Holger

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> Please first remove/purge the snap package, for a clean slate.
when that's done run:
```
sudo apt install cargo
```
That will take a minute or two and now the fun when the cargo install completes run:
```

cargo install starship
```
Stop on any errors and post them here for me to see please

I ran sudo snap remove --purge starship before attempting the reinstall with cargo.

I already had cargo on my system, so I just ran cargo install starship. build failed.
```

error: failed to run custom build command for `libz-ng-sys v1.1.8`

Caused by:
  process didn't exit successfully: `/tmp/cargo-install7SX8QJ/release/build/libz-ng-sys-5885ff41ac12f03c/build-script-build_zng` (exit status: 101)
  --- stdout
  CMAKE_TOOLCHAIN_FILE_x86_64-unknown-linux-gnu = None
  CMAKE_TOOLCHAIN_FILE_x86_64_unknown_linux_gnu = None
  HOST_CMAKE_TOOLCHAIN_FILE = None
  CMAKE_TOOLCHAIN_FILE = None
  CMAKE_GENERATOR_x86_64-unknown-linux-gnu = None
  CMAKE_GENERATOR_x86_64_unknown_linux_gnu = None
  HOST_CMAKE_GENERATOR = None
  CMAKE_GENERATOR = None
  CMAKE_PREFIX_PATH_x86_64-unknown-linux-gnu = None
  CMAKE_PREFIX_PATH_x86_64_unknown_linux_gnu = None
  HOST_CMAKE_PREFIX_PATH = None
  CMAKE_PREFIX_PATH = None
  CMAKE_x86_64-unknown-linux-gnu = None
  CMAKE_x86_64_unknown_linux_gnu = None
  HOST_CMAKE = None
  CMAKE = None
  running: cd "/tmp/cargo-install7SX8QJ/release/build/libz-ng-sys-9d9e141b7fa7637c/out/build" && CMAKE_PREFIX_PATH="" "cmake" "/home/kabir/.cargo/registry/src/github.com-1ecc6299db9ec823/libz-ng-sys-1.1.8/src/zlib-ng" "-DBUILD_SHARED_LIBS=OFF" "-DZLIB_COMPAT=OFF" "-DZLIB_ENABLE_TESTS=OFF" "-DWITH_GZFILEOP=ON" "-DCMAKE_INSTALL_PREFIX=/tmp/cargo-install7SX8QJ/release/build/libz-ng-sys-9d9e141b7fa7637c/out" "-DCMAKE_C_FLAGS= -ffunction-sections -fdata-sections -fPIC -m64" "-DCMAKE_C_COMPILER=/usr/bin/cc" "-DCMAKE_CXX_FLAGS= -ffunction-sections -fdata-sections -fPIC -m64" "-DCMAKE_CXX_COMPILER=/usr/bin/c++" "-DCMAKE_ASM_FLAGS= -ffunction-sections -fdata-sections -fPIC -m64" "-DCMAKE_ASM_COMPILER=/usr/bin/cc" "-DCMAKE_BUILD_TYPE=Release"

  --- stderr
  thread 'main' panicked at '
  failed to execute command: No such file or directory (os error 2)
  is `cmake` not installed?

  build script failed, must exit now', /home/kabir/.cargo/registry/src/github.com-1ecc6299db9ec823/cmake-0.1.50/src/lib.rs:1098:5
  note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
warning: build failed, waiting for other jobs to finish...
error: failed to compile `starship v1.14.2`, intermediate artifacts can be found at `/tmp/cargo-install7SX8QJ`
kabir@kabirsubuntu:~$ 


```

---

### Post by kabirgandhiok on 2023-04-22
> **Holger_Gehrke said:**
> Since starship installed through the 'curl ... | sh' command given on the website has no problem with a configuration in '~/.config/starship.toml' (with permissions 664), I suspect the fact you're using snap to install it is the reason for your problem. I might misunderstand something, but I think the AppArmor profiles of snaps denies access to hidden direct sub-directories of $HOME. That's why snaps have their configuration in directories in "$HOME/snap/" for example firefox has it's configuration in '~/snap/firefox/common/.mozilla/'.

Holger

ohh! yeah I was wondering why I have a snap directory in $HOME, and that dir does contain directories for all the snaps I have installed.

---

### Post by #&amp;thj^% on 2023-04-22
Easy enough:
```
sudo apt install cmake
```
Run the install again and have fun ;)

---

### Post by kabirgandhiok on 2023-04-22
> **TheFu said:**
> I don't know the answer.

Snap packages don't like certain types of storage.  Is the file system for /home/ a native linux file system, say ext4?  I don't have all my HOME directories under /home/ and snap programs refuse to work on those systems.  The error I see is this:
```
$ /snap/bin/lxc list
Sorry, home directories outside of /home are not currently supported. 
See [https://forum.snapcraft.io/t/11209](https://forum.snapcraft.io/t/11209) for details.
```

If you have setup sharing of a directory through samba using a GUI, that can block some things from working too. About 2 yrs ago, we were trying to help someone for 3 weeks and it turned out that he'd shared the directory using his file manager "Sharing" right click.

Any chance the file has been chattr'd to +i, making it immutable?  **lsattr** can show attributes for a file.

yes, its a native linux system, ext4, on /dev/sda2 and /dev/sda1 if /boot for efi
I have not setup sharing of any kind

lsattr returns:
```

kabir@kabirsubuntu:~/.config$ lsattr starship.toml
--------------e------- starship.toml

```

not sure what that means?

---

### Post by kabirgandhiok on 2023-04-22
> **1fallen said:**
> Easy enough:
```
sudo apt install cmake
```
Run the install again and have fun ;)

wow! it's working! and it is so much faster than the snap package, just as fast as running bash.
```

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> 


```
I had swapped out my toml for yours.
Thanks so much!!

---

### Post by #&amp;thj^% on 2023-04-22
Your very welcome, enjoy
in your first thread post under thread tools Mark as Solved to help others as well

---

