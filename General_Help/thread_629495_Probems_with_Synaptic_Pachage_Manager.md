---
title: "Probems with Synaptic Pachage Manager"
date: 2007-12-02
forum: General Help
---

### Post by Anthro-techie on 2007-12-02
Ever since I upgraded to Gutsy synaptic package manager hasn't been working.  So here's what happens: when I try to download software from the Ubuntu archives via synaptic, I get an error message for each package that synaptic was trying to fetch, sometimes it just says it failed to fetch the package, but more frequently the error messages say that synaptic couldn't establish a connection with archives.ubuntu.com.  I have already tried downloading the packages directly from archives.ubuntu.com only to get the same error messages with the same problem when I try installing them from my desktop!   I have already disabled ipv6 support on the OS because it was causing problems before ( not sure if this has anything to do with it though), and already tried making synaptic work with both ipv6 enabled and disabled, still same problem though. Otherwise my wireless internet connection seems to work fine, other than also having problems getting Pidgin IM, as well as the gnome IRC chat client, to establish a connection very frequently (and, yes, I have already run through the ubuntu wireless internet troubleshooting guide and there doesn't appear to be any DNS related problems, unless I'm reading things wrong).

If anyone could help me out with this it would be much appreciated, even if you can just point me to another thread that will help. This is really irritating me.  I'm wondering if this is a proxy server problem (again, not sure if that has anything to it).

-James

---

### Post by bapoumba on 2007-12-02
So, are you behind a proxy ?

Please close synaptic, update-manager etc. and paste the output to:
```
sudo aptitude update
```

---

### Post by Anthro-techie on 2007-12-02
Its giving me the same error messages as before, " Could not connect to archive.ubuntu.com:80 (71.83.48.43), connection timed out." I'm not behind a proxy server.

---

### Post by bapoumba on 2007-12-03
Please paste the output to:
```
cat /etc/apt/apt.conf
```
or look into Synaptic > Preferences > Network if you have a proxy declared.

You can also check the **/etc/environment** and **/etc/bash.bashrc** files for a proxy.

---

### Post by Anthro-techie on 2007-12-03
cat: /etc/apt/apt.conf: No such file or directory.  I checked synaptic, and there is no proxy configuration, its a direct connection to the ISP.

---

### Post by metalheart on 2007-12-03
Does the command apt-get update give any errors?

I missed that post, already answered.

---

### Post by Anthro-techie on 2007-12-13
Well, this is what I got.  So hwere do I go from here?

sudo apt-get update

Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy Release.gpg
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg                                
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg                      
  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                 
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US              b
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US    
  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-security Release.gpg
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release.gpg)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to security.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-security/Release.gpg)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/Release.gpg)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to archive.ubuntu.com:80 (71.85.2.236), connection timed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by oldos2er on 2007-12-13
>>cat /etc/apt/apt.conf<<

 In Ubuntu, the file you're looking for is named /etc/apt/apt-file.conf

---

### Post by Anthro-techie on 2007-12-14
Same error message as before:

cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory

---

### Post by Anthro-techie on 2007-12-14
oops, made mistake.  heres the one you wanted me to find:

cat /etc/apt/apt-file.conf
cat: /etc/apt/apt-file.conf: No such file or directory

still same error message as before though. . .

:(

---

### Post by moogyd on 2007-12-14
Hi,

I was about to hijack the thread with "I am having the same problem" with update manager (and not package manager).

However, I did a quick experiment, and used package manager to download a package (any package, I just wanted to show that this worked).

After I did this (or after I tried the command line rather than GUI), it worked :confused:

The only minor isse is that I got warnings that none of the upgrades could be validated.

So, in conclusion, I had the same problem (for a number of days), and now it works (within that last 1/2 hour).

So, I suggest you try again,

Steven

---

### Post by oldos2er on 2007-12-15
Anthro-techie, can you post the output of

cat /etc/apt/sources.list

?

---

### Post by Anthro-techie on 2007-12-15
So yeah. . . here's an example of whats happening when I try using synaptic.  So why am I not cconnecting to archive.ubuntu.com?

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/iceape/iceape-browser_1.1.4-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/iceape/iceape-browser_1.1.4-1ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (71.99.192.94), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/iceape/iceape-mailnews_1.1.4-1ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/iceape/iceape-mailnews_1.1.4-1ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (71.99.192.94), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/i/iceape/iceape_1.1.4-1ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/i/iceape/iceape_1.1.4-1ubuntu2_all.deb)
  Could not connect to archive.ubuntu.com:80 (71.99.192.94), connection timed out


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.46-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/w/wine/wine_0.9.46-0ubuntu1_i386.deb)
  Could not connect to archive.ubuntu.com:80 (71.99.192.94), connection timed out

help. . .

---

### Post by bapoumba on 2007-12-16
This error is typical of a non-functional proxy set up. Did you check the other files I suggested? Did you play around with anon proxy? Some game?

---

### Post by Anthro-techie on 2007-12-16
Moogyd: when I use synaptic via the command line I get the same exact errors as before where it says the connection times out with archives.ubuntu.com.

Oldos2er: Here's what I get when I try to display the file the asked me to look at:

cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted

Bapoumba:  I already tried looking at the things file you asked me to,  the details are posted further back in the thread.  When I tried looking at the files is said "no such file or directory."  And when I tried sudo apt-get update I got just the same errors as before when using synaptic.

let me know what to try next. . . I no nothing about proxy setups. . .

---

### Post by bapoumba on 2007-12-16
> **bapoumba said:**
> Please paste the output to:
```
cat /etc/apt/apt.conf
```
or look into Synaptic > Preferences > Network if you have a proxy declared.

You can also check the **/etc/environment** and **/etc/bash.bashrc** files for a proxy.

There were other files to look at:
```
cat /etc/environment
cat /etc/bash.bashrc
```

And Synaptic > Preferences > Network

You may have a proxy declared there for some reason.

If those files are clear, we'll have to digg a little more.

---

### Post by Anthro-techie on 2007-12-16
cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"

cat /etc/bash.bashrc
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

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
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e $HOME/.sudo_as_admin_successful ]; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
        cat <<-EOF
        To run a command as administrator (user "root"), use "sudo <command>".
        See "man sudo_root" for details.

        EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found ]; then
        function command_not_found_handle {
                /usr/bin/python /usr/lib/command-not-found -- $1
                return $?
        }
fi

- When I looked in Synaptic/perferences/network, I had direct connection to the internet selected rather than manual proxy configuration.

---

### Post by bapoumba on 2007-12-16
Looks to me it is a network problem (from googling around).
What type of router do you have?

Sometimes synaptic and apt-get have hard time getting the DNS from ISPs.
What is the output to (this should show the DNS you are using, usually the router IP):
```
cat /etc/resolv.conf
```

Please try to use OpenDNS:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
I use them.

---

### Post by Anthro-techie on 2007-12-16
cat /etc/resolv.conf
nameserver 192.168.10.1

so should I use "gksudo /etc/resolv.conf"  and switch it to those other addresses?

---

### Post by Anthro-techie on 2007-12-16
Thank you bapoumba! Problem was solved after changing the DNS like you said.  However, the DNS name servers goes back to the original (the one assigned by my ISP) in  /etc/resolv.conf and network manager everytime I restart my computer! :(  Is there a way I can make those my permanent DNS nameservers so I don't have to switch them back every time after restarting when  I want to use synaptic or connect to the Ubuntu IRC chat channel?

---

