---
title: "Midnight Commander"
date: 2008-06-07
forum: General Help
---

### Post by Barmaleychik on 2008-06-07
I just installed Midnight Commander but I can not find how can I launch it! It did nit show up in any folder of applications, systems etc. Where is it?

---

### Post by brian_p on 2008-06-07
> **Barmaleychik said:**
> I just installed Midnight Commander but I can not find how can I launch it! It did nit show up in any folder of applications, systems etc. Where is it?

I don't know where it is but

```
mc
```

in a terminal will get it out of bed in all its glory.

---

### Post by rbmorse on 2008-06-08
or you can do 

sudo mc

to give it root permissions. Very handy, when you need it.

---

### Post by Barmaleychik on 2008-06-08
Thank you guys, it works!

Is there a way to make it launchable just by clicking mouse?

---

### Post by Grishka on 2008-06-08
> **Barmaleychik said:**
> Thank you buys, it works!

Is there a way to make it launchable just by clicking mouse?

mc is a command-line program, so can only run it from the terminal. I guess it should be possible to make a launcher for a terminal running mc, but I suggest you use the graphical equivalents: gnome-commander or krusader.

---

### Post by rbmorse on 2008-06-08
right click in the top panel. 

select "add to panel"

double click "custom application launcher"

In the "type" pulldown select "application in terminal"

Put Midnight Commander in the "name" box

put mc in the "Command" box or sudo mc if you want to start mc with root permissions

Click OK

Clicking on the launcher in the panel will start MC. 

note: if you want the launcher to have the mc icon instead of the default springboard icon, just enter "mc"  (without the quote marks) into the command box. Once the mc icon appears in the launcher setup box you can change the command box to sudo mc if you want mc to have root permissions.

---

### Post by y-lee on 2008-06-29
Barmaleychik

You say in [another post ]("http://ubuntuforums.org/showpost.php?p=5287948&postcount=1")

> Midnight commander icon while is beautifully sitting on my desktop is not functional,

So evidently you have created an launcher on your desktop successfully but it is not functional. What exactly is the problem, I don't understand. :confused: 

You have not responded here to let any of us know of your problem and yet you are frustrated at a lack of help in another thread. The advice rbmorse has given you regarding creating a launcher for mc should have worked. It works for me.

---

### Post by Barmaleychik on 2008-06-30
I created a launcher for Midnight commander. That gave me two icons one on the very top bat next to Firefox and one on the desktop. Both icons have a blue design Norten Commander style. If I click on them nothing happens :(

If I type mc at the DOS prompt (I should say Linux prompt) it started the program.

I was also told that MC is a command line program and I do not need an icon to start it. I do not understand it. 

Gnome Commander works without problem but MC design looks more similar to Total Commander. What are differences between then?

Thank you in advance.

P.S. If you have some solution for my VmWare problem or USB Microphone it would be great!

---

