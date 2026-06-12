---
title: "HOWTO: Give your Terminal some Swagger! Cool Login Screen"
date: 2013-02-03
forum: General Help
---

### Post by strid3r on 2013-02-03
I wanted to be greeted by a terminal when I first logged in,
and after having easily achieved that I got bored and decided
that I want the terminal to have a cool CIA-esque text display.
What resulted is the following code, which I added to the end of
my ~/.bashrc file. If you want something similar, just replace
 "VOAR" with your username and you'll feel like you're 007 every
 time you open a terminal.

Instructions: just open up your .bashrc file and paste the
following at the end. Replace VOAR with your username. (You may
 have to adjust the number of "*" to line up the box correctly).

```
gedit ~/.bashrc
```

```

## LOGIN SCREEN MESSAGE
printf \#
sleep .2
printf \!
sleep .2
printf \$
sleep .2
printf @
sleep .2
printf \&
sleep .2
printf \*
sleep .2
printf \(
sleep .2
printf \\
sleep .2
printf =
sleep .2
printf \+
sleep .2
echo -ne '\b\b\b\b\b\b\b\b\b\b\b\b\b'
printf 'D'
sleep .2
printf 'E'
sleep .2
printf 'C'
sleep .2
printf 'R'
sleep .2
printf 'Y'
sleep .2
printf 'P'
sleep .2
printf 'T'
sleep .2
printf 'I'
sleep .2
printf 'N'
sleep .2
printf 'G'
sleep .2

# DOT DOT DOT
for i in {1..3}
do
 printf .
 sleep .5
done

# ERASE
echo -ne '\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b'
printf "                                                       "

# FIRST LINE
clear
for i in {1..67}
do
 printf \*
 sleep .005
done
echo ""

# SECOND LINE
for i in {1..67}
do
 printf \*
 sleep .005
done
echo ""
for i in {1..17}
do
 printf \*
 sleep .005
done
for i in {1..33}
do
 printf " "
 sleep .005
done
for i in {1..17}
do
 printf \*
 sleep .005
done
echo ""
#echo "*******************************************************************"
#echo "*******************************************************************"
#echo "*****************                                 *****************"
sleep .05
echo "*****************          WELCOME VOAR           *****************"
sleep .005
echo "*****************      ROOT ACCESS GRANTED        *****************"
sleep .005
echo "*****************   ENTERING ENCRYPTED HOME DIR   *****************"
echo "*****************                                 *****************"
echo "*******************************************************************"
echo "*******************************************************************"
echo
echo

```

---

### Post by rnerwein on 2013-02-03
> **strid3r said:**
> I wanted to be greeted by a terminal when I first logged in,
and after having easily achieved that I got bored and decided
that I want the terminal to have a cool CIA-esque text display.
What resulted is the following code, which I added to the end of
my ~/.bashrc file. If you want something similar, just replace
 "VOAR" with your username and you'll feel like you're 007 every
 time you open a terminal.

Instructions: just open up your .bashrc file and paste the
following at the end. Replace VOAR with your username. (You may
 have to adjust the number of "*" to line up the box correctly).

```
gedit ~/.bashrc
``````

## LOGIN SCREEN MESSAGE
printf \#
sleep .2
printf \!
sleep .2
printf \$
sleep .2
printf @
sleep .2
printf \&
sleep .2
printf \*
sleep .2
printf \(
sleep .2
printf \\
sleep .2
printf =
sleep .2
printf \+
sleep .2
echo -ne '\b\b\b\b\b\b\b\b\b\b\b\b\b'
printf 'D'
sleep .5
printf 'E'
sleep .5
printf 'C'
sleep .5
printf 'R'
sleep .5
printf 'Y'
sleep .5
printf 'P'
sleep .5
printf 'T'
sleep .5
printf 'I'
sleep .5
printf 'N'
sleep .5
printf 'G'
sleep .5

# DOT DOT DOT
for i in {1..3}
do
 printf .
 sleep .5
done

# ERASE
echo -ne '\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b\b'
printf "                                                       "

# FIRST LINE
clear
for i in {1..67}
do
 printf \*
 sleep .005
done
echo ""

# SECOND LINE
for i in {1..67}
do
 printf \*
 sleep .005
done
echo ""
for i in {1..17}
do
 printf \*
 sleep .005
done
for i in {1..33}
do
 printf " "
 sleep .005
done
for i in {1..17}
do
 printf \*
 sleep .005
done
echo ""
#echo "*******************************************************************"
#echo "*******************************************************************"
#echo "*****************                                 *****************"
sleep .05
echo "*****************          WELCOME VOAR           *****************"
sleep .005
echo "*****************      ROOT ACCESS GRANTED        *****************"
sleep .005
echo "*****************   ENTERING ENCRYPTED HOME DIR   *****************"
echo "*****************                                 *****************"
echo "*******************************************************************"
echo "*******************************************************************"
echo
echo

```
that's a joke - isn't it ????

---

### Post by strid3r on 2013-02-04
@rnerwein

If you don't like it, you don't have to add it to your .bashrc


Update:

I just edited the animation to speed it up, as it does get a little bothersome when you have a lot of things to do. I just hit Ctrl+C to cancel the animation and things go back to normal.

---

