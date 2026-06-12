---
title: "Duplicate lines in bash history"
date: 2006-11-02
forum: General Help
---

### Post by kyldere on 2006-11-02
Hello.

I seem to recall not having duplicate commands show up in the bash history before I installed Edgy. I have this line set in my ~.bashrc

   export HISTCONTROL=ignoredups

but it doesn't seem to do anything. Am I looking in the wrong place to set this function. Thanks.

---

### Post by bollix47 on 2006-11-02
From the man page: 


A value of **ignoredups**  causes  lines matching the previous history entry to not be saved.  
A value of **erasedups** causes all previous lines matching the current line to be removed from the history list before that line  is  saved.


Maybe try changing it to erasedups?

---

### Post by kyldere on 2006-11-02
That fixed it. Thanks.

---

### Post by wuch on 2006-11-11
Hi,

I still can't get ignoredups nor erasedups to work. My .bashrc file looks like this. Anyone have suggestions? Thanks.

# Source global definitions
if [ -f /etc/bashrc ]; then
        . /etc/bashrc
fi
# .bashrc

export HISTCONTROL=erasedups

---

### Post by wuch on 2006-11-11
Oh, and the funny thing is that if I use ignorespace, then ignore space would work.

---

### Post by chupacerveza on 2007-01-08
Re: Oh, and the funny thing is that if I use ignorespace, then ignore space would work.

erasedups first appeared in bash 3.0

What does bash --version show for you? (Ignorespace came in earlier versions.)

---

