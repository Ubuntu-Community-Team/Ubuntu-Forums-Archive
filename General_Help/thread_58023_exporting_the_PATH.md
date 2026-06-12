---
title: "exporting the PATH"
date: 2005-08-18
forum: General Help
---

### Post by kes on 2005-08-18
Hello,
I'm looking for some help in order to make run one specific application - [MuPad](http://mupad.de/about.html) 
I've made a deb-package from initial rmp, so the binaries were installed in /usr/local/MuPADscilab-3.1.1/linux/bin

now, accordind to the [instruction](http://www.mupad.de/download/INSTALL-unix) from the creators I should make some modifications, namely:
> 
{snip}
Please extend your PATH environment variable in order to start
    MuPAD:

      (for tcsh/csh in ~/.cshrc)
         set path = ($path /usr/local/MuPAD/share/bin)

      [B][COLOR=Navy](for sh/bash/ksh in ~/.profile)
         PATH=$PATH:/usr/local/MuPAD/share/bin
         export PATH[/COLOR][/B]

    Now you can start 'mupad' or 'xmupad' (make sure that you reread
    the initialisation files first).
{snip}

In my case it should be
[I]PATH=$PATH:/usr/local/MuPADscilab-3.1.1/linux/bin
export PATH
[/I]
I've found 2 files:
first, dot.profile in /usr/share/base-files/  which contains

> # ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

mesg n

second, profile in /etc/
> # /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "`id -u`" -eq 0 ]; then
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11"
else
  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
fi

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
	. /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

export PATH

umask 022

So, the question is in which one I should insert these lines? 
And does it matter where exactly put them (in the end, or in the middle) or does it not?

Thank you.

P.S. sorry, if there are too many details, I just want to be sure, since I'm not familiar with these things.

---

### Post by charlieg on 2005-08-18
Stick them in ~/.profile if it's just for your user account.  If you want it active for all accounts on the computer, stick it in /etc/profile instead.

---

