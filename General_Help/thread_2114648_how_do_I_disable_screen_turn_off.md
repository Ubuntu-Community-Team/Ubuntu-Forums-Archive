---
title: "how do I disable screen turn off"
date: 2013-02-10
forum: General Help
---

### Post by rhythmiccycle on 2013-02-10
I recently re-installed Ubuntu on to my laptop, and the screen turns off about every 10min, and I have to shake the mouse to get it back on. 

I set all the options to "never" turn off, but it still turns off. 
I also goggled the problem, and tried some things in the terminal, but nothing works.

I use that computer mainly to watch movies, and its very annoying to have to shake the mouse every 10 min.


please help.

---

### Post by rhythmiccycle on 2013-02-11
can anyone help?

---

### Post by c2tarun on 2013-02-11
> **rhythmiccycle said:**
> I recently re-installed Ubuntu on to my laptop, and the screen turns off about every 10min, and I have to shake the mouse to get it back on. 

I set all the options to "never" turn off, but it still turns off. 
I also goggled the problem, and tried some things in the terminal, but nothing works.

I use that computer mainly to watch movies, and its very annoying to have to shake the mouse every 10 min.


please help.

Can you please post the output of following: 

```
xset -p
```

---

### Post by guardian59 on 2013-02-11
tuve el mismo problema y un amigo lo soluciono al toque, a ver que tal te va a ti. abres la terminal y escribe sudo xset s off    te va a pedir tu pssw  y listo , no vas a tener ninguna  repuesta pero vas  a ver que ya no se pone la pantalla negra , suerte a mi me funciono

---

### Post by guardian59 on 2013-02-11
xset  s  off

---

### Post by guardian59 on 2013-02-11
xset  espacio  s  espacio  off

---

### Post by rhythmiccycle on 2013-02-11
> **c2tarun said:**
> Can you please post the output of following: 

```
xset -p
```

```

$ xset -p
xset:  unknown option -p

usage:  xset [-display host:dpy] option ...
    To turn bell off:
	-b                b off               b 0
    To set bell volume, pitch and duration:
	 b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
	-bc
    To enable bug compatibility mode:
	bc
    To turn keyclick off:
	-c                c off               c 0
    To set keyclick volume:
	 c [0-100]        c on
    To control Energy Star (DPMS) features:
	-dpms      Energy Star features off
	+dpms      Energy Star features on
	 dpms [standby [suspend [off]]]     
	      force standby 
	      force suspend 
	      force off 
	      force on 
	      (also implicitly enables DPMS features) 
	      a timeout value of zero disables the mode 
    To set the font path:
	 fp= path[,path...]
    To restore the default font path:
	 fp default
    To have the server reread font databases:
	 fp rehash
    To remove elements from font path:
	-fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
	+fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
	-led [1-32]         led off
	 led [1-32]         led on
	-led named 'name'   led off
	 led named 'name'   led on
    To set mouse acceleration and threshold:
	 m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
	 p pixel_value color_name
    To turn auto-repeat off or on:
	-r [keycode]        r off
	 r [keycode]        r on
	 r rate [delay [rate]]
    For screen-saver control:
	 s [timeout [cycle]]  s default    s on
	 s blank              s noblank    s off
	 s expose             s noexpose
	 s activate           s reset
    For status information:  q


```

---

### Post by rhythmiccycle on 2013-02-11
Thanks for the reply guardian59, but I only speak English.

---

### Post by c2tarun on 2013-02-12
> **rhythmiccycle said:**
> ```

$ xset -p
xset:  unknown option -p
 
usage:  xset [-display host:dpy] option ...
    To turn bell off:
    -b                b off               b 0
    To set bell volume, pitch and duration:
     b [vol [pitch [dur]]]          b on
    To disable bug compatibility mode:
    -bc
    To enable bug compatibility mode:
    bc
    To turn keyclick off:
    -c                c off               c 0
    To set keyclick volume:
     c [0-100]        c on
    To control Energy Star (DPMS) features:
    -dpms      Energy Star features off
    +dpms      Energy Star features on
     dpms [standby [suspend [off]]]     
          force standby 
          force suspend 
          force off 
          force on 
          (also implicitly enables DPMS features) 
          a timeout value of zero disables the mode 
    To set the font path:
     fp= path[,path...]
    To restore the default font path:
     fp default
    To have the server reread font databases:
     fp rehash
    To remove elements from font path:
    -fp path[,path...]  fp- path[,path...]
    To prepend or append elements to font path:
    +fp path[,path...]  fp+ path[,path...]
    To set LED states off or on:
    -led [1-32]         led off
     led [1-32]         led on
    -led named 'name'   led off
     led named 'name'   led on
    To set mouse acceleration and threshold:
     m [acc_mult[/acc_div] [thr]]    m default
    To set pixel colors:
     p pixel_value color_name
    To turn auto-repeat off or on:
    -r [keycode]        r off
     r [keycode]        r on
     r rate [delay [rate]]
    For screen-saver control:
     s [timeout [cycle]]  s default    s on
     s blank              s noblank    s off
     s expose             s noexpose
     s activate           s reset
    For status information:  q
 

```
 
This is not the output I was expecting but its my mistake :)
 
Anyway try running:
 
```
 
xset -dpms

```
 
I think this will solve your problem

---

