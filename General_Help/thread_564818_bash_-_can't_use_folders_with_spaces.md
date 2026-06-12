---
title: "bash - can't use folders with spaces"
date: 2007-10-01
forum: General Help
---

### Post by tvuolo on 2007-10-01
Hi, I'm having trouble with spaces in folder names using bash.

I open a Shell in Konsole and try to switch to a folder called "My Documents".  Normally I would type:
```
cd My\ Documents
```
or hit the tab key after a few chars.  But bash comes back with the following error:
bash: cd: My: No such file or directory
I have tried:
```
cd "My Documents"
```
Same error.

If I open a root shell in Konsole this works perfectly.  Is there some option I have possibly checked that is causing this?  I'm pretty sure this used to work.

I am running 32-bit Kubuntu Fiesty on a MacBook Pro C2D

---

### Post by bettlebrox on 2007-10-01
Are you sure your in the right directory? Can you do the following command in the directory where your doing this and show us the output:

ls -l |grep -i my

---

### Post by bodhi.zazen on 2007-10-01
LOL

You can :

1. My\ Documents (escape the white space with a \)

2. "My Documents" (use quotes)

3. Use tab completion. Start typing My<tab> ; when you hit the tab key you will automatically get My\ Documents

You need the full path, however

cd /media/windows/My\ Documents

??

---

### Post by hallowname on 2007-10-01
You mentioned escaped charachters in your first post, and you mentioned bash, you must know something is wrong... check the file /home/$(whoami)/.bashrc and other bash settings... this is very odd for bash to ignore escaped charachters...

---

### Post by tvuolo on 2007-10-02
> **hallowname said:**
> You mentioned escaped charachters in your first post, and you mentioned bash, you must know something is wrong... check the file /home/$(whoami)/.bashrc and other bash settings... this is very odd for bash to ignore escaped charachters...
Ah ha!  Messing around with KDE 4 was the culprit.  At some point either I put this in, or some KDE4 script put this in my .bashrc:
```
#For KDE4
function cd() {
  builtin cd $1 $2
  _f=`findup .my-setup`
  if test -n "$_f" -a "$_lastf" != "$_f"; then
    echo "Loading $_f"
    _lastf="$_f"
    source "$_f"
  fi
}
```
I Commented that out opened a new Shell and now I can navigate again!  Thanks Hallowname!

---

