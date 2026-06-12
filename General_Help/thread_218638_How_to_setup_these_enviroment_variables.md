---
title: "How to setup these enviroment variables?"
date: 2006-07-18
forum: General Help
---

### Post by bladehaze on 2006-07-18
I use Ubuntu 5.10, and I want to set the following global enviroment variable

XMODIFIERS="@im=SCIM"
GTK_IM_MODULE="scim"
XIM_PROGRAM="scim -d"

Here are the ways I failed.

1. Add 

XMODIFIERS="@im=SCIM"
GTK_IM_MODULE="scim"
XIM_PROGRAM="scim -d"

in /etc/environment, logout, login, it doesn't work

2. Add 

export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"

in ~/home/.xinitrc, it doesn't work

3. Add 
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"

in ~/.gnome2/session-manual, logout, login, it doesn't work. 

4. Add
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"

in a file /etc/X11/Xsession.d/75custom-scim_init, not working. 

5. I put 
export XMODIFIERS="@im=SCIM"
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"

in a file, and execute it, it does not work.

So, any information would be appreciated here.

---

### Post by schilcha on 2006-07-19
I have the file **.gnomerc** in my home-directory, where I set environment for my gnome-session. Here's my file:
```

export PATH="$PATH:$HOME/bin:$HOME/local/bin"
export R_HISTFILE=$HOME/.Rhistory
export R_HOME=$HOME/local/lib/R
export TEXINPUTS="~/local/share/texmf//:"

```

---

### Post by AZzKikR on 2006-07-19
If the environment variables are applicable to the whole system, I think you can better add them to /etc/profile.

---

