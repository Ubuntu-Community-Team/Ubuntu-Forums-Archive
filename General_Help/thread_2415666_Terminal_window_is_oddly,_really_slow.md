---
title: "Terminal window is oddly, really slow"
date: 2019-03-29
forum: General Help
---

### Post by maxoa on 2019-03-29
Greetings,

I can not recall what I did before but my when I open up my terminal window it takes more than a full second to get the command line.  

I have commented out almost all of the lines in my .bashrc with no change, .bashrc = 1.3 kB.  

```

# A minimal BASH profile.

# Extend the program search PATH and add the ~/bin folder.
export PATH=~/bin:$PATH

# Makes the prompt much more user friendly.
# But I do agree that the command to set it up looks a bit crazy.
export PS1='\[\e]0;\w\a\]\n\[\e[32m\]\u@\h \[\e[33m\]\w\[\e[0m\]\n\$ '

# This is required for Entrez Direct to work.
# Disables strict checking of an encryption page.
export PERL_LWP_SSL_VERIFY_HOSTNAME=0

# This is necessary for the sort to work correctly.
export LC_ALL=C

# Alias definitions.
# Put all your aliases into a ~/.bash_aliases, 
# instead of adding them here directly.
# See: /usr/share/doc/bash-doc/examples bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi


# added by Anaconda3 5.3.0 installer
# >>> conda init >>>
# !! Contents within this block are managed by 'conda init' !!
__conda_setup="$(CONDA_REPORT_ERRORS=false '/home/mcc/anaconda3/bin/conda' shell.bash hook 2> /dev/null)"
if [ $? -eq 0 ]; then
    \eval "$__conda_setup"
else
    if [ -f "/home/mcc/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/home/mcc/anaconda3/etc/profile.d/conda.sh"
        CONDA_CHANGEPS1=false conda activate base
    else
        \export PATH="/home/mcc/anaconda3/bin:$PATH"
    fi

```



I backed up my .bash_history so it is now 0B, 

my .bash_profile is 90B 
```

if [ -f ~/.bashrc ]; then
   source ~/.bashrc
fi
```

and my .bash_logout is 220B.
```

if [ "$SHLVL" = 1 ]; then
    [ -x /usr/bin/clear_console ] && /usr/bin/clear_console -q
fi
```

I have run ClamScan, I have Conda ,... just really the basics nothing odd.

Could I have a virus?

I do not even know where to start beyond that basics that I have mentioned above.

Any suggestions would help.

---

### Post by him610 on 2019-03-30
> ...takes more than a full second to get the command line
If you are concerned about time then why not configure your system for terminal (command line) to be initiated as the system comes to life.

---

