---
title: "Doubleclicking with a Wacom stylus doesn't work"
date: 2007-04-22
forum: General Help
---

### Post by HarmH on 2007-04-22
In Dapper and Edgy I used the following code to map one of the buttons on my Wacom stylus to do a double click (comes from my xorg.conf):```
  Option        "Button2"        "17"
```However, in Feisty this code doesn't work anymore. I already tried replacing the "17" with "dblclick" and "dblclick 1" as described on [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom), but it still doesn't work. How can I make this work again?

---

### Post by HarmH on 2007-04-30
Is there no-one who knows how to do this? :)

---

### Post by fragos on 2007-04-30
Do "xsetwacom list param" and you get instructions for setting a wide variety of things.  There's also a Sourceforge project called expresskeys which gives you some different options.

---

### Post by Erikhh on 2007-05-02
I have excactely the same problem, and I have tried to use xsetwacom. It doesn't work either

---

### Post by HarmH on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: 112310 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **fragos said:**
> Do "xsetwacom list param" and you get instructions for setting a wide variety of things.  There's also a Sourceforge project called expresskeys which gives you some different options.
The xsetwacom thingie doesn't work, as I already mentioned in my startpost. I have tried all kinds of different options:[list][*]xsetwacom set stylus Button2 "dblclick 0"
[*]xsetwacom set stylus Button2 "dblclick 1"
[*]xsetwacom set stylus Button2 "dblclick 2"
[*]xsetwacom set stylus Button2 "2"
[*]xsetwacom set stylus Button2 "17"[/list]They all don't work and double clicking still doesn't work. I am getting the strong feeling this is a bug (so I reported it), especially since Erikhh has the same problem.

---

### Post by fragos on 2007-05-04
xsetwacom list param includes examples that add the command set before stylus.

xsetwacom set stylus Button3 "dblclick 1"

---

### Post by HarmH on 2007-05-05
I know :) . It was a mistake not to add the 'set' command to the above mentioned commands. While I was trying al the relevant options, I actually did use the 'set' command.

---

### Post by fragos on 2007-05-05
I have to admit that this is my first Wacom tablet and I'm still in learning mode.  I have a Graphire4.  Before learning about xsetwacom I discovered expresskeys which allowed me to set the buttons and scroll wheel on the pad itself.  I'm still using it.  xsetwacom however looks promising and development of it and expresskeys is active.  expresskeys can be found on sourceforge.

---

### Post by Eiríkr on 2008-01-23
Running Kubuntu Gutsy Gibbon 7.10.

Try entering: 

```
xsetwacom set stylus button1 196609
```

I'm not sure why (undoubtedly a bug somewhere), but entering "dblclick [any number]" seems to produce "dblclick 0", as confirmed by:

```
xsetwacom -x get stylus button1
```

Entering the specific numeric value above seems to equate to "dblclick 1".  I assume that "196610" would be "dblclick 2", but I haven't tested it.

Cheers,

---

