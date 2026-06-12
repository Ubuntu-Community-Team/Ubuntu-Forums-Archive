---
title: "Change Machine Name in Terminal into Bold"
date: 2013-08-30
forum: General Help
---

### Post by Abd_el_Rahman_Magdy on 2013-08-30
Hi there,

I have been able to change how my terminal looks using the profile preference. However, I need to make the machine name appear in bold and I don't know how to do that. The thing is, when I am working in terminal, sometimes I get lost between these lines and I can't easily find where my original command line is. Therefore, having the machine name written in bold will operate as a guide for me. Is there a way to do this???

---

### Post by sisco311 on 2013-08-30
Hi and welcome to the forums!

Assuming that you use bash as your user shell, you can change the prompt by editing the value of the PS1 variable. By default it's defined in the ~/.bashrc file. For detailed instructions please check out: [uhelp]community/CustomizingBashPrompt[/uhelp].

Here is how I set mine:
```

txtgreen=$(tput setaf 2)
txtdefault=$(tput setaf 9)

abold=$(tput bold)
areset=$(tput sgr0)

PS1='${abold}${txtgreen}[\u@\h \W\$ ${txtdefault}${areset}'

```

As you can see, instead of hard-coded ANSI codes I use the tput command ;)
[http://wiki.bash-hackers.org/scripting/terminalcodes](http://wiki.bash-hackers.org/scripting/terminalcodes)

---

### Post by CaptainMark on 2013-08-31
Check out this site for the easy way to generate a nice looking prompt [http://www.kirsle.net/wizards/ps1.html](http://www.kirsle.net/wizards/ps1.html)

---

### Post by nativehound on 2013-08-31
I use a two liner
```
[pwd 9 files, 40Kb]/var/spool
[01:38 AM]$:

```

This is the color code index and "PS1=" i use.
```
# Reset
Color_Off='\e[0m'       # Text Reset

# Regular Colors
Black='\e[0;30m'        # Black
Red='\e[0;31m'          # Red
Green='\e[0;32m'        # Green
Yellow='\e[0;33m'       # Yellow
Blue='\e[0;34m'         # Blue
Purple='\e[0;35m'       # Purple
Cyan='\e[0;36m'         # Cyan
White='\e[0;37m'        # White

# Bold
BBlack='\e[1;30m'       # Black
BRed='\e[1;31m'         # Red
BGreen='\e[1;32m'       # Green
BYellow='\e[1;33m'      # Yellow
BBlue='\e[1;34m'        # Blue
BPurple='\e[1;35m'      # Purple
BCyan='\e[1;36m'        # Cyan
BWhite='\e[1;37m'       # White

# Underline
UBlack='\e[4;30m'       # Black
URed='\e[4;31m'         # Red
UGreen='\e[4;32m'       # Green
UYellow='\e[4;33m'      # Yellow
UBlue='\e[4;34m'        # Blue
UPurple='\e[4;35m'      # Purple
UCyan='\e[4;36m'        # Cyan
UWhite='\e[4;37m'       # White

# Background
On_Black='\e[40m'       # Black
On_Red='\e[41m'         # Red
On_Green='\e[42m'       # Green
On_Yellow='\e[43m'      # Yellow
On_Blue='\e[44m'        # Blue
On_Purple='\e[45m'      # Purple
On_Cyan='\e[46m'        # Cyan
On_White='\e[47m'       # White

# High Intensty
IBlack='\e[0;90m'       # Black
IRed='\e[0;91m'         # Red
IGreen='\e[0;92m'       # Green
IYellow='\e[0;93m'      # Yellow
IBlue='\e[0;94m'        # Blue
IPurple='\e[0;95m'      # Purple
ICyan='\e[0;96m'        # Cyan
IWhite='\e[0;97m'       # White

# Bold High Intensty
BIBlack='\e[1;90m'      # Black
BIRed='\e[1;91m'        # Red
BIGreen='\e[1;92m'      # Green
BIYellow='\e[1;93m'     # Yellow
BIBlue='\e[1;94m'       # Blue
BIPurple='\e[1;95m'     # Purple
BICyan='\e[1;96m'       # Cyan
BIWhite='\e[1;97m'      # White

# High Intensty Backgrounds
On_IBlack='\e[0;100m'   # Black
On_IRed='\e[0;101m'     # Red
On_IGreen='\e[0;102m'   # Green
On_IYellow='\e[0;103m'  # Yellow
On_IBlue='\e[0;104m'    # Blue
On_IPurple='\e[10;95m'  # Purple
On_ICyan='\e[0;106m'    # Cyan
On_IWhite='\e[0;107m'   # White

# userset- time \@, user \u, working dictory \w  main prompt
export PS1="\[$ICyan\][pwd \$(/bin/ls -1 | /usr/bin/wc -l | /bin/sed 's: ::g') files, \$(/bin/ls -lah | /bin/grep -m 1 total | /bin/sed 's/total //')b]\[$IYellow\]\w\[$ICyan\]\n[\@]\[$IYellow\]\$\[$BIGreen\]:$RS"
export PS2="$HC$FYEL&gt; $RS"
```

---

### Post by Abd_el_Rahman_Magdy on 2013-09-01
Thank you guys... I'll test your methods when I am back home since I don't have my laptop now.. Thank you all very much

---

