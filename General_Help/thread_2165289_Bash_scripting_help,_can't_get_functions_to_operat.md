---
title: "Bash scripting help, can't get functions to operate and not sure why."
date: 2013-08-04
forum: General Help
---

### Post by yay101 on 2013-08-04
So, the problem is that only segments of this script work (there is much more to it then what i posted) as you can see i have tried various forms in which to format this, and very little has worked, functions don't seem to work at all, regardless of where they are called from. I have done a bunch of C before but this is doing my head in, ive looked at many examples that are formatted identically and work, but mine does not.

Please help, going crazy.

```
#!/bin/bash


echo "This script only understands yes and no, please keep to these answers where appropriate."


#read saved path if it exists

if [ ! -f ~/.contentpath]; then touch ~/.contentpath; else PATH=[$(head -n 0 ~/.contentpath)]; fi



Testinstalled () {

if [$PATH=""]; then

Install

else Help

fi

}


Help () {

echo "Where * is the name of a app managed by this script."

echo "Usage: content install|help|restart|update*|start*|autostarton|autostartoff"

echo "More to come"

}

#set a path and download files



Install () {

if [$PATH=""]; then

echo "Please enter a path to install the apps to, ~/ (home) is nominal."

read PATH

else echo "already installed!"

fi



echo "Install sabnzbd?"

read SABNZBD

echo "Install sickbeard?"

read SICKBEARD

echo "Install couchpotato?"

read COUCHPOTATO

echo "Install mylar?"

read MYLAR

echo "Install headphones?"

read HEADPHONES



if [$SABNZBD="yes"]
then updatesabnzbd

else :

fi



if [$SICKBEARD="yes"]

then updatesickbeard

else :

fi



if [$COUCHPOTATO="yes"]

then updatecouchpotato

else :

fi



if [$MYLAR="yes"]

then updatemylar

else :

fi


if [$HEADPHONES="yes"]

then updateheadphones

else :

fi



echo "All selected options have been installed."

}

```

---

### Post by Lars Noodén on 2013-08-04
Don't the functions all have to go first, before the part of the script they are called from?

---

### Post by Vaphell on 2013-08-04
why on earth is your code so spaced out o.O :-)

the most obvious failing is improper syntax of conditions. You see, in bash [x=y] is space dependent.
```
if [[COLOR="#0000FF"]_[/COLOR]"$COUCHPOTATO"[COLOR="#0000FF"]_[/COLOR]=[COLOR="#0000FF"]_[/COLOR]"yes"[COLOR="#0000FF"]_[/COLOR]]

```
**[] **conditions are not parsed like you would expect in other programming languages, in shells **[ **is simply a command and it gets a list of parameters just like any other  (*]* is simply a closing marker). Obviously parameters have to be delimited with spaces
in other words it's "[" "$couchpotato" "=" "yes" "]"
Given that [ ] is an ordinary command you don't even have to use it with *if* if you feel like it
```
$ [ "a" = "a" ] && echo true || echo false
true
$ "[" "a" "=" "a" "]" && echo true || echo false
true
```



also always put $var in "". If the value is null or has whitespaces you get unexpected results
unquoted variable in **[ $null = yes ]** expands to nothing at all (not empty string) so the result is** [ = yes ] **which doesn't make sense

```
$ x=''
$ [ $x = "a" ] && echo true || echo false
**bash: [: =: unary operator expected**
false
[ "$x" = "a" ] && echo true || echo false
false
```

---

### Post by kevdog on 2013-08-04
vaphell

Nice advice.  I read somewhere that variables should also include brackets but is this overkill.  Let me give you an example using your code above

$ x=''
[ "${x}" = "a" ] && echo true || echo false

Are these brackets necessary?

---

### Post by prodigy_ on 2013-08-04
Curly brackets are optional unless you need them for disambiguation (i.e. to denote where the variable name ends in a string). Example:
```
$foo="${test}string"
```

---

### Post by Vaphell on 2013-08-04
yes, mostly optional. To disambiguation stuff I'd add the case of positional parameters. They can go as $1... $9 but ${10} because $10 is treated as **$1**0
```
$ test_params() { echo "[$1][$10][${10}]"; }
$ test_params a b c d e f g h i j k
[a][a0][j]

```



curly brackets also are used for many nifty operations on the value
eg
```
${x//a/b} #replace all a's with b's
${x^} #capitalize first char
${x^^} #capitalize all
```

```
$ x=baobab
$ echo ${x//a/b} ${x^} ${x^^}
bbobbb Baobab BAOBAB
```
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

you could think of ${x} as a no-modifier version of the concept which shorthands to $x for convenience :-)

---

### Post by yay101 on 2013-08-06
Thanks heaps guys, this should get me going again when i get some time to have another go. You have actually been more helpful than the bash pages.

---

### Post by yay101 on 2013-08-06
Also it was so spaced out because it was copied from notepad as i was on my windows machine, sorry it is so ugly haha.

---

### Post by Vaphell on 2013-08-06
> You have actually been more helpful than the bash pages. 

well, man pages are a collection of facts, sorted by category, they sort of expect you to be on the same page when it comes to vocabulary and knowledge how the system works and are most useful when you need a detail or two that you know it's there somewhere. Overwhelming amount of meticulously sorted facts does nothing of value to noobs so they are better off with a 'getting started' style of prose where concepts are gradually introduced in plain language and practised. You don't learn English from reading a dictionary, right? :-)

---

