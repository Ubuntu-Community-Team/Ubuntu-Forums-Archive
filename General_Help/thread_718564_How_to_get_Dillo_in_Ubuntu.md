---
title: "How to get Dillo in Ubuntu"
date: 2008-03-08
forum: General Help
---

### Post by Indy452 on 2008-03-08
How do I go about getting Dillo the simple browser in Ubuntu?

And if I get it will it be located in the internet tab?

I'm using Ubuntu 7.1

Thank you.

Neal

---

### Post by jeffus_il on 2008-03-08
Install it using "Add/Remove Programs" or "Synaptic"

In Xubuntu it is installed in the Network Menu.
You can always run it by opening a terminal and typing ```
dillo
``` !!!!!!

---

### Post by Indy452 on 2008-03-08
I checked in Add/Remove but its not there. I know Epiphany is there as well as Opera but no Dillo.

I would use Epiphany but is it as simple and fast as Dillo? I've never used Epiphany is it any good?

Neal

---

### Post by unutbu on 2008-03-08
```

sudo apt-get install dillo

```

---

### Post by steveneddy on 2008-03-08
> **Indy452 said:**
> How do I go about getting Dillo the simple browser in Ubuntu?

And if I get it will it be located in the internet tab?

I'm using Ubuntu 7.1

Thank you.

Neal

You know about synaptic, right?

System --> Administration --> Synaptic Package Manager

It gives you a list of all available software for you to download.

You can browse the software and applications. Click the list and start typing the word you are looking for.

---

### Post by jeffus_il on 2008-03-08
Go with a standard browser like firefox or epiphany, Dillo is cute, tiny and fast, but won't give you java, flash and many other extras. It's also under development so there won't be support either. If it interests you have a look at it, it's tiny and it downloads and installs in a "millisecond", if you want to help and like to program in C ....

---

### Post by Indy452 on 2008-03-08
> **jeffus_il said:**
> Go with a standard browser like firefox or epiphany, Dillo is cute, tiny and fast, but won't give you java, flash and many other extras. It's also under development so there won't be support either. If it interests you have a look at it, it's tiny and it downloads and installs in a "millisecond", if you want to help and like to program in C ....

If I want to help and program in C.......??  I'm sorry I don't understand what "C" is.


I use firefox as my default browser but I like the Dillo for speedy browsing of forums etc. I don't need too much java in forums. No big loss to me.

I have dillo now but I lost the controls does anyone know how I can get them back?

I would like to edit the configuration of how dillo is setup but I somehow lost the control that says "F" or "V".

Neal

---

### Post by jeffus_il on 2008-03-08
The program Dillo is still under development, they are looking for programmers to help out. Dillo is written in a computer language called "C".
The "F" seems to be what is usually the "File" menu in other programs, maybe the decided on "F" to keep it smaller and save space, I guess. The "V", I don't know where they got it from, but it gives you movement back and forward thru multiple tabs, the optional keys are also shown there which may be more convenient, and has the program's options, Seems a nice little program "Dillo", Enjoy it. where did you hear about it?

---

### Post by Indy452 on 2008-03-09
> **jeffus_il said:**
> The program Dillo is still under development, they are looking for programmers to help out. Dillo is written in a computer language called "C".
The "F" seems to be what is usually the "File" menu in other programs, maybe the decided on "F" to keep it smaller and save space, I guess. The "V", I don't know where they got it from, but it gives you movement back and forward thru multiple tabs, the optional keys are also shown there which may be more convenient, and has the program's options, Seems a nice little program "Dillo", Enjoy it. where did you hear about it?

I discovered it using a DSL live cd to run in my windows computer at work! (Shhh don't tell the boss!):)

Thanks for the help Jeffus.:KS

I got help from another forum earlier today and have my dillo back. I'm a simple guy who likes speed so dillo is right up my alley. I'll be using it off and on for quite a while I think.

Neal

---

### Post by David Andersson on 2008-03-09
> I have dillo now but I lost the controls does anyone know how I can get them back?

Dillo has a feature to **hide toolbars** to use maximum space for the web page. Press the icon in the **lower right corner** to toggle this feature, or **double click** anywhere on the page (not on a link). This should give you the toolbars back.

About the "F" and "V". These means "File" and "View". Click "V" and "Options" to get a preference dialog. In the Interface tab, change "**Panel size**" from "tiny" to "**small**". Then restart dillo and the user interface makes a bit more sense. You'll see File and View instead of F and V, amongst other things. (You may then also have to update "Window Size" in the same tab to something larger than 1x1, eg 700x700. Strange defaults...)

If you get tired of the default fonts, go to the View > Options > Font tab and change the vw font to "Bitstream Vera Serif" or "FreeSerif" or whatever you like, and the fv font to "Bitstream Vera Sans Mono" or "FreeMono" or whatever. (You may then also have to update Font Factor from 0.1 to 1.0. Strange defaults...)

---

