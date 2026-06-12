---
title: "Help Needed: Gdebi Package installer doesn't work (gutsy 7.10)"
date: 2008-05-03
forum: General Help
---

### Post by the guitarist on 2008-05-03
hello everyone,

suddenly my ubuntu gutsy isn't able to install any .deb packages with the default package installer (Gdebi package installer)!!...whenever i double click on a .deb file nothing happens at all.

---

### Post by macaholic on 2008-05-03
Could you possibly elaborate more? Also, what happens when you run gdebi-gtk in a terminal?
Tip: you can always install packages in terminal by running:```
sudo dpkg -i /path/to/package
```

---

### Post by mac9416 on 2008-05-03
I use dpkg with the terminal. Use **only if you have experience using the command line**.
If you're feeling adventurous here's how you install using dpkg:
[LIST=1]
[*]Go to Applications>Accessories>Terminal
[*]Type "cd /home/YOURNAME/" (assuming your package is in your Home directory)
[*]Type "dpkg -i YOURPACKAGE.deb"
[/LIST]

The rest should go smoothly.

Good luck!

---

### Post by the guitarist on 2008-05-03
> **macaholic said:**
> Could you possibly elaborate more? Also, what happens when you run gdebi-gtk in a terminal?
Tip: you can always install packages in terminal by running:```
sudo dpkg -i /path/to/package
```

it runs smoothly.. but i want to go back using the graphical oackage installer it's much easier and i'm still a linux newbie.

so what can i do ?

---

### Post by the guitarist on 2008-05-03
thaaanx everyone... but i solved the problem..i just re-installed the Gdebi package installer through synaptic..and it worked like a charm ..

---

