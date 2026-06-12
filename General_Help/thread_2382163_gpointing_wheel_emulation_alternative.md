---
title: "gpointing wheel emulation alternative?"
date: 2018-01-09
forum: General Help
---

### Post by thatguymark on 2018-01-09
I installed gpointing device settings via the Software Center in 14.04.5 and the wheel emulation for a Kensington Orbit trackball 64327 worked inconsistently, the last time I booted up the system I could not get it to work. The reviews for gpointing seem to indicate it is buggy. Is there any alternative? I simply want to be able to hold down the second button and use the trackball to scroll.

---

### Post by dragonfly41 on 2018-01-10
There is a package named **Actiona** in Software Centre which I use to emulate key presses and other automation actions.

It might be installed by default under Accessories.

Looking at the Device > Key action it should do what you want.
One Key Press action to hold down a prescribed key.
Do your scrolling.
Then some hot key to break the Key Press action..
Then a Key Release action to release the prescribed key.

---

### Post by thatguymark on 2018-01-10
> **dragonfly41 said:**
> There is a package named **Actiona** in Software Centre which I use to emulate key presses and other automation actions.

It might be installed by default under Accessories.

Looking at the Device > Key action it should do what you want.
One Key Press action to hold down a prescribed key.
Do your scrolling.
Then some hot key to break the Key Press action..
Then a Key Release action to release the prescribed key.

Thanks, I see there is a wheel emulation under Device already, but I can't find any way of executing it other than the toolbar button or the context menu there, when I use Ctrl-Space or Ctrl-Alt-Space as labeled in the context menu it doesn't work...

---

### Post by dragonfly41 on 2018-01-11
I have no personal experience with the device > wheel action.
You can refer to the wiki page here ...

[https://wiki.actiona.tools/doku.php?id=en:actions:actionwheel](https://wiki.actiona.tools/doku.php?id=en:actions:actionwheel)

There is also the forum ...

[https://www.jmgr.net/forum/](https://www.jmgr.net/forum/)

Note that most of the dialogue is in the French community.

The documentation is sparse and you need to dig around to learn how to apply this tool.
But it can be useful.

[COLOR=#b22222][Later edit][/COLOR]

Other options are to automate Arrow Up. Arrow Down, Arrow Left, Arrow Right to emulate trackball vectors.

There are also PgUp and PgDn, Home and End to use by binding scrolling emulation to some events.


[COLOR=#b22222][Reading Further][/COLOR]

As an alternative to exploring Actiona you can try xinput.

Run this command to probe your device

```
xinput --list
```

and then using the listed id from the above explore properties

```
xinput list-props <id>
```

For example here is my Dell mouse.

```

xinput --list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PixArt Dell MS116 USB Optical Mouse     	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Dell KB216 Wired Keyboard               	id=11	[slave  keyboard (3)]
    &#8627; Dell KB216 Wired Keyboard               	id=12	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=13	[slave  keyboard (3)]

```

And then I explored id=10

```
xinput list-props 10
```

Read tips here ... 

[https://unix.stackexchange.com/questions/101867/make-mouse-movements-scroll-when-the-middle-button-is-held-down?noredirect=1&lq=1](https://unix.stackexchange.com/questions/101867/make-mouse-movements-scroll-when-the-middle-button-is-held-down?noredirect=1&lq=1)

---

