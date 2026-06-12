---
title: "Question about .bashrc and .bash_profile"
date: 2018-03-22
forum: General Help
---

### Post by again? on 2018-03-22
I add this to ~/.bashrc to display some info when I login via ssh.
(nothing special... just a customized banner really)
```
# info when no $DISPLAY
if [ -z "$DISPLAY" ]; then
	printf "Host: $HOSTNAME \nOS: $(lsb_release -s -d)"  | lolcat -as 64
	echo
		# last login
		last -a -n2 | sed -n 2p | awk '{print "Last Login:",$1,"\nTime:",$3,$4,$5,$6,"\nFrom:",$NF}'| lolcat -as 64
	echo
		/usr/lib/update-notifier/apt-check --human-readable  | lolcat -as 64
		if [ -x /usr/lib/update-notifier/update-motd-reboot-required ]; then
			exec /usr/lib/update-notifier/update-motd-reboot-required | lolcat -as 64
		fi
read -t 10
clear
fi
```

I noticed that if I have a **~/.bash_profile**, this file is read instead of **~/.bashrc**, when logging in via ssh.
**~/.bash_profile** doesn't appear to be read when I log in to a normal X session.
Should I use **~/.bash_profile** for my purpose?
What is the actual purpose of ~/.bash_profile?

---

### Post by TheFu on 2018-03-22
Startup files all have different purposes. Some are used only for "login" sessions.  Others are used with every new shell program startup.   I always have to check the manpages to be certain I'm using the correct .file for the purpose I want.

 ```
      --noprofile
              Do not read either the system-wide startup file /etc/profile  or
              any   of  the  personal  initialization  files  ~/.bash_profile,
              ~/.bash_login, or ~/.profile.   By  default,  bash  reads  these
              files  when  it  is  invoked  as  a  login shell (see INVOCATION
              below).
```
is from the bash manpage.

Interactive shells and non-interactive shells read different files.  It isn't worth quoting here. The manpage is pretty clear.

---

### Post by monkeybrain20122 on 2018-03-22
My experience is that  in normal Xsession both terminal and GUI applications read environmental variables from .profile but only terminal reads from .bashrc.

---

### Post by again? on 2018-03-22
I'm testing using a ~/.bash_profile including my bash aliases.
eg
_~/.bash_profile_
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

if [ -z "$DISPLAY" ]; then
	printf "Host: $HOSTNAME \nOS: $(lsb_release -s -d)"  | lolcat -as 64
	echo
		# last login
		last -a -n2 | sed -n 2p | awk '{print "Last Login:",$1,"\nTime:",$3,$4,$5,$6,"\nFrom:",$NF}'| lolcat -as 64
	echo

		/usr/lib/update-notifier/apt-check --human-readable  | lolcat -as 64
		if [ -x /usr/lib/update-notifier/update-motd-reboot-required ]; then
			exec /usr/lib/update-notifier/update-motd-reboot-required | lolcat -as 64
		fi
	read -t 10
clear
fi
```
Seems to do as I want. ~/.bash_profile is read from ssh and tty console logins.

---

